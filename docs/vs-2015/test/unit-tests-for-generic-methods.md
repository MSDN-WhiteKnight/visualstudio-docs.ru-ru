---
title: Модульные тесты для универсальных методов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.assetid: ffc89814-a7df-44fc-aef5-dd3dfeb28a9b
caps.latest.revision: 49
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6132da236498867865717ccc7d1f470e2b990a86
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695132"
---
# <a name="unit-tests-for-generic-methods"></a>Модульные тесты для универсальных методов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно создать модульные тесты для универсальных методов точно так, как и для других методов, как описано в разделе [как: Создание и выполнение модульного теста](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48). В следующих разделах содержатся сведения о создании модульных тестов для универсальных методов и примеры.  
  
## <a name="type-arguments-and-type-constraints"></a>Аргументы типа и ограничения типа  
 Когда [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] создает модульный тест для универсального класса, например `MyList<T>`, создается два метода: универсальный вспомогательный метод и метод теста. Если `MyList<T>` имеет одно или несколько ограничений типа, аргумент типа должен соответствовать всем этим ограничениям. Чтобы убедиться, что тестируемый универсальный код работает должным образом при всех допустимых входных данных, метод теста вызывает универсальный вспомогательный метод со всеми ограничениями, которые требуется проверить.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры иллюстрируют модульные тесты для универсальных методов.  
  
