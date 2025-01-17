---
title: Перечисления Visual C++ в конструкторе классов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b38d36c1fdc0033115f1d7a4cf18265dc1f2a3ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696365"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Перечисления Visual C++ в конструкторе классов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Конструктор классов поддерживает типы C++ `enum` и ограниченные типы `enum class`. Ниже представлен пример.  
  
```  
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
```  
  
 Фигура перечисления C++ в схеме классов выглядит и работает подобно фигуре структуры, за исключением того, что она называется **Перечисление** или **Класс перечисления**, имеет розовый, а не синий цвет, и располагает цветной границей на левом и верхнем полях. Фигуры перечисления и структуры имеют прямые углы.  
  
 Дополнительные сведения об использовании типа `enum` см. в статье [Enumerations](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) (Перечисления).  
  
## <a name="see-also"></a>См. также раздел  
 [Working with Visual C++ Code (Class Designer)](../ide/working-with-visual-cpp-code-class-designer.md)  (Работа с кодом Visual C++ (конструктор классов))  
 [Перечисления](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)
