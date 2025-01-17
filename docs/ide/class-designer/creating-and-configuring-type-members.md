---
title: Создание и настройка членов типов (конструктор классов)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39932fe8d4afa31c66d6daa4af33d963b5612eb2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975545"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Создание и настройка членов типа в конструкторе классов

Можно добавить эти члены в типы на схеме классов и настроить данные члены в окне **Сведения о классах**:

|**Type**|**Элементы, которые тип может содержать**|
|--------------| - |
|Класс|метод, свойство (для C# и Visual Basic), поле, событие (для C# и Visual Basic), конструктор (метод), деструктор (метод), константа|
|Enum|член|
|Интерфейс|метод, свойство, событие (для C# и Visual Basic)|
|Абстрактный класс|метод, свойство (для C# и Visual Basic), поле, событие (для C# и Visual Basic), конструктор (метод), деструктор (метод), константа|
|Структура (структура в коде C#)|метод, свойство (для C# и Visual Basic), поле, событие (для C# и Visual Basic), конструктор (метод), константа|
|делегат|параметр|
|Модуль (только в Visual Basic)|метод, свойство, поле, событие, конструктор, константа|

> [!NOTE]
> Способствуют более лаконичному объявлению свойств, если в методах доступа "get" и "set" свойства не требуется дополнительная логика, определяемая посредством автоматически внедренных свойств (только C#). Чтобы отобразить полную сигнатуру, необходимо в меню **Диаграмма классов** выбрать **Изменить формат членов** > **Показать полную сигнатуру**. Дополнительные сведения об автоматически реализуемых свойствах см. в статье [Автоматически реализуемые свойства](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Типичные задачи

|Задача|Справочные материалы|
|----------| - |
|**Начало работы**. Перед созданием и настройкой элементов типа необходимо открыть окно **Сведения о классах**.|- [Открытие окна "Сведения о классах"](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Примечания об использовании окна сведений о классах](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Отображение информации только для чтения](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Сочетания клавиш и кнопок мыши в диаграмме классов и окне "Сведения о классах"](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Создание и изменение элементов типа**. В окне **Сведения о классах** вы можете создавать новые элементов, изменять существующие элементов, а также добавлять параметры в метод.|- [Создание членов](creating-and-configuring-type-members.md#create-members)<br />- [Изменение членов типов](creating-and-configuring-type-members.md#modify-type-members)<br />- [Добавление параметров в методы](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Открытие окна "Сведения о классах"

По умолчанию окно **Сведения о классах** открывается автоматически при открытии новой диаграммы классов. См. практическое руководство по [ добавлению диаграмм классов в проекты](how-to-add-class-diagrams-to-projects.md). Кроме того, можно открыть окно **Сведения о классах** следующим образом:

- Щелкните любой класс на диаграмме правой кнопкой мыши для вызова контекстного меню и выберите пункт **Сведения о классах**.

- В строке меню выберите **Вид** > **Другие окна** > **Сведения о классах**.

## <a name="create-members"></a>Создание членов

Элемент можно создать с помощью следующих инструментов:

- **Конструктор классов**

- Панель инструментов окна **Сведения о классах**

- Окно **Сведения о классах**

> [!NOTE]
> С помощью процедур, описанных в данном подразделе, можно создать конструкторы и деструкторы. Не забывайте, что конструкторы и деструкторы — это специальные типы методов, которые отображаются в секции **Методы** в фигурах диаграммы классов и в разделе **Методы** таблицы окна **Сведения о классах**.

> [!NOTE]
> Единственная сущность, которую можно добавить к делегату — это параметр. Обратите внимание, что процедура под названием "Создание члена с помощью панели инструментов окна **Сведения о классах**" не подходит для данного действия.

### <a name="create-a-member-using-class-designer"></a>Создание члена с помощью конструктора классов

1. Правой кнопкой мыши щелкните тип, в который нужно добавить член, выберите пункт **Добавить** и нужный тип члена.

     Будет создана и добавлена в тип новая сигнатура элемента. При этом элементу будет присвоено имя по умолчанию, которое можно изменить в **конструкторе классов**, окне **Сведения о классах** или в окне **Свойства**.

2. Дополнительно укажите другие сведения об элементе, например его тип.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Создание члена с помощью панели инструментов окна "Сведения о классах"

1. В рабочей области конструирования выберите тип, в который необходимо добавить элемент.

     Тип станет активным, и его содержимое отобразится в окне **Сведения о классах**.

2. На панели инструментов в окне **Сведения о классах** щелкните верхний значок и выберите в раскрывающемся списке пункт **Создать \<член>** .

     Курсор переместится в поле **Имя** в строке типа добавляемого члена. Например, если выбрана команда **Создать свойство**, то курсор переместится в новую строку в разделе **Свойства** окна **Сведения о классах**.

3. Введите имя добавляемого элемента и нажмите клавишу ВВОД (или переместите фокус, например, нажав клавишу TAB).

     Будет создана и добавлена в тип новая сигнатура элемента. Теперь член существует в коде и отображается в **конструкторе классов**, окне **Сведения о классах** и в окне "Свойства".

4. Дополнительно укажите другие сведения об элементе, например его тип.

### <a name="create-a-member-using-the-class-details-window"></a>Создание члена с помощью окна "Сведения о классах"

1. В рабочей области конструирования выберите тип, в который необходимо добавить элемент.

     Тип станет активным, и его содержимое отобразится в окне **Сведения о классах**.

2. В окне **Сведения о классах** в разделе, содержащем тип добавляемого члена, щелкните **\<добавить член>** . Например, если необходимо добавить поле, щелкните **\<добавить поле>** .

3. Введите имя добавляемого элемента и нажмите клавишу ВВОД.

     Будет создана и добавлена в тип новая сигнатура элемента. Теперь член существует в коде и отображается в **конструкторе классов**, окне **Сведения о классах** и окне "Свойства".

4. Дополнительно укажите другие сведения об элементе, например его тип.

     **Примечание.** Для создания элементов также можно использовать сочетания клавиш. Дополнительные сведения см. в разделе [Сочетания клавиш и кнопок мыши в диаграмме классов и окне "Сведения о классах"](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Изменение членов типов

Конструктор классов позволяет изменять члены типов, отображаемые на схеме. Можно изменить члены любого типа, которые отображаются на схеме классов и не являются доступными только для чтения. Изменить члены типа можно с помощью редактирования прямо на рабочей области конструирования, а также с помощью окна "Свойства" и окна **Сведения о классах**.

Все члены, отображаемые в окне **Сведения о классах**, представляют члены типов на диаграмме классов. Существует четыре типа членов: методы, свойства, поля и события.

Все строки члена отображаются под заголовками, которые группируют члены по типу. Например, все свойства отображаются под заголовком **Свойства**, который можно свернуть или развернуть как узел в таблице.

Каждая строка члена отображает следующие элементы:

- **Значок члена**

     Каждый тип члена представлен своим значком. Наведите указатель мыши на значок члена, чтобы отобразить сигнатуру члена. Щелкните значок члена или пробел слева от значка члена, чтобы выбрать строку.

- **Имя члена**

     Столбец **Имя** в строке члена отображает имя члена. Это имя также отображается в свойстве **Имя** окна "Свойства". Данную ячейку можно использовать для изменения имени любого члена с разрешениями на чтение и запись.

     При наведении указателя мыши на имя члена отображается полное имя, если столбец **Имя** слишком узкий, чтобы показать полное имя.

- **Тип члена**

     Ячейка **MemberType** используется технологией IntelliSense, которая позволяет выбирать тип из списка всех доступных типов в текущем проекте или в проектах, на которые имеются ссылки.

- **Модификатор члена**

     Измените модификатор видимости члена на `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`) или `Default`.

- **\<добавить член>**

     Последняя строка в окне **Сведения о классах** содержит текст **\<добавить член>** в ячейке **Имя**. Если выбрана данная ячейка, то можно создать новый член. Дополнительные сведения см. в разделе [Создание членов](creating-and-configuring-type-members.md#create-members).

- **Свойства члена в окне "Свойства"**

     В окне **Сведения о классах** отображается подмножество свойств члена, которые отображаются в окне "Свойства". Изменение значения свойства в одном месте изменяет значение свойства глобально. Это касается отображения его значения в других местах.

- **Сводка**

     Ячейка **Сводка** содержит сводную информацию о члене. Щелкните многоточие в ячейке **Сводка**, чтобы просмотреть или изменить сведения в полях **Сводка**, **Тип возвращаемого значения** и **Примечания** для члена.

- **Скрыть**

     Если установлен флажок **Скрыть**, член в типе отображаться не будет.

### <a name="to-modify-a-type-member"></a>Изменение члена типа

1. Выберите тип в конструкторе классов.

2. Если окно **Сведения о классах** не отображается, нажмите кнопку окна **Сведения о классах** на панели инструментов конструктора классов.

3. Измените значения в полях сетки окна **Сведения о классах**. После каждого изменения нажимайте клавишу ВВОД или перемещайте фокус от измененного поля (например, нажимая клавишу TAB). Изменения немедленно отражаются в коде.

    > [!NOTE]
    > Если необходимо изменить только имя члена, это можно сделать с помощью редактирования прямо на схеме.

## <a name="add-parameters-to-methods"></a>Добавление параметров в методы

Добавить параметры в методы можно с помощью окна **Сведения о классах**. Параметры можно настроить так, чтобы они были обязательными или необязательными. Если предоставить значение для свойства **Дополнительное значение по умолчанию** параметра, конструктор сформирует код как необязательный параметр.

Строки параметров содержат следующие элементы:

- **Name**

     Столбец **Имя** в строке параметра отображает имя параметра. Это имя также отображается в свойстве **Имя** окна "Свойства". Данную ячейку можно использовать для изменения имени любого параметра с разрешениями на чтение и запись.

     Если столбец **Имя** слишком узкий, чтобы показать полное имя, необходимо навести указатель мыши на имя параметра.

- **Type**

     Ячейка **Тип параметра** использует технологию IntelliSense, которая позволяет выбирать тип из списка всех типов, доступных в текущем проекте или в проектах, на которые имеются ссылки.

- **Модификатор**

     Ячейка **Модификатор** в строке параметра принимает и отображает новый модификатор параметра. Чтобы ввести новый модификатор параметра, используйте раскрывающийся список для выбора из значений **None**, **ref**, **out** или **params** в C# и значений **ByVal**, **ByRef** или **ParamArray** в VB.

- **Сводка**

     Ячейка **Сводка** в строке параметра позволяет ввести комментарии к коду, отображаемые в IntelliSense при вводе параметра в редактор кода.

- **\<добавить параметр>**

     Строка последнего параметра члена содержит текст **<добавить параметр\>** в ячейке **Имя**. Щелчок на данной ячейке позволяет создать новый параметр. Дополнительные сведения см. в разделе [Добавление параметра в метод](creating-and-configuring-type-members.md#add-parameters-to-methods).

В окне **Свойства** отображаются те же свойства параметров, которые отображаются в окне **Сведения о классах**: **Имя**, **Тип**, **модификатор**, **Сводка**, а также свойство **Дополнительное значение по умолчанию**. Изменение свойства в одном месте обновляет значение свойства глобально, включая отображение его значения в других местах.

> [!NOTE]
> Инструкции по добавлению параметра в делегат см. в разделе [Создание членов](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Несмотря на то что деструктор является методом, у него не может быть параметров.

### <a name="to-add-a-parameter-to-a-method"></a>Добавление параметра в метод

1. В области диаграммы щелкните тип, содержащий метод, в который необходимо добавить параметр.

     Тип получает фокус, и его содержимое отображается в окне **Сведения о классах**.

2. В окне **Сведения о классах** разверните строку метода, в который необходимо добавить параметр.

     Отобразится строка соответствующего параметра, содержащая пару круглых скобок и слова **\<добавить параметр>** .

3. Щелкните **\<добавить параметр>** , введите имя нового параметра и нажмите клавишу **ВВОД**.

     Новый параметр добавлен в метод и в код метода. Он отображается в окне **Сведения о классах** и в окне "Свойства".

4. Дополнительно можно указать другие сведения о параметре, например его тип.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Добавление необязательного параметра в метод

1. На поверхности схемы щелкните тип, содержащий метод, в который необходимо добавить необязательный параметр.

     Тип получает фокус, и его содержимое отображается в окне **Сведения о классах**.

2. В окне **Сведения о классах** разверните строку метода, в который необходимо добавить необязательный параметр.

     Отобразится строка соответствующего параметра, содержащая пару круглых скобок и слова **\<добавить параметр>** .

3. Щелкните **\<добавить параметр>** , введите имя нового параметра и нажмите клавишу **ВВОД**.

     Новый параметр добавлен в метод и в код метода. Он отображается в окне **Сведения о классах** и в окне "Свойства".

4. В окне свойств введите значение свойства **Дополнительное значение по умолчанию**. После настройки свойства "Дополнительное значение по умолчанию" параметра этот параметр станет необязательным.

    > [!NOTE]
    > Необязательные параметры должны находиться в конце списка параметров.

## <a name="class-details-usage-notes"></a>Примечания об использовании окна сведений о классах

Обратите внимание на следующие советы по работе с окном **Сведения о классах**.

### <a name="editable-and-non-editable-cells"></a>Изменяемые и неизменяемые ячейки

Все ячейки в окне **Сведения о классах** являются изменяемыми за немногими исключениями:

- Весь тип доступен только для чтения в случаях, когда, например, тип находится в сборке, на которую существует ссылка. При выборе фигуры в конструкторе классов окно **Сведения о классах** отображает сведения о ней в состоянии только для чтения.

- Для индексаторов имя доступно только для чтения, а остальные параметры (тип, модификатор, общие сведения) являются изменяемыми.

- Параметры всех универсальных шаблонов в окне **Сведения о классах** доступны только для чтения. Чтобы изменить параметр универсального шаблона, необходимо отредактировать его исходный код.

- Имя параметра типа, которое определено в универсальном типе, доступно только для чтения.

- Если код типа является нечитаемым (нераспознанным), в окне **Сведения о классах** отображается содержимое типа как доступное только для чтения.

### <a name="the-class-details-window-and-source-code"></a>Окно "Сведения о классах" и исходный код

- Чтобы просмотреть исходный код, необходимо щелкнуть фигуру правой кнопкой мыши в окне **Сведения о классах** (или конструкторе классов) и затем выбрать пункт "Просмотреть код". Откроется файл исходного кода и будет отображено место выбранного элемента.

- Изменение исходного кода сразу отражается в сведениях о сигнатуре в конструкторе классов и в окне **Сведения о классах**. Если окно **Сведения о классах** закрыто, то обновленные сведения отобразятся при следующем открытии окна.

- Если код типа является нечитаемым (нераспознанным), в окне **Сведения о классах** отображается содержимое типа как доступное только для чтения.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Функциональные возможности буфера обмена в окне "Сведения о классах"

Из окна **Сведения о классах** можно копировать или вырезать поля или строки и вставлять их в другой тип. Вырезать строку можно только в том случае, если она доступна не только для чтения. При вставке строки окно **Сведения о классах** присваивает строке новое имя (производное от имени копируемой строки) для предотвращения конфликта.

## <a name="display-of-read-only-information"></a>Отображение информации только для чтения

Конструктор классов и окно **Сведения о классах** могут отображать типы (и члены типов) для следующих элементов:

- проекта, который содержит схему классов;

- проекта, на который имеются ссылки из проекта, содержащего схему классов;

- сборки, на которую имеется ссылка из проекта, содержащего схему классов.

В двух последних случаях упоминаемая сущность (тип или член) доступна только для чтения в схеме классов, отображающей ее.

Весь проект или его часть, например отдельные файлы, могут быть доступны только для чтения. В наиболее распространенных случаях проект или один из его файлов доступны только для чтения, если проект находится под контролем системы управления версиями (и не извлечен), если проект существует во внешней сборке или если операционная система задает для файлов проекта права только на чтение.

**Система управления версиями**

Поскольку диаграмма классов сохраняется как файл в проекте, то для сохранения всех изменений, выполненных в конструкторе классов или окне **Сведения о классах**, необходимо извлекать проект.

**Проекты, доступные только для чтения**

Проект может быть доступен только для чтения не только по причине того, что он находится под влиянием системы управления версиями файлов. При закрытии проект отображает диалоговое окно, в котором спрашивается, нужно ли переписать файл проекта, отменить изменения (не сохранять) или не закрывать проект. Если выбрать вариант "переписать", файлы проекта будут перезаписаны и станут доступными для чтения и записи. Будет добавлен новый файл схемы классов.

**Типы, доступные только для чтения**

При попытке сохранить проект, содержащий типы, у которых файлы исходного кода доступны только для чтения, откроется диалоговое окно **Сохранение файла, доступного только для чтения**, которое позволяет выбрать либо сохранение файла под новым именем или в новом месте, либо перезапись файла, доступного только для чтения. Если переписать файл, новая копия уже не будет доступной только для чтения.

Если файл кода содержит синтаксическую ошибку, фигура отображает код, файл которого будет временно доступен только для чтения до устранения синтаксической ошибки. Фигуры в данном состоянии отображают красный текст и красный значок, который отображает подсказку "Файл исходного кода содержит ошибку разбора".

Ссылочный тип (например, тип .NET Framework), который существует в другом узле проекта или в узле сборки, на которую имеется ссылка, отображается на рабочей области конструирования как доступный только для чтения. Локальный тип, который существует в открытом проекте, доступен для чтения и записи, и его фигура отображается на рабочей области конструирования.

Индексаторы доступны для чтения и записи в коде и в окне **Сведения о классах**, однако имя индексатора доступно только для чтения.

С помощью конструктора классов или окна **Сведения о классах** невозможно изменить разделяемые методы, поэтому для их изменения необходимо использовать редактор кода.

С помощью конструктора классов или окна **Сведения о классах** невозможно изменить машинный код C++, поэтому для его изменения необходимо использовать редактор кода.

## <a name="see-also"></a>См. также

- [Просмотр типов и отношений](designing-and-viewing-classes-and-types.md)
- [Рефакторинг классов и типов](refactoring-classes-and-types.md)