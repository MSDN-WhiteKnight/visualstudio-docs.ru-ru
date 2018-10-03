---
title: Свойства элементов на UML схемы последовательностей | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b1f83999f3859583c4429ff3bf19482f01d90546
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557673"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Свойства элементов на схемах последовательностей UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [схемы последовательностей свойства элементов на UML](https://docs.microsoft.com/visualstudio/modeling/properties-of-elements-on-uml-sequence-diagrams).  
  
На схеме последовательностей UML каждый элемент имеет свойства. Чтобы просмотреть свойства элемента, щелкните правой кнопкой мыши элемент на схеме или в **Обозреватель моделей UML** и нажмите кнопку **свойства**. Свойства отображаются в **свойства** окна.  
  
> [!NOTE]
>  В этом разделе описываются свойства элементов на схемах последовательностей UML. Дополнительные сведения о чтении UML-схемы последовательностей, см. в разделе [схемы последовательностей UML: Справочник по](../modeling/uml-sequence-diagrams-reference.md). Дополнительные сведения о рисовании схем последовательностей UML см. в разделе [UML-схемы последовательностей: рекомендации по](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Свойства элементов  
  
|Свойство|По умолчанию|Элемент|Описание|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Имя по умолчанию|Все|Идентифицирует элемент.|  
|**Полное имя**|Пакет :: Имя|Все|Уникально идентифицирует элемент. Перед именем элемента указывается полное имя пакета, содержащего его.|  
|**Рабочие элементы**|0 связанных|Все|Число рабочих элементов, связанных с этим элементом. Чтобы связать рабочие элементы, см. в разделе [связывание элементов модели и рабочими элементами](../modeling/link-model-elements-and-work-items.md).|  
|**Описание**|(пусто)|Все|Здесь можно делать общие заметки об элементе.|  
|**Цвет**|(по умолчанию для типа элемента)|Линия жизни, сообщение|Цвет фигуры. Это свойство фигуры, а не отображаемый ею элемент.|  
|**Type**|(пусто)|Линия жизни|Тип экземпляра, который представляет жизненная линия.<br /><br /> Если в заголовке линии жизни отображается символ ссылки, этот класс или интерфейс существует в обозревателе моделей UML отдельно и может отображаться на схеме классов.|  
|**Субъекта**|False|Линия жизни|Указывает, представляет ли линия жизни пользователя, устройство или программный компонент, являющийся внешним по отношению к компоненту, изображенному на схеме.|  
|**Тип**|**Полный** -сообщение, имеющее и отправителя и получателя.<br /><br /> **Найти** -сообщение, которое имеет неопределенное отправителем.<br /><br /> **Потеряно** -сообщение, получатель которого не указан.|Сообщение|Указывает, какие окончания сообщения присоединены к линии жизни.<br /><br /> Это свойство нельзя изменить. Оно задается при создании сообщения.|  
|**Сортировка**|**AsynchCall** -асинхронное сообщение.<br /><br /> **SynchCall** -синхронное сообщение.<br /><br /> **Ответ** — возвращаемая часть синхронного сообщения.<br /><br /> **CreateMessage** -сообщение создания экземпляра.|Сообщение|Тип сообщения. Это свойство нельзя изменить. Оно определяется средством, используемым для создания сообщения.|  
|**Операция**|(пусто)|Сообщение|Метод, вызываемый сообщением в получающей линии жизни.<br /><br /> Является видимым, только если получающая линия жизни связана с интерфейсом или классом.|  
|**Ссылается на**|Схема последовательностей|Использование взаимодействия|Схема последовательностей, вызываемая этим использованием взаимодействия.|  
|**Оператор взаимодействия**|Задается при использовании **окружить** команды|Объединенный фрагмент|Оператор, представленный этим фрагментом или коллекцией фрагментов.|  
|**Guard**|(пусто)|Операнд взаимодействия в объединенном фрагменте|Последовательность во фрагменте встречается, только если условие имеет значение true.<br /><br /> Чтобы выбрать верхний фрагмент любого объединенного фрагмента, нужно щелкнуть под названием фрагмента.|  
|**Мин., макс.**|(без ограничений)|Зациклить объединенный фрагмент|Минимальное и максимальное число выполнений цикла.|  
|**Сообщения**|(пусто)|Включение и<br /><br /> игнорирование объединенных фрагментов|Сообщения, рассматриваемые или игнорируемые в этом фрагменте.|  
  
## <a name="see-also"></a>См. также  
 [Схемы последовательностей UML: Справочник по](../modeling/uml-sequence-diagrams-reference.md)   
 [UML-схемы последовательностей: рекомендации](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Описание потока управления с использованием фрагментов на схемах последовательностей UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)


