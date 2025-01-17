---
title: Шаг 2. Создание задачи на сложение случайных чисел | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b36897236b71617c6eb36949d307e6b3e1d0204b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693970"
---
# <a name="step-2-create-a-random-addition-problem"></a>Шаг 2. Создание задачи на сложение случайных чисел
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Во второй части этого урока вам предстоит реализовать логику головоломки, добавив арифметические задачи на основе случайных чисел. Также необходимо будет создать метод с именем `StartTheQuiz()`, который проставляет числа для задач и запускает таймер обратного отсчета. Далее в этом уроке вы добавите задачи на вычитание, умножение и деление.  
  
> [!NOTE]
> Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание математической викторины](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-random-addition-problem"></a>Создание задачи на сложение случайных чисел  
  
1. В конструкторе форм выберите форму (Form1).  
  
2. В строке меню выберите **Вид**, **Код**.  
  
     Откроется файл Form1.cs или Form1.vb (в зависимости от того, на каком языке вы программируете), позволяя вам увидеть код, стоящий за формой.  
  
3. Создайте объект `Random`, добавив оператор `new` в начале кода следующим образом.  
  
     [!code-csharp[VbExpressTutorial3Step2#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial3Step2#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#1)]  
  
     Вы добавили в форму объект `Random` и назвали этот объект **randomizer**.  
  
     `Random` называется объектом. В следующем уроке мы подробно рассмотрим, что означает это слово применительно к программированию. Пока что просто запомните, что операторы `new` можно использовать для создания кнопок, меток, панелей, диалоговых окон открытия файлов, диалоговых окон выбора цвета, проигрывателей звука, генераторов случайных чисел и даже форм, и все они будут называться объектами. При выполнении программы форма запускается, и стоящий за ней код создает объект `Random` и присваивает ему имя **randomizer**.  
  
     Вскоре вам предстоит создать метод для проверки ответов, поэтому в головоломке необходимо предусмотреть переменные для хранения случайных чисел, генерируемых для каждой задачи. См. статьи о [переменных](https://msdn.microsoft.com/library/4cfaa06d-4ae3-4307-897b-cf599dc24caa) или [типах](https://msdn.microsoft.com/library/f782d7cc-035e-4500-b1b1-36a9881130ad). Для правильного использования переменных их необходимо объявить, т. е. указать их имена и типы данных.  
  
4. Добавьте в форму две целочисленные переменные и назовите их **addend1** и **addend2**.  
  
    > [!NOTE]
    > Целочисленная переменная в C# называется int, а в Visual Basic — Integer. В переменных этого типа можно хранить положительные и отрицательные числа в диапазоне от -2147483648 до 2147483647, причем это могут быть только целые числа, без десятичных знаков.  
  
     Для добавления целочисленной переменной используется синтаксис, похожий на тот, с помощью которого вы добавили объект `Random`, как показано в следующем коде.  
  
     [!code-csharp[VbExpressTutorial3Step2#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial3Step2#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#2)]  
  
5. Добавьте метод с именем `StartTheQuiz()`, который использует метод `Random` объекта `Next()` для отображения случайных чисел в метках. В конечном итоге метод `StartTheQuiz()` подставит числа для всех задач и затем запустит таймер, поэтому добавьте комментарий. Функция должна выглядеть следующим образом.  
  
     [!code-csharp[VbExpressTutorial3Step2#3](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#3)]
     [!code-vb[VbExpressTutorial3Step2#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#3)]  
  
     Обратите внимание, что при вводе точки (.) после слова **randomizer** в коде открывается окно IntelliSense, в котором отображаются все методы объекта `Random`, которые можно вызвать. Например, в списке Intellisense присутствует метод `Next()`, как показано ниже.  
  
     ![Метод Next](../ide/media/express-randomwhite.png "Express_RandomWhite")  
Метод Next  
  
     При вводе точки после объекта IntelliSense отображает список членов объекта, таких как свойства, методы и события.  
  
    > [!NOTE]
    > При использовании метода `Next()` с объектом `Random`, например при вызове `randomizer.Next(50)`, возвращается случайное число, которое меньше 50 (от 0 до 49). В этом примере мы вызвали `randomizer.Next(51)`. Мы использовали число 51, а не 50, чтобы при сложении двух случайных чисел получился ответ, который находится в диапазоне от 0 до 100. Если методу `Next()` передать число 50, он выберет число из диапазона от 0 до 49, поэтому максимальный возможный ответ будет равен 98, а не 100. После выполнения первых двух операторов в методе каждая из двух целочисленных переменных — `addend1` и `addend2` — содержит случайное число в диапазоне от 0 до 50. На этом снимке экрана показан код на Visual C#, однако для Visual Basic IntelliSense работает точно так же.  
  
     Более внимательно ознакомимся с этими операторами.  
  
     [!code-csharp[VbExpressTutorial3Step2#18](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#18)]
     [!code-vb[VbExpressTutorial3Step2#18](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#18)]  
  
     Операторы задают свойства **Text** двух меток — **plusLeftLabel** и **plusRightLabel** — так, чтобы они отображали два случайных числа. Для преобразования чисел в текст необходимо использовать метод `ToString()` целого числа. (В программировании под "строкой" понимается текст. Элементы управления Label могут отображать только текст, но не числа.  
  
6. В окне разработки либо двойным щелчком нажмите кнопку **Запуск**, либо выберите ее и нажмите клавишу ВВОД.  
  
     Когда игрок нажимает эту кнопку, головоломка должна запуститься; вы только что добавили обработчик событий Click для реализации этого поведения.  
  
7. Добавьте следующие два оператора.  
  
     [!code-csharp[VbExpressTutorial3Step2#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial3Step2#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#4)]  
  
     Первый оператор вызывает новый метод `StartTheQuiz()`. Второй оператор устанавливает свойству **Enabled** элемента управления **startButton** значение **False**, чтобы игрок не мог нажать кнопку в процессе работы головоломки.  
  
8. Сохраните код, запустите его и нажмите кнопку **Запуск**.  
  
     Появляется задача на сложение случайных чисел, как показано на рисунке ниже.  
  
     ![Задача на сложение случайных чисел](../ide/media/express-additionproblem.png "Express_AdditionProblem")  
Задача на сложение случайных чисел  
  
     В следующем шаге руководства вам предстоит добавить сумму.  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
- Следующий раздел руководства: [Шаг 3. Добавление таймера с обратным отсчетом](../ide/step-3-add-a-countdown-timer.md).  
  
- Предыдущий раздел руководства: [Шаг 1. Создание проекта и добавление меток в форму](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
