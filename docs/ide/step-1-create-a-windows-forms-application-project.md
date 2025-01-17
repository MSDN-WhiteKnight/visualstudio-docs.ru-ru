---
title: Шаг 1. Создание проекта приложения Windows Forms
ms.date: 03/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f529d737816406b3a4f6aa9921a8dc6b902d2fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979874"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Шаг 1. Создание проекта приложения Windows Forms

Первый шаг в создании программы для просмотра изображений — это создание проекта приложения Windows Forms.

 > [!TIP]
 > ![Ссылка на видео](../data-tools/media/playvideo.gif)Видеоверсию этого раздела см. на страницах [Tutorial 1: reate a picture viewer in Visual Basic - Video 1](http://go.microsoft.com/fwlink/?LinkId=205209) (Руководство 1. Создание приложения для просмотра рисунков на Visual Basic — видео 1) или [Tutorial 1: Create a picture viewer in C# - Video 1](http://go.microsoft.com/fwlink/?LinkId=205199) (Руководство 1. Создание приложения для просмотра рисунков на C# —видео 1). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Откройте Visual Studio 2017.

1. В строке меню выберите **Файл** > **Создать** > **Проект**. Диалоговое окно должно выглядеть следующим образом.

     ![Диалоговое окно "Новый проект"](../ide/media/newprojectdialogcallouts.png)<br/>
*Диалоговое окно **Новый проект***

2. Выберите **Visual C#** или **Visual Basic** в левой области диалогового окна **Новый проект**.

3. В списке шаблонов выберите **Приложение Windows Forms (.NET Framework)** . Назовите новую форму **PictureViewer** и нажмите кнопку **ОК**.

    >[!NOTE]
    >Если вы не видите шаблон **Приложение Windows Forms (.NET Framework)** , используйте Visual Studio Installer, чтобы установить рабочую нагрузку **Разработка классических приложений .NET**.<br/><br/>![Рабочая нагрузка разработки классических приложений .NET в Visual Studio Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Дополнительные сведения см. в разделе [Установка Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Запустите Visual Studio 2019.

1. На начальном экране выберите **Создать проект**.

   ![Просмотр окна "Создание проекта"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. В поле поиска окна **Создание проекта** введите *Windows Forms*. Затем выберите **Visual Basic** в списке языков и **Windows** в списке платформ. 

   Применив фильтры языка и платформы, выберите шаблон **Приложение Windows Forms (.NET Framework)** и нажмите кнопку **Далее**.

   ![Выбор шаблона Visual Basic для приложения Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Если шаблон **Приложение Windows Forms (.NET Framework)** отсутствует, его можно установить из окна **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > После этого в Visual Studio Installer выберите рабочую нагрузку **Разработка классических приложений .NET**.
   > 
   > ![Рабочая нагрузка .NET Core в Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Вам может быть предложено сохранить результаты работы; в таком случае сделайте это. Выберите **Продолжить**, чтобы установить рабочую нагрузку. 

1. В поле **Имя проекта** окна *Настроить новый проект* введите **PictureViewer**. Затем нажмите **Создать**.

::: moniker-end

Visual Studio создает решение для программы. Решение играет роль контейнера для всех проектов и файлов, необходимых программе. Более подробно эти термины поясняются далее в этом учебнике.

## <a name="about-the-windows-forms-application-project"></a>О проекте приложения Windows Forms

1. Среда разработки содержит три окна: главное окно, **Обозреватель решений** и окно **Свойства**.

     Если какое-либо из этих окон отсутствует, восстановите макет окон по умолчанию, выбрав в строке меню **Окно** > **Сбросить макет окна**. Можно также отобразить окна с помощью команд меню. В строке меню выберите **Вид** > **Окно "Свойства"** или **Обозреватель решений**. Если открыты какие-либо другие окна, закройте их с помощью кнопки **Закрыть** (x) в верхнем правом углу.

    ::: moniker range="vs-2017"

    - **Главное окно**. В этом окне выполняется основная часть работы, например работа с формами и редактирование кода. В окне показана форма в **редакторе форм**. В верхней части окна находятся две вкладки — вкладка **Начальная страница** и вкладка **Form1.cs [Design]** . (В Visual Basic имя вкладки заканчивается на *.vb*, а не на *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **Главное окно**. В этом окне выполняется основная часть работы, например работа с формами и редактирование кода. В окне показана форма в **редакторе форм**.

    ::: moniker-end

    - **Окно "Обозреватель решений"** . В этом окне можно просматривать все элементы, входящие в решение, и переходить к ним. Если выбрать файл, содержимое в окне **Свойства** изменится. Если открыть файл кода (с расширением *.cs* в Visual C# и *.vb* в Visual Basic), откроется файл кода или конструктор для файла кода. Конструктор — это визуальная поверхность, на которую можно добавлять элементы управления, такие как кнопки и списки. При работе с формами Visual Studio такая поверхность называется **конструктор Windows Forms**.

    - **Окно "Свойства"** . В этом окне производится изменение свойств элементов, выбранных в других окнах. Например, выбрав форму Form1, можно изменить ее название путем задания свойства **Text**, а также изменить цвет фона путем задания свойства **Backcolor**.

    > [!NOTE]
    > В верхней строке в **обозревателе решений** отображается текст **Решение "PictureViewer" (1 проект)** . Это означает, что Visual Studio автоматически создала для вас решение. Решение может содержать несколько проектов, но пока что вы будете работать с решениями, которые содержат только один проект.

1. В строке меню выберите **Файл** > **Сохранить все**.

     Другой вариант — нажать кнопку **Сохранить все** на панели инструментов, показанной на следующем рисунке.

     ![Кнопка "Сохранить все" на панели инструментов](../ide/media/express_iconsaveall.png)<br/>
     *Кнопка **Сохранить все** на панели инструментов*

     Visual Studio автоматически заполняет имя папки и имя проекта, а затем сохраняет проект в папке проектов.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: [Шаг 2. Запуск программы](../ide/step-2-run-your-program.md).

- Предыдущая статья с общими сведениями: [Руководство 1. Создание средства просмотра рисунков](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>См. также

- [Создание новой формы Windows Forms](/dotnet/framework/winforms/creating-a-new-windows-form/)