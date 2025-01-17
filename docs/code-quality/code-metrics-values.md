---
title: Рассчитать метрики кода
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b44f2a36297db3265a3904f1f76596ca6ba0e35
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260476"
---
# <a name="code-metrics-values"></a>Значения метрик кода

Повышенная сложность современных программных приложений также увеличивает усложняет код, надежный и удобный в сопровождении. Метрики кода представляют собой набор оценок программного обеспечения, которые дают разработчикам более глубокое представление о разрабатываемом коде. Используя преимущества метрик кода, разработчикам понять типы и методы должны быть переработаны или более тщательное тестирование. Группы разработчиков могут определять потенциальные риски, понять текущее состояние проекта и отслеживания хода выполнения во время разработки программного обеспечения.

Разработчики могут использовать Visual Studio для получения данных метрик кода, которые измеряют сложности и удобства сопровождения управляемого кода. Данные метрик кода могут создаваться для всего решения или отдельного проекта.

Сведения о способах получения данных метрик кода в Visual Studio, см. в разделе [как: Создание данных для метрик кода](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Оценки программного обеспечения

Ниже показан код, Результаты метрик, которые вычисляет Visual Studio:

- **Индекс удобства поддержки** -вычисляет значение индекса от 0 до 100, представляющий относительной простоты обслуживания кода. Высокое значение означает превосходные возможности сопровождения. Цветовые индикаторы позволяют быстро определить проблемные места в коде. Зеленый рейтинг от 20 до 100 и указывает, что код имеет высокое удобство поддержки. Желтый рейтинг от 10 до 19 и указывает, что код поддерживать. Красный рейтинг оценку от 0 до 9, указывает на низкий удобство поддержки. Дополнительные сведения см. в разделе [диапазона индекса удобства обслуживания и значение](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) записи блога.

- **Сложность организации циклов** -измеряет структурной сложности кода. Она создается в расчете количества разных путей кода в потоке программы. Это программа, которая имеет сложный поток управления требует дополнительные тесты для достижения приемлемого уровня покрытия кода и менее понятным. Дополнительные сведения см. в разделе [запись Википедии для Цикломатическая сложность](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Глубина наследования** -указывает, сколько различных классов, наследующих от друга, все вплоть до базового класса. Глубина наследования похоже на соединение, в том, что изменения в базовом классе может повлиять на любой из его наследуемые классы классов. Чем выше это число, глубже наследования и тем выше вероятность изменения базового класса с последующим получением перестали изменены. Глубина наследования низкое значение действует и высокое значение неправильный. 

- **Связанность классов** -измеряет увязка с уникальным классы с помощью параметров, локальных переменных, типы возвращаемых значений, вызовы методов, экземпляров универсального класса или шаблона, базовые классы, реализации интерфейса, полей, определенных для внешних типов и атрибут оформления. Разработка хорошего программного обеспечения определяет, что типы и методы должны иметь высокую слаженность и низкой связанностью. Высокая связанность свидетельствует о трудно повторно использовать и обслуживать из-за большого количества взаимозависимостей для других типов. Дополнительные сведения см. в разделе [взаимозависимости классов](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) записи блога.

- **Строки кода** -Указывает приблизительное число строк кода. Число зависит от кода IL и поэтому не точное число строк в файле исходного кода. Большое число может означать, что тип или метод пытается сделать слишком много работы и требует разделения. Он также может указывать, что тип или метод может быть трудно обслуживать.

   > [!NOTE]
   > [Командной строки версии](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) кода средство метрики подсчитывать фактические строки кода, так как они анализируют исходный код вместо IL.

## <a name="anonymous-methods"></a>Анонимные методы

*Анонимный метод* — это метод, не имеет имени. Анонимные методы часто используются для передачи блока кода в качестве аргумента делегата. Результаты метрик для анонимного метода, объявленного в члене, например, метод или метод доступа, связаны с членом, который объявляет метод. Они не связаны с членом, который вызывает метод.

Дополнительные сведения о метриками кода анонимных методов, см. в разделе [анонимные методы и анализ кода](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Созданный код

Некоторые программные средства и компиляторы создают код, который добавляется в проект, и что разработчик проекта отсутствует или не следует изменять. В основном показатели качества кода игнорирует созданный код при расчете значения метрик. Это позволяет отражать разработчик может просматривать, изменять значения метрик.

Код, созданный для форм Windows Forms не учитывается, так как это код, который разработчик может просматривать, изменять.

## <a name="next-steps"></a>Следующие шаги

- [Практическое руководство. Создание данных для метрик кода](../code-quality/how-to-generate-code-metrics-data.md)
- [В окне результатов метрики кода](../code-quality/working-with-code-metrics-data.md)
