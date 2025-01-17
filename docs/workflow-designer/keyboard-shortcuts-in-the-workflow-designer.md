---
title: 'Конструктор рабочих процессов: Сочетания клавиш'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2143b67297ba2e4bd2751054b789274595505cb3
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66431882"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Сочетания клавиш конструктора рабочих процессов

Все основные функциональные возможности конструктора рабочих процессов может осуществляться с помощью клавиатуры.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Перемещение по конструктору рабочих процессов с помощью клавиатуры

В Visual Studio глобальные и отладочные сочетания клавиш применяются в конструктор рабочих процессов. Кроме того будут созданы несколько определенные сочетания клавиш конструктора рабочих процессов. В Visual Studio все сочетания клавиш могут быть переназначены. Тем не менее, в повторно размещенном приложении эти сочетания клавиш жестко запрограммированы.

### <a name="workflow-designer-keyboard-shortcuts"></a>Сочетания клавиш конструктора рабочих процессов

В следующей таблице перечислены сочетания клавиш по умолчанию, назначенные команд конструктора рабочих процессов.

|Сочетание клавиш|Цель|
|-|-------------|
|CTRL+E, A|Отображает или скрывает конструктор аргументов.|
|CTRL+E, C|Свертывает выделенное действие на месте.|
|CTRL+E, E|Развертывает выделенное действие на месте.|
|CTRL+E, F|Соединяет выделенные действия в блок-схему.|
|CTRL+E, I|Отображает или скрывает конструктор импорта.|
|CTRL+E, M|Перемещает фокус ввода к следующему элементу в последовательности табуляции.|
|CTRL+E, N|Создает новую переменную в области выбранного (или ближайшего) действия.|
|CTRL+E, O|Отображает или скрывает карту общих сведений.|
|CTRL+E, P|Переходит к родителю выбранного действия. Переходит на один уровень выше в строке навигатора и изменяет корневое действие в области конструктора.|
|CTRL+E, S|Добавляет элемент с фокусом ввода к текущему выделению.|
|CTRL+E, V|Отображает или скрывает конструктор переменных.|
|CTRL+E, X|Развертывает все действия в рабочем процессе.|
|CTRL+ALT+F6|Перемещает фокус ввода от текущей области пользовательского интерфейса к следующей области в последовательности. Порядок выглядит следующим образом:<br /><br /> 1.  Строка навигатора.<br />2.  Область конструктора<br />3.  Конструктор аргументов, переменных или импорта (если открыт)<br />4.  Оболочка|

### <a name="flowchart"></a>Блок-схема

Следующий список содержит жесты, используемые для создания блок-схемы с помощью клавиатуры. Как и в остальной части конструктора рабочих процессов действия добавляются в область конструктора, с помощью глобальных сочетаний клавиш элементов в Visual Studio.

- Для перемещения действия выделите его и с помощью клавиш перемещения курсора переместите в другое место.

- Чтобы изменить размер блок-схемы, переместите действие за текущую границу блок-схемы с помощью клавиш перемещения курсора. Блок-схема автоматически изменит размер.

- Чтобы задать действие в качестве начального узла, используйте **задайте в качестве начального узла** команду в контекстном меню.

- Соединение действий

    1. Выберите исходное действие, перейдя к нему по табуляции.

    2. Нажмите CTRL+E, M нужное количество раз, чтобы переместить фокус ввода к целевому действию.

    3. Нажмите CTRL+E, S, чтобы добавить целевое действие к выделению.

    4. Нажмите CTRL+E, F, чтобы добавить соединитель из источника в назначение.

Замечания о соединении действий с помощью клавиатуры:

- Можно одновременно создавать несколько соединений, добавляя несколько действий к выделению до нажатия CTRL+E, F. Соединения создаются в порядке добавления действий к выделению.

- Если пара действий не может быть соединена, например, если исходное действие уже имеет исходящее соединение, то могут быть выполнены другие соединения между действиями в выделении.

- Когда **FlowDecision** включен в выделение и **FlowDecision** не имеет исходящих соединителей, разъему помещается на **True** ветви.

### <a name="expression-editing"></a>Редактирование выражений

По умолчанию сочетания клавиш по умолчанию для Visual Basic текста при правке применять в редакторе выражений в конструкторе рабочих процессов, со следующими ограничениями:

- Переназначение сочетания клавиш для следующих команд не действует. При изменении выражения для доступа к этим командам можно использовать только сочетания клавиш по умолчанию.

   - Вырезать
   - Копировать
   - Вставить
   - Выделить все
   - Отменить
   - Повторить

- Чтобы переназначить сочетания клавиш для команд редактирования выражений внутри конструктора рабочих процессов в Visual Studio, измените сочетания клавиш в области конструктора рабочих процессов. Изменения, внесенные в области текстовый редактор не применяются автоматически к конструктора рабочих процессов. Если необходимо переназначить сочетания клавиш в обоих местах, то необходимо дважды применить изменения (по одному разу в каждой из областей).