---
title: Навигация по коду с помощью отладчика | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81b5bbca0b547510056b1aecfa0e7237e40a9814
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571139"
---
# <a name="navigating-through-code-with-the-debugger"></a>Навигация по коду с помощью отладчика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [перемещение по коду с помощью отладчика в Visual Studio](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger).  
  
Ознакомиться с командами и сочетания клавиш для перемещения по коду в отладчике, и, чтобы быстрее и проще находить и устранять неполадки в работе приложения. Срок действия кода в отладчике перейти, вы можете [проверять состояние приложения](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) или Дополнительные сведения о процессе его выполнения.  
  
## <a name="start-debugging"></a>Начать отладку  
 Часто, началом сеанса отладки с помощью командлета **F5** (**Отладка** / **начать отладку**). Эта команда запускает приложение с подключенным отладчиком.  
  
 Зеленая стрелка также запускает отладчик (то же, что **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Включают несколько способов, что можно запустить приложение с подключенным отладчиком **F11** ([шаг с заходом в код](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([шаг с обходом кода](#BKMK_Step_over_Step_out)), или с помощью с помощью **выполнить до текущей позиции**.  См. в разделе других подразделах в этом разделе сведения на этих параметров действия.  
  
 При отладке, желтая линия показывает код, который будет выполнена следующей.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Во время отладки, можно переключаться между команд, таких как **F5**, **F11** и использовать другие функции, описанные в этом разделе (например, установка точек останова), чтобы быстро найти код, который вы хотите просмотреть.  
  
 Многие возможности отладчика, такие как просмотр значений переменных в окне "Локальные" или вычисление выражений в окне контрольных значений, доступны только в том случае, когда отладчик приостановлена (также называется *режим приостановки выполнения*). Когда отладчик приостанавливает выполнение, состояние приложения приостанавливается при функции, переменные, и объекты остаются в памяти. В режиме приостановки, можно проверить, проверив положения элементов и состояний для поиска ошибок и нарушений целостности. Для некоторых типов проектов можно также внести корректировки в приложение в режиме приостановки.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Пошаговое выполнение кода, по одной строке  
 Чтобы остановить на каждую строку кода (каждой инструкции) во время отладки, используйте **F11** сочетания клавиш (или **Отладка** / **шаг с заходом** меню).  
  
> [!TIP]
>  При выполнении каждой строкой кода, наводите указатель мыши на переменные, их значения, или использовать ["Локальные"](../debugger/autos-and-locals-windows.md) и [Watch](../debugger/autos-and-locals-windows.md) окон контрольных значений, их изменить.  
  
 Ниже приведены некоторые сведения о поведении **шаг с заходом**:  
  
-   При вызове вложенных функций команда **Шаг с заходом** позволяет попасть в самую глубокую вложенную функцию. Если использовать **Шаг с заходом** на вызове `Func1(Func2())`, отладчик заходит в функцию `Func2`.  
  
-   Отладчик фактически осуществляет пошаговое выполнение операторов кода, а не физических строк. Например, предложение `if` может быть записано в одной строке:  
  
    ```csharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```vb  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     При пошаговом выполнении этой строки отладчик обрабатывает условие как один шаг, а следствие как другой (в этом примере условие выполняется).  
  
 Визуальном отслеживании стека вызовов при пошаговом выполнении функций, см. в разделе [сопоставление методов в стеке вызовов при отладке](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Пошаговое выполнение кода, пропуская функции  
 При выполнении кода в отладчике, часто вы увидит, что не нужно увидеть, что происходит в определенную функцию (вы вообще не заботятся о его или вы знаете, что он работает, как проверенная библиотека кода). Используйте следующие команды, чтобы пропустить кода (функции по-прежнему выполняются, само собой, но отладчик пропускает их).  
  
|Команда клавиатуры|Команда меню|Описание|  
|----------------------|------------------|-----------------|  
|**F10**|**Шаг с обходом**|Если текущая строка содержит вызов функции **шаг с обходом** выполняет код, а затем приостанавливает выполнение на первой строке кода после возврата вызываемой функции.|  
|**SHIFT+F11**|**Шаг с выходом**|**Шаг с выходом** продолжает выполнение кода и приостанавливает выполнение, когда текущая функция возвращает (отладчик пропускает через текущую функцию).|  
  
> [!TIP]
>  Если вам нужно найти точку входа в приложение, начните с **F10** или **F11**. Эти команды зачастую полезно при проверке состояние приложения или найти дополнительные сведения о его поток выполнения.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Выполнение до определенного расположения или функции  
 Часто предпочтительный способ отладки кода, эти методы полезны, когда вы знаете точно какой код, который требуется проверить или по крайней мере вы знаете, где вы хотите начать отладку.  
  
-   **Задание точек останова в коде**  
  
     Для установки простой точки останова в коде откройте исходный файл в редакторе Visual Studio. Установите курсор в строке кода, где требуется приостановить выполнение и щелкните правой кнопкой мыши в окне кода, чтобы открыть контекстное меню и выберите **точки останова / вставить точку останова** (или нажмите клавишу **F9**). Отладчик приостанавливает выполнение справа, перед выполнением указанной строки.  
  
     ![Установите точку останова](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Точки останова в Visual Studio предоставляют широкий набор дополнительных функций, таких как условные точки останова и точки трассировки. См. в разделе [использование точек останова](../debugger/using-breakpoints.md).  
  
-   **Выполнение до расположения курсора**  
  
     Чтобы осуществить выполнение до расположения курсора, поместите курсор в исполняемую строку кода в окне исходного кода. В контекстном меню редактора (правой кнопкой мыши в редакторе), выберите **выполнить до текущей позиции**. Это аналогично заданию временной точки останова.  
  
-   **Приостановка выполнения кода вручную**  
  
     Чтобы приостановить выполнение на следующей доступной строке кода в выполняющемся приложении, выберите **Отладка**, **Прервать все** (на клавиатуре: **Ctrl+Alt+Break**).  
  
     Если во время приостановки выполнения кода отсутствуют соответствующие исходные файлы или файлы символов (PDB-файлы), отладчик отображает страницу **Исходный файл не найден** или **Символы не найдены** , которая поможет найти необходимые файлы. См. статью [Указание файлов символов (.pdb) и файлов с исходным кодом в отладчике Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Если у вас нет доступа к вспомогательным файлам, можно выполнить отладку инструкций на языке ассемблера в окне "Дизассемблирование".  
  
-   **Выполнение до функции в стеке вызовов**  
  
     В **стек вызовов** (доступно во время отладки), выберите функцию, щелкните правой кнопкой и выберите **выполнить до текущей позиции**. Визуальном отслеживании стека вызовов, см. в разделе [сопоставление методов в стеке вызовов при отладке](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Выполнение до функции, указанной по имени**  
  
     Можно настроить отладчик для запуска приложения, пока не достигнет указанной функции. Можно задать функцию по имени или выбрать ее из стека вызовов.  
  
     Чтобы указать функцию по имени, последовательно выберите **Отладка**, **Создать точку останова**, **Прервать в функции**, а затем введите имя функции и другие идентификационные сведения.  
  
     ![Новое диалоговое окно точки останова](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Если функция перегружается или находится в нескольких пространствах имен, необходимые функции можно выбрать в диалоговом окне **Выбор точек останова** .  
  
     ![Точки останова диалоговое окно выбора](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Переместите указатель для изменения хода выполнения  
 Приостановив отладчик, можно переместить указатель инструкции, чтобы задать следующий оператор кода, который будет выполнен. Желтая стрелка на границе исходного текста или в окне "Дизассемблированный код" отмечает текущее расположение оператора, который должен быть выполнен следующим. Посредством перемещения этой стрелки можно пропустить часть кода или вернуться к строке, выполненной ранее. Это можно использовать при возникновении таких ситуаций, как пропуск раздела кода, содержащего известную ошибку.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Чтобы задать следующий оператор для выполнения, воспользуйтесь одной из следующих процедур.  
  
-   В окне исходного кода перетащите желтую стрелку в то место этого же исходного файла, где необходимо задать следующий оператор.  
  
-   В окне исходного кода, установите курсор в строке, который требуется выполнить следующей, щелкните правой кнопкой мыши и выберите **задать следующий оператор**.  
  
-   В окне дизассемблирования, установите курсор на инструкцию ассемблера, который требуется выполнить следующей, щелкните правой кнопкой мыши и выберите **задать следующий оператор**.  
  
> [!CAUTION]
>  Установка следующего оператора заставит программный счетчик инструкций перейти непосредственно на новое место. Следует применять эту команду с осторожностью.  
>   
>  -   Инструкции между старой и новой точками не выполняются.  
> -   При перемещении точки выполнения обратно, промежуточные инструкции не отменяются.  
> -   Перемещение следующего оператора на другую функцию или область обычно приводит к повреждению стека вызова, вызывая ошибку времени выполнения или исключение. При попытке перемещения следующего оператора в другую область, отладчик открывает диалоговое окно с предупреждением и предоставляет возможность отменить операцию. В Visual Basic нельзя переместить следующий оператор на другую область или функцию.  
> -   Если при использовании машинного кода C++ включены проверки времени выполнения, установка следующего оператора может вызвать исключение, когда выполнение достигнет конца метода.  
> -   При включенной операции "Изменить и продолжить" команда **Задать следующий оператор** завершится неудачей, если вы внесете изменения, которые операция "Изменить и продолжить" не сможет немедленно применить. Например, это может произойти, если были внесены изменения внутри блока catch. При возникновении такой ситуации появится сообщение об ошибке, указывающее, что операция не поддерживается.  
  
> [!NOTE]
>  В управляемом коде нельзя перемещать следующий оператор в следующих случаях:  
>   
>  -   Следующий оператор находится в методе, отличном от метода текущего оператора.  
> -   Отладка была запущена через JIT–отладку.  
> -   Выполняется очистка стека вызова.  
> -   Вызвано исключение System.StackOverflowException или System.Threading.ThreadAbortException.  
  
 Нельзя устанавливать следующий оператор, если приложение выполняется. Чтобы задать следующий оператор, отладчик должен находиться в режиме приостановки.  
  
## <a name="step-into-non-user-code"></a>Шаг с заходом в код, не написанный пользователем  
 По умолчанию, отладчик пытается Показать только код приложения во время отладки, который определяется с помощью отладчика, устанавливается флажок *Just My Code*. (См. в разделе [Just My Code](../debugger/just-my-code.md) чтобы увидеть, как это работает для различных типов проектов и языков и как его настроить поведение.) Тем не менее, иногда при отладке, может потребоваться взгляните на код платформы, библиотеки стороннего кода или вызовы в операционную систему (системные вызовы).  
  
 Только мой код можно отключить, перейдя к **средства** / **параметры** / **Отладка** и очистить **включить только мой код** флажок.  
  
 При отключении Just My Code, отладчик может войти в код, не написанный пользователем, и не написанный пользователем код отображается в окнах отладчика.  
  
> [!NOTE]
>  Режим "Только мой код" не поддерживается для проектов устройств.  
  
 **Шаг с заходом в системные вызовы**  
  
 Если вы загрузили отладочные символы для системного кода и Just My Code не включена, можно выполнить пошаговую отладку системного вызова, так же, как любых других вызовов.  
  
 Чтобы получить доступ к файлам символов Microsoft, см. в разделе [использование серверов символов для поиска файлов символов не на локальном компьютере](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) в [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) раздела.  
  
 Чтобы загрузить символы для определенного системного компонента во время отладки, выполните следующие действия.  
  
1.  Откройте окно "Модули" (на клавиатуре: **Ctrl+Alt+U**).  
  
2.  Выберите модуль, для которого требуется загрузить символы.  
  
     Определить, для каких модулей символы загружены, можно по значению в столбце **Состояние символов** .  
  
3.  В контекстном меню выберите команду **Загрузить символы** .  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Шаг с заходом в свойства и операторы в управляемом коде  
 По умолчанию отладчик обходит свойства и операторы при пошаговом выполнении в управляемом коде. В большинстве случаев это делает отладку более удобной и эффективной. Включение захода в свойства или операторы, выберите **Отладка** / **параметры**. На странице **Отладка** / **Общие** снимите флажок **Обход свойств и операторов (только управляемый код)** .




