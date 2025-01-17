---
title: Практическое руководство. Предоставить контекст для редакторов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc482050422a9481bddc2902832376fa9dc0c29a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325381"
---
# <a name="how-to-provide-context-for-editors"></a>Практическое руководство. Предоставить контекст для редакторов
Контекст редактора, активен только в том случае, когда редактор имеет фокус, или имевшему непосредственно перед фокус был перемещен в окно инструментов. Можно предоставить контекст для редактора, выполнив следующие задачи:

1. Создайте контейнер контекста.

2. Опубликуйте контейнер контекста идентификатора элемента выбора (идентификатор SEID).

3. Поддерживать контекст, в контейнере.

   Эти задачи, охватываются следующие процедуры. Дополнительные сведения о предоставлении контекста см. в разделе **надежные программирования** далее в этой статье.

## <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Чтобы создать контейнер контекста для редактор или конструктор

1. Вызовите `QueryService` на вашей <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс для <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> службы.

     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> возвращается интерфейс.

2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> метод, чтобы создать новый контейнер контекста или подконтекста.

     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> возвращается интерфейс.

3. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> метод для добавления атрибутов, ключевые слова для поиска, или **F1** ключевые слова в контейнер контекста или подконтекста.

4. При создании контейнера вложенного контекста, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> метод, чтобы связать контейнер вложенного контекста в контейнере родительского контекста.

5. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> для получения уведомления при **динамической справки** окно сейчас обновить.

     Наличие **динамической справки** окно вызов редактора готовности обновление дает возможность отложить изменение контекста, пока не происходит обновление. Это может повысить производительность, так как он позволяет отложить выполнения длительной алгоритмов, пока не станет доступна время простоя системы.

## <a name="to-publish-the-context-bag-to-the-seid"></a>Чтобы опубликовать контейнер контекста в идентификатор seid

1. Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> службу, чтобы вернуть указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> интерфейс.

2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, указав идентификатор элемента (`elementid` параметр) значение SEID_UserContext, чтобы указать, что вы передаете контекста на глобальном уровне.

3. Когда редактор или конструктор становится активным, значения в его <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> объекта передаются глобального выделения. Требуется только для завершения этого процесса, один раз за сеанс и как сохранить указатель на глобальном контексте, созданного при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.

## <a name="to-maintain-the-context-bag"></a>Чтобы сохранить контейнер контекста

1. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> чтобы убедиться, что **динамической справки** окно вызывает редактор или конструктор, перед обновлением.

     Для каждого контейнера контекста, которая называется <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> после контейнер контекста создается и реализовал <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, вызовы IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> для уведомления о поставщике контекста, что контейнер контекста будут обновлены. Этот вызов можно использовать для изменения атрибутов и ключевых слов в контейнере контекста, а также в любой подконтекстов перед **динамической справки** происходит обновление окна.

2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> на контейнер контекста для указания, что редактор или конструктор имеет новый контекст.

     При **динамической справки** вызовы в окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> чтобы указать, что он обновляется, редактора или конструктора в это время можно обновить контекст соответствующим образом для любой подконтекстов и родительским контейнером контекста.

    > [!NOTE]
    > `SetDirty` Флаг автоматически присваивается `true` каждый раз, когда добавляется или удаляется из контейнера контекстов контекста. **Динамической справки** окно вызывает только <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> на контейнер контекста при `SetDirty` флаг имеет значение `true`. Он сбрасывается до `false` после обновления.

3. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> Чтобы добавить контекст в активном контексте коллекцию или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> удаляемый контекст.

## <a name="robust-programming"></a>Отказоустойчивость
 Если вы создаете собственный редактор, необходимо выполнить все три процедуры, описанные в этой статье, чтобы предоставить контекст для редактора.

> [!NOTE]
> Чтобы правильно активировать окно редактора или конструктора и убедитесь, что команда правильное обновление маршрутизации, необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> этот компонент, чтобы сделать его окну.

 Идентификатор SEID — это коллекция свойств, которые изменяются на основании выбора. Идентификатор SEID информация доступна через глобального выделения. Глобального выделения подключен в события, вызванные <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> интерфейс, и список всего содержимого, выбрал (текущий редактор, окно текущего средства, текущей иерархии и т. д.).

 Для редакторов и конструкторов в какой контекст может меняться всякий раз, когда курсор перемещается в word, неэффективно постоянного обновления контейнера контекста. Чтобы сделать обновление более эффективно любое время, определение курсора, перемещение в пределах окна редактора или конструктора, можно вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Благодаря этому удерживать изменения контекста, пока есть время простоя и IDE контекст службы отправляет уведомление в редактор или конструктор, **динамической справки** окно обновляется. Этот подход используется в **для поддержания контейнер контекста** процедуру в этой статье.

 После предоставления контекста для действий в свой редактор или конструктор, следует указать определенный **F1** ключевое слово, чтобы пользователи могли получить справку по редактора или конструктора, сам.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>