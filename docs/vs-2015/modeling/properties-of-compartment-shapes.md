---
title: Свойства фигур секции | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9176fe7bc7f9824610b7a77f1e1ef3b374b69ef3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701717"
---
# <a name="properties-of-compartment-shapes"></a>Свойства фигур, состоящих из секций
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Фигуры секций являются одной из фигур, которые можно использовать для отображения класс домена в доменном языке. Можно развернуть и свернуть секции.  
  
 Дополнительные сведения см. в разделе [способ определения доменного языка](../modeling/how-to-define-a-domain-specific-language.md). Дополнительные сведения об использовании этих свойств см. в разделе [Настройка и расширение доменного языка](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Фигуры секций имеют свойства, которые перечислены в следующей таблице.  
  
|Свойство|Описание|Значение по умолчанию|  
|--------------|-----------------|-------------|  
|По умолчанию, разверните узел свернутого состояния|Если `Expanded`, секции отображаются при создании. Если `Collapsed`, они не являются.|Разреженный|  
|Цвет заливки|Цвет заливки этой фигуры.|Белый|  
|Режим градиентной заливки|Отображение режима заливки градиента данной фигуры.|Горизонтально|  
|Geometry|Геометрия этой фигуры (прямоугольник или прямоугольник со скругленными углами).|Прямоугольник|  
|Содержит точки подключения по умолчанию|Если `True`фигуры будет использовать верхней, нижней, левой и правой соединения указывает в созданном конструкторе.|False|  
|Отображается заголовок одной секции|Если `False`и фигура содержит одну секцию, заголовок секции не виден.|True|  
|Цвет контура|Цвет контура данной фигуры.|Черный|  
|Отображение стиля пунктира контура|Отображение стиля пунктира контура этой фигуры (сплошная, тире, точка, DashDot, DashDotDot и пользовательский).|Сплошная|  
|Толщина контура|Толщина контура данной фигуры.|0.03125|  
|Цвет текста|Цвет, используемый для декораторов текста, которые связаны с данной фигурой.|Черный|  
|Модификатор доступа|Уровень доступа фигуры секции (`public` или `internal`).|Public|  
|Настраиваемые атрибуты|Используется для добавления атрибутов в исходный класс код, созданный из данной фигуры секции|\<none>|  
|Создает двойной производным|Если `True`, будет создан базовый класс и разделяемый класс (для поддержки настройки посредством переопределений). Дополнительные сведения см. в разделе [переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Имеет пользовательский конструктор|Если `True`, пользовательский конструктор будет предоставляться в исходном коде. Дополнительные сведения см. в разделе [переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Модификатор наследования|Описывает тип наследования класса источника кода, который создается между фигурой секции (`none`, `abstract` или `sealed`).|Нет|  
|Базовая фигура секций|Базовый класс для этой фигуры.|(нет)|  
|name|Имя данной фигуры.|Текущее имя|  
|Пространство имен|Пространство имен, связанное с данной фигурой.|Текущее пространство имен|  
|Тип подсказки|Как подсказка определяется (фиксированное значение, переменная или none). Если так, то значение `Fixed Tooltip Text` свойство используется в качестве подсказки; Если переменная, то подсказки определен в пользовательском коде.|Нет|  
|Примечания|Неофициальные примечания, связанные с данной фигурой.|\<none>|  
|Начальная высота|Начальная высота данной фигуры в дюймах. Для фигуры секции это высоту области заголовка только и его размер нельзя изменить.|1|  
|Начальная ширина|Начальная ширина данной фигуры в дюймах.|1.5|  
|Цвет заливки предоставляемого как свойство<br /><br /> Режима градиентной заливки предоставляемого<br /><br /> Цвет контура в виде свойства<br /><br /> Отображение стиля пунктира контура в виде свойства<br /><br /> Предоставляемые Толщина контура как свойство<br /><br /> Предоставляет цвет текста|Если `True`, пользователь может задать свойство заявленным фигуры. Для этого щелкните правой кнопкой мыши определения фигуры и нажмите кнопку **добавить предоставленный**.|False|  
|Описание|Используется для документирования созданного конструктора.|\<none>|  
|Отображаемое имя|Имя, которое будет отображаться в созданном конструкторе для данной фигуры.|\<none>|  
|Фиксированный текст всплывающей подсказки|Текст, используемый для фиксированной подсказки.|\<none>|  
|Ключевое слово Help|Ключевое слово, используемое для индексации справки F1 для данной фигуры.|\<none>|  
  
## <a name="see-also"></a>См. также  
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
