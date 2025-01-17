---
title: Составляющие пакета VSIX | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86c2beeab5fba0224fbdfb104d01ee5c28bba158
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699145"
---
# <a name="anatomy-of-a-vsix-package"></a>Составляющие пакета VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет VSIX является VSIX-файл, содержащий одно или несколько расширений Visual Studio вместе с метаданными, используемый для классификации и установить расширения Visual Studio. Эти метаданные содержатся в манифест VSIX и файл [Content_Types] .xml. Пакет VSIX также может содержать один или несколько файлов Extension.vsixlangpack для предоставления текста локализованной установки и может содержать дополнительные пакеты VSIX для установки зависимостей.  
  
 Формат пакета VSIX соответствует стандарту Open Packaging Conventions (OPC). Пакет содержит двоичные файлы и вспомогательные файлы, а также файл [Content_Types] .xml и .vsix файл манифеста. Один пакет VSIX может содержать выходные данные из нескольких проектов или даже несколькими пакетами, которые имеют свои собственные манифестов.  
  
> [!NOTE]
> Имена файлов, включенных в пакетах VSIX не должны содержать пробелы, а также символы, которые зарезервированы в универсальных кодов ресурса (URI), как определенные в разделе [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Манифест VSIX  
 Манифест VSIX содержит сведения о расширения должны быть установлены и соответствует схеме VSX. Дополнительные сведения см. в разделе [Справочник по схеме 1.0 VSIX расширения](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Пример манифеста VSIX, см. в разделе [элемент PackageManifest (корневой элемент, Схема VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Должен иметь имя манифеста VSIX `extension.vsixmanifest` когда он включен в VSIX-файл.  
  
## <a name="the-content"></a>Содержимое  
 Пакет VSIX может содержать шаблоны, элементы панели инструментов, пакеты VSPackage или любого другого расширения, поддерживаемый Visual Studio.  
  
## <a name="language-packs"></a>Языковые пакеты  
 Пакет VSIX может содержать один или несколько файлов Extension.vsixlangpack для предоставления локализованного текста во время установки. Дополнительные сведения см. в разделе [локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Зависимости и ссылки  
 Пакет VSIX может содержать другие пакеты VSIX как ссылки. Каждый из этих пакетов необходимо включить собственный манифест VSIX.  
  
 Если пользователь пытается установить расширение, которое имеет зависимости, то установщик проверяет, что необходимые сборки установлены в системе пользователя. Если необходимые сборки не найдены, **расширения и обновления** отображает список сборок, отсутствует.  
  
 Если манифест расширения включает один или несколько [ссылку](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) элементов, **расширения и обновления** сравнивает манифесте каждой ссылки в расширения, установленные в системе и устанавливает ссылки на расширения, если они еще не установлены. Если установлена более ранняя версия модуля, на который указывает ссылка, новая версия заменяет его.  
  
 Если проект в решении нескольких проектов содержит ссылку на другой проект в том же решении, пакет VSIX содержит зависящие от этого проекта. Это поведение можно переопределить, выбрав ссылку для внутреннего проекта, а затем в **свойства** окно, задание **выходной группы включены в VSIX** свойства `BuiltProjectOutputGroup`.  
  
 Чтобы включить вспомогательные библиотеки DLL из указанных сборок в пакете VSIX, добавьте `SatelliteDllsProjectOutputGroup` для **выходной группы включены в VSIX** свойство.  
  
## <a name="installation-location"></a>Расположение установки  
 Во время установки **расширения и обновления** ищет содержимое пакета VSIX в папке % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 По умолчанию установки применяется только к текущему пользователю, так как % LocalAppData % является каталогом конкретного пользователя. Тем не менее если задать [AllUsers](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) манифеста для `True`, расширение будет установлено в... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions и будут доступны для всех пользователей компьютера.  
  
## <a name="contenttypesxml"></a>[Content_Types].xml  
 Файл [Content_Types] .xml определяет типы файлов в развернутом VSIX-файл. Visual Studio использует этот файл во время установки пакета, но не устанавливает сам файл. Дополнительные сведения об этом файле см. в разделе [структура Content_types\].xml файл](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Файл [Content_Types] .xml требуется по Open Packaging Conventions (OPC) standard. Дополнительные сведения об OPC см. в разделе [OPC: Новый стандартный для упаковки Your данных](http://go.microsoft.com/fwlink/?LinkID=148207) на сайте MSDN.
