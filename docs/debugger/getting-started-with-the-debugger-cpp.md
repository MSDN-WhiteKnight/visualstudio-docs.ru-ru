---
title: Сведения об отладке C++ с помощью отладчика Visual Studio
description: Сведения о запуске отладчика Visual Studio, пошаговой отладке кода и просмотру данных.
ms.custom: debug-experiment
ms.date: 08/01/2018
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cbcd4d4458de757cae5c20391f57c0708edbfd4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679745"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Учебник. Сведения об отладке кода C++ с помощью Visual Studio

В этом пошаговом руководстве рассматриваются возможности отладчика Visual Studio. Более полное описание функций отладчика см. в статье c [Знакомство с отладчиком Visual Studio](../debugger/debugger-feature-tour.md). *Отладка приложения* обычно означает запуск и выполнение приложения с подключенным отладчиком. При этом в отладчике доступно множество способов наблюдения за выполнением кода. Вы можете пошагово перемещаться по коду и просматривать значения, хранящиеся в переменных, задавать контрольные значения для переменных, чтобы отслеживать изменение значений, изучать путь выполнения кода, просматривать выполнение ветви кода и т. д. Если вы не знакомы с процессом отладки, перед выполнением задач в этой статье рекомендуется прочесть документ об [отладке для начинающих](../debugger/debugging-absolute-beginners.md).

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Запуск отладчика и попадание в точки останова.
> * Использование команд для пошагового выполнения кода в отладчике.
> * Проверка переменных в подсказках к данным и окнах отладчика.
> * Просмотр стека вызовов

## <a name="prerequisites"></a>Предварительные требования

::: moniker range=">=vs-2019"

У вас должна быть установлена среда Visual Studio 2019 и должна иметься рабочая нагрузка **Разработка классических приложений на C++**.

::: moniker-end
::: moniker range="vs-2017"

У вас должна быть установлена среда Visual Studio 2017 и должна иметься рабочая нагрузка **Разработка классических приложений на C++**.

::: moniker-end

Установите Visual Studio бесплатно со страницы  [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) , если вы еще не сделали этого.

Если вам нужно установить рабочую нагрузку, но вы уже используете Visual Studio, выберите пункт **Средства** > **Получить средства и компоненты...**, после чего запустится Visual Studio Installer. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Разработка классических приложений на C++**, а затем нажмите **Изменить**.

## <a name="create-a-project"></a>Создание проекта

1. Запустите Visual Studio.

    ::: moniker range=">=vs-2019"
    Нажмите клавишу **ESC**, чтобы закрыть окно запуска. Нажмите **CTRL+Q**, чтобы открыть поле поиска, введите **c++**, выберите **Шаблоны** и затем **Create new Console App project** (Создание проекта консольного приложения). В появившемся диалоговом окне введите такое имя, как **get-started-debugging**, а затем выберите **Создать**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    В верхней строке меню выберите **Файл** > **Создать** > **Проект**. В левой области диалогового окна **Новый проект** в разделе **Visual C++** выберите **Рабочий стол Windows**, а затем в средней области выберите **Консольное приложение Windows**. Введите имя, например **MyDbgApp**, и нажмите **ОК**.
    ::: moniker-end

    Если шаблон проекта **Консольное приложение Windows** отсутствует, перейдите в меню **Инструменты** > **Получить инструменты и компоненты**, после чего запустится Visual Studio Installer. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Разработка классических приложений на C++**, а затем нажмите **Изменить**.

    Visual Studio создаст проект.

1. В файле *get-started-debugging.cpp* замените код

    ```c++
    int main()
    {
        return 0;
    }
    ```

    следующим кодом:

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Запуск отладчика

