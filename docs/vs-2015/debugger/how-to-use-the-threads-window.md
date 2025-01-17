---
title: Практическое руководство. Использование окна потоков | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 835843d2328d9d17ac899fc12c97251b7e6b4659
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685323"
---
# <a name="how-to-use-the-threads-window"></a>Практическое руководство. Использование окна потоков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В **потоков** окна, можно проверить и работа с потоками в приложении, в котором производится отладка.  
  
 **Потоков** окно содержит таблицу, где каждая строка представляет поток в приложении. По умолчанию в таблице перечисляются все потоки приложения, но можно фильтровать этот список, чтобы в нем показывались только нужные потоки. В каждом столбце содержится свой тип сведений. Можно также скрывать некоторые столбцы. Если отображаются все столбцы, то в них имеются следующие сведения (слева направо):  
  
- Столбец флагов, где можно пометить поток, которому планируется уделить особое внимание. Сведения о способе пометки потока см. в разделе [как: Снять отметку с потока и отметки](../debugger/how-to-flag-and-unflag-threads.md).  
  
- Столбец активных потоков, в котором желтая стрелка указывает активный поток. Контур стрелки указывает поток, где выполнение было передано в отладчик.  
  
- **Идентификатор** столбец, который содержит идентификационный номер для каждого потока.  
  
- **Managed ID** столбец, который содержит управляемые идентификационные номера управляемых потоков.  
  
- **Категории** , подразделяющий потоков потоки пользовательского интерфейса, обработчики вызова удаленной процедуры и рабочие потоки. Особая категория идентифицирует главный поток приложения.  
  
- **Имя** столбец, в котором каждый поток по имени, если он имеется, или \<No Name >.  
  
- **Расположение** столбца, которое показывает, где поток выполняется. Можно развернуть это расположение, чтобы отобразить полный стек вызова для потока.  
  
- **Приоритет** столбец, в котором содержится приоритет, назначенный системой каждому потоку.  
  
- **Affinity Mask** столбец, который является дополнительным столбцом и обычно скрыт. В этом столбце показывается маска сходства процессора для каждого потока. В многопроцессорной системе маска сходства определяет, какой процессор в каком потоке может работать.  
  
- **Счетчик приостановок** столбец, в котором содержится счетчик приостановок. Этот счетчик определяет, может ли поток выполняться. Описание счетчика приостановок см. в разделе "Замораживание и размораживание потоков" далее в этой теме.  
  
- **Имя_процесса** столбец, содержащий процесс, к которому принадлежит каждый поток. Этот столбец может быть полезен при отладке нескольких процессов, но обычно он скрыт.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Открытие окна потоков в режиме приостановки или в режиме выполнения  
  
- На **Отладка** последовательно выберите пункты **Windows**, а затем нажмите кнопку **потоков**.  
  
### <a name="to-display-or-hide-a-column"></a>Отображение или скрытие столбца  
  
- На панели инструментов в верхней части **потоков** окно, нажмите кнопку **столбцы**, а затем выберите или очистите имя столбца, который требуется отобразить или скрыть.  
  
### <a name="to-switch-the-active-thread"></a>Переключение активного потока  
  
- Выполните одно из следующих действий.  
  
    - Дважды щелкните любой поток.  
  
    - Щелкните правой кнопкой мыши поток и нажмите кнопку **переключиться на поток**.  
  
         Рядом с новым активным потоком появится желтая стрелка. Серый контур стрелки указывает поток, где выполнение было передано в отладчик.  
  
## <a name="grouping-and-sorting-threads"></a>Группирование и сортировка потоков  
 При группировании потоков в таблице появляется заголовок для каждой группы. В заголовке содержится описание группы, например "Рабочие потоки" или "Непомеченные потоки", и элемент управления "Дерево". Потоки-элементы каждой группы отображаются под заголовком группы. Если требуется скрыть потоки-элементы в какой-либо группе, можно свернуть эту группу с помощью элемента управления "Дерево".  
  
 Поскольку группирование имеет приоритет перед сортировкой, можно, например, группировать потоки по категориям, а затем по идентификаторам внутри каждой категории.  
  
#### <a name="to-sort-threads"></a>Сортировка потоков  
  
1. На панели инструментов в верхней части **потоков** окно, нажмите кнопку в верхней части любого столбца.  
  
     Теперь потоки отсортированы по значениям в этом столбце.  
  
2. Если требуется изменить порядок сортировки, нажмите кнопку же еще раз.  
  
     Потоки, которые отображались вверху списка, теперь отображаются внизу.  
  
#### <a name="to-group-threads"></a>Группирование потоков  
  