- [Редактирование созданного кода теста](#EditingGeneratedTestCode). Этот пример состоит из двух разделов: «Созданный код теста» и «Измененный код теста». В этом примере демонстрируется внесение изменений в исходный код теста, созданный из универсального метода, для создания полезного метода теста.  
  
- [Использование ограничения типа](#TypeConstraintNotSatisfied). В этом примере показан модульный тест для универсального метода, использующий ограничение типа. В этом примере ограничение типа не удовлетворяется.  
  
### <a name="EditingGeneratedTestCode"></a> Пример 1. Редактирование созданного кода теста  
 В этом разделе код теста проверяет метод тестируемого кода с именем `SizeOfLinkedList()`. Этот метод возвращает целое число, указывающее число узлов в связанном списке.  
  
 В первом примере кода в разделе «Созданный код теста» показан неизмененный код, созданный в Visual Studio Enterprise автоматически. Во втором примере, в разделе «Измененный код теста», показано, как настроить тест для проверки работы метода SizeOfLinkedList для двух типов данных, `int` и `char`.  
  
 Этот код иллюстрирует два метода:  
  
- вспомогательный метод теста, `SizeOfLinkedListTestHelper<T>()` (по умолчанию вспомогательный метод теста содержит строку TestHelper в имени);  
  
- метод теста, `SizeOfLinkedListTest()` (методы теста помечаются атрибутом TestMethod).  
  
#### <a name="generated-test-code"></a>Созданный код теста  
 Следующий код теста создан из метода `SizeOfLinkedList()`. Поскольку это автоматически созданный тест, для правильного тестирования метода SizeOfLinkedList в него необходимо внести изменения.  
  
```  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T); // TODO: Initialize to an appropriate value  
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value  
    int expected = 0; // TODO: Initialize to an appropriate value  
    int actual;  
    actual = target.SizeOfLinkedList();  
    Assert.AreEqual(expected, actual);  
    Assert.Inconclusive("Verify the correctness of this test method.");  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()  
{  
   SizeOfLinkedListTestHelper<GenericParameterHelper>();  
}  
```  
  
 В приведенном выше коде параметр универсального типа — `GenericParameterHelper`. Хотя его можно изменить, чтобы указать определенные типы данных, как показано в следующем примере, можно запустить тест без изменения этого оператора.  
  
#### <a name="edited-test-code"></a>Измененный код теста  
 В следующем примере кода метод теста и вспомогательный метод теста были изменены для успешного тестирования метода `SizeOfLinkedList()` тестируемого кода.  
  
##### <a name="test-helper-method"></a>Вспомогательный метод теста  
 Вспомогательный метод теста выполняет следующие шаги, которые соответствуют строкам кода, помеченным как шаги 1–5.  
  
1. Создание универсального связанного списка.  
  
2. Добавление четырех узлов в связанный список. Тип данных содержимого этих узлов неизвестен.  
  
3. Назначение ожидаемого размера связанного списка переменной `expected`.  
  
4. Вычисление фактического размера связанного списка и назначение его переменной `actual`.  
  
5. Сравнение `actual` и `expected` с помощью оператора Assert. Если фактический размер не равен ожидаемому, тест не пройден.  
  
##### <a name="test-method"></a>Метод теста  
 Метод теста компилируется в код, который вызывается при выполнении теста SizeOfLinkedListTest. Он выполняет следующие шаги, которые соответствуют строкам кода, помеченным как шаги 6 и 7.  
  
1. Указание `<int>` при вызове вспомогательного метода теста, чтобы убедиться, что тест работает для переменных `integer`.  
  
2. Указание `<char>` при вызове вспомогательного метода теста, чтобы убедиться, что тест работает для переменных `char`.  
  
```  
  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T);   
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1  
    for (int i = 0; i < 4; i++) // step 2  
    {  
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);  
        target.Append(newNode);  
    }  
    int expected = 5; // step 3  
    int actual;  
    actual = target.SizeOfLinkedList(); // step 4  
    Assert.AreEqual(expected, actual); // step 5  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()   
{  
    SizeOfLinkedListTestHelper<int>();  // step 6  
    SizeOfLinkedListTestHelper<char>(); // step 7  
}  
```  
  
> [!NOTE]
> При каждом выполнении теста SizeOfLinkedListTest его метод TestHelper вызывается два раза. Для прохождения теста оператор Assert каждый раз должен иметь значение true. В случае сбоя теста может быть непонятно, что вызвало сбой: вызов, указывающий `<int>`, или вызов, указывающий `<char>`. Чтобы найти ответ, можно проверить стек вызовов или задать точки останова в методе теста, а затем выполнить отладку во время выполнения теста. Дополнительные сведения см. в разделе [Практическое руководство. Отладка во время выполнения теста в решении ASP.NET](https://msdn.microsoft.com/library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).  
  
### <a name="TypeConstraintNotSatisfied"></a> Пример 2. Использование ограничения типа  
 В этом примере показан модульный тест для универсального метода, использующий ограничение типа, которое не удовлетворяется. В первом разделе показан код из проекта тестируемого кода. Ограничение типа выделено.  
  
 Во втором разделе показан код из тестового проекта.  
  
#### <a name="code-under-test-project"></a>Проект тестируемого кода  
  
```  
using System;  
using System.Linq;  
using System.Collections.Generic;  
using System.Text;  
  
namespace ClassLibrary2  
{  
    public class Employee  
    {  
        public Employee(string s, int i)  
        {  
        }  
    }  
  
    public class GenericList<T> where T : Employee  
    {  
        private class Node  
        {  
            private T data;  
            public T Data  
            {  
                get { return data; }  
                set { data = value; }  
            }  
        }  
    }  
}  
```  
  
#### <a name="test-project"></a>Тестовый проект  
 Как и для всех новых создаваемых модульных тестов, в этот модульный тест необходимо добавить операторы Assert с определенным результатом, чтобы тест возвращал полезные результаты. Их нужно добавить не в метод, помеченный атрибутом TestMethod, а в метод TestHelper, который в этом тесте имеет имя `DataTestHelper<T>()`.  
  
 В этом примере параметр универсального типа `T` имеет ограничение `where T : Employee`. Это ограничение не удовлетворяется в методе теста. Поэтому метод `DataTest()` содержит оператор Assert, предупреждающий вас о необходимости предоставить ограничение типа, которое было помещено в `T`. Сообщение этого оператора Assert выглядит следующим образом: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`  
  
 Другими словами, при вызове метода `DataTestHelper<T>()` из метода теста `DataTest()` необходимо передать параметр типа `Employee` или класс, производный от `Employee`.  
  
 `using ClassLibrary2;`  
  
 `using Microsoft.VisualStudio.TestTools.UnitTesting;`  
  
 `namespace TestProject1`  
  
```  
{  
    [TestClass()]  
    public class GenericList_NodeTest  
    {  
  
        public void DataTestHelper<T>()  
            where T : Employee  
        {  
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value  
            T expected = default(T); // TODO: Initialize to an appropriate value  
            T actual;  
            target.Data = expected;  
            actual = target.Data;  
            Assert.AreEqual(expected, actual);  
            Assert.Inconclusive("Verify the correctness of this test method.");  
        }  
  
        [TestMethod()]  
        public void DataTest()  
        {  
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +  
            "Please call DataTestHelper<T>() with appropriate type parameters.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Anatomy of a Unit Test](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)  (Составляющие модульного теста)  
 [Модульное тестирование кода](../test/unit-test-your-code.md)
