---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: gewarren
author: gewarren
manager: jillfra
ms.topic: include
ms.openlocfilehash: 9a8fd8ca5081e3353cdbb488da5d43f54275d8da
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65848354"
---
*Интегрированная среда разработки* Visual Studio — это оригинальная среда запуска, которая позволяет редактировать, отлаживать и создавать код, а затем публиковать приложения. Интегрированная среда разработки (IDE) — это многофункциональная программа, которую можно использовать для различных аспектов разработки программного обеспечения. Помимо стандартного редактора и отладчика, которые существуют в большинстве сред IDE, Visual Studio включает в себя компиляторы, средства выполнения кода, графические конструкторы и многие другие функции для упрощения процесса разработки программного обеспечения.

::: moniker range="vs-2017"

![Интегрированная среда разработки Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![](../media/vs-2019/ide-overview.png "Интегрированная среда разработки Visual Studio")](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

На рисунке показана среда Visual Studio с открытым проектом и несколькими окнами основных инструментов, которые вам, скорее всего, понадобятся:

- [Обозреватель решений](../../ide/solutions-and-projects-in-visual-studio.md) (вверху справа) позволяет просматривать файлы кода, перемещаться по ним и управлять ими. **Обозреватель решений** позволяет упорядочить код путем объединения файлов в [решения и проекты](../tutorial-projects-solutions.md).

- В [окне редактора](../../ide/writing-code-in-the-code-and-text-editor.md) (центр), где вы, скорее всего, будете проводить большую часть времени, отображается содержимое файла. Здесь вы можете редактировать код или разрабатывать пользовательский интерфейс, например окно с кнопками или текстовые поля.

::: moniker range="vs-2017"

- В окно [вывода](../../ide/reference/output-window.md) (в центре внизу) Visual Studio отправляет уведомления, такие как сообщения об отладке и ошибках, предупреждения компилятора, сообщения о состоянии публикаций и многие другие. Каждый источник сообщений имеет собственную вкладку.

::: moniker-end

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (правый нижний угол) позволяет отслеживать рабочие элементы и использовать код совместно с другими пользователями с помощью технологий управления версиями, таких как [Git](https://git-scm.com/) и [система управления версиями Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Выпуски

::: moniker range="vs-2017"

Среда Visual Studio доступна для Windows и Mac. Функции [Visual Studio для Mac](/visualstudio/mac/) аналогичны возможностям Visual Studio 2017 и оптимизированы для разработки кроссплатформенных и мобильных приложений. Эта статья посвящена версии Visual Studio 2017 для Windows.

Есть три выпуска Visual Studio 2017: Community, Professional и Enterprise. Сведения о функциях, поддерживаемых в каждом выпуске, см. в статье [Сравнение интегрированных сред разработки Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/).

::: moniker-end

::: moniker range="vs-2019"

Среда Visual Studio доступна для Windows и Mac. Функции [Visual Studio для Mac](/visualstudio/mac/) во многом аналогичны возможностям Visual Studio 2019 и оптимизированы для разработки кроссплатформенных и мобильных приложений. Эта статья посвящена версии Visual Studio 2019 для Windows.

Существует три выпуска Visual Studio 2019: Community, Professional и Enterprise. Сведения о функциях, поддерживаемых в каждом выпуске, см. в [сравнительном анализе интегрированных сред разработки Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

::: moniker-end

## <a name="popular-productivity-features"></a>Популярные средства повышения производительности

Ниже перечислены некоторые популярные возможности Visual Studio, которые помогут вам повысить продуктивность разработки программного обеспечения.

- Волнистые линии и [быстрые действия](../../ide/quick-actions.md)

   Волнистые линии обозначают ошибки или потенциальные проблемы кода прямо во время ввода. Эти визуальные подсказки позволяют устранять проблемы немедленно и не ждать, пока ошибка будет обнаружена во время сборки или запуска программы. Если навести указатель мыши на волнистую линию, на экран будут выведены дополнительные сведения об ошибке. Кроме того, в поле слева может появляться значок лампочки с быстрыми действиями по устранению ошибки.

   ![Волнистые линии в Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Очистка кода

   Вы можете одним нажатием кнопки отформатировать код и применить к нему исправления, предложенные [параметрами стиля кода](../../ide/reference/options-text-editor-csharp-formatting.md), [соглашениями в файле EditorConfig](../../ide/create-portable-custom-editor-options.md) и (или) [анализаторами Roslyn](../../code-quality/roslyn-analyzers-overview.md). **Очистка кода** помогает устранить многие проблемы в коде еще до проверки кода. (Сейчас эта возможность доступна только для кода на C#.)

   ![Кнопка очистки кода в Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Рефакторинг](../../ide/refactoring-in-visual-studio.md)

   Рефакторинг включает в себя такие операции, как интеллектуальное переименование переменных, извлечение одной или нескольких строк кода в новый метод, изменение порядка параметров методов и многое другое.

   ![Рефакторинг в Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense — это набор функций, отображающих сведения о коде непосредственно в редакторе и в некоторых случаях автоматически создающих небольшие отрывки кода. По сути, это базовая документация, встроенная в редактор, с которой вам не приходится искать информацию где-то еще. Функции IntelliSense зависят от языка. Дополнительные сведения см. в руководствах по [IntelliSense для C# ](../../ide/visual-csharp-intellisense.md), [IntelliSense для Visual C++](../../ide/visual-cpp-intellisense.md), [IntelliSense для JavaScript](../../ide/javascript-intellisense.md) и [IntelliSense для Visual Basic](../../ide/visual-basic-specific-intellisense.md). На следующем рисунке показано, как IntelliSense отображает список членов типа:

   ![Список элементов Visual Studio](../media/intellisense-list-members.png)

- Поле поиска

   Среда Visual Studio может показаться сложной, ведь там столько разных меню, параметров и свойств. Поле поиска позволяет быстро найти нужное содержимое в Visual Studio. Когда вы начнете вводить в поле то, что вы ищете, Visual Studio представит результаты, один из которых точно вам подойдет. Если вам нужно добавить функциональные возможности в Visual Studio, например поддержку дополнительных языков программирования, поле поиска предоставляет результаты, которые открывают Visual Studio Installer для установки рабочей нагрузки или отдельного компонента.

   > [!TIP]
   > Нажмите клавиши **CTRL**+**Q**, чтобы открыть поле поиска.

   ::: moniker range="vs-2017"

   ![Поле поиска "Быстрый запуск" в Visual Studio 2017](../media/quick-launch-nuget.png)

   Дополнительные сведения см. в разделе [Быстрый запуск](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Поле поиска в Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Предоставляет возможности совместного редактирования и отладки в реальном времени независимо от типа приложения или языка программирования. Вы можете мгновенно и безопасно поделиться своим проектом и, при необходимости, сеансами отладки, экземплярами терминалов, веб-приложениями localhost, голосовыми звонками и многим другим.

- [Иерархия вызовов](../../ide/reference/call-hierarchy.md)

   В окне **Иерархия вызовов** показаны методы, вызывающие выбранный метод. Это может быть полезно, если вы собираетесь изменить или удалить метод или хотите отследить ошибку.

   ![Окно «Иерархия вызовов»](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens помогает находить ссылки на код, изменения кода, связанные ошибки, рабочие элементы, проверки кода и модульные тесты — все это не выходя из редактора.

   ![CodeLens](../media/codelens-overview.png)

- [Перейти к определению](../../ide/go-to-and-peek-definition.md)

   С функцией "Перейти к определению" вы напрямую переходите туда, где определена функция или тип.

   ![Перейти к определению](../media/go-to-definition-menu.png)

- [Показать определение](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   В окне **Просмотр определений** показано определение метода или типа, при этом не нужно открывать отдельный файл.

   ![Показать определения](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Установка интегрированной среды разработки Visual Studio

В рамках этого раздела вы создадите простой проект для тестирования некоторых возможностей Visual Studio. Вы примените [IntelliSense](../../ide/using-intellisense.md) в качестве вспомогательного средства для написания кода, выполните отладку приложения для просмотра значения переменной в процессе выполнения программы, а также измените цветовую тему.

::: moniker range="vs-2017"

Чтобы начать работу, [скачайте](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) и установите Visual Studio. Этот модульный установщик позволяет выбрать и установить *рабочие нагрузки*, которые являются группами функций, необходимыми для предпочитаемого языка программирования или платформы. Выполните следующие инструкции по [созданию программы](#create-a-program) и в процессе установки выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**.

::: moniker-end

::: moniker range=">=vs-2019"

Чтобы начать работу, [скачайте](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) и установите Visual Studio. Этот модульный установщик позволяет выбрать и установить *рабочие нагрузки*, которые являются группами функций, необходимыми для предпочитаемого языка программирования или платформы. Выполните следующие инструкции по [созданию программы](#create-a-program) и в процессе установки выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**.

::: moniker-end

![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../media/dotnet-core-cross-platform-workload.png)

При первом запуске Visual Studio вы можете выполнить [вход](../../ide/signing-in-to-visual-studio.md) с использованием либо учетной записи Майкрософт, либо рабочей или учебной учетной записи.

## <a name="create-a-program"></a>Создание программы

Давайте создадим простую программу.

::: moniker range="vs-2017"

1. Запустите Visual Studio.

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

   ![Параметры меню "Файл" > "Новый" > "Проект".](../media/file-new-project-menu.png)

   В диалоговом окне **Создать проект** отображается несколько *шаблонов проекта*. Шаблон содержит основные файлы и параметры, необходимые для данного типа проекта.

1. В разделе **Visual C#** выберите категорию шаблонов **.NET Core** и щелкните шаблон **Консольное приложение (.NET Core)**. В текстовом поле **Имя** введите **HelloWorld**, а затем нажмите кнопку **ОК**.

   ![Шаблон приложения .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Если категория **.NET Core** не отображается, необходимо установить рабочую нагрузку **Кросс-платформенная разработка .NET Core**. Для этого щелкните ссылку **Открыть Visual Studio Installer** внизу слева в диалоговом окне **Новый проект**. Когда Visual Studio Installer откроется, прокрутите список вниз и выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core**, а затем щелкните **Изменить**.

   Visual Studio создаст проект. Это простейший вариант приложения "Hello World", в котором вызывается метод <xref:System.Console.WriteLine?displayProperty=nameWithType> для вывода литеральной строки "Hello World!" в окне консоли (выходных данных программы).

   Вы должны увидеть примерно следующее:

   ![Интегрированная среда разработки Visual Studio](../media/overview-ide-console-app.png)

   Код C# для вашего приложения отображается в окне редактора, который занимает большую часть пространства. Обратите внимание, что текст автоматически выделяется цветом для обозначения разных частей кода, таких как ключевые слова и типы. Кроме того, небольшие вертикальные штриховые линии кода указывают, какие фигурные скобки соответствуют друг другу, а номера строк помогут вам найти нужный код позже. Чтобы свернуть или развернуть блоки кода, используйте небольшие рамки со знаком минус. Эта функция структурирования кода позволяет скрыть ненужный код на экране. Файлы вашего проекта перечислены в окне **обозревателя решений**, которое находится справа.

   ![Visual Studio IDE с выделенными красным цветом элементами](../media/overview-ide-console-app-red-boxes.png)

   Есть и другие доступные меню и окна инструментов, но об этом позже.

1. Теперь запустите приложение. Это можно сделать, выбрав **Запуск без отладки** в меню **Отладка** в строке меню. Можно также нажать клавиши **CTRL**+**F5**.

   ![Параметры меню "Отладка" -> "Запустить без отладки"](../media/overview-start-without-debugging.png)

   Когда Visual Studio создаст приложение, откроется окно консоли с сообщением **Hello World!**. Теперь у вас есть выполняемое приложение.

   ![Окно консоли](../media/overview-console-window.png)

1. Чтобы закрыть окно консоли, нажмите любую клавишу.

1. Давайте добавим дополнительный код в приложение. Перед строкой `Console.WriteLine("Hello World!");` добавьте следующий код C#:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Этот код отображается сообщение **What is your name?** (Введите имя) в окне консоли и ожидает, чтобы пользователь ввел текст и нажал клавишу **ВВОД**.

1. Измените строку с текстом `Console.WriteLine("Hello World!");`, указав следующий код:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Снова запустите приложение, выбрав пункты **Отладка** > **Запуск без отладки** или нажав клавиши **CTRL**+**F5**.

   Visual Studio выполнит повторную сборку приложения. В открывшемся окне консоли отобразится запрос на ввод имени.

1. Введите свое имя в окне консоли и нажмите клавишу **ВВОД**.

   ![Строка ввода в окне консоли](../media/overview-console-input.png)

1. Нажмите любую клавишу, чтобы закрыть окно консоли и остановить выполняющуюся программу.

::: moniker-end

::: moniker range=">=vs-2019"

1. Запустите Visual Studio.

   Отображается начальное окно, где можно клонировать репозиторий, открыть недавно использованные проекты или создать проект.

1. Выберите **Создать проект**.

   ![Начальное окно Visual Studio для создания проекта](../media/vs-2019/start-window-create-new-project.png)

   Откроется окно **Создание проекта** с отображением нескольких *шаблонов* проектов. Шаблон содержит основные файлы и параметры, необходимые для данного типа проекта.

1. Чтобы найти нужный шаблон, введите **консоль .net core** в поле поиска. Список доступных шаблонов автоматически отфильтруется по введенным словам. Вы можете еще больше сузить поиск, выбрав **C#** в раскрывающемся списке **Язык**. Выберите шаблон **Консольное приложение (.NET Core)** и щелкните **Далее**.

    ![Создание нового проекта в Visual Studio](../media/vs-2019/create-new-project.png)

1. В окне **Настроить новый проект** введите **HelloWorld** в поле **Имя проекта**, при необходимости измените расположение каталога для вашего проекта и нажмите кнопку **Создать**.

   ![Настройка нового проекта в Visual Studio](../media/vs-2019/configure-new-project.png)

   Visual Studio создаст проект. Это простейший вариант приложения "Hello World", в котором вызывается метод <xref:System.Console.WriteLine?displayProperty=nameWithType> для вывода литеральной строки "Hello World!" в окне консоли (выходных данных программы).

   Вы должны увидеть примерно следующее:

   ![Интегрированная среда разработки Visual Studio](../media/vs-2019/overview-ide-console-app.png)

   Код C# для вашего приложения отображается в окне редактора, который занимает большую часть пространства. Обратите внимание, что текст автоматически выделяется цветом для обозначения разных частей кода, таких как ключевые слова и типы. Кроме того, небольшие вертикальные штриховые линии кода указывают, какие фигурные скобки соответствуют друг другу, а номера строк помогут вам найти нужный код позже. Чтобы свернуть или развернуть блоки кода, используйте небольшие рамки со знаком минус. Эта функция структурирования кода позволяет скрыть ненужный код на экране. Файлы вашего проекта перечислены в окне **обозревателя решений**, которое находится справа.

   ![Visual Studio IDE с выделенными красным цветом элементами](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Есть и другие доступные меню и окна инструментов, но об этом позже.

1. Теперь запустите приложение. Это можно сделать, выбрав **Запуск без отладки** в меню **Отладка** в строке меню. Можно также нажать клавиши **CTRL**+**F5**.

   ![Параметры меню "Отладка" -> "Запустить без отладки"](../media/overview-start-without-debugging.png)

   Когда Visual Studio создаст приложение, откроется окно консоли с сообщением **Hello World!**. Теперь у вас есть выполняемое приложение.

   ![Окно консоли](../media/vs-2019/overview-console-window.png)

1. Чтобы закрыть окно консоли, нажмите любую клавишу.

1. Давайте добавим дополнительный код в приложение. Перед строкой `Console.WriteLine("Hello World!");` добавьте следующий код C#:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Этот код отображается сообщение **What is your name?** (Введите имя) в окне консоли и ожидает, чтобы пользователь ввел текст и нажал клавишу **ВВОД**.

1. Измените строку с текстом `Console.WriteLine("Hello World!");`, указав следующий код:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Снова запустите приложение, выбрав пункты **Отладка** > **Запуск без отладки** или нажав клавиши **CTRL**+**F5**.

   Visual Studio выполнит повторную сборку приложения. В открывшемся окне консоли отобразится запрос на ввод имени.

1. Введите свое имя в окне консоли и нажмите клавишу **ВВОД**.

   ![Окно консоли](../media/vs-2019/overview-console-input.png)

1. Нажмите любую клавишу, чтобы закрыть окно консоли и остановить выполняющуюся программу.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Использование рефакторинга и IntelliSense

Рассмотрим несколько примеров того, как [рефакторинг](../../ide/refactoring-in-visual-studio.md) и [IntelliSense](../../ide/using-intellisense.md) помогают повысить эффективность кода.

Во-первых, переименуем переменную `name`:

1. Дважды щелкните переменную `name`, чтобы выбрать ее.

2. Введите имя переменной, **username**.

   Обратите внимание, что вокруг переменной отображается серый прямоугольник, а в поле появляется значок лампочки.

::: moniker range="vs-2017"

3. Выберите значок лампочки для отображения доступных [быстрых действий](../../ide/quick-actions.md). Выберите **Переименовать name в username**.

   ![Действие переименования в Visual Studio](../media/rename-quick-action.png)

   Переменная переименовывается во всем проекте, то есть в нашем случае только в двух местах.

   ![Анимированный GIF-файл, демонстрирующий рефакторинг переименования в Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Выберите значок лампочки для отображения доступных [быстрых действий](../../ide/quick-actions.md). Выберите **Переименовать name в username**.

   ![Действие переименования в Visual Studio](../media/vs-2019/rename-quick-action.png)

   Переменная переименовывается во всем проекте, то есть в нашем случае только в двух местах.

::: moniker-end

4. Теперь рассмотрим возможности IntelliSense. Под строкой `Console.WriteLine($"\nHello {username}!");` введите `DateTime now = DateTime.`.

   Появится поле с членами класса <xref:System.DateTime>. Кроме того, в отдельном поле отображается описание выбранного элемента.

   ![Список членов IntelliSense в Visual Studio](../media/intellisense-list-members.png)

5. Выберите член с именем **Now**, который является свойством класса, дважды щелкнув его или нажав клавишу **TAB**. Завершите строку кода, добавив в конце точку с запятой.

6. Ниже введите или вставьте следующие строки кода:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> будет немного отличаться от <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> в том, что не добавляет знак завершения строки после ее вывода. Это означает, что следующий фрагмент текста, отправляемый на вывод, будет выводиться в той же строке. Можно навести указатель мыши на каждый из этих методов в коде, чтобы просмотреть его описание.

7. Далее мы снова используем рефакторинг, чтобы сделать код более кратким. Щелкните переменную `now` в строке `DateTime now = DateTime.Now;`.

   Обратите внимание, что на поле в этой строке отображается маленький значок отвертки.

8. Щелкните значок отвертки, чтобы увидеть предложения Visual Studio. В этом случае отображается рефакторинг [Встроенная временная переменная](../../ide/reference/inline-temporary-variable.md) для удаления строки кода без изменения его общего поведения:

   ![Рефакторинг встроенной временной переменной в Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Щелкните **Встроенная временная переменная**, чтобы выполнить рефакторинг кода.

::: moniker range="vs-2017"

10. Снова запустите программу, нажав клавиши **Ctrl**+**F5**. Выходные данные выглядят следующим образом:

    ![Окно консоли с выходными данными программы](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Снова запустите программу, нажав клавиши **Ctrl**+**F5**. Выходные данные выглядят следующим образом:

    ![Окно консоли с выходными данными программы](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Отладка кода

При написании кода требуется запустить его и проверить на ошибки. Система отладки Visual Studio позволяет просматривать код с шагом в одну инструкцию, проверяя значения переменных. Можно задать *точки останова*, которые останавливают выполнение кода на определенной строке. Вы увидите, как значение переменной изменяется по мере выполнения кода, и многое другое.

Зададим точку останова, чтобы увидеть значение переменной `username` во время выполнения программы.

1. Найдите строку кода "`Console.WriteLine($"\nHello {username}!");`". Чтобы задать точку останова в этой строке кода, то есть чтобы приостановить выполнение программы в этой строке, щелкните в крайнем левом поле редактора. Кроме того, можно щелкнуть в любом месте строки кода и нажать клавишу **F9**.

   В крайнем левом поле отображается красный кружок, и код выделяется красным цветом.

   ![Точка останова в строке кода в Visual Studio](../media/breakpoint.png)

1. Начните отладку, выбрав пункты **Отладка** > **Начать отладку** или нажав клавишу **F5**.

1. Если появляется окно консоли с запросом имени, введите имя и нажмите клавишу **ВВОД**.

   Фокус возвращается в редактор кода Visual Studio, и строка кода с точкой останова выделяется желтым. Это означает, что она является следующей строкой кода, которую будет выполнять программа.

1. Наведите указатель мыши на переменную `username` для просмотра ее значения. Кроме того, можно щелкнуть `username` правой кнопкой мыши и выбрать пункт **Добавить контрольное значение**, чтобы добавить переменную в окно **контрольных значений**, где можно будет просмотреть ее значение.

   ![Значение переменной во время отладки в Visual Studio](../media/debugging-variable-value.png)

1. Чтобы разрешить программе продолжить выполнение, нажмите клавишу **F5** еще раз.

Дополнительные сведения о выполнении отладки в Visual Studio см. в статье [Обзор возможностей отладчика Visual Studio](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Настройка Visual Studio

Вы можете настроить пользовательский интерфейс Visual Studio, в том числе изменить цветовую тему по умолчанию. Чтобы задать **темную** тему, выполните следующие действия.

1. В строке меню выберите **Сервис** > **Параметры**, чтобы открыть диалоговое окно **Параметры**.

::: moniker range="vs-2017"

2. Откройте страницу параметров **Окружение** > **Общие**, измените значение **Цветовая тема** на **Темная** и щелкните **ОК**.

   Цветовая тема для всей интегрированной среды разработки изменится на тему **Темная**.

   ![Visual Studio в темной теме](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Откройте страницу параметров **Окружение** > **Общие**, измените значение **Цветовая тема** на **Темная** и щелкните **ОК**.

   Цветовая тема для всей интегрированной среды разработки изменится на тему **Темная**.

   ![Visual Studio в темной теме](../media/vs-2019/dark-theme.png)

::: moniker-end

Дополнительные сведения о других способах персонализации интегрированной среды разработки см. в разделе [Персонализация Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).