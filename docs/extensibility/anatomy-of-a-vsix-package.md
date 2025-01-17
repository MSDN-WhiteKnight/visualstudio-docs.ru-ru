---
title: Составляющие пакета VSIX | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8f0b748e80726d69e5b826982596a0a32675bd7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352279"
---
# <a name="anatomy-of-a-vsix-package"></a>Составляющие пакета VSIX
Пакет VSIX является *.vsix* файл, содержащий одно или несколько расширений Visual Studio вместе с метаданными Visual Studio использует для классификации и установить расширения. Эти метаданные содержатся в манифесте VSIX и *[Content_Types] .xml* файл. Пакет VSIX также может содержать один или несколько *Extension.vsixlangpack* файлы для обеспечения локализованный текст программы установки и может содержать дополнительные пакеты VSIX для установки зависимостей.

 Формат пакета VSIX соответствует стандарту Open Packaging Conventions (OPC). Пакет содержит двоичные файлы и вспомогательные файлы, вместе с *[Content_Types] .xml* файл и *.vsix* файл манифеста. Один пакет VSIX может содержать выходные данные из нескольких проектов или даже несколькими пакетами, которые имеют свои собственные манифестов.

> [!NOTE]
> Имена файлов, включенных в пакетах VSIX не должны содержать пробелы, а также символы, которые зарезервированы в универсальных кодов ресурса (URI), как определенные в разделе [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).

## <a name="the-vsix-manifest"></a>Манифест VSIX
 Манифест VSIX содержит сведения о расширения должны быть установлены и соответствует схеме VSX. Дополнительные сведения см. в разделе [Справочник по схеме 1.0 расширение VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Пример манифеста VSIX, см. в разделе [элемент PackageManifest (корневой элемент, Схема VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 Должен иметь имя манифеста VSIX `extension.vsixmanifest` при включении в ^ файл .vsix *.

## <a name="the-content"></a>Содержимое
 Пакет VSIX может содержать шаблоны, элементы панели инструментов, пакеты VSPackage или любого другого расширения, поддерживаемый Visual Studio.

## <a name="language-packs"></a>Языковые пакеты
 Пакет VSIX может содержать один или несколько *Extension.vsixlangpack* файлов для предоставления локализованного текста во время установки. Дополнительные сведения см. в разделе [пакетов VSIX локализация](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Зависимости и ссылки
 Пакет VSIX может содержать другие пакеты VSIX как ссылки. Каждый из этих пакетов необходимо включить собственный манифест VSIX.

 Если пользователь пытается установить расширение, которое имеет зависимости, то установщик проверяет, что необходимые сборки установлены в системе пользователя. Если необходимые сборки не найдены, **расширения и обновления** отображает список сборок, отсутствует.

 Если манифест расширения включает один или несколько [ссылку](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) элементов, **расширения и обновления** сравнивает манифесте каждой ссылки в расширения, установленные в системе и устанавливает ссылки на расширения, если они еще не установлены. Если установлена более ранняя версия модуля, на который указывает ссылка, новая версия заменяет его.

 Если проект в решении нескольких проектов содержит ссылку на другой проект в том же решении, пакет VSIX содержит зависящие от этого проекта. Это поведение можно переопределить, выбрав ссылку для внутреннего проекта, а затем в **свойства** окно, задание **выходной группы включены в VSIX** свойства `BuiltProjectOutputGroup`.

 Чтобы включить вспомогательные библиотеки DLL из указанных сборок в пакете VSIX, добавьте `SatelliteDllsProjectOutputGroup` для **выходной группы включены в VSIX** свойство.

## <a name="installation-location"></a>Расположение установки
 Во время установки **расширения и обновления** ищет содержимое пакета VSIX, расположенный в узле *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 По умолчанию установки применяется только для текущего пользователя, так как *% LocalAppData %* является каталогом конкретного пользователя. Тем не менее если задать [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) манифеста для `True`, расширение будет установлено в <em>... \\</em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> и будут доступны для всех пользователей компьютера.

## <a name="contenttypesxml"></a>[Content_Types].xml
 *[Content_Types] .xml* файл определяет типы файлов в развернутом представлении *.vsix* файл. Visual Studio использует этот файл во время установки пакета, но не устанавливает сам файл. Дополнительные сведения об этом файле см. в разделе [структура файл [Content_types] .xml](the-structure-of-the-content-types-dot-xml-file.md).

 Объект *[Content_Types] .xml* файл необходим в стандарте Open Packaging Conventions (OPC). Дополнительные сведения об OPC см. в разделе [OPC: Новый стандарт упаковки данных](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) на сайте MSDN.