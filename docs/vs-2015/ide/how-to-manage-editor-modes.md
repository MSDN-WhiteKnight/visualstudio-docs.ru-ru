---
title: Практическое руководство. Управление режимами редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 71f3b5b2c910bbbd61607f9112122569e5d3562e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685608"
---
# <a name="how-to-manage-editor-modes"></a>Практическое руководство. Управление режимами редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предусмотрено несколько режимов отображения редактора кода Visual Studio.  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enabling-full-screen-mode"></a>Включение полноэкранного режима  
 Включив режим **Во весь экран**, вы можете скрыть все окна инструментов и просматривать только окна документов.  
  
#### <a name="to-enable-full-screen-mode"></a>Включение полноэкранного режима  
  
- Нажмите клавиши ALT + SHIFT + ВВОД, чтобы перейти в режим **Во весь экран** или выйти из него.  
  
     — или —  
  
- Введите команду `View.Fullscreen` в **командном окне**.  
  
## <a name="enabling-virtual-space-mode"></a>Включение режима виртуального пространства  
 В режиме **виртуального пространства** в конце каждой строки кода вставляются пробелы. Этот параметр позволяет помещать комментарии на одинаковом расстоянии от кода.  
  
#### <a name="to-enable-virtual-space-mode"></a>Включение режима виртуального пространства  
  
1. В меню **Сервис** выберите пункт **Параметры**.  
  
2. Разверните папку **Текстовый редактор** и выберите **Все языки**, чтобы задать этот параметр как глобальный. В противном случае выберите папку конкретного языка. (Например, чтобы включить нумерацию строк только в Visual Basic, выберите соответствующую папку в параметрах текстового редактора).  
  
3. Перейдите на вкладку **Общие** и в разделе **Параметры** выберите **Включить виртуальное пространство**.  
  
    > [!NOTE]
    > **Виртуальное пространство** включено в режиме **Выбор столбцов**. Когда режим **виртуального пространства** не включен, точка вставки курсора переходит с конца одной строки непосредственно на первый символ следующей строки.  
  
## <a name="see-also"></a>См. также  
 [Настройка редактора](../ide/customizing-the-editor.md)   
 [Практическое руководство. Размещение и закрепление Windows](../misc/how-to-arrange-and-dock-windows.md)   
 [Страница "Шрифты и цвета", папка "Среда", диалоговое окно "Параметры"](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
