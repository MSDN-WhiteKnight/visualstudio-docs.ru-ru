---
title: Создание приложения Vue.js с помощью Node.js
description: Вы можете создавать приложения Node.js в Visual Studio, используя платформу Vue.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a5c903b0aa82f3711bdbe1fd7925829fbdc06c9a
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226044"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Создание приложения Vue.js с помощью инструментов Node.js для Visual Studio

Visual Studio поддерживает разработку приложений на базе платформы [Vue.js](https://vuejs.org/) с использованием JavaScript или TypeScript.

Следующие новые функции поддерживают разработку приложений Vue.js в Visual Studio:

* Поддержка блоков скриптов, стиля и шаблона в *VUE*-файлах
* Распознавание атрибута `lang` в *VUE*-файлах
* Шаблоны проектов и файлов Vue.js

## <a name="prerequisites"></a>Предварительные требования

* У вас должна быть установлена среда Visual Studio 2017 15.8 или последующей версии и рабочая нагрузка **Разработка Node.js**.

    > [!IMPORTANT]
    > Для выполнения инструкций из этой статьи вам потребуются функции, доступные в Visual Studio 2017, начиная с версии 15.8.

    ::: moniker range=">=vs-2019"
    Если у вас не установлена нужная версия, установите [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Установите Visual Studio бесплатно со страницы  [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , если вы еще не сделали этого.
    ::: moniker-end

    Если вам нужно установить рабочую нагрузку, но вы уже используете Visual Studio, выберите пункт **Средства** > **Получить средства и компоненты...**, после чего запустится Visual Studio Installer. Выберите рабочую нагрузку **Разработка Node.js**, а затем элемент **Изменить**.

* Чтобы создать проект ASP.NET Core, вам нужны ASP.NET и рабочие нагрузки веб-разработки и кроссплатформенной разработки .NET Core.

* У вас должна быть установлена среда выполнения Node.js.

    Если она не установлена, установите версию LTS с веб-сайта [Node.js](https://nodejs.org/en/download/). Как правило, Visual Studio автоматически обнаруживает установленную среду выполнения Node.js. В противном случае вы можете указать в проекте ссылку на установленную среду на странице свойств. (После создания проекта щелкните правой кнопкой мыши узел проекта и выберите **Свойства**.)

## <a name="create-a-vuejs-project-using-a-template"></a>Создание проекта Vue.js с помощью шаблона

Для создания проекта вы можете использовать новые шаблоны Vue.js. Использование шаблона — это самый простой способ приступить к работе. Подробные инструкции см. в разделе [Создание первого приложения Vue.js с помощью Visual Studio](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Создание проекта Vue.js с ASP.NET Core и интерфейсом командной строки Vue

Vue.js предоставляет официальный интерфейс командной строки для быстрого формирования шаблонов проектов. Если вы хотите использовать интерфейс командной строки для создания приложения, выполните действия, описанные в этой статье, чтобы настроить среду разработки.

> [!IMPORTANT]
> Предполагается, что у вас уже есть опыт работы с платформой Vue.js. Если это не так, посетите [Vue.js](https://vuejs.org/), чтобы узнать больше об этой платформе.

### <a name="create-a-new-aspnet-core-project"></a>Создание проекта ASP.NET Core

В этом примере используется пустое приложение ASP.NET Core (C#). Но вы можете выбрать другие проекты и языки программирования.

#### <a name="create-an-empty-project"></a>Создание пустого проекта

1. Откройте Visual Studio и создайте новый проект.

    ::: moniker range=">=vs-2019"
    Нажмите клавишу **ESC**, чтобы закрыть окно запуска. Нажмите клавиши **CTRL+Q**, чтобы открыть поле поиска, введите **asp.net** и выберите **Создать проект веб-приложения ASP.NET Core**. В появившемся диалоговом окне введите имя **client-app**, а затем выберите команду **Создать**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    В верхней строке меню выберите **Файл** > **Создать** > **Проект**. На левой панели диалогового окна **Новый проект** разверните узел **Visual C#** и выберите **Интернет**. В средней области выберите **Веб-приложение ASP.NET Core**, присвойте ему имя **client-app** и нажмите кнопку **ОК**.
    ::: moniker-end

    Если шаблон проекта **Веб-приложение ASP.NET Core** отсутствует, сначала установите рабочую нагрузку **ASP.NET и разработка веб-приложений** и рабочую нагрузку разработки **NET Core**. Чтобы установить рабочую нагрузку, щелкните ссылку **Открыть установщик Visual Studio** в левой области диалогового окна **Создать проект** (выберите пункты **Файл** > **Создать** > **Проект**). Запускается Visual Studio Installer. Выберите необходимые рабочие нагрузки.

1. Выберите **Пустой** и нажмите **OK**.

    Visual Studio создаст проект и откроет его в обозревателе решений (правая панель).

#### <a name="configure-the-project-startup-file"></a>Настройка файла запуска проекта

* Откройте файл *./Startup.cs*и добавьте следующие строки в метод Configure:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Установка интерфейса командной строки Vue

Чтобы установить модуль npm vue-cli, откройте командную строку и введите `npm install --g vue-cli` или `npm install -g @vue/cli` для версии 3.0 (сейчас доступно в бета-версии).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Создание нового клиентского приложения по шаблону с помощью интерфейса командной строки Vue

1. Перейдите в командную строку и измените текущий каталог на корневую папку проекта.

1. Введите `vue init webpack client-app` и выполните дальнейшие действия, чтобы указать дополнительные данные.

    > [!NOTE]
    > Для преобразования файлов *.vue* необходимо использовать WebPack или аналогичную платформу с загрузчиком. С помощью TypeScript и Visual Studio выполнить компиляцию файлов *.vue* нельзя. Это же касается и объединения — с помощью TypeScript нельзя преобразовать модули ES2015 (т. е. операторы `import` и `export`) в единый итоговый файл *.js* для загрузки в браузер. Снова-таки, воспользуйтесь WebPack. Сделать это из среды Visual Studio с помощью MSBuild можно с помощью шаблона Visual Studio. Сейчас готовые шаблоны ASP.NET для разработки Vue.js не предоставляются.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Изменение конфигурации webpack для вывода скомпилированных файлов в wwwroot

* Откройте файл *./client-app/config/index.js* и измените `build.index` и `build.assetsRoot` на путь wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Указание проекта для сборки клиентского приложения при каждом запуске сборки

1. В Visual Studio перейдите в раздел **Проект** > **Свойства** > **События сборки**.

1. В **командной строке событий перед сборкой** введите `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Настройка имен модулей вывода webpack

* Откройте файл *./client-app/build/webpack.base.conf.js* и добавьте следующие свойства для выходного свойства:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Добавление поддержки TypeScript с помощью интерфейса командной строки Vue

Для этих действий потребуется vue-cli 3.0 (в настоящее время существует как бета-версия).

1. Перейдите в командную строку и измените текущий каталог на корневую папку проекта.

1. Введите `vue create client-app` и выберите **Выбрать компоненты вручную**.

1. Выберите **Typescript**, а затем другие необходимые параметры.

1. Выполните оставшиеся шаги и ответьте на вопросы.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Настройка проекта Vue.js для TypeScript

1. Откройте файл *./client-app/tsconfig.json* и добавьте `noEmit:true` в параметры компилятора.

    Этот параметр позволяет избежать загромождения проекта при каждой сборке в Visual Studio.

1. Затем создайте файл *vue.config.js* в *./client-app/* и добавьте следующий код.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Приведенный выше код настраивает webpack и задает папку wwwroot.

#### <a name="build-with-vue-cli-30"></a>Сборка с vue-cli 3.0

Неизвестная проблема с vue-cli 3.0 препятствует автоматизации сборки. Каждый раз при попытке обновления папки wwwroot выполняйте команду `npm run build` в папке client-app.

## <a name="limitations"></a>Ограничения

* Атрибут `lang` поддерживает только языки JavaScript и TypeScript. Допустимые значения: js, jsx, ts и tsx.
* Атрибут `lang` не работает с тегами шаблона или стиля.
* Отладка блоков скрипта в *VUE*-файлах не поддерживается в связи с предварительной обработкой.
* TypeScript не распознает *VUE*-файлы как модули. Вам нужен файл, который содержит подобный код, чтобы сообщить TypeScript, как выглядят *VUE*-файлы (шаблон vue-cli 3.0 уже включает этот файл).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Выполнение команды `npm run build` как события перед сборкой в свойствах проекта не работает при использовании vue-cli 3.0.

## <a name="see-also"></a>См. также

- [руководство по началу работы с Vue](https://vuejs.org/v2/guide);
- [Проект интерфейса командной строки Vue](https://github.com/vuejs/vue-cli).
- [документация по настройке Webpack](https://webpack.js.org/configuration/).
