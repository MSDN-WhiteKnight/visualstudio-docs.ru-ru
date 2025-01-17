---
title: Поиск и замена текста и выбор нескольких точек вставки
ms.date: 08/14/2018
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5fc437d1365fe58c8eb7ae725196c4ad3370836
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548378"
---
# <a name="find-and-replace-text"></a>Поиск и замена текста

С помощью элементов управления [Поиск и замена](#find-and-replace-control) (**CTRL**+**F** или **CTRL**+**H**) и [Поиск и замена в файлах](#find-in-files-and-replace-in-files) (**CTRL**+**SHIFT**+**F** или **CTRL**+**SHIFT**+**H**) можно найти и заменить текст в редакторе Visual Studio. Вы можете найти и заменить только *несколько* экземпляров текста с помощью *[выбора нескольких точек вставки](#multi-caret-selection)* .

> [!TIP]
> Если необходимо переименовать символы кода, такие как имена переменных или методов, то вместо поиска и замены лучше выполнить *[рефакторинг](../ide/reference/rename.md)* . Рефакторинг обладает интеллектуальными возможностями и может распознавать области, в то время как функция поиска и замены слепо заменяет все вхождения.

Возможность поиска и замены доступна в редакторе, в некоторых других текстовых окнах (например, в **результатах поиска**), в окнах конструкторов (например, в конструкторе XAML и в конструкторе Windows Forms) и в окнах инструментов.

В качестве области поиска можно задать текущий документ, текущее решение или пользовательский набор папок. Вы также можете указать набор расширений имен файлов для поиска по нескольким файлам. Синтаксис поиска можно настроить с помощью [регулярных выражений](../ide/using-regular-expressions-in-visual-studio.md) .NET.

> [!TIP]
> Поле [Найти/команда](../ide/find-command-box.md) доступно как элемент управления панели инструментов, но оно не отображается по умолчанию. Чтобы отобразить поле **Найти/команда**, выберите на **стандартной** панели инструментов команду **Добавить или удалить кнопки** и щелкнув **Найти**.

## <a name="find-and-replace-control"></a>Элемент управления "Поиск и замена"

- Нажмите **CTRL**+**F** для быстрого *поиска* строки в текущем файле.
- Нажмите **CTRL**+**H** для быстрого *поиска и замены* строки в текущем файле.

Элемент управления **Поиск и замена** отображается в правом верхнем углу окна редактора кода. Он немедленно выделяет все вхождения заданной поисковой строки в текущем документе. Вы можете переходить от одного вхождения к другому, нажав кнопку **Найти далее** или **Найти предыдущий** на элементе управления поиска.

![Поиск и замена в Visual Studio](media/find-and-replace-box.png)

Перейти к параметрам замены можно, нажав кнопку рядом с текстовым полем **Найти**. Чтобы изменять по одному вхождению за раз, выберите **Заменить следующий** рядом с текстовым полем **Заменить**. Чтобы заменить все найденные совпадения, нажмите кнопку **Заменить все**.

Чтобы изменить цвет выделения совпадений, в меню **Сервис** последовательно выберите **Параметры**, затем **Среда**, а затем **Шрифты и цвета**. В списке **Показать параметры для** выберите **Текстовый редактор**, а затем в списке **Отображаемые элементы** выберите **Найти выделенный текст (расширение)** .

### <a name="search-tool-windows"></a>Окна инструмента поиска

Элемент управления **Найти** можно использовать в текстовых окнах и окнах кода, таких как окна **вывода** и **результатов поиска**, выбрав **Правка** > **Поиск и замена** (или нажав клавиши **CTRL+F**).

Версия элемента управления **Найти** также доступна в некоторых окнах инструментов. Например, можно фильтровать список элементов управления в окне **панели элементов** путем ввода текста в поле поиска. Другие окна инструментов, для которых поддерживается поиск содержимого, включают **обозреватель решений**, окно **Свойства** и **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Поиск и замена в файлах

- Нажмите **CTRL**+**SHIFT**+**F** для быстрого *поиска* строки в нескольких файлах.
- Нажмите **CTRL**+**SHIFT**+**H** для быстрого *поиска и замены* строки в нескольких файлах.

Функции **Найти/Заменить в файлах** аналогичны функциям элемента управления **Поиск и замена** за исключением того, что можно определить область поиска. Вы можете выполнить поиск не только в текущем открытом файле в редакторе, но также во всех открытых документах, всем решении, текущем проекте и выбранном наборе папок. Также можно выполнять поиск по расширению имени файла. Чтобы перейти к диалоговому окну **поиска и замены в файлах**, выберите **Поиск и замена** в меню **Правка** (или нажмите клавиши **CTRL**+**SHIFT**+**F**).

![Поиск в файлах в Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Результаты поиска

При выборе варианта **Найти все** откроется окно **Результаты поиска** со списком найденных совпадений. При выборе результата в списке отображается связанный файл и выделяется искомый текст. Если файл не открыт для редактирования, он открывается на вкладке предварительного просмотра в правой части набора вкладок. Для поиска в списке **Результаты поиска** можно использовать элемент управления **Найти**.

### <a name="create-custom-search-folder-sets"></a>Создание пользовательских наборов папок поиска

Область поиска можно определить, нажав кнопку **Выбор папок поиска** (она выглядит как **...** ) рядом с полем **Поиск в**. В диалоговом окне **Выбор папок поиска** можно указать набор папок для поиска и сохранить спецификацию для дальнейшего использования.

> [!TIP]
> Если к вашему компьютеру подключен диск удаленного компьютера, можно указать папки для поиска на удаленном компьютере.

### <a name="create-custom-component-sets"></a>Создание пользовательских наборов компонентов

В качестве области поиска можно определить наборы компонентов, нажав кнопку **Изменить настраиваемый набор компонентов** рядом с полем **Поиск в**. Можно указать установленные компоненты .NET и COM, проекты Visual Studio, включенные в решение, а также любые сборки или библиотеки типов (*DLL*, *TLB*, *OLB*, *EXE* или *OCX*). Для поиска ссылок выберите поле **Искать по ссылкам**.

## <a name="multi-caret-selection"></a>Выбор нескольких точек вставки

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Выбор блока](/visualstudio/mac/block-selection).

**Новая возможность в Visual Studio 2017 версии 15.8**

Используйте *выбор нескольких точек вставки*, чтобы внести одинаковые изменения в несколько мест одновременно. Например, вы можете вставить одинаковый текст или изменить существующий текст в нескольких местах одновременно.

На следующем снимке экрана `-0000` выбран в трех местах. Если пользователь нажмет **Удалить**, все три фрагмента будут удалены:

![Выбор нескольких точек вставки в файле XML в Visual Studio](media/multi-caret-selection.png)

Чтобы выбрать несколько точек вставки, выберите первый фрагмент текста обычным образом, а затем нажмите клавишу **ALT** и выберите фрагменты в других местах. Можно также автоматически добавить совпадающий текст в качестве дополнительного выделения или выбрать поле текста для внесения одинаковых правок в каждой строке.

> [!TIP]
> Если вы выбрали **ALT** как клавишу-модификатор для команды "Перейти к определению" по щелчку мыши в меню **Сервис** > **Параметры**, функция выбора нескольких точек вставки недоступна.

### <a name="commands"></a>Команды

Используйте следующие клавиши и действия для выбора нескольких точек вставки:

|Сочетание клавиш|Действие|
|-|-|
|**CTRL**+**ALT** + щелчок|Добавить дополнительную точку вставки|
|**CTRL**+**ALT** + двойной щелчок|Добавить дополнительное выделенное слово|
|**CTRL**+**ALT** + щелчок + перетаскивание|Добавить дополнительный выделенный фрагмент|
|**SHIFT**+**ALT**+ **.**|Добавить следующий совпадающий текст как выделенный фрагмент|
|**CTRL**+**SHIFT**+**ALT**+ **,**|Выделить все совпадающие фрагменты текста|
|**SHIFT**+**ALT**+ **,**|Удалить последний выделенный фрагмент|
|**CTRL**+**SHIFT**+**ALT**+ **.**|Пропустить следующий совпадающий фрагмент|
|**ALT** + щелчок|Добавить выделенное поле|
|**ESC** или щелчок|Отменить выбор всех элементов|

Некоторые команды также доступны в меню **Изменить** в разделе **Несколько точек вставки**:

![Всплывающее меню "Несколько точек вставки" в Visual Studio](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>См. также

- [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Рефакторинг кода в Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Выбор блока (Visual Studio для Mac)](/visualstudio/mac/block-selection)