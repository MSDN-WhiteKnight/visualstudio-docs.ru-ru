---
title: Специальные знаки MSBuild | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7af1f137624c0af1fce02fde524d7fb4178cbad
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65084060"
---
# <a name="msbuild-special-characters"></a>Специальные символы в MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] резервирует некоторые знаки для специального применения в определенных контекстах. Эти знаки следует экранировать, только если вы хотите использовать их именно в том контексте, для которого они зарезервированы. Например, звездочка имеет специальное значение только в атрибутах `Include` и `Exclude` определения элемента, а также в вызовах `CreateItem`. Если требуется, чтобы звездочка отображалась как звездочка в одном из этих контекстов, нужно экранировать ее. В любом другом контексте просто введите звездочку там, где она нужна.

 Чтобы экранировать специальный символ, используйте синтаксис %\<xx>, где \<xx> представляет шестнадцатеричное ASCII-значение знака. Дополнительные сведения см. в разделе [Практическое руководство. Пропуск специальных знаков в MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Специальные символы
 В следующей таблице перечислены специальные знаки [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:

|**Знак**|**ASCII**|**Зарезервированное использование**|
|-------------------|---------------|------------------------|
|%|%25|Ссылки на метаданные|
|$|%24|Ссылки на свойства|
|@|%40|Списки элементов|
|&#96;|%27|Условия и другие выражения|
|;|%3B|Разделитель элементов списка|
|?|%3F|Подстановочный знак для имен файлов в атрибутах `Include` и `Exclude`|
|*|%2A|Подстановочный знак для использования в именах файлов в атрибутах `Include` и `Exclude`|

## <a name="see-also"></a>См. также
- [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)
- [Элементы](../msbuild/msbuild-items.md)