---
title: Сохранение данных в базе данных (несколько таблиц) | Документация Майкрософт
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 132aa0f37cc63e6afe2eff61a6d0f6dec5b200b5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692452"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Сохранение данных в базе данных (несколько таблиц)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Одним из наиболее распространенных сценариев в разработке приложений является отображение данных на форме в приложении Windows, изменение этих данных и отправка обновленных данных обратно в базу данных. Это пошаговое руководство описывает создание формы, отображающей данные из двух связанных таблиц, правку записей и сохранение изменений в базе данных. В данном примере используются таблицы `Customers` и `Orders` из учебной базы данных "Борей".  
  
 Вы можете сохранить данные из приложения в базе данных, вызвав метод `Update` адаптера таблицы. При перетаскивании таблиц из **источников данных** окна в форму, код, необходимый для сохранения данных автоматически добавляется. Дополнительные таблицы, которые добавляются в форму требуется Ручное добавление этого кода. Это пошаговое руководство описывает добавление кода для сохранения обновлений из нескольких таблиц.  
  
> [!NOTE]
> Диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от ваших текущих параметров или выпуск, который вы используете. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 В данном пошаговом руководстве представлены следующие задачи.  
  
- Создание нового **приложения Windows** проекта.  
  
- Создание и настройка источника данных в приложении с помощью [мастер настройки источника данных](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Настройка элементов управления из элементов в [окна "Источники данных"](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Дополнительные сведения см. в разделе [задать для элемента управления создается при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
- Создание элементов управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.  
  
- Изменение нескольких записей в каждой таблице в наборе данных.  
  
- Изменение кода для отправки обновленных данных в наборе данных обратно в базу данных.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
- Доступ к примеру базы данных "Борей".
  
## <a name="create-the-windows-application"></a>Создание приложения Windows  
 Первым шагом является создание **приложения Windows**. Присвоение проекту имени является необязательным при выполнении этого шага, но мы будем присвойте ему имя, так как мы планируем впоследствии его сохранить.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Чтобы создать новый проект приложения Windows  
  
1. На **файл** меню, создайте новый проект.  
  
2. Задайте для проекта имя `UpdateMultipleTablesWalkthrough`.  
  
3. Выберите **приложения Windows**, а затем выберите **ОК**. Дополнительные сведения см. в разделе [клиентских приложений](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Создается проект **UpdateMultipleTablesWalkthroug**, который добавляется в **Обозреватель решений**.  
  
## <a name="create-the-data-source"></a>Создание источника данных  
 На этом шаге **Мастер настройки источника данных** используется для создания источника данных из базы данных Northwind. Для создания подключения необходимо иметь доступ к учебной базе данных "Борей".
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1. На **данных** меню, выберите**Показать источники данных**.  
  
2. В **источников данных** выберите**добавить новый источник данных** запустить **мастер настройки источника данных**.  
  
3. На **Выбор типа источника данных**выберите **базы данных**, а затем выберите **Далее**.  
  
4. На **Выбор подключения базы данных**экрана выполните одно из следующих:  
  
    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         -или-  
  
    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.  
  
5. Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных, а затем выберите **Далее**.  
  
6. На **сохранение подключения в файле конфигурации приложения**выберите **Далее**.  
  
7. На **Выбор объектов базы данных**экрана, разверните узел **таблиц** узла.  
  
8. Выберите **клиентов** и **заказы** таблиц, а затем выберите **Готово**.  
  
     Объект **NorthwindDataSet** добавляется в проект, и таблицы отображаются в окне **Источники данных**.  
  
## <a name="set-the-controls-to-be-created"></a>Настройка элементов управления должен быть создан  
 В этом пошаговом руководстве данные в `Customers` таблица находится в **сведения** макета, где данные отображаются в отдельных элементах управления. Данные из `Orders` таблица находится в **сетки** макет, который отображается в <xref:System.Windows.Forms.DataGridView> элемента управления.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Установка типа удаления для элементов в окне "Источники данных"  
  
1. В **источников данных** окне разверните **клиентов** узла.  
  
2. На **клиентов** выберите **сведения** в списке элементов управления, чтобы изменить контроль **клиентов** таблицы на отдельные элементы управления. Дополнительные сведения см. в разделе [задать для элемента управления создается при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Создание формы с привязкой к данным  
 Вы можете создавать элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Создание элементов управления с привязкой к данным на форме  
  
1. Перетащите главный узел **Customers** из окна **Источники данных** на форму **Form1**.  
  
     Привязанные к данным элементы управления с метками описания отображаются на форме вместе с панелью инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.  
  
2. Перетащите связанный узел **Заказы** из окна **Источники данных** на **Form1**.  
  
    > [!NOTE]
    > Связанный узел **Заказы** расположен под столбцом **Факс** и является дочерним для узла **Клиенты**.  
  
     На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. OrdersTableAdapter и <xref:System.Windows.Forms.BindingSource> отображаются в области компонентов.  
  
## <a name="addcode-to-update-the-database"></a>Addcode обновление базы данных  
 Вы можете обновить базу данных, вызвав методы `Update` адаптеров таблицы **Клиенты** и **Заказы**. По умолчанию, обработчик событий для **Сохранить** кнопки<xref:System.Windows.Forms.BindingNavigator> добавляется в код формы для отправки обновлений в базу данных. Эта процедура изменяет код для отправки обновлений в правильном порядке. Это исключает вероятность возникновения ошибок целостности данных. Этот код также реализует обработку ошибок, упаковывая вызов обновления в блок try-catch. Вы можете изменить этот код в соответствии с потребностями своего приложения.  
  
> [!NOTE]
> Для ясности в этом пошаговом руководстве используется транзакция. Тем не менее если вы обновляете двух или нескольких связанных таблицах, включать всю логику обновления в рамках транзакции. Транзакция — это процесс, который гарантирует, что все связанные изменения в базу данных выполнены успешно, прежде чем изменения будут зафиксированы. Дополнительные сведения см. в разделе [транзакции и параллельность](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Добавление логики обновления в приложение  
  
1. Выберите **Сохранить** кнопку <xref:System.Windows.Forms.BindingNavigator>. Откроется редактор кода для `bindingNavigatorSaveItem_Click` обработчик событий.  
  
2. Замените код в обработчике событий на вызов методов `Update` связанных адаптеров таблицы. Следующий код сначала создает три временные таблицы данных для хранения обновленной информации для каждого <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> и <xref:System.Data.DataRowState>). Затем обновления выполняются в правильном порядке. Код должен выглядеть следующим образом:  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>Тестирование приложения  
  
#### <a name="to-test-the-application"></a>Тестирование приложения  
  
1. Выберите **F5**.  
  
2. Внесите изменения в данные одной или нескольких записей в каждой таблице.  
  
3. Нажмите кнопку **Сохранить**.  
  
4. Проверьте значения в базе данных и убедитесь, что изменения были сохранены.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые может потребоваться выполнить после создания формы с привязкой к данным в приложении Windows. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.  
  
- Добавление функциональности поиска в форму. Дополнительные сведения см. в разделе [Практическое руководство. Добавление параметризованного запроса в Windows Forms приложения](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
- Изменение источника данных для добавления или удаления объектов базы данных. Дополнительные сведения см. в разделе [Практическое руководство. Изменить набор данных](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
