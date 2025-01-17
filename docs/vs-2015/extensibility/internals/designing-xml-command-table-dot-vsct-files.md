---
title: Проектирование таблицы команд XML (. Файлы Vsct) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 987536af051de4a66b3eccadb105fd98455ddf06
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085915"
---
# <a name="designing-xml-command-table-vsct-files"></a>Проектирование таблицы команд XML (. Файлы Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Команда table (.vsct) XML-файл описывает макет и внешний вид элементов команду для VSPackage. Команда элементы включают кнопки, поля со списком, меню, панелей инструментов и группы элементов команды. В этом разделе описывается файлов таблицы команд XML, как они влияют на элементы команды и меню и способах их создания.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Команды, меню, группы и vsct-файл  
 vsct-файлы являются построена на основе команд, меню и группы команд. XML-теги в vsct-файле представляют каждый из этих элементов, а также другие связанные элементы, такие как кнопки, размещения команд и точечные рисунки.  
  
 При создании нового пакета VSPackage, выполнив [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пакет шаблона, шаблон создает vsct-файл с необходимые элементы для команды меню, окна инструментов или пользовательского редактора, в зависимости от сделанного выбора. Затем этот vsct-файл можно изменить в соответствии с требованиями конкретного пакета VSPackage. Как изменить vsct-файл, см. Примеры в [расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
 Чтобы создать новый, пустой vsct-файл, см. в разделе [как: Создать. Файл Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). После создания, добавить элементы XML, атрибуты и значения в файл для описания макета элемента команды. Подробную схему XML, см. в разделе [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Различия между файлами .ctc и .vsct  
 Хотя назначение тегов XML в vsct-файл такие же, как в настоящем рекомендуется использовать формат файла .ctc, их реализации немного отличается.  
  
- Новый  **\<extern >** тег — где ссылаются другие h-файлы для компиляции, например, для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] панели инструментов.  
  
- Хотя поддержка файлов .vsct **/ include** инструкции, как файлы .ctc, он также предоставляет новую \< **импорта >** элемент. Разница в том, **/ include** привносит **все** сведениями, но \< **импорта >** привносит только имена.  
  
- Хотя файлы .ctc требует файл заголовка, в которой вы определяете в директивах препроцессора, одно не является обязательным для vsct-файлы. Вместо этого поместите вашей директивы в таблице символов, расположенных в  **\<символ >** элементов, расположенных в нижней части файла .vsct.  
  
- функция файлы .vsct  **\<заметки >** тег, который позволяет внедрить все сведения, которые, например заметки или даже изображения.  
  
- Значения хранятся как атрибуты элемента.  
  
- Флаги команд можно сохранять отдельно или с накоплением.  IntelliSense, однако не поддерживает флаги команды с накоплением. Дополнительные сведения о флаги команды, см. в разделе [элемент Commandflag](../../extensibility/command-flag-element.md).  
  
- Можно указать несколько типов, например раскрывающиеся списки разбиения, комбинировать и т. д.  
  
- Идентификаторы GUID невозможности их проверить.  
  
- Каждый элемент пользовательского интерфейса имеет строка, представляющая текст, отображаемый с ним.  
  
- Родительским является необязательным. Если этот параметр опущен, используется значение «Неизвестно для группы».  
  
- Значок аргумент является необязательным.  
  
- В разделе точечного рисунка — так же, как .ctc файла, за исключением того, что теперь можно указать имя файла с помощью href, который будет извлечено компилятор vsct.exe во время компиляции.  
  
- Идентификатор ресурса — старый идентификатор ресурса точечного рисунка можно использовать и по-прежнему работает так же, как и в файлы .ctc.  
  
- HRef--новый метод, который позволяет указать имя файла для ресурса точечного рисунка. Предполагается, что все используются, поэтому используемый раздел можно пропустить. Компилятор сначала выполняет поиск по локальные ресурсы для файла, затем на любых net общих ресурсов и все ресурсы, определенные в параметре/i.  
  
- Сочетание клавиш — Вы больше не нужно указать эмулятор. Если вы укажете, компилятор предполагает, что редактор и эмулятором совпадают.  
  
- Keychord--была удалена. Новый формат: Key1, Mod1, Key2, Mod2.  Можно указать символ, шестнадцатеричное или VK константа.  
  
  Новый компилятор, vsct.exe, компилирует файлы .ctc и .vsct. Старый ctc.exe компилятор, тем не менее, будет распознавать ни компиляции vsct-файлы.  
  
  Компилятор vsct.exe можно использовать для преобразования существующего файла cto в vsct-файл. Дополнительные сведения об этом см. в разделе [как: Создать. Vsct-файл из существующего. Руководитель технологического отдела компании файл](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Элементы файла .vsct  
 Таблицы команд имеет следующие иерархии и элементов:  
  
 [Элемент CommandTable](../../extensibility/commandtable-element.md) — представляет все команды, группы меню и меню, связанных с пакетом VSPackage.  
  
 [Элемент extern](../../extensibility/extern-element.md) — ссылается на любой внешний h-файлы, которые необходимо объединить с vsct-файле.  
  
 [Включите элемент](../../extensibility/include-element.md) — ссылается на все файлы дополнительных заголовков (h), чтобы скомпилировать вместе с файлом your.vsct. Vsct-файл может включать h-файлы, содержащие константы, которые определяют команды, группы меню и меню, которые предоставляет интегрированную среду разработки или другом пакете VSPackage.  
  
 [Команды элемент](../../extensibility/commands-element.md) — представляет все отдельные команды, которые могут быть выполнены. Каждая команда имеет следующие четыре дочерних элемента:  
  
 [Элемент Menus](../../extensibility/menus-element.md) — представляет все меню и панелей инструментов в VSPackage. Меню являются контейнерами для группы команд.  
  
 [Группирует элемент](../../extensibility/groups-element.md) — представляет все группы в VSPackage. Группы представляют собой коллекции команд по отдельности.  
  
 [Кнопки элемент](../../extensibility/buttons-element.md) , представляющий все кнопки и пункты меню в VSPackage. Кнопки — визуальные элементы управления, которые могут быть связаны с командами.  
  
 [Элемент bitmaps](../../extensibility/bitmaps-element.md) — представляет все точечных рисунков для всех кнопок в VSPackage. Точечные рисунки имеют рисунков, отображаемых рядом с полем или командных кнопок, в зависимости от контекста.  
  
 [Элемент CommandPlacements](../../extensibility/commandplacements-element.md) — указывает, что дополнительных расположениях, где должен размещаться отдельные команды в меню вашего VSPackage.  
  
 [Элемент VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) , указывает ли команда отображает все время или только в определенных контекстах, например при отображении определенного диалоговое окно или окно. Меню и команд, которые имеют значение для этого элемента будет отображаться только в том случае, если активен заданный контекст. Поведение по умолчанию является отображение команды все время.  
  
 [Элемент KeyBindings](../../extensibility/keybindings-element.md) — указывает все сочетания клавиш для команд. То есть один или несколько комбинаций параметров, которые должны быть нажаты для выполнения команды, такие как **CTRL + S**.  
  
 [Элемент UsedCommands](../../extensibility/usedcommands-element.md) — Informs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среды, что несмотря на то, что указанная команда реализуется другим кодом, при активном текущий пакет VSPackage, она предоставляет реализацию команды.  
  
 `Symbols Element` — Содержит имена и идентификаторы GUID для всех команд в пакете.  
  
## <a name="vsct-file-design-guidelines"></a>. Рекомендации по проектированию Vsct-файл  
 Чтобы успешно спроектировать vsct-файл, соблюдайте следующие правила.  
  
- Команды могут размещаться только в группах, группы могут находиться только в меню и меню может размещаться только в группы. Только меню отображаются в интегрированной среде разработки, групп и команд не.  
  
- Подменю не могут быть непосредственно назначены меню, но должны быть назначены группе, которая в свою очередь назначается меню.  
  
- Команды, подменю и группам могут назначаться одной родительской группы или меню с помощью родительское поле их определение директивы.  
  
- Упорядочение таблицы команд исключительно через родительского поля в директивы имеет существенное ограничение. Директивы, которые определяют объекты могут принимать только один родительский элемент аргумент.  
  
- Повторное использование команды, группы или подменю требует использования новой директивы для создания нового экземпляра объекта с собственным `GUID:ID` пары.  
  
- Каждый `GUID:ID` пары должно быть уникальным. Повторное использование команду, которая например, добавленную в меню, панели инструментов, или в контекстном меню, обрабатывается <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.  
  
- Команды и подменю можно также назначить в несколько групп и групп можно назначить несколько меню, используя [элемент Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Заметки о Vsct-файл  
 Если внести изменения в vsct-файл, после и скомпилировать его и поместите его в собственном вспомогательной библиотеке DLL, необходимо запустить **/nosetupvstemplates/Setup для devenv.exe**. Это заставляет VSPackage ресурсам, указанным в экспериментальном реестр, чтобы быть привязанном и внутреннюю базу данных, которая описывает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] создаются заново.  
  
 Во время разработки можно для нескольких проектов VSPackage, будет создан и зарегистрирован в экспериментальном кусте реестра, может привести к путанице помехи в интегрированной среде разработки. Чтобы устранить эту проблему, можно сбросить экспериментальный куст значения по умолчанию для удаления всех зарегистрированных пакетов VSPackage и любые изменения, они могли быть внесены в интегрированной среде разработки. Чтобы сбросить экспериментальный куст, используйте средство CreateExpInstance.exe, входящий в состав Visual Studio SDK. Его можно найти в  
  
 **%PROGRAMFILES(x86)%\Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Запустите инструмент с помощью командной строки **/Reset CreateExpInstance**. Помните, что данное средство удаляет с экспериментальном кусте все зарегистрированные объекты VSPackage обычно не устанавливается вместе с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Расширение меню и команд](../../extensibility/extending-menus-and-commands.md)