1. Нажмите клавишу **F5** (**Отладка > Начать отладку**) или кнопку **Начать отладку** ![Начать отладку](../debugger/media/dbg-tour-start-debugging.png "Начать отладку ") на панели инструментов отладки.

     При нажатии клавиши **F5** происходит запуск приложения с присоединенным отладчиком. Но пока мы не сделали ничего особенного, чтобы проанализировать код. Поэтому приложение будет просто загружено, и вы увидите выходные данные консоли.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     В этом руководстве мы более подробно рассмотрим приложение с отладчиком и познакомимся с возможностями отладчика.

2. Остановите отладчик, нажав красную кнопку остановки ![Остановить отладку](../debugger/media/dbg-tour-stop-debugging.png "Остановить отладку").

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Установка точки останова и запуск отладчика

1. В цикле `for` функции `main` установите точку останова, щелкнув левое поле следующей строки кода:

    `shape->Draw()`

    В месте установки точки останова появится красный круг.

    Точки останова — это один из самых простых и важных компонентов надежной отладки. Точка останова указывает, где Visual Studio следует приостановить выполнение кода, чтобы вы могли проверить значения переменных или поведение памяти либо выполнение ветви кода.

2. Нажмите клавишу **F5** или кнопку **Начать отладку** ![Start Debugging](../debugger/media/dbg-tour-start-debugging.png "Start Debugging". Будет запущено приложение и отладчик перейдет к строке кода, где задана точка останова.

    ![Установка точки останова и попадание в нее](../debugger/media/get-started-set-breakpoint-cpp.gif)

    Желтая стрелка представляет оператор, на котором приостановлен отладчик. В этой же точке приостанавливается выполнение приложения (этот оператор пока не выполнен).

     Если приложение еще не запущено, клавиша **F5** запускает отладчик и останавливается в первой точке останова. В противном случае **F5** продолжает выполнение приложения до следующей точки останова.

    Точки останова полезны, если вам известны строка или раздел кода, которые вы хотите подробно рассмотреть.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Переход по коду в отладчике с помощью пошаговых команд

Здесь мы используем в основном сочетания клавиш, так как они позволяют быстро выполнять приложение в отладчике (эквивалентные команды, например команды меню, отображаются в круглых скобках).

1. Во время приостановки в вызове метода `shape->Draw` в функции `main` нажмите клавишу **F11** (или выберите **Отладка > Шаг с заходом**), чтобы перейти в код для класса `Rectangle`.

     ![Использование клавиши F11 для выполнения шага с заходом в код](../debugger/media/get-started-f11-cpp.png "F11 —шаг с заходом")

     F11 — это команда **Шаг с заходом**, которая выполняет приложение с переходом к следующему оператору. Клавишу F11 удобно использовать для более детальной проверки потока выполнения. (Мы также покажем другие варианты более быстрого перемещения по коду.) По умолчанию отладчик пропускает непользовательский код (дополнительные сведения см. в статье об [отладке в режиме "Только мой код"](../debugger/just-my-code.md)).

2. Нажимайте клавишу **F10** (или выберите **Отладка > Шаг с обходом**) несколько раз, пока отладчик не остановится в вызове метода `Shape::Draw`, а затем еще раз нажмите клавишу **F10**.

     ![Использование клавиши F10 для шага с обходом кода](../debugger/media/get-started-step-over-cpp.png "F10 — шаг с обходом")

     Обратите внимание, что в этот раз отладчик не заходит в метод `Draw` базового класса (`Shape`). Клавиша **F10** перемещает отладчик без захода в функции или методы в коде приложения (код продолжает выполняться). Нажав клавишу F10 (а не **F11**) в вызове метода `Shape::Draw`, мы пропускаем код реализации для `Draw` (пока это нас не интересует).

## <a name="navigate-code-using-run-to-click"></a>Переход по коду с помощью команды "Выполнение до щелкнутого"

1. В редакторе кода прокрутите вниз и наведите указатель мыши на метод `std::cout` в классе `Triangle`, пока в левой части не появится зеленая кнопка **Выполнение до щелкнутого** ![Выполнение до щелкнутого](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

     ![Использование функции "Выполнение до щелкнутого"](../debugger/media/get-started-run-to-click-cpp.png "Выполнение до щелкнутого")

   > [!NOTE]
   > Кнопка **Выполнение до щелкнутого** доступна начиная с версии [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Если кнопка с зеленой стрелкой отсутствует, воспользуйтесь клавишей **F11**, чтобы переместить отладчик в нужное место.

2. Нажмите кнопку **Выполнение до щелкнутого** ![Выполнение до щелкнутого](../debugger/media/dbg-tour-run-to-click.png "Выполнение до щелкнутого").

    Использование этой кнопки аналогично установке временной точки останова. Функция **Выполнение до щелкнутого** удобна для быстрой работы в видимой области кода приложения (можно щелкнуть в любом открытом файле).

    Отладчик перемещается к реализации метода `std::cout` для класса `Triangle`.

    Во время приостановки можно заметить опечатку. Текст выходных данных "Drawing a trangle" содержит ошибку. Ее можно исправить прямо во время выполнения приложения в отладчике.

## <a name="edit-code-and-continue-debugging"></a>Изменение кода и продолжение отладки

1. Щелкните "Drawing a trangle" и исправьте "trangle" на "triangle".

1. Нажмите клавишу **F11** один раз. Вы увидите сообщение о повторной компиляции кода, а затем отладчик переместится далее.

    > [!NOTE]
    > В зависимости от типа кода, изменяемого в отладчике, может появиться предупреждающее сообщение. В некоторых случаях перед продолжением потребуется перекомпилировать код.

## <a name="step-out"></a>Шаг с выходом

Предположим, что вы закончили изучать метод `Draw` в классе `Triangle` и хотите выйти из функции, но остаться в отладчике. Это можно сделать с помощью команды **Шаг с выходом**.

1. Нажмите сочетание клавиш **SHIFT** + **F11** (или **Отладка > Шаг с выходом**).

     Эта команда возобновляет выполнение приложения (и перемещает отладчик) до возврата текущей функции.

     Вы должны вернуться в цикл `for` в методе `main`.

## <a name="restart-your-app-quickly"></a>Быстрый перезапуск приложения

Нажмите кнопку **Перезапустить** ![Перезапустить приложение](../debugger/media/dbg-tour-restart.png "Перезапустить приложение") на панели инструментов отладки (**CTRL** + **SHIFT** + **F5**).

Кнопка **Перезапустить** позволяет сэкономить время, затрачиваемое на остановку приложения и перезапуск отладчика. Отладчик приостанавливается в первой точке останова, достигнутой при выполнении кода.

Отладчик еще раз останавливается в заданной вами точке останова в методе `shape->Draw()`.

## <a name="inspect-variables-with-data-tips"></a>Проверка переменных с помощью подсказок по данным

Функции, позволяющие проверять переменные, являются самыми полезными возможностями отладчика. Реализовывать эту задачу можно разными способами. Часто при попытке выполнить отладку проблемы пользователь старается выяснить, хранятся ли в переменных значения, которые требуются ему в определенное время.

1. Во время приостановки в методе `shape->Draw()` наведите указатель мыши на контейнер `shapes` (векторный объект). Вы увидите значение его свойства по умолчанию, свойство `size` со значением `size=3`.

1. Разверните объект `shapes`, чтобы увидеть все его свойства, такие как первый индекс массива `[0]`, который имеет адрес памяти.

    Вы можете развернуть другие объекты, чтобы просмотреть их свойства.

1. Разверните первый индекс `[0]`, чтобы просмотреть свойство прямоугольника `privateHeight`.

     ![Просмотр подсказки по данным](../debugger/media/get-started-data-tip-cpp.png "Просмотр подсказки по данным")

     Часто при отладке бывает необходимо быстро проверить значения свойств для объектов. Лучше всего для этого подходят подсказки по данным.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Проверка переменных с помощью окон "Видимые" и "Локальные"

1. Взгляните на окно **Видимые** в нижней части редактора кода.

     ![Проверка переменных в окне видимых переменных](../debugger/media/get-started-autos-window-cpp.png "Окно видимых переменных")

    В окне **Видимые** отображаются переменные и их текущие значения. Для C++ в окне **Видимые** отображаются переменные в предыдущих трех строках кода.

2. Затем посмотрите на окно **Локальные** на вкладке рядом с окном **Видимые**.

    В окне **Локальные** показаны переменные, которые находятся в текущей [области](https://www.wikipedia.org/wiki/Scope_(computer_science)), то есть текущем контексте выполнения кода.

## <a name="set-a-watch"></a>Установка контрольного значения

1. В основном окне редактора кода щелкните правой кнопкой мыши объект `shapes` и выберите команду **Добавить контрольное значение**.

    В нижней части редактора кода откроется окно **Контрольное значение**. В окне **Контрольное значение** можно указать переменную (или выражение), которую необходимо отслеживать.

    Теперь у вас есть контрольное значение, заданное для объекта `shapes`, и по мере перемещения по отладчику вы можете наблюдать за изменением его значения. В отличие от других окон переменных, в окне **Контрольное значение** всегда отображаются просматриваемые вами переменные (они выделяются серым цветом, когда находятся вне области действия).

## <a name="examine-the-call-stack"></a>Просмотр стека вызовов

1. Во время приостановки в цикле `for` щелкните окно **Стек вызовов**, которое по умолчанию открыто в нижней правой области.

2. Несколько раз нажимайте клавишу **F11**, пока отладчик не приостановится в методе `Shape::Draw` класса `Rectangle` в редакторе кода. Взгляните на окно **Стек вызовов**.

    ![Просмотр стека вызовов](../debugger/media/get-started-call-stack-cpp.png "Просмотр стека вызовов")

    В окне **Стек вызовов** показан порядок вызова методов и функций. В верхней строке приведена текущая функция (в данном примере метод `Rectangle::Draw`). Во второй строке показано, что функция `Rectangle::Draw` была вызвана из функции `main` и т. д.

   > [!NOTE]
   > Окно **Стек вызовов** аналогично перспективе "Отладка" в некоторых интегрированных средах разработки, например Eclipse.

    Стек вызовов хорошо подходит для изучения и анализа потока выполнения приложения.

    Дважды щелкните строку кода, чтобы просмотреть исходный код. При этом также изменится текущая область, проверяемая отладчиком. Это действие не перемещает отладчик.

    Для выполнения других задач можно воспользоваться контекстными меню из окна **Стек вызовов**. Например, можно вставлять точки останова в указанные функции, перемещать отладчик с помощью функции **Выполнение до текущей позиции** и изучать исходный код. Дополнительные сведения см. в разделе [Практическое руководство. просмотреть стек вызовов](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Изменение потока выполнения

1. Приостановив отладчик в вызове метода `Shape::Draw` с помощью мыши захватите желтую стрелку (указатель выполнения) в левой части и переместите ее вверх на одну строку в вызов метода `std::cout`.

1. Нажмите клавишу **F11**.

    Отладчик повторно выполнит метод `std::cout` (вы увидите это в выходных данных окна консоли).

    Изменяя поток выполнения, можно решать множество задач, например тестировать различные пути выполнения кода или повторно выполнять код без перезапуска отладчика.

    > [!WARNING]
    > Как правило, при работе с этой функцией необходимо соблюдать осторожность — вы увидите соответствующее предупреждение во всплывающей подсказке. Могут отображаться и другие предупреждения. При перемещении указателя предыдущее состояние приложения не возвращается.

1. Чтобы продолжить выполнение приложения, нажмите клавишу **F5**.

    Поздравляем с завершением этого учебника!

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как запускать отладчик, осуществлять пошаговое выполнение кода и проверять переменные. Возможно, вы захотите получить более полное представление о функциях отладчика, а также воспользоваться ссылками на дополнительные сведения.

> [!div class="nextstepaction"]
> [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
