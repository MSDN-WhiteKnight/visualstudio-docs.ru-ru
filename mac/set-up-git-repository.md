---
title: Настройка репозитория Git
description: Использование Git и Subversion в Visual Studio для Mac.
author: conceptdev
ms.author: crdun
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: ca216f3f2a65e1c17e2ab8cc1ca17f6f707afb79
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938472"
---
# <a name="set-up-a-git-repository"></a>Настройка репозитория Git

Git — это распределенная система управления версиями, которая позволяет командам одновременно работать с одним документом. Это означает, что все файлы хранятся на одном сервере, но при каждом извлечении репозитория из этого центрального источника весь репозиторий клонируется локально на ваш компьютер.

Существует много удаленных узлов, которые позволяют работать с Git для управления версиями, но наиболее распространенным из них является GitHub. В приведенном ниже примере используется узел GitHub, но в Visual Studio для Mac можно использовать любой узел Git для управления версиями.

Если нужно использовать GitHub, создайте и настройте учетную запись перед выполнением описанных ниже действий.

## <a name="creating-a-remote-repo-on-github"></a>Создание удаленного репозитория в GitHub

В приведенном ниже примере используется узел GitHub, но в Visual Studio для Mac можно использовать любой узел Git для управления версиями.

Чтобы настроить репозиторий Git, выполните следующие действия:

1. Создайте репозиторий Git на сайте github.com:

    ![Создание репозитория Git](media/version-control-git1-sml.png)

2. Задайте имя, описание и конфиденциальность для репозитория. **Не** инициализируйте репозиторий. Задайте для файла GITIGNORE и лицензии значение "Нет":

    ![Настройка сведений о репозитории Git](media/version-control-git2.png)

3. На следующей странице вы можете отобразить и скопировать SSH- или HTTPS-адрес в созданный репозиторий:

    ![Просмотр и копирование адреса](media/version-control-git3.png)

   Вам потребуется HTTPS-адрес, чтобы связать Visual Studio для Mac и этот репозиторий.

## <a name="publishing-an-existing-project"></a>Публикация существующего проекта

Если у вас есть проект, который еще _не_ зарегистрирован в системе управления версиями, выполните указанные ниже действия. чтобы настроить его в Git.

1. Выберите имя решения на панели решения в Visual Studio для Mac.

2. В строке меню выберите **Управление версиями > Опубликовать в системе управления версиями**, чтобы отобразить диалоговое окно **Выбрать репозиторий**:

    ![Запуск извлечения в Visual Studio для Mac](media/version-control-git4-sml.png)

    Если этот пункт меню недоступен для выбора, убедитесь в том, что имя решения выбрано.

3. Откройте вкладку **Зарегистрированные репозитории** и нажмите кнопку **Добавить**:

    ![](media/version-control-git5.png)

4. Введите имя репозитория, которое требуется отображать локально, и вставьте URL-адрес из шага 3. Диалоговое окно "Конфигурация репозитория" должно выглядеть следующим образом. Нажмите кнопку "ОК":

    ![Диалоговое окно для ввода сведений Git](media/version-control-git6.png)

    Для подключения к Git также можно использовать SSH.

5. Чтобы попытаться опубликовать приложение в Git, выберите репозиторий и убедитесь, что поля **Имя модуля** и **Сообщение** заполнены:

    ![Попытка публикации проекта в Git](media/version-control-git7.png)

6. Нажмите кнопку **ОК**, а затем кнопку **Опубликовать** в диалоговом окне оповещения.

7. В окне **Учетные данные Git** введите имя пользователя GitHub и пароль. 

> [!NOTE]
> Если в вашей учетной записи включена двухфакторная проверка подлинности (2FA), необходимо будет создать маркер доступа, используемый вместо пароля. Если маркер доступа еще не создан, выполните действия, описанные в документации Git по созданию [маркера доступа](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).

8. Введите имя пользователя и личный маркер доступа и нажмите клавишу **ОК**:

    ![Ввод имени пользователя и пароля для Git](media/version-control-git9-sml.png)

9. Через несколько секунд решение должно опубликоваться на основе исходной фиксации. Подтвердите публикацию, просмотрев пункт меню "Управление версиями", который теперь должен быть заполнен разными параметрами:

    ![Меню "Управление версиями"](media/version-control-git10.png)

