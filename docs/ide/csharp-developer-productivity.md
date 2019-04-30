---
title: Повышение производительности разработок на .NET
description: Общие сведения о навигации, анализе кода, модульном тестировании и других возможностях, которые помогут вам эффективнее писать код .NET.
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 3e1f82a58dac3b0a6f607d1de7f881c5de9e91aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973367"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Руководство по повышению производительности работы в Visual Studio для разработчиков на платформе C#

Узнайте, как Visual Studio выводит производительность труда разработчиков на новый уровень. Воспользуйтесь новыми возможностями для повышения производительности и эффективности работы, такими как переход к декомпилированным сборкам, варианты имен переменных, предлагаемые в процессе ввода, иерархическое представление в **обозревателе тестов**, команда "Перейти ко всем" (**CTRL**+**T**) для перехода к объявлениям файлов, типов, членов и символов, интеллектуальный **помощник по исправлению ошибок**, настройка и применение стиля кода, а также разнообразные возможности рефакторинга и исправления ошибок в коде.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Мне привычнее использовать сочетания клавиш из другого редактора

::: moniker range="vs-2017"

**Новая возможность в Visual Studio 2017 версии 15.8**

::: moniker-end

Если вы переходите из другой интегрированной среды разработки или среды написания кода, вы можете изменить схему клавиатуры на *Visual Studio Code* или *ReSharper (Visual Studio)*:

