---
title: Общие, отладка, диалоговое окно "Параметры" | Документация Майкрософт
ms.date: 11/09/2018
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80fc504752e181ec75da32f2d1da5dcbf902daf7
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037387"
---
# <a name="general-debugging-options"></a>Общие параметры отладки

Чтобы задать параметры отладчика Visual Studio, выберите **средства** > **параметры**, а затем в разделе **Отладка** установите или снимите флажки, расположенные рядом с полем  **Общие** параметры. Вы можете восстановить все параметры по умолчанию с **средства** > **Импорт и экспорт параметров** > **сбросить все параметры**. Чтобы сбросить подмножество параметров, сохраните параметры с **мастер импорта и экспорта параметров** перед внесением изменений, которые вы хотите протестировать, затем импортировать сохраненные параметры впоследствии.

Можно задать следующие **Общие** параметры:

**Запрашивать подтверждение перед удалением всех точек останова** Запрашивает подтверждение перед выполнением команды **Удалить все точки останова**.

**Прерывать все процессы при прерывании одного** При возникновении прерывания одновременно прерываются все процессы, к которым присоединен отладчик.

**Прерывать выполнение, когда исключения пересекают границу домена приложения или границу между управляемым и машинным кодом** При отладке управляемого кода или в смешанном режиме отладки в среде CLR могут перехватываться исключения, пересекающие границы домена приложений или границы между управляемым и машинным кодом при следующих условиях:

