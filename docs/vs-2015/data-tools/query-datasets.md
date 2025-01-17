---
title: Запрашивайте наборы данных | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2081b302bfb288b08119913081154b970fadcda
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692579"
---
# <a name="query-datasets"></a>Наборы данных запросов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для поиска определенных записей в наборе данных, используйте метод FindBy в объект DataTable, написание собственных цикл по коллекции строк таблицы или использовать [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.  
  
## <a name="dataset-case-sensitivity"></a>Чувствительность к регистру набора данных  
 В наборе данных, имена таблиц и столбцов не учитывается регистр, по умолчанию — то есть таблицу в набор данных с именем «Customers» можно также обращаться как к «customers». Это соответствует соглашения об именовании в нескольких базах данных, включая SQL сервера SQL Server, поведением по умолчанию является то, что имена элементов данных должны отличаться только регистром.  
  
> [!NOTE]
> В отличие от наборов данных XML-документов учитывается регистр, поэтому имена элементов данных, определенные в схемах чувствительны к регистру. Например протокол схемы позволяет определить таблицу с именем «Customers» и другой таблицей с именем «customers». Это может привести к конфликту имен, когда схемы, содержащей элементы, отличающиеся только регистром используется для создания класса набора данных.  
  
 Чувствительность к регистру, однако может быть фактор в способ интерпретации данных в наборе данных. Например при фильтрации данных в таблице набора данных, условия поиска может возвращать различные результаты в зависимости от того, является ли сравнение с учетом регистра. Учет регистра фильтрации, поиска и сортировки с помощью свойства набора данных можно управлять <xref:System.Data.DataSet.CaseSensitive%2A> свойство. Все таблицы в наборе данных наследуют значение этого свойства по умолчанию. (Это свойство для каждой отдельной таблицы можно переопределить, задав в таблице <xref:System.Data.DataTable.CaseSensitive%2A> свойство.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Поиск конкретной строки в таблице данных  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Чтобы найти строку в типизированный набор данных со значением первичного ключа  
  
- Чтобы найти строку, вызовите строго типизированный `FindBy` метод, который использует первичный ключ таблицы.  
  
     В следующем примере `CustomerID` столбец является первичным ключом `Customers` таблицы. Это означает, что созданный `FindBy` метод `FindByCustomerID`. Примере показано, как присвоить определенный <xref:System.Data.DataRow> переменной с помощью созданного `FindBy` метод.  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Чтобы найти строку в нетипизированный набор данных со значением первичного ключа  
  
- Вызовите <xref:System.Data.DataRowCollection.Find%2A> метод <xref:System.Data.DataRowCollection> коллекции, передавая первичный ключ в качестве параметра.  
  
     В следующем примере показано, как объявить новую строку с именем `foundRow` и ей присваивается значение, возвращаемое <xref:System.Data.DataRowCollection.Find%2A> метод. Если первичный ключ найден, содержимое индекса столбца 1 отображаются в окне сообщения.  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>FindRows по значениям столбца  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Чтобы найти строки, на основе значений в любом столбце  
  
- Данные таблицы создаются с помощью<xref:System.Data.DataTable.Select%2A> метод, возвращающий массив <xref:System.Data.DataRow>s, основанное на выражении, передаваемый <xref:System.Data.DataTable.Select%2A> метод. Дополнительные сведения о создании допустимых выражениях см. в разделе «Синтаксис выражений» страницы <xref:System.Data.DataColumn.Expression%2A> свойство.  
  
     В следующем примере показано, как использовать <xref:System.Data.DataTable.Select%2A> метод <xref:System.Data.DataTable> для поиска конкретных строк.  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="access-related-records"></a>Записей, связанных с доступом к  
 Если таблицы в наборе данных связаны, <xref:System.Data.DataRelation> объект можно сделать связанные записи, доступные в другой таблице. Например, набор данных, содержащий `Customers` и `Orders` таблицы могут быть сделаны доступными.  
  
 Можно использовать <xref:System.Data.DataRelation> объект для поиска связанных записей путем вызова <xref:System.Data.DataRow.GetChildRows%2A> метод <xref:System.Data.DataRow> в родительской таблице. Этот метод возвращает массив связанных дочерних записей. Или можно вызвать <xref:System.Data.DataRow.GetParentRow%2A> метод <xref:System.Data.DataRow> в дочерней таблице. Этот метод возвращает одиночный <xref:System.Data.DataRow> из родительской таблицы.  
  
 Эта страница содержит примеры использования типизированных наборов данных. Сведения о навигации по связям в нетипизированные наборы данных, см. в разделе [переходы отношений DataRelation](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).  
  
> [!NOTE]
> Если вы работаете в приложении Windows Forms и используя возможности привязки данных для отображения данных, автоматически созданный конструктором формы может обеспечить достаточную функциональность для вашего приложения. Дополнительные сведения см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 В следующих примерах кода показано, как для перемещения вверх и вниз по связи в типизированных наборах данных. Использование примеров кода типизированные <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) и созданные `FindBy` *PrimaryKey* (`FindByCustomerID`) методы для поиска нужной строки и возврата связанных записей. Примеры компилируются и работают только в том случае, если у вас есть:  
  
- Экземпляр набора данных с именем `NorthwindDataSet` с `Customers` таблицы.  
  
- `Orders` Таблицы.  
  
- Отношение с именем `FK_Orders_Customers`по две таблицы, доступные в области кода  
  
Кроме того обе таблицы должны заполняться данными для любой записи должны быть возвращены.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Чтобы вернуть дочерние записи, выбранной родительской записи  
  
- Вызовите <xref:System.Data.DataRow.GetChildRows%2A> метод конкретного `Customers` данных строки, а возвращает только те строки из `Orders` таблицы:  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Для возврата родительской записи выбранной дочерней записи  
  
- Вызовите <xref:System.Data.DataRow.GetParentRow%2A> метод конкретного `Orders` строку данных и возврат одной строки из `Customers` таблицы:  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
