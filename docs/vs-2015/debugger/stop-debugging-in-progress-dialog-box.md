---
title: Остановка отладки в диалоговое окно хода выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.stopnow
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e96e76f809f6c2f8f02267fe080e9e6742af4587
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560930"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Остановка отладки - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [остановить отладку в диалоговое окно хода выполнения](https://docs.microsoft.com/visualstudio/debugger/stop-debugging-in-progress-dialog-box).  
  
Это диалоговое окно появляется, когда отладчик пытается остановить сеанс отладки, но на остановку требуется некоторое время. Обычно остановка сеанса отладки происходит очень быстро и это диалоговое окно не появляется. Но в ряде случаев требуется дополнительное время на то, чтобы отсоединиться от всех отлаживаемых процессов. Если остановка сеанса отладки длится дольше нескольких секунд (или если возникает ошибка отсоединения), появляется это диалоговое окно. Если это случается часто, это может быть связано с внутренней проблемой и, возможно, следует связаться со службой технической поддержки.  
  
 Можно ожидать процессы отсоединятся и это диалоговое окно исчезнет, или использовать **остановить** кнопку, чтобы выполнить немедленное завершение.  
  
 **Остановить**  
 Нажмите эту кнопку, чтобы немедленно остановить сеанс отладки. С помощью **остановить**будет завершена, а не отсоединяет отлаживаемые процессы. Если отлаживаются системные процессы, завершение этих процессов с помощью **остановить** может иметь неожиданные и нежелательные эффекты.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отсоединение программ](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)