1. Машинный код вызывает управляемый код с использованием COM-взаимодействия; при этом в управляемом коде возникает исключение. См. в разделе [Введение во взаимодействие COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Управляемый код, выполняемый в домене приложения 1, вызывает управляемый код домена приложения 2; при этом в управляемом коде домена приложения 2 возникает исключение. См. [Программирование с использованием доменов приложений и сборок](/dotnet/articles/framework/app-domains/index).

3. Когда код вызывает функцию с помощью отражения, и что функция создает исключение. См. в разделе [отражения](/dotnet/framework/reflection-and-codedom/reflection).

В условиях 2 и 3 исключения иногда перехватываются управляемым кодом в `mscorlib` , а не среда CLR. Этот параметр не влияет на прерывание по исключениям, перехватываемым с помощью библиотеки `mscorlib`.

**Включить отладку на уровне адреса** Предоставляет дополнительные возможности для отладки на уровне адреса (окно **Дизассемблированный код**, окно **Регистры** и точки останова с указанием адреса).

- **Показывать дизассемблированный код, если исходный код недоступен**   Автоматически отображает **Дизассемблированный код** окна при отладке кода, для которого источник недоступен.

**Включить фильтры точек останова** Позволяет задать фильтры точек останова, чтобы последние оказывали воздействие только на определенные процессы, потоки и компьютеры.

**Использовать новое вспомогательное приложение по обработке исключений** Позволяет по исправлению, которая заменяет помощник по исключениям. (Помощник по исправлению ошибок поддерживается начиная с Visual Studio 2017)

> [!NOTE]
> Для управляемого кода, этот параметр был ранее вызван **включить помощник по исключениям** .

**Включить только мой код** В отладчике отображается и доступен для входа только код пользователя ("мой код"). Системный код игнорируется, так же как и любой другой код, который является оптимизированным или не содержит символов отладки.

- **Выводить предупреждение, если пользовательский код отсутствует при запуске (только управляемый код)**   При запуске отладки с включенным режимом "Только мой код" выводится предупреждение в случае отсутствия кода пользователя ("моего кода").

**Разрешить шаги в исходном коде .NET Framework** Позволяет отладчику при пошаговом выполнении заходить в исходный код .NET Framework. Включение этого параметра автоматически отключает только мой код. .NET framework они будут загружены расположение кэша. Изменить расположение кэша с **параметры** диалоговом окне **Отладка** категории **символы** страницы.

**Обход свойств и операторов (только управляемый код)** Запрещает отладчику при пошаговом выполнении заходить в свойства и операторы в управляемом коде.

**Включить вычисление свойств и другие неявные вызовы функций** Включение автоматического вычисления свойств и неявных вызовов функций в окнах переменных и диалоговом окне **Быстрая проверка**.

- **Вызов функции преобразования ToString() для объектов в окнах переменных (только C# и JavaScript)** Неявный вызов функции преобразования строковых значений при вычислении объектов в окнах переменных. Результат отображается в виде строки вместо имени типа. Применимо только при отладке кода C#. Этот параметр можно переопределить с помощью атрибута DebuggerDisplay (см. в разделе [использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Включить поддержку сервера системы управления версиями** Дает отладчику Visual Studio указание получать исходные файлы с серверов системы управления версиями, реализующих протокол SrcSrv (`srcsrv.dll`). Team Foundation Server и инструменты отладки для Windows — два исходных сервера, которые реализуют этот протокол. Дополнительные сведения о настройке SrcSrv см. в разделе [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) документации. Кроме того, см. в разделе [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Так как при чтении *PDB*-файлов может выполняться произвольный код в файлах, убедитесь, что вы доверяете серверу.

- **Выводить диагностические сообщения сервера системы управления версиями в окно "Вывод"**   При включенной поддержке сервера системы управления версиями данный параметр включает вывод диагностических сведений.

- **Разрешить выполнение частично доверенных сборок (только управляемых) на исходном сервере**   Если поддержка сервера системы управления версиями включена, этот параметр переопределяет поведение по умолчанию для неизвлечения исходного кода для частично доверенных сборок.

- **Всегда выполнять ненадежные команды исходного сервера без запроса**   При включенной поддержке сервера источника, этот параметр переопределяет поведение по умолчанию запроса при выполнении команды без доверия.

**Включите поддержку ссылок на источник** Указывает отладчику Visual Studio для загрузки исходных файлов для *.pdb* файлы, содержащие ссылки на исходные данные. Дополнительные сведения о ссылки на источник, см. в разделе [спецификация источника ссылки](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Так как ссылка на источник будет загружать файлы по протоколу http или https, убедитесь, что вы доверяете *.pdb* файл.

- **Вернуться к проверке подлинности с помощью диспетчера учетных данных Git для всех запросов со ссылкой на источник**   Если включена поддержка ссылок на источник, а ссылки на источник запроса не проходит проверку подлинности, Visual Studio затем вызывает Git Credential Manager.

**Выделять всю исходную строку для точек останова и текущего оператора (только C++)**: При выделении точки останова или текущего оператора отладчик выделяет всю строку.

**Требовать точного соответствия исходной версии файлов** Дает отладчику указание проверять во время отладки, соответствует ли исходный файл версии исходного кода, использованной для сборки исполняемого файла. Если версии не совпадают, будет предложено найти соответствующий источник. Если соответствующий исходный код не найден, в процессе отладки исходный код не отображается.

**Перенаправлять весь текст окна "Вывод" в окно "Интерпретация"** Включает перенаправление всех сообщений отладчика, обычно отображаемых в окне **Вывод**, в окно **Интерпретация**.

**Показывать базовую структуру объектов в окнах переменных** Отключение всех пользовательских настроек представления структуры объектов. Дополнительные сведения о настройках представлений см. в разделе [Создание настраиваемых представлений собственных объектов](../debugger/create-custom-views-of-dot-managed-objects.md).

**Отключать JIT-оптимизацию при загрузке модуля (только управляемый код)** Отключение JIT-оптимизации управляемого кода при загрузке модуля (и JIT-компиляции), если присоединен отладчик. Отключение оптимизации позволяет упростить процесс отладки некоторых проблем, однако может отрицательно сказаться на производительности. В режиме "Только мой код" при отключении JIT-оптимизации в коде пользователя ("Мой код") может отображаться посторонний код. Дополнительные сведения см. в разделе [JIT отладка и оптимизация](../debugger/jit-optimization-and-debugging.md).

**Включить отладку JavaScript для ASP.NET (Chrome, Microsoft Edge и IE)** Позволяет отладчику скриптов для приложений ASP.NET. При первом использовании в браузере Chrome необходимо войти в браузере, чтобы включить расширения Chrome, установленных. Отключите этот параметр, чтобы вернуться к поведению предыдущих версий.

**Включить средства разработчика Microsoft Edge для приложений JavaScript UWP (экспериментальная функция)** Включает средства разработки для приложений JavaScript универсальной платформы Windows в Microsoft Edge.

**Включить устаревший отладчик Chrome JavaScript для ASP.NET** Включает устаревший отладчик Chrome JavaScript сценарий для приложений ASP.NET. При первом использовании в браузере Chrome необходимо войти в браузере, чтобы включить расширения Chrome, установленных.

**Использовать экспериментальный способ для запуска отладки JavaScript в Chrome при запуске Visual Studio от имени администратора** Сообщает Visual Studio, чтобы повторить новый способ запуска Chrome, во время отладки JavaScript.

**Загружать экспорты из DLL (только машинный код)** Загружает таблицы экспорта библиотеки DLL. Символьные данные из таблиц экспорта библиотеки DLL можно использовать при работе с сообщениями Windows, процедурами Windows (WindowProcs), COM-объектами, при маршалинге или при работе с любой библиотекой DLL, для которой нет символов. Считывание данных экспорта библиотеки DLL связано с определенными дополнительными затратами. Поэтому данная возможность по умолчанию отключена.

Чтобы посмотреть, какие символы доступны в таблице экспорта библиотеки DLL, воспользуйтесь командой `dumpbin /exports`. Символы доступны для любой 32-разрядной системной библиотеки DLL. В выходных данных команды `dumpbin /exports` можно увидеть точное имя функции, включая символы, отличные от буквенно-цифровых. Это полезно при задании точки останова в функции. Имена функций из таблиц экспорта библиотеки DLL могут отображаться в отладчике в сокращенном виде. Вызовы функций перечисляются в том порядке, в котором эти функции вызываются, при этом текущая функция (наиболее глубоко вложенная) располагается наверху. Дополнительные сведения см. в разделе [dumpbin /exports](/cpp/build/reference/dash-exports).

**Показать параллельную диаграмму с накоплением сверху вниз** Определяет направление, в котором отображаются стеки в окне **Параллельные стеки**.

**Игнорировать исключения обращения к памяти GPU, если записываемые данные не изменили значение** Пропускает состояния гонки, обнаруженные во время отладки, если данные не были изменены. Дополнительные сведения см. в разделе [отладка кода GPU](../debugger/debugging-gpu-code.md).

**Использовать режим совместимости управляемого кода** Меняет ядро отладки по умолчанию на предыдущую версию для поддержки следующих сценариев.

- При использовании языка .NET Framework, отличное от C#, Visual Basic или F# , предоставляет собственный вычислитель выражений (сюда входят C++выполняет).

- Вы хотите включить изменить и продолжить для проектов C++ во время отладки в смешанном режиме.

> [!NOTE]
> Выбор совместимости управляемого режима отключению некоторых функций, реализованных только в ядре отладки по умолчанию. Ядру отладки был заменен в Visual Studio 2012.

**Использовать устаревшие вычислители выражений C# и VB** Отладчик будет использовать Visual Studio 2013 C# или вычислители выражений Visual Basic, а не вычислители выражений на основе Visual Studio 2015 Roslyn.

**Предупреждать об использовании настраиваемых визуализаторов отладчика для потенциально небезопасных процессов (только для управляемого режима)** Visual Studio предупреждает об использовании настраиваемого визуализатора отладчика, выполняющего код в отлаживаемом процессе, так как выполняемый код может быть небезопасным.

**Включить распределитель кучи отладки Windows (только собственный код)** Позволяет отладочной куче Windows улучшать диагностику кучи. Включение этого параметра повлияет на производительность отладки.

**Включить средства отладки пользовательского интерфейса для XAML** При запуске отладки (клавиша **F5**) поддерживаемого типа проекта появятся окна динамического визуального дерева и динамического обозревателя свойств. Дополнительные сведения см. в разделе [свойства проверять XAML во время отладки](../debugger/inspect-xaml-properties-while-debugging.md).

- **Предварительный просмотр выбранных элементов в динамическом визуальном дереве**   Элемент XAML, контекст которого выбран, также выбирается в окне **Динамическое визуальное дерево**.

- **Показать средства среды выполнения в приложении** Показывает **динамическое визуальное дерево** команды в панели инструментов в главном окне отлаживаемого приложения XAML. Этот параметр впервые появился в Visual Studio 2015 с обновлением 2.

- **Включить XAML "Горячий" перезагрузить**: Позволяет использовать функцию "Горячий" перезагрузить XAML с кодом XAML, когда приложение запущено. (Эта функция раньше назывался «"XAML Изменить и продолжить»)

**Включить средства диагностики при отладке** При отладке появится окно **Средства диагностики**.

**Показывать подсказку с затраченным временем при отладке** При отладке окно кода отображает время, прошедшее с момента вызова этого метода.

**Включить функцию "Изменить и продолжить"** Включает функцию, изменить и продолжить, во время отладки.

- **Включить функцию "Изменить машинный код и продолжить"** При отладке машинного кода C++ можно использовать функцию "Изменить и продолжить". Дополнительные сведения см. в разделе [изменить и продолжить (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Применить изменения при продолжении (только машинный код)** Visual Studio автоматически компилирует и применяет необработанные изменения кода, внесенные при продолжении процесса из состояния приостановки. Если этот параметр не выбран, можно применить изменения с помощью пункта **Применить изменения кода** в меню **Отладка**.

- **Предупреждать об устаревшем коде (только машинный код)**   Получать предупреждения об устаревшем коде.

**Показать выполнения до щелчка кнопки в редакторе во время отладки**: Если этот параметр выбран, [выполнение до щелкнутого](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) кнопка будет присутствовать во время отладки.

**Автоматически закрыть консоль при остановке отладки** Указывает Visual Studio, чтобы закрыть консоль в конце сеанса отладки.

## <a name="options-available-in-older-versions-of-visual-studio"></a>Параметры, доступные в более ранних версиях Visual Studio

При использовании более ранней версии Visual Studio, может присутствовать некоторые дополнительные параметры.

**Включить помощник по исключениям** Для управляемого кода позволяет по исключениям. Начиная с Visual Studio 2017, по исправлению заменить по исключениям.

**Очищать стек вызовов от кадров необработанных исключений** При выборе этого параметра стек вызовов в окне **Стек вызовов** откатывается до точки перед возникновением необработанного исключения.

**Предупреждать об отсутствии символов при запуске (только машинный код)** Отображает диалоговое окно предупреждения при отладке программы, для которого нет информация о символах отладчик.

**Предупреждать, если отладка скриптов запрещена при запуске** При запуске отладчика с отключенной отладкой скриптов отображается диалоговое окно с предупреждением.

**Используйте режим совместимости машинного кода** При выборе этого параметра отладчик использует собственный отладчик Visual Studio 2010 вместо нового собственного отладчика.

- Этот параметр используется при отладке кода .NET C++, так как новое ядро отладки не поддерживает вычисление выражений .NET C++. Однако включение режима совместимости машинного кода отключает множество функций, которые зависят от работы текущей реализации отладчика. Например, модуль предыдущих версий отсутствуют многие визуализаторы для встроенных типов, таких как `std::string` в проектах Visual Studio 2015.   Используйте проекты Visual Studio 2013 для оптимальной производительности отладки в таких случаях.

## <a name="see-also"></a>См. также

- [Отладка в Visual Studio](../debugger/index.md)
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
