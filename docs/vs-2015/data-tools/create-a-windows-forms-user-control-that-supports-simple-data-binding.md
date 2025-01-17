---
title: Создать пользовательский элемент управления Windows Forms, который поддерживает простую привязку данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ac931dfcf7b56619707a2bd42a32f5a369b04d9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704990"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Создание пользовательского элемента управления Windows Forms с простой привязкой данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При отображении данных на формах в приложениях Windows вы можете выбрать имеющиеся элементы управления в **области элементов** или создать пользовательские элементы управления, если вашему приложению требуется функциональность, отсутствующая в стандартных элементах управления. В этом пошаговом руководстве демонстрируется создание элемента управления, реализующего <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Элементы управления, реализующие <xref:System.ComponentModel.DefaultBindingPropertyAttribute>, могут содержать одно свойство, которое можно привязать к данным. Такие элементы управления похожи на <xref:System.Windows.Forms.TextBox> или <xref:System.Windows.Forms.CheckBox>.  
  
 Дополнительные сведения о создании элементов управления, см. в разделе [Разработка Windows Forms элементов управления во время разработки](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 При создании элементов управления для использования в сценариях привязки данных, должны реализовывать один из следующих атрибутов привязки к данным:  
  
|Использование атрибута привязки данных|  
|-----------------------------------|  
|Реализуйте <xref:System.ComponentModel.DefaultBindingPropertyAttribute> на простых элементах управления, таких как <xref:System.Windows.Forms.TextBox>, которые отображают отдельный столбец (или свойство) данных. (Этот процесс описан в данном пошаговом руководстве.)|  
|Реализуйте <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.DataGridView>, которые отображают списки (или таблицы) данных. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает сложную привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Реализуйте <xref:System.ComponentModel.LookupBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.ComboBox>, которые отображают списки (или таблицы) данных, но также должны представлять отдельный столбец или отдельное свойство. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms с привязкой данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 В этом пошаговом руководстве создается простой элемент управления, отображающий данные из одного столбца в таблице. В данном примере используется столбец `Phone` таблицы `Customers` из учебной базы данных "Борей". Этот простой элемент управления отображает номера телефонов заказчиков в стандартный формат номера телефона, с помощью <xref:System.Windows.Forms.MaskedTextBox> и задавая маску для номера телефона.  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
- Создайте новый **приложения Windows**.  
  
- Добавление нового **пользовательского элемента управления** в проект.  
  
- Визуальное проектирование пользовательского элемента управления.  
  
- Реализация атрибута `DefaultBindingProperty`.  
  
- Создание набора данных с помощью **конфигурации источника данных** мастера.  
  
- Настройка столбца **Phone** в окне **Источники данных** для использования нового элемента управления.  
  
- Создание формы для отображения данных в новом элементе управления.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
- Доступ к примеру базы данных "Борей".
  
## <a name="create-a-windows-application"></a>Создание приложения Windows  
 Первым шагом является создание **приложения Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1. В Visual Studio из **файл** меню, создайте новый **проекта**.  
  
2. Назовите проект **SimpleControlWalkthrough**.  
  
3. Выберите **приложения Windows** и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [клиентских приложений](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Создается проект **SimpleControlWalkthrough**, который добавляется в **Обозреватель решений**.  
  
## <a name="add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект  
 В этом пошаговом руководстве создается простой элемент управления можно привязать к данным из **пользовательский элемент управления**, поэтому необходимо добавить **пользовательский элемент управления** элемент **SimpleControlWalkthrough** проекта.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект  
  
1. В меню **Проект** выберите пункт **Добавить пользовательский элемент управления**.  
  
2. Тип `PhoneNumberBox` в имя области, а также выберите **добавить**.  
  
     Элемент управления **PhoneNumberBox** добавляется в **Обозреватель решений** и открывается в конструкторе.  
  
## <a name="design-the-phonenumberbox-control"></a>Порядок проектирования элемента управления PhoneNumberBox  
 В этом пошаговом руководстве расширяется существующий <xref:System.Windows.Forms.MaskedTextBox> для создания элемента управления `PhoneNumberBox`.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Порядок проектирования элемента управления PhoneNumberBox  
  
1. Перетащите <xref:System.Windows.Forms.MaskedTextBox> из **области элементов** на рабочую область конструирования пользовательского элемента управления.  
  
2. Выберите смарт-тег на только что перетащенном <xref:System.Windows.Forms.MaskedTextBox> и выберите **Установка маски**.  
  
3. Выберите **Номер телефона** в диалоговом окне **Маска ввода** и нажмите кнопку **ОК** для задания маски.  
  
## <a name="add-the-required-data-binding-attribute"></a>Добавьте необходимый атрибут привязки данных  
 Для простых элементов управления, поддерживающих привязку к данным, реализуйте <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Реализация атрибута DefaultBindingProperty  
  
1. Переключите элемент управления `PhoneNumberBox` в представление кода. (В меню **Вид** выберите **Код**.)  
  
2. Замените код в `PhoneNumberBox` следующим кодом:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3. В меню **Построение** выберите пункт **Построить решение**.  
  
## <a name="create-a-data-source-from-your-database"></a>Создать источник данных из базы данных  
 В этом шаге **Мастер настройки источника данных** используется для создания источника данных на основе таблицы `Customers` в учебной базе данных "Борей". Для создания подключения необходимо иметь доступ к учебной базе данных "Борей".
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1. В меню **Данные** выберите команду **Показать источники данных**.  
  
2. В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.  
  
3. На странице **Выбор типа источника данных** выберите **База данных** и нажмите кнопку **Далее**.  
  
4. На странице **Выбор подключения к базе данных** выполните одно из следующих действий:  
  
    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.  
  
5. Если базе данных требуется пароль, выберите параметр для включения конфиденциальных данных и нажмите кнопку **Далее**.  
  
6. На **сохранение подключения в файле конфигурации приложения** щелкните **Далее**.  
  
7. Разверните узел **Таблицы** на странице **Выбор объектов базы данных**.  
  
8. Выберите таблицу `Customers` и нажмите кнопку **Готово**.  
  
     Объект **NorthwindDataSet** добавляется в проект, и таблица `Customers` отображается в окне **Источники данных**.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Порядок настройки столбца телефона на использование элемента управления PhoneNumberBox  
 Вы можете задать создаваемый элемент управления в окне **Источники данных** перед перетаскиванием элементов на форму.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Порядок настройки столбца телефона на привязку к элементу управления PhoneNumberBox  
  
1. Откройте **Form1** в конструкторе.  
  
2. Разверните узел **Customers** в окне **Источники данных**.  
  
3. Щелкните стрелку раскрывающегося списка в узле **Customers** и выберите **Сведения** в списке элементов управления.  
  
4. Щелкните стрелку раскрывающегося списка в столбце **Phone** и выберите **Настроить**.  
  
5. Выберите **PhoneNumberBox** в списке **Связанные элементы управления** диалогового окна **Настройка данных интерфейса пользователя**.  
  
6. Щелкните стрелку раскрывающегося списка в столбце **Phone** и выберите **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols в форму  
 Вы можете создавать элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Создание элементов управления с привязкой к данным на форме  
  
- Перетащите главный **клиентов** узел из **источников данных** окна в форму и убедитесь, что `PhoneNumberBox` элемент управления используется для отображения данных в `Phone` столбца.  
  
     Привязанные к данным элементы управления с метками описания отображаются на форме вместе с панелью инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.  
  
## <a name="run-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
- Нажмите клавишу F5 для запуска приложения.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после создания элемента управления, поддерживающего привязку к данным. Некоторые типичные дальнейшие действия.  
  
- Помещение пользовательских элементов управления в библиотеку элементов управления, чтобы их можно было повторно использовать в других приложениях.  
  
- Создание элементов управления, поддерживающих более сложных сценариев привязки к данным. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает сложную привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) и [создать пользовательский элемент управления Windows Forms с привязкой данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Задание поведения, при котором элемент управления создается при перетаскивании из окна "Источники данных"](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
