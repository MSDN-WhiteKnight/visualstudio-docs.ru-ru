---
title: Пользовательский интерфейс свойств проекта | Документация Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86b3ebb0c931cec5dac40a980ba261c236307fe7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328268"
---
# <a name="project-property-user-interface"></a>Пользовательский интерфейс свойств проекта

Подтип проекта можно использовать элементы в проекте **страницы свойств** диалоговое окно, так как они предоставляются по базовому проекту, скрыть или сделать доступным только для чтения элементы управления и целые страницы, передаваемой или добавьте страницы подтипа проекта **Страницы свойств** диалоговое окно.

## <a name="extending-the-project-property-dialog-box"></a>Расширение диалоговое окно свойств проекта

Подтипа проекта реализует расширителей автоматизации и Обзор объектов конфигурации проекта. Эти расширения реализуют <xref:EnvDTE.IFilterProperties> интерфейс, чтобы сделать определенным свойствам скрытого или только для чтения. **Страницы свойств** диалоговое окно базового проекта, реализованный в базовый проект, учитывает фильтрации выполняемых расширителей автоматизации.

Процесс расширения **свойство проекта** описывается диалоговое окно ниже:

- Базовый проект получает расширителей из подтипа проекта путем реализации <xref:EnvDTE80.IInternalExtenderProvider> интерфейс. Обзор автоматизации проектов и объектов обзора конфигурации проекта базового проекта все реализация этого интерфейса.

- Реализация <xref:EnvDTE80.IInternalExtenderProvider> для объекта Просмотр проекта и объект автоматизации project делегировать <xref:EnvDTE80.IInternalExtenderProvider> реализации агрегатора подтип проекта (то есть они `QueryInterface` для <xref:EnvDTE80.IInternalExtenderProvider> на <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объект проекта).

- Объект обзора конфигурации базового проекта также реализует <xref:EnvDTE80.IInternalExtenderProvider> для подключения непосредственно в автоматизированного расширителя из объект конфигурации подтипа проекта. Его реализация делегирует <xref:EnvDTE80.IInternalExtenderProvider> интерфейс, реализованный на статистическую функцию подтип проекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, реализованный объект обзора конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, тоже реализован объект обзора конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объекта.

- Подтип проекта можно определить соответствующие идентификаторы CATID для различных объектов являются расширяемыми базового проекта во время выполнения путем извлечения следующие <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> значения:

    - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

    - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

    - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Чтобы определить CATID для проекта области, подтипа проекта извлекает выше свойства [VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) из `VSITEMID typedef`. Подтип проекта также может потребоваться указать, какие **страницы свойств** страницах диалогового окна отображаются для проекта, зависящие от конфигурации и конфигурации независимо. Некоторые подтипов проекта может потребоваться удалить встроенные страницы и добавить определенные страницы подтип проекта. Для этого проекта управляемый клиент вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> метод для следующих свойств:

- `VSHPROPID_PropertyPagesCLSIDList` — Список разделенных точкой с запятой значений CLSID страниц свойств, независимых от конфигурации.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` Список разделенных точкой с запятой значений CLSID страниц свойств, зависимых от конфигурации.

Так как статистические выражения подтипа проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта, его можно переопределить эти свойства контроля, позволяющий определить **страницы свойств** диалоговое окно. Подтип проекта можно получить из внутреннего базового проекта эти свойства и затем добавить или удалить CLSID при необходимости.

Новые страницы свойств, добавленные подтипом проекта, передаются в объект обзора конфигурации проекта от реализации базового проекта. Этот объект обзора конфигурации проекта поддерживает расширителей автоматизации. Дополнительные сведения о AutomationExtenders, см. в разделе [реализация и использование расширителей автоматизации](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). На страницах свойств, реализуемый вызов подтип проекта <xref:EnvDTE.Project.Extender%2A> извлекаемого собственные объект конфигурации подтипа проекта обзора, расширяющий объект обзора конфигурации базового проекта.

## <a name="see-also"></a>См. также

- <xref:EnvDTE.IFilterProperties>
- [Диалоговое окно страниц свойств](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))