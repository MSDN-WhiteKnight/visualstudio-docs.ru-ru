---
title: Вызов преобразования текста в расширении VS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bcd32aef240732b67a2c490e3738c9b3d2921ffc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698055"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Вызов преобразования текста в расширении VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы создаете [расширение Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14) такие как команды меню или [предметно ориентированного языка](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), службы текстовых шаблонов можно использовать для преобразования текстовых шаблонов. Получите службу типа <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> и выполните приведение к типу <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.  
  
## <a name="getting-the-text-templating-service"></a>Получение службы текстовых шаблонов  
  
```csharp  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
  
// Process a text template:  
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));  
  
```  
  
## <a name="passing-parameters-to-the-template"></a>Передача параметров в шаблоны  
 Параметры можно передавать в шаблон. Чтобы получить значения параметров в шаблоне, можно воспользоваться директивой `<#@parameter#>`.  
  
 Для этого типа параметра необходимо использовать сериализуемый или маршалируемый тип. Это значит, что тип должен объявляться с типом <xref:System.SerializableAttribute> или наследоваться от типа <xref:System.MarshalByRefObject>. Это ограничение является обязательным, потому что текстовый шаблон выполняется в отдельном домене приложения. Все встроенные типы, такие как **System.String** и **System.Int32** являются сериализуемыми.  
  
 Для передачи значений параметров вызывающий код может размещать значения либо в словаре `Session`, либо в типе <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 В следующем примере оба метода использованы для преобразования короткого тестового шаблона:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte;   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;  
  
// Create a Session in which to pass parameters:  
sessionHost.Session = sessionHost.CreateSession();  
sessionHost.Session["parameter1"] = "Hello";  
sessionHost.Session["parameter2"] = DateTime.Now;  
  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);  
  
// Process a text template:  
string result = t4.ProcessTemplate("",  
   // This is the test template:  
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"  
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"  
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"  
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");  
  
// This test code yields a result similar to the following line:  
//     Test: Hello    07/06/2010 12:37:45    42  
  
```  
  
## <a name="error-reporting-and-the-output-directive"></a>Отчеты об ошибках и директива Output  
 Любые ошибки, возникающие в процессе обработки, отображаются в окне ошибок [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Кроме того, чтобы настроить уведомления об ошибках, можно задать обратный вызов, реализующий <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.  
  
 Если необходимо записать строку результатов в файл, полезно знать, какие расширение файла и кодировка были заданы в директиве `<#@output#>` шаблона. Эти сведения также передаются обратному вызову. Дополнительные сведения см. в разделе [директива Output T4](../modeling/t4-output-directive.md).  
  
```csharp  
void ProcessMyTemplate(string MyTemplateFile)  
{  
  string templateContent = File.ReadAllText(MyTemplateFile);  
  T4Callback cb = new T4Callback();  
  // Process a text template:  
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);  
  // If there was an output directive in the MyTemplateFile,  
  // then cb.SetFileExtension() will have been called.  
  // Determine the output file name:  
  string resultFileName =   
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),   
        Path.GetFileNameWithoutExtension(MyTemplateFile))   
      + cb.fileExtension;  
  // Write the processed output to file:  
  File.WriteAllText(resultFileName, result, cb.outputEncoding);  
  // Append any error messages:  
  if (cb.errorMessages.Count > 0)  
  {  
    File.AppendAllLines(resultFileName, cb.errorMessages);  
  }  
}  
  
class T4Callback : ITextTemplatingCallback  
{  
  public List<string> errorMessages = new List<string>();  
  public string fileExtension = ".txt";  
  public Encoding outputEncoding = Encoding.UTF8;  
  
  public void ErrorCallback(bool warning, string message, int line, int column)  
  { errorMessages.Add(message); }  
  
  public void SetFileExtension(string extension)  
  { fileExtension = extension; }  
  
  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)  
  { outputEncoding = encoding; }  
}  
  
```  
  
 Код можно протестировать с использованием файла шаблона, аналогичного следующему:  
  
```  
<#@output extension=".htm" encoding="ASCII"#>  
<# int unused;  // Compiler warning "unused variable"  
#>  
Sample text.  
```  
  
 Предупреждение компилятора отображается в окне ошибок [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и создает вызов `ErrorCallback`.  
  
## <a name="reference-parameters"></a>Параметры ссылок  
 Можно передавать значения из текстового шаблона, используя класс параметров, наследуемый от <xref:System.MarshalByRefObject>.  
  
## <a name="related-topics"></a>См. также  
 Создание текста из предварительно обработанного текстового шаблона  
 Вызовите метод `TransformText()` сгенерированного класса. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Создание текста за пределами расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
 Определите пользовательское ведущее приложение. Дополнительные сведения см. в разделе [обработки текстовых шаблонов с помощью пользовательского хост-](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 Создание исходного кода с возможностью последующей компиляции и выполнения  
 Вызовите метод `t4.PreprocessTemplate()` типа <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.
