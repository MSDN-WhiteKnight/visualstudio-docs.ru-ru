---
title: Команды консоли JavaScript | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console commands [Windows Store apps]
- JavaScript debugging, console [Windows Store apps]
- debugging JavaScript, console [Windows Store apps]
ms.assetid: 359e2b24-6bb7-48e7-8b55-b570df0cb774
caps.latest.revision: 50
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0bc4597c5be26e25f79edc0784bb1fddd9baa76
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570585"
---
# <a name="javascript-console-commands"></a>JavaScript Console commands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команды консоли JavaScript](https://docs.microsoft.com/visualstudio/debugger/javascript-console-commands).  
  
Применяется к Windows и Windows Phone] (.. /Image/windows_and_phone_content.PNG «windows_and_phone_content»)  
  
 Для отправки сообщений и выполнения других задач в окне консоли JavaScript системы Visual Studio можно использовать команды. Примеры использования этого окна см. в разделе [краткое руководство: Отладка JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md). Информация в этом разделе относится к приложениям Магазина Windows, приложениям Магазина Windows Phone и приложениям, созданным с помощью инструментов Visual Studio для Apache Cordova. Сведения о поддерживаемых командах консоли в приложениях Cordova см. в разделе [отладка приложения](http://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1). Информацию об использование консоли в инструментах Internet Explorer, вызываемых кнопкой F12, см. в [этой статье](http://msdn.microsoft.com/library/ie/dn255006.aspx).  
  
 Если окно консоли JavaScript закрыто, его можно открыть при отладке в Visual Studio, выбрав **Отладка** > **Windows** > **Консоль JavaScript**.  
  
> [!NOTE]
>  Если во время сеанса отладки окно недоступно, убедитесь, что в свойствах отладки проекта тип отладчика установлен на **Скрипт** .  
  
## <a name="console-object-commands"></a>команды объекта console  
 В этой таблице показан синтаксис для команд объекта `console` , которые можно использовать в окне консоли JavaScript или для отправки сообщений в консоль из кода. Этот объект предоставляет несколько форм, позволяющих при необходимости разделять информационные сообщения и сообщения об ошибках.  
  
 Чтобы отличить эту консоль от именованной консоли локальных объектов, можно воспользоваться более длинной командой из `window.console.[command]` .  
  
> [!TIP]
>  Более ранние версии Visual Studio не поддерживают полный набор команд. Для быстрого получения информации о поддерживаемых командах используйте IntelliSense для объекта консоли.  
  
|Команда|Описание|Пример|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Отправляет сообщение, если `expression` имеет значение **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Удаляет сообщения из окна консоли (включая сообщения об ошибках в скрипте), а также скрипт, появляющийся в окне консоли. Не удаляет скрипт, введенный после появления на консоли запроса на ввод.|`console.clear();`|  
|`count(title)`|Отправляет количество вызовов команды count в окно консоли. Каждый вызов команды count однозначно определяется дополнительным параметром `title`.<br /><br /> Существующая запись в окне консоли определяется параметром `title` (при его наличии) и обновляется командой count. Новая запись не создается.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Отправляет `message` в окно консоли.<br /><br /> Эта команда идентична команде console.log.<br /><br /> Объекты, передаваемые с помощью данной команды, преобразуются в строковый параметр.|`console.debug("logging message");`|  
|`dir(object)`|Отправляет указанный объект в окно консоли и отображает его в визуализаторе объекта. Визуализатор можно использовать для изучения свойств в окне консоли.|`console.dir(obj);`|  
|`dirxml(object)`|Отправляет заданный параметром `object` объект узла XML в окно консоли и отображает его в виде дерева узла XML.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Отправляет `message` в окно консоли. Текст сообщения красный и ему предшествует символ ошибки.<br /><br /> Объекты, передаваемые с помощью данной команды, преобразуются в строковый параметр.|`console.error("error message");`|  
|`group(title)`|Запускает группирование сообщений, отправляемых в окно консоли, и посылает необязательный заголовок `title` в качестве метки группы. Группы могут быть вложенными и отображаются в окне консоли в представлении в виде дерева.<br /><br /> В некоторых сценариях команды group* могут упростить просмотр выходных данных в окне консоли, например при использовании модели компонентов.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Запускает группирование сообщений, отправляемых в окно консоли, и посылает необязательный заголовок `title` в качестве метки группы. Группы, отправляемые с помощью команды `groupCollapsed` , по умолчанию отображаются в свернутом представлении. Группы могут быть вложенными и отображаются в окне консоли в представлении в виде дерева.|Использование совпадает с использованием команды `group` .<br /><br /> См. пример для команды `group` .|  
|`groupEnd()`|Завершает текущую группу.<br /><br /> Требования:<br /><br /> Visual Studio 2013|См. пример для команды `group` .|  
|`info(message)`|Отправляет `message` в окно консоли. Перед сообщением стоит символ "Информация".|`console.info("info message");`<br /><br /> Дополнительные примеры см. в разделе [Formatting console.log output](#ConsoleLog) далее в этой статье.|  
|`log(message)`|Отправляет `message` в окно консоли.<br /><br /> При передаче объекта эта команда отправляет указанный объект в окно консоли и отображает его в визуализаторе объекта. Визуализатор можно использовать для изучения свойств в окне консоли.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Используется в веб-приложениях. Не поддерживается в приложениях Магазина, использующих JavaScript.|Не поддерживается.|  
|`profile(reportName)`|Используется в веб-приложениях. Не поддерживается в приложениях Магазина, использующих JavaScript.|Не поддерживается.|  
|`profileEnd()`|Используется в веб-приложениях. Не поддерживается в приложениях Магазина, использующих JavaScript.|Не поддерживается.|  
|`select(element)`|Выбирает заданный элемент HTML `element` в [проводника DOM](../debugger/quickstart-debug-html-and-css.md).|console.select(element);|  
|`time (name)`|Запускает таймер, определяемый дополнительным параметром `name` . При применении с командой `console.timeEnd`вычисляет время, прошедшее между моментами действия команд `time` и `timeEnd`, и отправляет результат (в мс) на консоль, используя строку `name` в качестве префикса. Используется для включения инструментирования кода приложения для измерения производительности.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Останавливает таймер, определяемый дополнительным параметром `name` . См. консольную команду `time` .|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Отправляет данные трассировки стека в окно консоли. Трассировка включает весь стек вызовов, в частности имя файла, номер строки и номер столбца.|`console.trace();`|  
|`warn(message)`|Отправляет `message` в окно консоли, предваряя его символом предупреждения.<br /><br /> Объекты, передаваемые с помощью данной команды, преобразуются в строковый параметр.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Разные команды  
 Эти команды также доступны в окне консоли JavaScript (но недоступны в коде).  
  
|Команда|Описание|Пример|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Возвращает указанный элемент в окно консоли. `$0` возвращает элемент, выбранный в настоящее время в проводнике DOM, `$1` возвращает элемент, ранее выбранный в проводнике DOM, и так далее до четвертого ранее выбранного элемента.|$3|  
|`$(id)`|Возвращает элемент по идентификатору. Это команда быстрого доступа к `document.getElementById(id)`, где `id` — это строка, представляющая идентификатор элемента.|`$("contenthost")`|  
|`$$(selector)`|Возвращает массив элементов, соответствующих указанному селектору, при помощи синтаксиса селектора CSS. Это команда быстрого доступа к `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Позволяет изменить контекст для оценки выражений с назначенного по умолчанию окна верхнего уровня страницы на окно заданного фрейма. Вызов `cd()` без параметров возвращает контекст в окно верхнего уровня.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Выбирает указанный элемент в [проводника DOM](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Возвращает визуализатор для заданного объекта. Визуализатор можно использовать для изучения свойств в окне консоли.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Проверка наличия консольной команды  
 Перед попыткой использования той или иной команды можно проверить, существует ли она. В приведенном ниже примере проверяется наличие команды `console.log` . Если команда `console.log` существует, код вызывает ее.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Просмотр объектов в окне консоли JavaScript  
 При использовании окна консоли JavaScript можно взаимодействовать с любым объектом, находящимся в области. Чтобы проверить в окне консоли объект вне области, используйте `console.log` , `console.dir`и прочие команды в коде. Кроме того, для взаимодействия в окне консоли с объектом, находящимся в области, можно установить в коде точку останова (**Точка останова** > **Insert Точка останова**).  
  
##  <a name="ConsoleLog"></a> Форматирование вывода команды console.log  
 При передаче множественных аргументов команде `console.log`, консолью обрабатывает их как массив и объединяет вывод.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` также поддерживает шаблоны подстановки "printf" для форматирования вывода. При использовании шаблонов подстановки в первом аргументе, дополнительные аргументы будут использоваться для замены указанных шаблонов в том порядке, в котором они используются.  
  
 Поддерживаются следующие шаблоны подстановки:  
  
-   %s — строка  
     %i — целое число  
     %d — целое число  
     %f — число с плавающей запятой  
     %o — объект  
     %b — двоичные данные  
     %x — шестнадцатеричные данные  
     %e — экспонента  
  
 Несколько примеров использования шаблонов подстановки в `console.log`:  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
user.age = 10.01;  
console.log("Hi, %s %s!", user.first, user.last);  
console.log("%s is %i years old!", user.first, user.age);  
console.log("%s is %f years old!", user.first, user.age);  
  
// Output:  
// Hi, Fred Smith!  
// Fred is 10 years old!  
// Fred is 10.01 years old!  
```  
  
## <a name="see-also"></a>См. также  
 [Краткое руководство: Отладка JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Краткое руководство по отладке HTML и CSS](../debugger/quickstart-debug-html-and-css.md)


