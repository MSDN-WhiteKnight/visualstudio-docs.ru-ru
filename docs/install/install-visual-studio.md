---
title: Установка Visual Studio
titleSuffix: ''
description: Сведения о поэтапной установке среды Visual Studio.
ms.date: 04/16/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4833c6e8e1391028fbb034ff96967450d006356a
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263728"
---
# <a name="install-visual-studio"></a>Установка Visual Studio

::: moniker range="vs-2019"

Вас приветствует Visual Studio 2019! В этой версии можно легко выбрать и установить только необходимые компоненты. Поскольку она занимает меньше памяти, она быстро устанавливается и при этом меньше влияет на систему.

::: moniker-end

::: moniker range="vs-2017"

Предлагаем ознакомиться с новым способом установки Visual Studio. В этой версии стало проще выбирать и устанавливать только нужные компоненты. Мы также сократили минимальные требования к месту на диске, поэтому установка Visual Studio выполняется еще быстрее и с меньшим влиянием на функционирование системы.

::: moniker-end

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Установка Visual Studio для Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

Хотите ознакомиться с другими новыми возможностями этой версии? Обратитесь к [заметкам о выпуске](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

Хотите ознакомиться с другими новыми возможностями этой версии? Обратитесь к [заметкам о выпуске](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

Готовы к установке? Мы последовательно опишем каждое действие.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Шаг 1. Подготовка компьютера к установке Visual Studio

Перед началом установки Visual Studio:

::: moniker range="vs-2017"

1. Проверьте [требования к системе](/visualstudio/productinfo/vs2017-system-requirements-vs). Так вы узнаете, поддерживает ли ваш компьютер Visual Studio 2017.

1. Примените актуальные обновления Windows. Эти обновления гарантируют, что на компьютере установлены последние обновления для системы безопасности и необходимые системные компоненты для Visual Studio.

1. Перезагрузите систему. Перезагрузка гарантирует, что ожидающие установки или обновления компоненты не будут препятствовать установке Visual Studio.

1. Освободите место. Удалите ненужные файлы и приложения с системного диска. Например, запустите приложение очистки диска.

::: moniker-end

::: moniker range="vs-2019"

1. Проверьте [требования к системе](/visualstudio/releases/2019/system-requirements). Так вы узнаете, поддерживает ли ваш компьютер Visual Studio 2019.

1. Примените актуальные обновления Windows. Эти обновления гарантируют, что на компьютере установлены последние обновления для системы безопасности и необходимые системные компоненты для Visual Studio.

1. Перезагрузите систему. Перезагрузка гарантирует, что ожидающие установки или обновления компоненты не будут препятствовать установке Visual Studio.

1. Освободите место. Удалите ненужные файлы и приложения с системного диска. Например, запустите приложение очистки диска. 

::: moniker-end

::: moniker range="vs-2017"

Сведения об использовании предыдущих версий Visual Studio параллельно с Visual Studio 2017 см. в разделе [Совместимость с предыдущими версиями](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Сведения об использовании предыдущих версий Visual Studio параллельно с Visual Studio 2019 см. в разделе [Целевая платформа и совместимость для Visual Studio 2019](/visualstudio/releases/2019/compatibility/).

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Шаг 2.Скачивание Visual Studio

Теперь скачайте файл начального загрузчика Visual Studio. Для этого нажмите кнопку ниже, выберите нужный выпуск Visual Studio, щелкните **Сохранить**, а затем **Открыть папку**.

::: moniker range="vs-2017"

 > [!div class="button"]
 > [Скачать Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

 > [!div class="button"]
 > [Скачать Visual Studio 2012](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Шаг 3. Установка установщика Visual Studio

Запустите файл начального загрузчика, чтобы установить Visual Studio Installer. Новый установщик имеет меньший размер и включает все необходимое для установки и настройки Visual Studio.

1. В папке **Загрузки** дважды щелкните файл начального загрузчика, имя которого совпадает с именем одного из следующих файлов или похоже на них:

   * **vs_community.exe** для Visual Studio Community.
   * **vs_professional.exe** для Visual Studio Professional;
   * **vs_enterprise.exe** для Visual Studio Enterprise;

   Если появляется оповещение системы контроля учетных записей, нажмите кнопку **Да**.

2. Мы попросим вас принять [условия лицензии](https://visualstudio.microsoft.com/license-terms/) и [заявление о конфиденциальности](https://privacy.microsoft.com/privacystatement) корпорации Майкрософт. Нажмите **Продолжить**.

   ![Условия лицензии и заявление о конфиденциальности](media/privacy-and-license-terms.png "Условия лицензии и заявление о конфиденциальности корпорации Майкрософт")

## <a name="step-4---choose-workloads"></a>Шаг 4. Выбор рабочих нагрузок

Когда завершится установка программы установки, вы можете с ее помощью выбрать нужные наборы функций (рабочих нагрузок). Ниже описывается порядок действий.

 ::: moniker range="vs-2017"

1. Найдите нужную рабочую нагрузку на экране **Установка Visual Studio**.

   ![Visual Studio 2017: Установка рабочей нагрузки](../install/media/vs-installer-installing-workloads.png)

     Например, выберите рабочую нагрузку "Разработка классических приложений .NET". В нее входит основной редактор кода по умолчанию, который предоставляет базовую поддержку редактирования кода для более чем 20 языков, возможность открывать и изменять код в любой папке без наличия проекта и интегрированное управление исходным кодом.

1. Выбрав нужные рабочие нагрузки, нажмите кнопку **Установить**.

    Далее будут отображаться экраны состояния, на которых демонстрируется ход установки Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. После установки новых рабочих нагрузок и компонентов выберите команду **Запуск**.

   ![Visual Studio 2019: Установка рабочей нагрузки](../install/media/vs-2019/vs-installer-workloads.png)

     Например, выберите рабочую нагрузку "ASP.NET и разработка веб-приложений". В нее входит основной редактор кода по умолчанию, который предоставляет базовую поддержку редактирования кода для более чем 20 языков, возможность открывать и изменять код в любой папке без наличия проекта и интегрированное управление исходным кодом.

1. Выбрав нужные рабочие нагрузки, нажмите кнопку **Установить**.

    Далее будут отображаться экраны состояния, на которых демонстрируется ход установки Visual Studio.

 ::: moniker-end

> [!TIP]
> В любой момент после установки можно установить рабочие нагрузки или компоненты, которые не были установлены изначально. Если среда Visual Studio открыта, выберите пункт **Сервис** > **Получить средства и компоненты...**; откроется Visual Studio Installer. **Visual Studio Installer** можно также открыть из меню "Пуск". Здесь можно выбрать рабочие нагрузки или компоненты, которые нужно установить. Затем выберите **Изменить**.

## <a name="step-5---choose-individual-components-optional"></a>Шаг 5. Выбор отдельных компонентов (необязательно)

Если вы не хотите пользоваться функцией рабочих нагрузок для настройки установки Visual Studio или хотите добавить дополнительные компоненты, которые не устанавливает рабочая нагрузка, это можно сделать путем установки или добавления отдельных компонентов на вкладке **Отдельные компоненты**. Выберите нужные компоненты и следуйте указаниям.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — установка отдельных компонентов](media/vs-installer-installing-components.png "Установка отдельных компонентов Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 — установка отдельных компонентов](media/vs-2019/vs-installer-individual-components.png "Установка отдельных компонентов Visual Studio")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Шаг 6. Установка языковых пакетов (необязательно)

По умолчанию при первом запуске установщик пытается использовать язык операционной системы. Чтобы установить Visual Studio на нужном языке, выберите в Visual Studio Installer вкладку **Языковые пакеты** и следуйте указаниям.

::: moniker range="vs-2017"

  ![Visual Studio 2017 — установка языковых пакетов](media/vs-installer-installing-language-packs.png "Установка языковых пакетов Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019 — установка языковых пакетов](media/vs-2019/vs-installer-language-packs.png "Установка языковых пакетов Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Изменение языка установщика из командной строки

Язык по умолчанию можно изменить еще одним способом — запустив установщик из командной строки. Например, можно принудительно запустить установщик на английском языке, выполнив команду `vs_installer.exe --locale en-US`. Программа установки запомнит этот параметр и использует его при следующем запуске. Установщик поддерживает следующие токены языков: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru и tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Шаг 7. Выбор расположения установки (дополнительно)

::: moniker range="vs-2017"

**Новая возможность в версии 15.7**. Теперь можно уменьшить место, занимаемое установкой Visual Studio на системном диске. Вы можете переместить кэш загрузки, общие компоненты, пакеты SDK и средства на другие диски и оставить Visual Studio на самом быстром диске.

  ![Visual Studio 2017 — изменение расположения установки](media/installation-options-by-location.png "Изменение расположения установки")

::: moniker-end

::: moniker range="vs-2019"

Вы можете уменьшить место, занимаемое установкой Visual Studio на системном диске. Вы можете переместить кэш загрузки, общие компоненты, пакеты SDK и средства на другие диски и оставить Visual Studio на самом быстром диске.

  ![Visual Studio 2019 — выбор расположения установки](media/vs-2019/vs-installer-installation-locations.png "Выберите расположение установки")

::: moniker-end

> [!IMPORTANT]
> Вы можете выбрать другой диск только в том случае, если вы устанавливаете Visual Studio впервые. Если вы уже установили ее и хотите изменить диск, необходимо удалить Visual Studio, а затем переустановить ее.

Дополнительные сведения см. в разделе [Выбор места установки](change-installation-locations.md).

## <a name="step-8---start-developing"></a>Шаг 8. Начало разработки

::: moniker range="vs-2017"

1. Когда установка Visual Studio завершится, нажмите кнопку **Запустить**, чтобы приступить к разработке в Visual Studio.

2. Выберите **Файл**, а затем **Создать проект**.

3. Выберите тип проекта.

   Например, чтобы [создать приложение C++](../ide/getting-started-with-cpp-in-visual-studio.md), нажмите **Установленные**, разверните узел **Visual C++**, а затем выберите тип проекта C++, который нужно создать.

   Чтобы [создать приложение C#](../get-started/csharp/tutorial-console.md), нажмите **Установленные**, разверните узел **Visual C#**, а затем выберите тип проекта C#, который нужно создать.

::: moniker-end

::: moniker range="vs-2019"

1. Когда установка Visual Studio завершится, нажмите кнопку **Запустить**, чтобы приступить к разработке в Visual Studio.

1. На начальном экране выберите **Создать проект**.

1. В поле поиска введите тип приложения, которое вы хотите создать, чтобы просмотреть список доступных шаблонов. Список шаблонов зависит от рабочих нагрузок, выбранных во время установки. Чтобы просмотреть различные шаблоны, выберите разные рабочие нагрузки.

   Можно также фильтровать поиск по определенному языку программирования с помощью раскрывающегося списка **Язык**. Вы также можете выбирать фильтры из списка **Платформа** и **Тип проекта**. 

1. Новый проект откроется в Visual Studio, и вы можете приступить к написанию кода!

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Обновление Visual Studio](update-visual-studio.md)
* [Изменение Visual Studio](modify-visual-studio.md)
* [Удаление Visual Studio](uninstall-visual-studio.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Установка Visual Studio для Mac](/visualstudio/mac/installation)