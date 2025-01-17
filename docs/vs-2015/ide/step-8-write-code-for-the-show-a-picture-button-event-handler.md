---
title: Шаг 8. Написание кода для показа изображения обработчика событий кнопки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ef4d1221b59e6f1e5ed3de94f91742bbea778462
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679329"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Шаг 8. Написание кода для обработчика событий кнопки "Показать рисунок"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

На этом шаге выполняется создание кнопки **Показать рисунок**, которая работает следующим образом.  
  
- Когда пользователь нажимает эту кнопку, программа открывает диалоговое окно **Открыть файл**.  
  
- Если пользователь открывает файл рисунка, программа показывает этот рисунок в PictureBox.  
  
  Среда IDE содержит мощное средство IntelliSense, которое помогает в написании кода. По мере написания кода, среда IDE открывает поле, в котором содержатся предлагаемые завершения для частей вводимых слов. Она пытается определить, что требуется сделать далее и автоматически переходит к последнему выбранному элементу из списка. Для перемещения по списку можно использовать клавиши со стрелками ВВЕРХ или ВНИЗ или можно продолжать вводить буквы, чтобы сузить выбор. Когда появится необходимый элемент, для его выбора нажмите клавишу TAB. Либо можно проигнорировать предложение, если оно не требуется.  
  
  ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo")видеоверсию этого раздела, см. в разделе [учебник 1: Create a Picture Viewer in Visual Basic — видео 4](http://go.microsoft.com/fwlink/?LinkId=205215) или [учебник 1: Create a Picture Viewer в C# — видео 4](http://go.microsoft.com/fwlink/?LinkId=205203). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.  
  
### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Написание кода для обработчика событий кнопки "Показать рисунок"  
  
1. Перейдите к конструктору Windows Forms и дважды щелкните кнопку **Показать рисунок**. Среда интегрированной разработки немедленно переключается на конструктор кода и перемещает курсор внутрь метода `showButton_Click()`, который был добавлен ранее.  
  