10. Начав вносить дополнительные изменения, выберите  **Отправить изменения**,  чтобы отправить изменения в  **удаленный** репозиторий. Это позволит всем соответствующим пользователям просмотреть их на сайте github.com:

    ![Отправка изменений в удаленный репозиторий](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Публикация нового проекта

Диалоговое окно создания проекта можно использовать для создания нового проекта с помощью локального репозитория git. Чтобы включить его, установите флажок **Использовать git для управления версиями**, как показано на следующем снимке экрана. Это действие инициализирует репозиторий и добавит необязательный GITIGNORE-файл:

![Создание нового проекта с поддержкой git](media/version-control-git-publish-new1.png)

Выполните следующие действия, чтобы отправить локальный репозиторий в новый репозиторий GitHub:

> [!NOTE]
> Если вы еще не создали репозиторий GitHub, см. раздел [Создание удаленного репозитория на GitHub](#creating-a-remote-repo-on-github).

1. Создайте первую фиксацию, перейдя в раздел **Управление версиями > Проверка решения и фиксация** в строке меню.

2. На вкладке "Состояние" выберите **Фиксация** в левом верхнем углу.

3. Напишите сообщение о фиксации, например, "Первая фиксация", а затем щелкните **Фиксировать**:

    ![Фиксация начальных изменений в репозитории git](media/version-control-git-publish-new2.png)

4. Далее в строке меню перейдите к разделу **Управление версиями > Управление ветвями и удаленными репозиториями**.

5. Перейдите на вкладку **Удаленные источники** и нажмите кнопку **Добавить**.

6. В окне **Удаленный источник** добавьте сведения о ранее созданном репозитории GitHub и нажмите кнопку **ОК**:

    ![Настройка удаленных источников для репозитория git](media/version-control-git-publish-new3.png)

7. Закройте окно **Конфигурация репозитория Git**, а затем в строке меню перейдите к разделу **Управление версиями > Отправить изменения**.

8. В окне **Отправить в репозиторий** щелкните кнопку **Отправить изменения**:

    ![Отправка изменений в удаленный репозиторий](media/version-control-git-publish-new4.png)

9. При запросе введите свои имя пользователя и пароль GitHub.

> [!NOTE]
> Если в вашей учетной записи включена двухфакторная проверка подлинности (2FA), необходимо будет создать маркер доступа, используемый вместо пароля. Если маркер доступа еще не создан, выполните действия, описанные в документации Git по созданию [маркера доступа](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).

Visual Studio для Mac теперь будет отправлять изменения в удаленный репозиторий GitHub:

![Подтверждение выполнения операции отправки](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Извлечение существующего репозитория

Высока вероятность того, что вы будете работать с репозиторием GitHub, который размещен только на удаленном компьютере, но отсутствует на вашем. Visual Studio для Mac позволяет быстро извлекать такие репозитории. Чтобы клонировать репозиторий на свой компьютер, выполните указанные ниже действия.

1. В строке меню выберите **Управление версиями > Извлечь**.

2. Откроется вкладка **Подключение к репозиторию**.

    ![Вкладка "Подключение к репозиторию" с введенными сведениями](media/version-control-git13.png)

3. На странице удаленного репозитория в GitHub нажмите кнопку **Clone or Download** (Клонировать или скачать) и скопируйте предоставленный URL-адрес.

    ![URL-адрес в GitHub](media/version-control-git14.png)

4. Замените весь текст в поле **URL-адреса** на вкладке **Подключение к репозиторию**. В результате большинство полей на этой вкладке будет заполнено автоматически, как показано на рисунке в шаге 2.

5. Укажите каталог, в который необходимо клонировать репозиторий, и нажмите кнопку **Извлечь**.

> [!NOTE]
> Если размер репозитория превышает 4 ГБ, могут возникнуть проблемы.

## <a name="troubleshooting"></a>Устранение неполадок

При наличии проблем с инициализацией проекта с пустым удаленным репозиторием попробуйте выполнить следующие действия:

1. Перейдите в папку решения.
1. Нажмите клавиши **COMMAND + SHIFT +.** , чтобы отобразить скрытые файлы и папки.
1. При наличии папки **.git** удалите ее.
1. При наличии файла **GITIGNORE** удалите его.
1. Нажмите клавиши **COMMAND + SHIFT +.** , чтобы скрыть файлы и папки.
1. Откройте решение в Visual Studio для Mac.
1. На панели решения выберите узел решения.
1. Перейдите в меню "Управление версиями" и выберите **Publish in Version Control** (Опубликовать в системе управления версиями).
1. Выполните действия из приведенного выше руководства, начиная с шага 6.

## <a name="see-also"></a>См. также

- [Управление версиями в Visual Studio (в Windows)](/visualstudio/version-control/)