- В **потоков** панели инструментов в окне щелкните **группировать по** , а затем выберите условия, которые требуется группировать потоки.  
  
#### <a name="to-sort-threads-within-groups"></a>Сортировка потоков в группах  
  
1. На панели инструментов в верхней части **потоков** окно, нажмите кнопку **группировать по** , а затем выберите условия, которые требуется группировать потоки.  
  
2. В **потоков** окно, нажмите кнопку в верхней части любого столбца.  
  
     Теперь потоки отсортированы по значениям в этом столбце.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Сворачивание и разворачивание всех групп  
  
- На панели инструментов в верхней части **потоков** окно, нажмите кнопку **развернуть группы** или **свернуть группы**.  
  
## <a name="searching-for-specific-threads"></a>Поиск конкретных потоков  
 В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] можно искать потоки, соответствующие указанной строке. При поиске потоков в **потоков** окно, в окне отображаются все потоки, которые соответствуют строке поиска в любом столбце. Эти сведения включают расположение потока, которое отображается в верхней части стека вызовов в **расположение** столбца. По умолчанию Однако полный стек вызова не ищется.  
  
#### <a name="to-search-for-specific-threads"></a>Поиск конкретных потоков  
  
- В панели инструментов, находящейся в верхней части окна **Потоки**, перейдите в поле **Поиск** и выполните одно из следующих действий:  
  
    - введите строку поиска и нажмите клавишу ВВОД;  
  
         \- или -  
  
    - Щелкните стрелку раскрывающегося списка рядом с полем **поиска** поле и выберите строку поиска из предыдущего поиска.  
  
- Чтобы включить в поиск полный стек вызова, выберите **Поиск в стеке вызова** (необязательно).  
  
## <a name="freezing-and-thawing-threads"></a>Замораживание и размораживание потоков  
 Если поток заморожен, то система не начнет его выполнение, даже если будут доступны все ресурсы.  
  
 В машинном коде, можно приостановить или возобновить потоков путем вызова функций Windows `SuspendThread` и `ResumeThread` или функций MFC [CWinThread::SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) и [CWinThread::ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). При вызове метода `SuspendThread` или `ResumeThread`, изменении *счетчик приостановок*, которое отображается в **потоков** окна. Однако замораживание или размораживание собственного потока не приводит к изменению счетчика приостановок. В машинном коде поток не может выполняться, если он является размороженным и имеет счетчик приостановок, равный нулю.  
  
 В управляемом коде замораживание или размораживание потока приводит к изменению счетчика приостановок. В управляемом коде замороженный поток имеет счетчик приостановок со значением 1. В машинном коде замороженный поток имеет счетчик приостановок со значением 0 до тех пор, пока этот поток не будет приостановлен путем вызова `SuspendThread`.  
  
> [!NOTE]
> При отладке вызова управляемого кода из машинного кода управляемый код выполняется в том же физическом потоке, что и вызывающий его машинный код. Приостановка выполнения или замораживание присущего данному объекту кода приводит также к замораживанию управляемого кода.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Заморозка и разморозка выполнения потока  
  
- На панели инструментов в верхней части **потоков** окно, нажмите кнопку **Заморозить потоки** или **Разморозить потоки**.  
  
     Это действие влияет только на потоки, выбранные в окне **Потоки**.  
  
## <a name="displaying-flagged-threads"></a>Отображение помеченных потоков  
 Поток, которому планируется уделить особое внимание, можно пометить, поставив рядом с ним значок в окне **Потоки**. Дополнительные сведения см. в разделе [Практическое руководство. Снять отметку с потока и отметки](../debugger/how-to-flag-and-unflag-threads.md). В окне "Потоки" можно выбрать отображение всех потоков или только помеченных потоков.  
  
#### <a name="to-display-only-flagged-threads"></a>Отображение только помеченных потоков  
  
- Нажмите кнопку флага в левом верхнем углу **потоков** окна.  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Отображение стека вызовов потоков и переключение между фреймами  
 В многопотоковых программах каждый поток имеет свой собственный стек вызовов. Окно **Потоки** обеспечивает удобный способ просмотра этих стеков.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Просмотр стека вызовов потока  
  
- В **расположение** столбец, нажмите перевернутый треугольник рядом с расположением потока.  
  
     Расположение будет развернуто, и будет отображен стек вызова для потока.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Просмотр и сворачивание стеков вызовов всех потоков  
  
- На панели инструментов в верхней части **потоков** окно, нажмите кнопку **развернуть стеки вызовов** или **свернуть стеки вызовов**.  
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Пошаговое руководство: Отладка многопоточных приложений](../debugger/walkthrough-debugging-a-multithreaded-application.md)