2. Введите `i` в пустой строке между двумя фигурными скобками { } (В Visual Basic введите пустую строку между Private Sub... and End Sub.) Откроется окно **IntelliSense**, как показано на рисунке ниже.  
  
     ![IntelliSense с кодом Visual C#](../ide/media/express-ifintellisense.png "Express_IfIntellisense")  
IntelliSense с кодом Visual C#  
  
3. Окно **IntelliSense** должно выделить слово **if** (в противном случае введите в нижнем регистре `f`). Обратите внимание, каким образом небольшое окно *подсказка* рядом с окном **IntelliSense** отображается с описанием **Фрагмент кода для инструкции if**. (в Visual Basic подсказка также указывает такой фрагмент, но немного с другим содержимым). Необходимо использовать этот фрагмент, поэтому нажмите клавишу TAB, чтобы вставить **if** в свой код. Затем снова нажмите клавишу TAB, чтобы использовать фрагмент **if**. (Если вы выберете что-то другое и окно **IntelliSense** исчезнет, нажмите клавишу BACKSPACE, чтобы удалить **i**, и повторно введите эту букву, чтобы снова открыть окно **IntelliSense**).  
  
     ![Код Visual C#](../ide/media/express-highlighttrue.png "Express_HighlightTrue")  
Код Visual C#  
  
4. Далее IntelliSense используется для ввода дополнительного кода для открытия диалогового окна **Открыть файл**. Если пользователь нажимает кнопку **ОК**, PictureBox загружает выбранный пользователем файл. Следующие действия показывают как ввести код. Хотя представлено множество действий, это просто несколько нажатий клавиш.  
  
    1. Начните с выделенным текстом **true** во фрагменте. Введите `op`, чтобы перезаписать его. (в Visual Basic необходимо начинать с первой заглавной буквы, поэтому введите `Op`).  
  
    2. Откроется окно **IntelliSense** и отобразит компонент **openFileDialog1**. Нажмите клавишу TAB, чтобы выбрать его. (в Visual Basic он начинается с заглавной буквы, поэтому будет представлен **OpenFileDialog1**; убедитесь, что выделен **OpenFileDialog1**).  
  
         Дополнительные сведения о `OpenFileDialog` см. в разделе [OpenFileDialog](https://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).  
  
    3. Введите точку (`.`). Так как точка введена сразу после элемента **openFileDialog1**, окно **IntelliSense** открывается с методами и свойствами компонента **OpenFileDialog**. Это те же самые свойства, которые отображаются в окне **Свойства** при выборе этого окна в конструкторе Windows Forms. Также можно выбрать методы, которые дают указания компонентам на выполнение определенных действий (например, открыть диалоговое окно).  
  
        > [!NOTE]
        > Окно **IntelliSense** может показывать свойства и методы. Чтобы определить, какие элементы отображаются, проверьте значок слева от каждого элемента в окне **IntelliSense**. Рядом с каждым методом представлен значок кубика, рядом с каждым свойством представлен значок гаечного ключа. Также рядом с каждым событием представлен значок с изображением молнии. Ниже представлены эти значки.  
  
         ![Значок метода](../ide/media/express-iconmethod.png "Express_IconMethod")  
Значок метода  
  
         ![Значок свойства](../ide/media/express-iconproperty.png "Express_IconProperty")  
Значок свойства  
  
         ![Значок события](../ide/media/express-iconevent.png "Express_IconEvent")  
Значок события  
  
    4. Начните набирать `ShowDialog` (для IntelliSense регистр значения не имеет). Метод `ShowDialog()` будет открывать диалоговое окно **Открыть файл**. После выделения **ShowDialog** в окне нажмите клавишу TAB. Также можно выделить "ShowDialog" и нажать клавишу F1 для получения соответствующей справки.  
  
         Дополнительные сведения о методе `ShowDialog()` см. в разделе [Метод ShowDialog](https://msdn.microsoft.com/library/c7ykbedk.aspx).  
  
    5. При использовании метода в элементе управления или компоненте (такое использование называется *вызов метода*) необходимо добавить круглые скобки. Введите открывающую и закрывающую скобки сразу после "g" в разделе `ShowDialog`: `()`; теперь строка должна принять вид "openFileDialog1.ShowDialog()".  
  
        > [!NOTE]
        > Методы являются важнейшей частью любой программы. В этом руководстве показано несколько способов использования методов. Можно вызвать метод компонента, чтобы указать ему выполнение некоторых действий, аналогично тому, как вы вызывали метод `ShowDialog()` компонента **OpenFileDialog**. Можно создать собственные методы, чтобы программа выполняла определенные действия, например метод, создание которого выполняется сейчас, выполняла вызов метода `showButton_Click()`, который открывает диалоговое окно и рисунок при нажатием пользователем кнопки.  
  
    6. В Visual C# добавьте пробел, затем два знака равенства (`==`). В Visual Basic добавьте пробел, затем один знак равенства (`=`). В Visual C# и в Visual Basic используются разные операторы равенства.  
  
    7. Добавьте еще один пробел. Как только это будет сделано, откроется другое окно **IntelliSense**. Начните вводить `DialogResult` и нажмите клавишу TAB, чтобы добавить его.  
  
        > [!NOTE]
        > При написании кода для вызова метода, в некоторых случаях он возвращает значение. В этом случае метод `ShowDialog()` компонента **OpenFileDialog** возвращает значение DialogResult. DialogResult — это специальное значение, которое указывает на событие, которое происходит в диалогом окне. В компоненте **OpenFileDialog** пользователь может нажать кнопку **ОК** или **Отмена**, чтобы метод `ShowDialog()` возвращал значение DialogResult.OK или значение DialogResult.Cancel.  
  
    8. Чтобы открыть значение DialogResult в окне **IntelliSense**, введите точку. Введите букву `O` и нажмите клавишу TAB, чтобы вставить **ОК**.  
  
         Дополнительные сведения о `DialogResult` см. в разделе [DialogResult](https://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).  
  
        > [!NOTE]
        > Первая строка кода должна быть завершена. В Visual C# это выглядит следующим образом.  
        >   
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`  
        >   
        >  В Visual Basic это выглядит следующим образом.  
        >   
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`  
  
    9. Теперь добавьте несколько строк кода. Их можно ввести вручную (или копировать и вставить), однако попробуйте использовать для добавления строк IntelliSense. Чем больше вы знакомы с IntelliSense, тем быстрее можете писать собственный код. Итоговая реализация метода `showButton_Click()` будет выглядеть следующим образом. (Выберите вкладку **VB** для просмотра версии кода для Visual Basic.)  
  
         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
- Следующий раздел руководства: [Шаг 9. Просмотрите, комментарий и тестировать код](../ide/step-9-review-comment-and-test-your-code.md).  
  
- Предыдущий раздел руководства: [Шаг 7. Добавление компонентов диалогового окна в форму](../ide/step-7-add-dialog-components-to-your-form.md).
