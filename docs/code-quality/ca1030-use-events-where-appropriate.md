---
title: CA1030. По возможности используйте события
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee7e96009d689fec48d242f4db1790e6e0eacafa
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842368"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030. По возможности используйте события

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Имя метода начинается с одного из следующих:

- Дополнительный компонент
- RemoveOn
- Fire
- Raise

По умолчанию это правило считывает только внешним видимым методам, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Данное правило отслеживает методы с именами, которые, как правило, используются для событий. События следуют шаблоне разработки наблюдателя или публикации-подписки; они используются при изменении состояния в один объект необходимо передать другим объектам. Если метод вызывается в ответ на четко определенное изменение состояния, метод должен вызываться с помощью обработчика событий. Объекты, вызывающие методы, должны создавать события, а не вызывать методы напрямую.

Некоторые распространенные события находятся в приложениях пользовательского интерфейса, когда действия пользователя, например на нажатие кнопки приводит к сегмент кода для выполнения. Модели событий .NET Framework не ограничивается пользовательские интерфейсы. он должен использоваться везде, где необходимо сообщить состояние изменяется на один или несколько объектов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Если метод вызывается при изменении состояния объекта, рекомендуется изменить способы использования модели событий .NET.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, если метод не работает с моделью событий .NET.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).