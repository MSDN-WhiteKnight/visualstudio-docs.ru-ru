---
title: Событий текстового буфера в интерфейсе API для прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6851d6f3cbf622794dbf817ec42d941c943add52
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316534"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Событий текстового буфера, старый API
Объект текстового буфера выдает несколько различных событий, которые позволяют реагировать на них различных ситуациях.

 Если вы используете старый API, должны реализовывать следующие интерфейсы для получения уведомления об изменениях в текстовый буфер. Разработка интерфейсов для буфера текста с помощью `IConnectionPointContainer` изменяется интерфейс в текстовом буфере, чтобы получать уведомления об строки из буфера. Дополнительные сведения см. в разделе [Практическое руководство. Зарегистрировать события буфера текста старый API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). В случае использования `IVsTextStreamEvents` или `IVsTextLinesEvents` интерфейсы, возвращаются изменения в любом одного или двух трехмерной координатах, соответственно.

## <a name="text-buffer-interfaces"></a>Интерфейсы буфера текста
 Ниже перечислены интерфейсы, реализованные объект текстового буфера.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Разрешает создание составных действий (то есть действия, которые группируются в единое единый отмены и повтора).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Включает сохранение данных документа, управляемых текстовым буфером.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы; Многие клиенты используют.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Предоставляет возможности, используя двухмерные координаты чтения и записи. Наследует от `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, поточно ориентированный, последовательный доступ к текста в буфере.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Обеспечивает чтение и запись с помощью одноразмерных координат. Наследует от `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к общей коллекции свойств. Наиболее важным свойством является имя или моникер буфера. Случайные данные можно сохранить в буфере, с этим интерфейсом, создать GUID и использовать его в качестве ключа.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки подключения для событий.|

## <a name="text-buffer-event-interfaces"></a>Интерфейсы событий буфера текста
 Ниже приведены интерфейсы для уведомления о событии текстового буфера.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Уведомляет клиентов, когда новая языковая служба связана с текстовым буфером.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Уведомляет клиентов, при инициализации текстового буфера, и при изменении данных в текстовом буфере.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в одномерный массив координат.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в двухмерные координаты.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Уведомляет клиентов об изменениях пользовательских данных.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Уведомляет клиентов о последнем жесте фиксации, инициирующем событие и предоставляет диапазон измененного текста. `IVsPreliminaryTextChangeCommitEvents` Интерфейс не запускается в ответ для отмены или повтора команды. События возникают только для буферов, которые имеют в диспетчере отмены. `IVsPreliminaryTextChangeCommitEvents` возникает до других событий, таких как красивое, чтобы убедиться, что другие события, не изменяйте текст перед фиксацией изменений. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Уведомляет клиентов о последнем жесте фиксации, инициирующем событие и предоставляет диапазон измененного текста. `IVsFinalTextChangeCommitEvents` Интерфейс не запускается в ответ для отмены или повтора команды. События возникают только для буферов, которые имеют в диспетчере отмены. `IVsFinalTextChangeCommitEvents` предназначен для использования только с помощью языковых служб или других объектов, имеющих полный контроль над изменением. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|

## <a name="see-also"></a>См. также

- [Доступ к текстового буфера, используя старый API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)
- [Практическое руководство. Регистрация для событий текстового буфера с предыдущих версий API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)