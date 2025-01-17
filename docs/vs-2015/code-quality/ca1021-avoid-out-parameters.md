---
title: CA1021. Не используйте параметры out | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b52d5a97fc3c2e3a6bf5b4bb938bad9da50d3a7d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991832"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021. Не используйте параметры out
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет `out` параметра.

## <a name="rule-description"></a>Описание правила
 Передачи типов по ссылке (с помощью `out` или `ref`) требуется опыт работы с указателями, понимание отличия между типами значения и ссылочными типами и умение работать с методами с несколькими возвращаемыми значениями. Кроме того, разница между `out` и `ref` параметров не все понимают.

 Когда ссылочный тип передается «по ссылке», метод предполагает использование параметра для возвращения другого экземпляра объекта. Передача ссылочного типа по ссылке также известен как с помощью двойного указателя, указателя на указатель или двойное косвенное направление. С помощью о вызовах по умолчанию, который используется передача «по значению», параметр, принимающий ссылочный тип, уже получает указатель на объект. Указатель, а не объект, на который он указывает, передается по значению. Передача по значению означает, что метод не может изменить указатель, чтобы он указывал на новый экземпляр ссылочного типа. Тем не менее его можно изменить содержимое объекта, на который он указывает. Для большинства приложений этого достаточно и выдает требуемое поведение.

 Если метод должен возвращать другой экземпляр, используйте возвращаемое значение метода для выполнения этой задачи. См. в разделе <xref:System.String?displayProperty=fullName> класс для различных методов, которые обрабатывают строки и вернуть новый экземпляр строки. При использовании этой модели, вызывающей стороне необходимо решить, сохраняются ли исходный объект.

 Несмотря на то, что возвращаемые значения широко распространены и активно используются, правильное применение `out` и `ref` параметры требуются промежуточные проектирования и навыками программирования. Архитекторам библиотеки для широкого использования, не стоит ожидать, пользователи, разрабатывающим `out` или `ref` параметров.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, причиной является типом значения, имеют метод возвращал объект в качестве возвращаемого значения. Если метод должен возвращать несколько значений, измените его, чтобы возвращать одиночный экземпляр объекта, который содержит значения.

 Чтобы устранить нарушение этого правила, вызванное ссылочный тип, убедитесь, что требуемое поведение — вернуть новый экземпляр класса ссылки. Если это так, метод должен использовать ее возвращаемое значение для этого.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила. Однако такой подход может привести к проблем с удобством использования.

## <a name="example"></a>Пример
 Следующая библиотека показаны две реализации класса, который создает ответы на отзывы от пользователя. Первая реализация (`BadRefAndOut`) вынуждает пользователя библиотеки управлять тремя возвращаемыми значениями. Во второй реализации (`RedesignedRefAndOut`) упрощает взаимодействие с пользователем, возвращение экземпляра класса контейнера (`ReplyData`), управляющий данными как единое целое.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении демонстрируется рабочей среды пользователя. Вызов переработанной библиотеки (`UseTheSimplifiedClass` метод) более прост, и сведения, возвращаемые этим методом, легче управлять. Выходные данные из двух методов будут идентичны.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Пример
 В следующем примере библиотеки иллюстрирует как `ref` параметров для ссылочных типов используются и показан более эффективный способ реализации этой функции.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Пример
 Следующее приложение вызывает каждый метод в библиотеке с целью демонстрации поведения.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 В этом примере формируются следующие данные:

 **Указатель Changing - передаются по значению:** 
**12345**
**12345**
**Changing указатель - передается по ссылке:** 
**12345**
**12345 ABCDE**
**передача по возвращаемое значение:** 
**12345 ABCDE**
## <a name="try-pattern-methods"></a>Попробуйте методы шаблона

### <a name="description"></a>Описание
 Методы, которые реализуют **попробуйте\<что-то >** шаблонов, такого как <xref:System.Int32.TryParse%2A?displayProperty=fullName>, не вызывают это нарушение. Следующий пример показывает структуру (тип значения), который реализует <xref:System.Int32.TryParse%2A?displayProperty=fullName> метод.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1045: Не передавайте типы по ссылке](../code-quality/ca1045-do-not-pass-types-by-reference.md)