![Схемы клавиатуры в Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Некоторые расширения также предоставляют схемы клавиатуры.

- [Сочетания клавиш в Visual Studio (IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Эмуляция Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Ниже приведены широко используемые сочетания клавиш в Visual Studio.

| Сочетание клавиш (все профили) | Команда | Описание |
|-|-|-|
| **CTRL**+**T** | Перейти ко всем | Переход к любому объявлению файла, типа, элемента или символа |
| **F12** (также **CTRL**+**щелчок**) | Перейти к определению | Переход к месту определения символа |
| **CTRL**+**F12** | Перейти к реализации | Переход от любого базового типа или элемента к его различным реализациям |
| **SHIFT**+**F12** | Найти все ссылки | Просмотр всех символьных или литеральных ссылок |
| **CTRL**+**.** (также **ALT**+**ВВОД** в профиле C#) | Быстрые действия и операции рефакторинга | Просмотр доступных исправлений кода, действия для создания кода, операций рефакторинга или других быстрых действий в выбранной позиции курсора или для выбранного кода |
| **CTRL**+**D** | Дублировать строку | Дублирование строки кода, в которой находится курсор (доступно в **Visual Studio 2017 версии 15.6** и более поздних версиях) |
| **SHIFT**+**ALT**+**+**/**-** | Расширение или сужение выделенного фрагмента | Расширение или сужение выделенного в настоящее время фрагмента в редакторе (доступно в **Visual Studio 2017 версии 15.5** или более поздней) |
| **SHIFT** + **ALT** + **.** | Переместить курсор на следующее совпадение | Добавляет выделение и курсор в следующем месте, соответствующем текущему выделению (доступно в **Visual Studio 2017 версии 15.8** и более поздних версий) |
| **CTRL**+**Q** | Поиск | Поиск всех параметров Visual Studio |
| **F5** | Начало отладки | Начало отладки приложения |
| **CTRL**+**F5** | Запуск без отладки | Запуск приложения без отладки |
| **CTRL**+**K**,**D** (профиль по умолчанию) или **CTRL**+**E**,**D** (профиль C#) | [Форматировать документ](code-styles-and-quick-actions.md#format-document-command) | Очистка нарушений форматирования в файле на основе заданных параметров перевода строки, интервалов и отступов |
| **CTRL**+**\\**,**CTRL**+**E** (профиль по умолчанию) или **CTRL**+**W**,**E** (профиль C#) | Просмотреть список ошибок | Просмотр всех ошибок в документе, проекте или решении |
| **Alt** + **PgUp или PgDn** | Перейти к следующей или предыдущей проблеме | Переход к предыдущей или следующей ошибке, предупреждению или предложению в документе (доступно в **Visual Studio 2017 версии 15.8** и более поздних версий) |

> [!NOTE]
> Некоторые расширения отменяют привязку настраиваемых сочетаний клавиш по умолчанию в Visual Studio. Чтобы использовать вышеприведенные команды, восстановите заданные по умолчанию сочетания клавиш в Visual Studio, выбрав пункты меню **Сервис** > **Импорт и экспорт параметров** > **Сбросить все параметры** или **Сервис** > **Параметры** > **Клавиатура** > **Сброс**.

Дополнительные сведения о сочетаниях клавиш и командах см. в [этой статье](../ide/tips-and-tricks-for-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Быстрый переход к файлам или типам

В Visual Studio 2017 есть функция **Перейти ко всем** (**CTRL**+**T**). Функция **Перейти ко всем** позволяет быстро перейти к объявлению любого файла, типа, члена или символа.

- Изменить расположение этой панели поиска или отключить динамический предварительный просмотр навигации можно с помощью значка **шестеренки**.
- Для фильтрации результатов используйте синтаксис запроса, например `t mytype`.
- Область поиска можно ограничить текущим документом.
- При сопоставлении поддерживается "верблюжий" стиль.

![Команда "Перейти ко всем" в Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules-on-a-codebase"></a>Принудительное применение правил стиля кода в базе кода

Можно использовать файл *.editorconfig*, чтобы определить соглашения о написании кода и привязать их к исходному коду.

::: moniker range="vs-2017"

- Вы можете установить [расширение языковых служб EditorConfig](https://aka.ms/editorconfig), чтобы упростить добавление и редактирование файла *.editorconfig* в Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

- Автоматически создайте *EDITORCONFIG*-файл с использованием параметров стиля кода, последовательно выбрав **Сервис** > **Параметры** > **Текстовый редактор** > **C#** > **Стиль кода**.

   ![Создайте EDITORCONFIG-файл с использованием параметров в VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Попробуйте [расширение IntelliCode для Visual Studio](/visualstudio/intellicode/intellicode-visual-studio). Это экспериментальное расширение определяет стили существующего кода, а затем создает непустой файл *.editorconfig* с помощью параметров определенного стиля.

- См. [документацию по всем вариантам соглашений о написании кода в .NET](editorconfig-code-style-settings-reference.md).

- Пример файла *.editorconfig* см. в [этой публикации Gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8).

![Применение стиля кода в Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="refactorings-and-code-fixes"></a>Рефакторинг и исправления кода

В Visual Studio включено множество возможностей рефакторинга, действий по созданию кода и исправлений кода. Красной волнистой линией обозначаются ошибки, зеленой волнистой линией — предупреждения, а тремя серыми точками — предлагаемые варианты кода. Чтобы получить доступ к исправлениям кода, щелкните значок лампочки или отвертки либо нажмите клавиши **CTRL**+**.** или **ALT**+**ВВОД**. Для каждого исправления отображается окно предварительного просмотра, в котором в реальном времени можно увидеть, как будет работать исправление.

Популярные исправления и операции рефакторинга:

- *Переименование*
- *Извлечение метода*
- *Изменение сигнатуры метода*
- *Создание конструктора*
- *Создание метода*
- *Переместить тип в файл*
- *Добавить проверку значений NULL*
- *Добавить параметр*
- *Удалить ненужные директивы Using*
- *Цикл Foreach в запрос LINQ или метод LINQ*
- *Подъем элементов*
- Дополнительные сведения см. в статье [Возможности создания кода в Visual Studio](code-generation-in-visual-studio.md).

Вы можете [установить анализаторы FxCop](../code-quality/install-fxcop-analyzers.md), чтобы отметить проблемы в коде. Вы также можете создать собственные исправления кода или операции рефакторинга с помощью [анализаторов Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).

Участники сообщества написали бесплатные расширения, которые реализуют дополнительные проверки кода:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Рефакторинг в Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Функции поиска использования, перехода к реализации и перехода к декомпилированным сборкам

Visual Studio обладает множеством функций, упрощающих [навигацию и поиск по коду](../ide/navigating-code.md).

| Функция | Сочетание клавиш | Сведения и усовершенствования |
|- | - | -|
| Найти все ссылки | **SHIFT**+**F12**| Результаты выделяются цветом и могут быть сгруппированы по проекту, определению и ссылочному типу, например read или write. Можно также "блокировать" результаты. |
| Перейти к реализации | **CTRL**+**F12** | Вы можете использовать команду "Перейти к определению" для ключевого слова `override`, чтобы перейти к переопределяемому члену. |
| Перейти к определению | **F12** или **CTRL**+**щелчок**| Удерживайте клавишу **CTRL** во время щелчка, чтобы перейти к определению. |
| Показать определение | **ALT**+**F12** | Встроенное представление определения |
| Визуализатор структуры | Серые пунктирные линии между фигурными скобками | Наведите указатель мыши для просмотра структуры кода |
| Переход к декомпилированным сборкам | **F12** или **CTRL**+**щелчок** | Перейдите к внешнему источнику (декомпилированному с помощью ILSpy), включив эту функцию: **Сервис** > **Параметры** > **Текстовый редактор** > **C#** > **Дополнительно** > **Enable navigation to decompiled sources** (Включение навигации к декомпилированным источникам). |

!["Перейти ко всем" и "Найти все ссылки"](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Усовершенствования IntelliSense

Скачайте [расширение IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode), чтобы получить [контекстно зависимое завершение кода](/visualstudio/intellicode/intellicode-visual-studio) вместо алфавитного списка. Вы также можете обучить [пользовательскую модель IntelliSense](/visualstudio/intellicode/custom-model-faq) на основе собственных библиотек домена.

## <a name="unit-testing"></a>Модульное тестирование

Начиная с версии Visual Studio 2017 введено множество улучшений в тестировании. Тестирование можно выполнить с помощью платформ MSTest v1, MSTest v2, NUnit или XUnit.

- Тесты можно быстро обнаружить с помощью **обозревателя тестов**.

- Вы можете упорядочить тесты в **обозревателе тестов** с помощью новой *иерархической сортировки*.

   ![Иерархическое представление для обозревателя тестов в Visual Studio](../ide/media/VSGuide_Testing.png)

- [Live Unit Testing](../test/live-unit-testing.md) постоянно выполняет тесты, на которые влияют изменения в коде, и обновляет значки в редакторе, сообщая о результатах тестирования. Вы можете включать и исключать определенные тесты или тестовые проекты в своем наборе динамических тестов. (Только в Visual Studio Enterprise Edition.)

## <a name="debugging"></a>Отладка

Некоторые из возможностей отладки Visual Studio включают в себя:

::: moniker range=">=vs-2019"

- Возможность поиска строки в окнах **Контрольные значения**, **Видимые** и **Локальные**.
- Функция *выполнения до щелчка* позволяет навести указатель на строку кода, выбрать появившийся зеленый значок воспроизведения и выполнить программу до этой строки.
- Новый **помощник по исправлению ошибок** размещает наиболее важные сведения, например о том, какая переменная имеет значение `null` в `NullReferenceException`, в начале диалогового окна.
- [Обратная](../debugger/view-historical-application-state.md) отладка позволяет возвращаться к точкам останова или шагам и просматривать предыдущее состояние приложения.
- [Отладка моментального снимка](/azure/application-insights/app-insights-snapshot-debugger) позволяет изучить состояние динамического веб-приложения в момент, когда возникло исключение (нужно работать в Azure).

::: moniker-end

::: moniker range="vs-2017"

- Функция *выполнения до щелчка* позволяет навести указатель на строку кода, выбрать появившийся зеленый значок воспроизведения и выполнить программу до этой строки.
- Новый **помощник по исправлению ошибок** размещает наиболее важные сведения, например о том, какая переменная имеет значение `null` в `NullReferenceException`, в начале диалогового окна.
- [Обратная](../debugger/view-historical-application-state.md) отладка позволяет возвращаться к точкам останова или шагам и просматривать предыдущее состояние приложения.
- [Отладка моментального снимка](/azure/application-insights/app-insights-snapshot-debugger) позволяет изучить состояние динамического веб-приложения в момент, когда возникло исключение (нужно работать в Azure).

::: moniker-end

![Помощник по исправлению ошибок в Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Управление версиями

Вы можете использовать Git или TFVC для хранения и обновления кода в Visual Studio.

::: moniker range=">=vs-2019"

- Установите расширение [Запросы на вытягивание для Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs), чтобы создавать, просматривать, извлекать и выполнять запросы на вытягивание, не выходя из Visual Studio.

::: moniker-end

- Можно упорядочить локальные изменения с помощью [Team Explorer](reference/team-explorer-reference.md), а также использовать строку состояния для отслеживания ожидающих фиксаций и изменений.

- Вы можете настроить для проектов ASP.NET непрерывную интеграцию и поставку в Visual Studio с помощью расширения [Инструменты непрерывной поставки для Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio).

![Система управления версиями в Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>О каких еще функциях мне нужно знать?

Ниже перечислены функции редактора и возможности, повышающие производительность и эффективность написания кода. Некоторые из них может потребоваться включить, так как по умолчанию они отключены (например, потому что они индексируют данные на компьютере, конфликтуют с другими функциями или в настоящее время являются экспериментальными).

| Функция | Подробные сведения | Включение |
|-|-|-|
| Поиск файл в обозревателе решений | Выделяет активный файл в **обозревателе решений**. | **Сервис** > **Параметры** > **Проекты и решения** > **Отслеживать активный элемент в обозревателе решений** |
| Добавление директив using для типов в базовых сборках и пакетах NuGet | Для типа, на который нет ссылок, выводится значок лампочки с ошибкой с предложением установить пакет NuGet | **Сервис** > **Параметры** > **Текстовый редактор** > **C#** > **Дополнительно** > **Предлагать using для типов в эталонных сборках** и **Предлагать using для типов в пакетах NuGet** |
| Включить полный анализ решения | Вы можете просмотреть все ошибки в решении в **списке ошибок** | **Сервис** > **Параметры** > **Текстовый редактор** > **C#** > **Дополнительно** > **Включить полный анализ решения** |
| Включение навигации к декомпилированным источникам | Позволяет использовать функцию "Перейти к определению" для типов и членов из внешних источников и применять декомпилятор ILSpy для отображения тел методов. | **Сервис** > **Параметры** > **Текстовый редактор** > **C#** > **Дополнительно** > **Разрешить переход к декомпилированным исходным файлам** |
| Режим завершения/подсказки | Изменяет работу завершения в IntelliSense. Разработчики, использующие фоновые действия IntelliJ, как правило, изменяют этот режим на отличный от режима по умолчанию. | **Меню** > **Изменить** > **IntelliSense** > **Переключить режим завершения** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Отображает справочные сведения о коде и журнал изменений в редакторе. (Индикаторы системы управления версиями средства CodeLens недоступны в Visual Studio Community Edition.) | **Сервис** > **Параметры** > **Текстовый редактор** > **Все языки** > **CodeLens** |
| [Фрагменты кода](../ide/visual-csharp-code-snippets.md) | Помогают создать заглушку стандартного кода. | Введите имя фрагмента и дважды нажмите клавишу **TAB**. |