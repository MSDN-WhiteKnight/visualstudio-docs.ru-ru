---
title: Предоставляет контекст службы языка с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cdb7c2ff3d759581569d0f3681ce1b2f9cef39c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334425"
---
# <a name="provide-a-language-service-context-by-using-the-legacy-api"></a>Предоставить контекст службы языка с помощью предыдущих версий API
Существует два варианта для языковой службы для предоставления контекста пользователя с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базовый редактор: предоставьте текст маркера контекста, или передайте все контекста пользователя. Здесь описаны различия между ними.

 Дополнительные сведения о предоставлении контекста для языковой службы, которая подключена к собственного редактора см. в разделе [как: Предоставить контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md).

## <a name="provide-text-marker-context-to-the-editor"></a>Предоставить контекст маркеров текстовый редактор
 Для предоставления контекста для ошибки компилятора, обозначается меток текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] основной редактор, реализовывать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> интерфейс. В этом случае служба языка предоставляет контекст, только в том случае, когда курсор находится на текстовой метки. Это позволяет редактор для предоставления ключевое слово в позиции курсора для **динамической справки** окно без атрибутов.

## <a name="provide-all-user-context-to-the-editor"></a>Укажите все контекст пользователя в редактор
 Если вы создаете языковой службы и используете [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] основной редактор, а затем можно реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> интерфейс, чтобы предоставить контекст службы вашего языка.

 Для реализации `IVsLanguageContextProvider`, контекст (коллекция) присоединяется к редактора, который отвечает за обновление контейнер контекста. Когда **динамической справки** вызовы в окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> интерфейса на этот контейнер контекста во время простоя, контейнер контекста запрашивает редактор для обновления. Редактор затем уведомляет языковой службы, который необходимо обновить в редакторе и передает указатель на контейнер контекста. Это делается путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> метод из редактора для языковой службы. С помощью указателя на контейнер контекста, языковая служба теперь можно добавлять и удалять атрибуты и ключевые слова. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.

 Существует два разных способа реализации `IVsLanguageContextProvider`:

- Предоставляют ключевое слово в контекст

   При вызове редакторе обновить контейнер контекста передайте соответствующие ключевые слова и атрибуты и возвращается `S_OK`. Это возвращаемое значение указывает, что редактор для сохранения контекста ключевое слово и атрибут, а не предоставляют ключевое слово в позиции курсора в контекст.

- Получить ключевое слово из ключевого слова в позиции курсора

   Когда редактор вызывается обновить контейнер контекста, передать в соответствующие атрибуты и вернитесь `E_FAIL`. Это возвращаемое значение указывает, что редактор для сохранения атрибутов в контейнере контекста, но обновить контейнер контекста с ключевым словом в позиции курсора.

  На следующей диаграмме показано, как контекст предоставляется для языковой службы, которая реализует `IVsLanguageContextProvider`.

  ![График langserviceimplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2") контекст для языковой службы

  Как видно из диаграммы, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базовый текстовый редактор имеет контейнер контекста, подключенные к ней. Этот контейнер контекста указывает на три отдельные подконтекстов: языковой службы, используемый по умолчанию редактор и текстового маркера. Подконтекстов языковой службы и текст маркера содержат атрибуты и ключевые слова для языковой службы, если <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> реализации интерфейса и текстовые метки Если <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> реализации интерфейса. Если не реализовать любой из этих интерфейсов, редактор предоставляет контекст для ключевого слова в позиции курсора в редакторе контейнера вложенного контекста по умолчанию.

## <a name="context-guidelines-for-editors-and-designers"></a>Контекст, касающиеся редакторы и конструкторы
 Редакторы и конструкторы необходимо указать общее ключевое слово для окна редактора или конструктора. Это делается, чтобы раздел справки универсальный, но соответствующий, будет отображаться для конструктора или редактора, при нажатии клавиши **F1**. Редактор необходимо Кроме того, предоставить текущего ключевого слова в позиции курсора, либо указать основные термины, на основании текущего выбора. Это позволяет убедиться, что раздел справки для текста или элемента пользовательского интерфейса, на который указывает или выбранные отображает, когда пользователь нажимает **F1**. Конструктор предоставляет контекст для элемента, выбранного в конструкторе, например кнопки на форме. Редакторы и конструкторы необходимо также подключаться к службе языка как описано в [основные компоненты языковой службы прежних версий](../extensibility/internals/legacy-language-service-essentials.md).