---
title: Пошаговое руководство. Построение приложения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7b3921d9ef11ba01cad6d25f69f3a484e27c929
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698353"
---
# <a name="walkthrough-building-an-application"></a>Пошаговое руководство. Построение приложения

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Выполнив это пошаговое руководство, вы ознакомитесь с несколькими параметрами, которые можно настроить при создании приложений с помощью Visual Studio. Среди прочего, вы создадите настраиваемую конфигурацию сборки, скроете определенные предупреждения и расширите выходные данные о сборке для примера приложения.

В этом разделе содержатся следующие подразделы.

[Установка примера приложения](../ide/walkthrough-building-an-application.md#BKMK_installapp)

[Создание настраиваемой конфигурации сборки](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)

[Сборка приложения](../ide/walkthrough-building-an-application.md#BKMK_building)

[Скрытие предупреждений компилятора](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)

[Отображение дополнительных сведений о сборке в окне вывода](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)

[Создание сборки выпуска](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)

## <a name="BKMK_installapp"></a> Установка примера приложения

Вы будете использовать диалоговое окно **Расширения и обновления** для поиска и установки примера [Introduction to Building WPF Applications](http://code.msdn.microsoft.com/Introduction-to-Building-b8d16419?SRC=VSIDE) (Введение в создание приложений WPF) из коллекции примеров на веб-сайте Майкрософт. Коллекция примеров содержит различные примеры проектов и кода, которые можно скачать и посмотреть при планировании и разработке приложений.

#### <a name="to-install-the-sample-application"></a>Установка примера приложения

1. В строке меню выберите **Сервис**, **Расширения и обновления**.

2. Выберите категорию **В сети** и затем категорию **Галерея примеров**.

3. Укажите `Introduction` в поле поиска, чтобы найти пример.

    ![Диалоговое окно "Расширения и обновления"](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")

4. В списке результатов выберите **Общие сведения о сборке приложений WPF (Visual C#)** или **Общие сведения о сборке приложений WPF (Visual Basic)**.

5. Нажмите кнопку **Скачать**, а затем — кнопку **Закрыть**.

   Пример "Общие сведения о сборке приложений WPF" появляется в диалоговом окне **Новый проект**.

#### <a name="to-create-a-solution-for-the-sample-application"></a>Создание решения для примера приложения

1. Открывается диалоговое окно **Новый проект**.

     ![Выбор пунктов "Файл", "Создать", "Проект"](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. В категории **Установленные** выберите категорию **Примеры**, чтобы отобразить пример "Общие сведения о сборке приложений WPF".

3. Назовите решение `IntroWPFcsharp` для Visual C#.

     ![Диалоговое окно "Новый проект", установленные примеры](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")

     OR

     Назовите решение `IntroWPFvb` для Visual Basic.

     ![Диалоговое окно "Новый проект", пример для Visual Basic](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")

4. Нажмите кнопку **ОК** .

## <a name="BKMK_CreateBuildConfig"></a> Создание настраиваемой конфигурации сборки

При создании решения конфигурации отладочной сборки и сборки выпуска и их целевые платформы по умолчанию определяются для решения автоматически. Затем вы можете настроить эти конфигурации или создать собственные. Конфигурации указывают тип сборки. Целевые платформы указывают операционную систему, на которое ориентировано приложение для этой конфигурации. Дополнительные сведения см. в разделах [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md), [Общие сведения о платформах сборки](../ide/understanding-build-platforms.md) и [Конфигурации отладки и выпуска проекта](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

Конфигурации и параметры платформы можно изменять или создавать с помощью диалогового окна **Диспетчер конфигураций**. В этой процедуре вы создадите конфигурацию сборки для тестирования.

#### <a name="to-create-a-build-configuration"></a>Создание конфигурации сборки

1. Откройте диалоговое окно **Диспетчер конфигураций**.

    ![Меню "Сборка", команда "Диспетчер конфигураций"](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")

2. В списке **Активная конфигурация решения** выберите **Создать**.

3. В диалоговом окне **Создание конфигурации решения** введите для новой конфигурации имя `Test`, скопируйте параметры из существующей конфигурации отладки и нажмите кнопку **ОК**.

    ![Диалоговое окно конфигурации нового решения](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")

4. В списке **Активная платформа решения** выберите **Создать**.

5. В диалоговом окне **Создание платформы решения** выберите **x64** и не копируйте параметры из платформы x86.

    ![Диалоговое окно платформы нового решения](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")

6. Нажмите кнопку **ОК** .

   Активная конфигурация решения была изменена на "Тест", а для активной платформы решения задано значение x64.

   ![Диспетчер конфигураций с конфигурацией тестов](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")

   Активную конфигурацию решения можно быстро проверить или изменить с помощью списка **Конфигурации решения** на панели инструментов **Стандартная**.

   ![Стандартная панель инструментов параметра конфигурации решения](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")

## <a name="BKMK_building"></a> Сборка приложения

Далее вам предстоит создать решение с помощью настраиваемой конфигурации сборки.

#### <a name="to-build-the-solution"></a>Построение решения

- В строке меню последовательно выберите **Сборка**и **Собрать решение**.

  Окно **Вывод** отображает результат сборки. Построение выполнено успешно, но было создано несколько предупреждений.

  Рис. 1. Предупреждения Visual Basic

  ![Окно выходных данных Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

  Рис. 2. Visual C# предупреждения

  ![Окно выходных данных Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

## <a name="BKMK_hidewarning"></a> Скрытие предупреждений компилятора

Вы можете временно скрыть некоторые предупреждения во время сборки, чтобы они не засоряли выходные данные сборки.

#### <a name="to-hide-a-specific-visual-c-warning"></a>Скрытие определенного предупреждения Visual C#

1. В **обозревателе решений** выберите узел проекта верхнего уровня.

2. В строке меню выберите **Вид**, **Страницы свойств**.

     Открывается **Конструктор проектов**.

3. Выберите страницу **Сборка** и затем в поле **Отключить предупреждения** укажите номер предупреждения `1762`.

     ![Страница построения, конструктор проектов](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")

     Дополнительные сведения см. в разделе [Страница "Сборка" в конструкторе проектов (C#)](../ide/reference/build-page-project-designer-csharp.md).

4. Постройте решение.

     Окно **Вывод** отображает только сводные данные о сборке.

     ![Окно выходных данных, предупреждения сборки Visual C&#35;](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")

#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Отключение всех предупреждений сборки в Visual Basic

1. В **обозревателе решений** выберите узел проекта верхнего уровня.

2. В строке меню выберите **Вид**, **Страницы свойств**.

    Открывается **Конструктор проектов**.

3. На странице **Компиляция** установите флажок **Выключить все предупреждения**.

    ![Страница компиляции, конструктор проектов](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")

    Дополнительные сведения см. в статье [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Постройте решение.

   Окно **Вывод** отображает только сводные данные о сборке.

   ![Окно выходных данных, предупреждения сборки Visual Basic](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")

   Дополнительные сведения см. в разделе [Практическое руководство. Отключение предупреждений компилятора](../ide/how-to-suppress-compiler-warnings.md).

## <a name="BKMK_outputdetails"></a> Отображение дополнительных сведений о сборке в окне вывода

Вы можете изменить объем информации, отображаемый о процессе сборки в окне **Вывод**. В общем случае задан минимальный уровень детализации сборки, при котором в окне **Вывод** отображается только сводка по процессу сборки вместе с высокоприоритетными предупреждениями или ошибками. Чтобы отобразить дополнительные сведения о сборке, см. раздел [Диалоговое окно "Параметры", "Проекты и решения", "Сборка и запуск"](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> При отображении дополнительных сведений сборка будет занимать больше времени.

#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Изменение объема сведений в окне вывода

1. Откройте диалоговое окно **Параметры**.

    ![Команда "Параметры" в меню "Сервис"](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")

2. Выберите категорию **Проекты и решения** и затем страницу **Сборка и запуск**.

3. В списке **Степень подробности сообщений при сборке проекта MSBuild** выберите значение **Обычная** и нажмите кнопку **ОК**.

4. В строке меню выберите **Сборка** и **Очистить решение**.

5. Выполните сборку решения и просмотрите сведения в окне **Вывод**.

    Сведения о сборке включают в себя время запуска сборки (находится в начале), порядок обработки файлов и затраченное на это время (находится в конце). Они также включают фактический синтаксис компилятора, запускаемый Visual Studio при сборке.

    Например, параметр [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) в сборке Visual C# выводит указанный вами ранее код предупреждения 1762, а также три других предупреждения.

    В сборке Visual Basic параметр [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) не включает в себя определенные исключаемые предупреждения, поэтому предупреждения не отображаются.

   > [!TIP]
   > В окне **Вывод** можно искать содержимое, отобразив диалоговое окно **Найти** нажатием клавиш CTRL+F.

   Дополнительные сведения см. в разделе [Практическое руководство. Просмотр, сохранение и настройка файлов журнала сборки](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="BKMK_releasebuild"></a> Создание сборки выпуска

Вы можете создать версию примера приложения, оптимизированную для поставки. Для сборки выпуска вы указываете, что исполняемый файл копируется в общую сетевую папку перед запуском сборки.

Дополнительные сведения см. в разделе [Практическое руководство. Изменение выходного каталога построения](../ide/how-to-change-the-build-output-directory.md) и [построение и очистка проектов и решений в Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

#### <a name="to-specify-a-release-build-for-visual-basic"></a>Указание сборки выпуска для Visual Basic

1. Открывается **Конструктор проектов**.

     ![Меню "Просмотр", команда "Страница свойств"](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Откройте вкладку **Компиляция**.

3. В списке **Конфигурация** выберите **Выпуск**.

4. В списке **Платформа** выберите **x86**.

5. В поле **Выходной путь сборки** укажите сетевой путь.

     Например, можно указать \\\myserver\builds.

    > [!IMPORTANT]
    > Может появиться окно с предупреждением о том, что указанная вами сетевая общая папка может быть ненадежна. Если вы доверяете указанному расположению, нажмите кнопку **ОК** в окне сообщения.

6. Постройте приложение.

     ![Команда "Собрать решение" в меню "Сборка"](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

#### <a name="to-specify-a-release-build-for-visual-c"></a>Указание сборки выпуска для Visual C\#

1. Открывается **Конструктор проектов**.

    ![Меню "Просмотр", команда "Страница свойств"](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. Перейдите на страницу **Сборка**.

3. В списке **Конфигурация** выберите **Выпуск**.

4. В списке **Платформа** выберите **x86**.

5. В поле **Путь для создаваемых файлов** укажите сетевой путь.

    Например, можно указать \\\myserver\builds.

   > [!IMPORTANT]
   > Может появиться окно с предупреждением о том, что указанная вами сетевая общая папка может быть ненадежна. Если вы доверяете указанному расположению, нажмите кнопку **ОК** в окне сообщения.

6. Постройте приложение.

    ![Команда "Собрать решение" в меню "Сборка"](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Исполняемый файл копируется в указанный сетевой путь. Для него используется путь \\\myserver\builds\\*имя_файла*.exe.

   Поздравляем! Вы успешно выполнили это пошаговое руководство.

## <a name="see-also"></a>См. также

- [Пошаговое руководство: Сборка проекта (C++)](https://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)
- [Общие сведения о предварительной компиляции проектов веб-приложений ASP.NET](https://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [Пошаговое руководство: Использование MSBuild](../msbuild/walkthrough-using-msbuild.md)
