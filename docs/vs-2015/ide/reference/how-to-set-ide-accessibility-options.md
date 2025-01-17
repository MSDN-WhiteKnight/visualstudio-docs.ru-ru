---
title: Практическое руководство. Настройка специальных возможностей в интегрированной среде разработки | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4ee29fd6309db34d4e0e4a013149e268051ab0e5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704399"
---
# <a name="how-to-set-ide-accessibility-options"></a>Практическое руководство. Настройка параметров доступа в интегрированной среде разработки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] содержит функции, которые упрощают работу для людей с нарушениями зрения, а также для пользователей с ограниченной подвижностью. Например, они позволяют изменять размер и цвет текста в редакторах, размер текста и кнопок на панелях инструментов и включать автозавершение для методов и параметров.  
  
 Кроме того, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживает раскладки клавиатуры по Двораку, делающие наиболее часто вводимые символы более доступным. Вы также можете настроить сочетания клавиш по умолчанию, доступные в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Определение и настройка сочетаний клавиш в Visual Studio](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="editors-dialogs-and-tool-windows"></a>Редакторы, диалоговые окна и окна инструментов  
 По умолчанию диалоговые окна и окна инструментов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] используют те же размеры и цвета шрифтов, что и операционная система. Цвета рамок интегрированной среды разработки, диалоговых окон, панелей инструментов и окон инструментов определяются цветовой схемой: светлой или темной. Текущую цветовую тему можно изменить на [странице "Общие" папки "Среда" диалогового окна "Параметры"](../../ide/reference/general-environment-options-dialog-box.md).  
  
 Кроме того, в представлении кода в редакторе можно настроить отображение всплывающих окон. Эти окна могут предлагать доступные члены для текущего объекта или параметры для завершения функции или оператора. Такие окна могут быть удобны для лиц, испытывающих затруднения при вводе с клавиатуры. Тем не менее, они перехватывают фокус в редакторе кода, что может быть неудобно некоторым пользователям. Эти окна можно отключить, открыв диалоговое окно "Параметры" и сняв флажки **Автоматически отображать список членов** и **Сведения о параметрах** в разделе **Текстовый редактор**, **Все языки**, **Общие** диалогового окна **Параметры**. Дополнительные сведения см. в разделе [Практическое руководство. Настройка общих параметров редактора](https://msdn.microsoft.com/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Вы можете изменить порядок окон в интегрированной среде разработки (IDE) так, как вам удобно. Любое окно инструментов можно закрепить, сделать плавающим, скрыть или скрывать автоматически.  
  
 Дополнительные сведения об изменении макетов окон см. в разделе [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### <a name="changing-the-size-of-text"></a>Изменение размера текста  
 Вы можете изменить параметры для текстовых окон инструментов, таких как **командное окно**, окно **Интерпретация** и **окно вывода**, в области **Шрифты и цвета** страницы **Среда** в диалоговом окне **Параметры**. Если в раскрывающемся списке **Показать параметры для** выбран пункт **[Все окна текстовых инструментов]**, значение по умолчанию указано как **По умолчанию** в раскрывающихся списках **Основной цвет элемента** и **Цвет фона элемента**. Вы также можете изменить параметры отображения текста в редакторе.  
  
##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Изменение размера текста в текстовых окнах инструментов и редакторов  
  
1. В меню **Сервис** выберите пункт **Параметры**.  
  
2. В папке **Среда** выберите **Шрифты и цвета**.  
  
3. Выберите нужный пункт в раскрывающемся списке **Показать параметры для**.  
  
     Чтобы изменить размер шрифта для текста в редакторе, выберите **Текстовый редактор**.  
  
     Чтобы изменить размер шрифта для текста в текстовых окнах инструментов, выберите **[Все окна текстовых инструментов]**.  
  
     Чтобы изменить размер шрифта для текста в подсказках, выберите **Всплывающая подсказка редактора**.  
  
     Чтобы изменить размер шрифта для текста во всплывающих окнах завершения операторов, выберите **Завершение операторов**.  
  
4. В списке **Отображаемые элементы** выберите **Обычный текст**.  
  
5. В поле **Шрифт** выберите новый тип шрифта.  
  
6. В поле **Размер** выберите новый размер шрифта.  
  
    > [!NOTE]
    > Чтобы сбросить размер шрифта для текстовых окон инструментов и редакторов, выберите **По умолчанию**.  
  
7. Нажмите кнопку **ОК**.  
  
### <a name="changing-the-colors-used-in-the-ide"></a>Изменение цветов, используемых в интегрированной среде разработки  
 Вы можете изменить цвета по умолчанию для текста, индикаторов полей, пустого пространства и элементов кода в редакторе.  
  
> [!NOTE]
> Чтобы задать высокую контрастность цветов для всех окон приложений в операционной системе, нажмите левую клавишу <strong>ALT +</strong> левую клавишу **SHIFT + PRINT SCREEN**. Если окно [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] открыто, закройте и снова откройте [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], чтобы режим высокой контрастности вступил в силу.  
  
##### <a name="to-change-the-color-of-items-in-the-editor"></a>Изменение цвета элементов в редакторе  
  
1. В меню **Сервис** выберите пункт **Параметры**.  
  
2. В папке **Среда** выберите **Шрифты и цвета**.  
  
3. В поле **Показать параметры для** выберите **Текстовый редактор**.  
  
4. В списке **Отображаемые элементы** выберите элемент, отображение которого необходимо изменить, например **Обычный текст**, **Поле индикаторов**, **Видимое пустое пространство**, **Имя атрибута HTML** или **XML-атрибут**.  
  
5. Выберите настройки отображения в следующих полях: **Основной цвет элемента**, **Фоновый цвет элемента** и **Полужирный**.  
  
6. Нажмите кнопку **ОК**.  
  
## <a name="toolbars"></a>Панели инструментов  
 Для повышения удобства панели инструментов можно добавить текст для кнопок панели.  
  
#### <a name="to-assign-text-to-toolbar-buttons"></a>Назначение текста кнопкам панели инструментов  
  
1. В меню **Сервис** выберите пункт **Настроить**.  
  
2. В диалоговом окне **Настройка** выберите вкладку **Команды**.  
  
3. Выберите **Панель инструментов**, а затем — имя панели инструментов, которая содержит нужные вам кнопки.  
  
4. В списке выберите команду, которую требуется изменить.  
  
5. Выберите **Изменить выделенный объект**.  
  
6. Выберите **Изображение и текст**.  
  
#### <a name="to-modify-the-buttons-displayed-text"></a>Изменение отображаемого текста кнопки  
  
1. Еще раз выберите **Изменить выделенный объект**.  
  
2. Во вставке рядом с полем **Имя** добавьте новый заголовок для выбранной кнопки.  
  
## <a name="see-also"></a>См. также раздел  
 [Специальные возможности Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Ресурсы для создания приложений со специальными возможностями](../../ide/reference/resources-for-designing-accessible-applications.md)
