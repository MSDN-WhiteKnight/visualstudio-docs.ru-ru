---
title: Пошаговое руководство. С помощью файла конфигурации для определения источника данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f078d8a15cbef4c2f17b154af13a997b77da8766
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695062"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Пошаговое руководство. Использование файла конфигурации для определения источника данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В данном пошаговом руководстве демонстрируется использование источника данных, определенного в файле app.config, для модульного тестирования. Вы узнаете, как создать файл app.config, определяющий источник данных, который может использоваться классом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>. В данном пошаговом руководстве представлены следующие задачи:  
  
- создание файла app.config;  
  
- определение настраиваемого раздела конфигурации;  
  
- определение строк подключения;  
  
- определение источников данных;  
  
- доступ к источникам данных с помощью класса <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
- Visual Studio Enterprise  
  
- Microsoft Access или Microsoft Excel для предоставления данных хотя бы для одного из методов теста;  
  
- решение Visual Studio, содержащее тестовый проект.  
  
## <a name="create-the-appconfig-file"></a>Создание файла app.config  
  
#### <a name="to-add-an-appconfig-file-to-the-project"></a>Добавьте к проекту следующий файл app.config.  
  
1. Если файл app.config уже существует в тестовом проекте, переходите к разделу [Определение настраиваемого раздела конфигурации](#DefineCustomConfigurationSection).  
  
2. Щелкните проект правой кнопкой мыши в окне **обозревателя решений**, наведите указатель на пункт **Добавить** и выберите **Новый элемент**.  
  
     Откроется окно **Добавление нового элемента**.  
  
3. Выберите шаблон **Файл конфигурации приложения** и нажмите кнопку **Добавить**.  
  
## <a name="DefineCustomConfigurationSection"></a> Определение настраиваемого раздела конфигурации  
 Просмотрите файл app.config. Он содержит как минимум объявление XML и корневой элемент.  
  
#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Добавление настраиваемого раздела конфигурации в файл app.config  
  
1. Корневым элементом файла app.config должен быть элемент `configuration`. Создайте элемент `configSections` в элементе `configuration`. `configSections` должен быть первым элементом в файле app.config.  
  
2. В элементе `configSections` создайте элемент `section`.  
  
3. В элементе `section` добавьте атрибут с именем `name` и задайте для него значение `microsoft.visualstudio.testtools`. Добавьте еще один атрибут с именем `type` и задайте для него значение `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`.  
  
   Элемент `section` должен выглядеть примерно следующим образом.  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
> Имя сборки должно соответствовать сборке .NET Framework Microsoft Visual Studio, которую вы используете. При использовании .NET Framework 3.5 Visual Studio задайте в качестве значения версии 9.0.0.0. Если вы используете .NET Framework 2.0 Visual Studio, задайте версию 8.0.0.0.  
  
## <a name="define-connection-strings"></a>Определение строк подключения  
 Строки подключения определяют сведения, относящиеся к конкретному поставщику, для доступа к источникам данных. Строки подключения, определенные в файлах конфигурации, предоставляют сведения о поставщике данных для повторного использования в приложении. В этом разделе создайте две строки подключения, которые будут использоваться источниками данных, определенными в настраиваемом разделе конфигурации.  
  
#### <a name="to-define-connection-strings"></a>Определение строк подключения  
  
1. После элемента `configSections` создайте элемент `connectionStrings`.  
  
2. В элементе `connectionStrings` создайте два элемента `add`.  
  
3. В первом элементе `add` создайте следующие атрибуты и значения для подключения к базе данных Microsoft Access.  
  
|Атрибут|Значения|  
|---------------|------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 Во втором элементе `add` создайте следующие атрибуты и значения для подключения к таблице Microsoft Excel.  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 Элемент `connectionStrings` должен выглядеть примерно следующим образом.  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## <a name="define-data-sources"></a>Определение источников данных  
 Раздел источников данных содержит четыре атрибута, которые используются тестовой подсистемой для получения данных из источника данных.  
  
- `name` определяет удостоверение, используемое <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> для указания источника данных для использования.  
  
- `connectionString` определяет строку подключения, созданную в предыдущем разделе "Определение строк подключения".  
  
- `dataTableName` определяет таблицу или лист, которые содержат данные, используемые в тесте.  
  
- `dataAccessMethod` определяет способ доступа к значениям данных в источнике данных.  
  
  В этом разделе мы определим два источника данных для использования в модульном тесте.  
  
#### <a name="to-define-data-sources"></a>Определение источников данных  
  
1. После элемента `connectionStrings` создайте элемент `microsoft.visualstudio.testtools`. Этот раздел файла был создан в разделе "Определение настраиваемого раздела конфигурации".  
  
2. В элементе `microsoft.visualstudio.testtools` создайте элемент `dataSources`.  
  
3. В элементе `dataSources` создайте два элемента `add`.  
  
4. В первом элементе `add` создайте следующие атрибуты и значения для источника данных Microsoft Access.  
  
|Атрибут|Значения|  
|---------------|------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 Во втором элементе `add` создайте следующие атрибуты и значения для источника данных Microsoft Excel.  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 Элемент `microsoft.visualstudio.testtools` должен выглядеть примерно следующим образом.  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 Окончательный файл app.config должен выглядеть примерно следующим образом.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>   
    </configSections>  
    <connectionStrings>  
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
    </connectionStrings>  
    <microsoft.visualstudio.testtools>  
        <dataSources>  
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
        </dataSources>  
    </microsoft.visualstudio.testtools>  
</configuration>  
```  
  
## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Создание модульного теста с помощью источников данных, определенных в файле app.config  
 Определив файл app.config, мы создадим модульный тест, использующий данные, находящиеся в источниках данных, которые определены в файле app.config. В этом разделе мы рассмотрим:  
  
- создание источников данных, определенных в файле app.config;  
  
- использование источников данных в двух методах теста, сравнивающих значения в каждом источнике данных.  
  
#### <a name="to-create-a-microsoft-access-data-source"></a>Создание источника данных Microsoft Access  
  
1. Создайте файл базы данных Microsoft Access с именем `testdatasource.accdb`.  
  
2. Создайте таблицу с именем `MyDataTable` в `testdatasource.accdb`.  
  
3. Создайте два поля в таблице `MyDataTable` с именем `Arg1` и `Arg2`, используя тип данных `Number`.  
  
4. Добавьте пять сущностей в таблицу `MyDataTable` со следующими значениями для `Arg1` и `Arg2` соответственно: (10,50), (3,2), (6,0), (0,8) и (12312,1000).  
  
5. Сохраните и закройте базу данных.  
  
6. Измените строку подключения так, чтобы она указывала на расположение базы данных. Измените значение `Data Source` так, чтобы оно отражало расположение базы данных.  
  
#### <a name="to-create-a-microsoft-excel-data-source"></a>Создание источника данных Microsoft Excel  
  
1. Создайте электронную таблицу Microsoft Excel с именем `data.xlsx`.  
  
2. Создайте лист с именем `Sheet1`, если он еще не существует в `data.xlsx`.  
  
3. Создайте на листе `Sheet1` два заголовка столбцов и назовите их `Val1` и `Val2`.  
  
4. Добавьте пять сущностей в таблицу `Sheet1` со следующими значениями для `Val1` и `Val2` соответственно: (1,1), (2,2), (3,3), (4,4) и (5,0).  
  
5. Сохраните и закройте таблицу.  
  
6. Измените строку подключения так, чтобы она указывала на расположение таблицы. Измените значение `dbq` так, чтобы оно отражало расположение таблицы.  
  
#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Создание модульного теста с помощью источников данных файла app.config  
  
1. Добавьте модульный тест в тестовый проект.  
  
     Дополнительные сведения см. в разделе [Создание и запуск модульных тестов для существующего кода](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2. Замените автоматически созданное содержимое модульного теста следующим кодом.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
    namespace TestProject1  
    {  
         [TestClass]  
        public class UnitTest1  
        {  
            private TestContext context;  
  
            public TestContext TestContext  
            {  
                get { return context; }  
                set { context = value; }  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]  
            [DataSource("MyJetDataSource")]  
            public void MyTestMethod()  
            {  
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());  
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());  
                Assert.AreNotEqual(a, b, "A value was equal.");  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\data.xlsx")]  
            [DataSource("MyExcelDataSource")]  
            public void MyTestMethod2()  
            {  
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);  
            }  
        }  
    }  
    ```  
  
3. Проверьте атрибуты DataSource. Обратите внимание на имена параметров из файла app.config.  
  
4. Выполните построение решения и запустите тесты MyTestMethod и MyTestMethod2.  
  
> [!IMPORTANT]
> Разверните элементы как источники данных, чтобы они были доступны для теста в каталоге развертывания.  
  
## <a name="see-also"></a>См. также  
 [Модульное тестирование кода](../test/unit-test-your-code.md)   
 [Создание и запуск модульных тестов для существующего кода](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Тестирование приложения](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Практическое руководство. Создание модульного теста на основе данных](../test/how-to-create-a-data-driven-unit-test.md)
