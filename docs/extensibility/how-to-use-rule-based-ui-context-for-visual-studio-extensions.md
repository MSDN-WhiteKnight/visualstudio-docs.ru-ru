---
title: Практическое руководство. Использовать контекст пользовательского интерфейса на основе правил для расширений Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: d9136268bf1bfb7ccebf79de035fb19f40223002
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324702"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Практическое руководство. Использовать контекст пользовательского интерфейса на основе правил для расширений Visual Studio

Visual Studio позволяет загружать пакеты VSPackage, при некоторых известных <xref:Microsoft.VisualStudio.Shell.UIContext>активируются s. Тем не менее эти контексты пользовательского интерфейса не нормально детального, оставляет разработчикам расширений нет другого выбора, но Выбор доступного контекста пользовательского интерфейса, который активирует перед запятой им это действительно требуется VSPackage для загрузки. Список известных контекстов пользовательского интерфейса, см. в разделе <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Загрузка пакетов может повлиять на производительность и загружая их быстрее, чем требуется не рекомендуется. Visual Studio 2015 представляет концепцию основанном на правилах контекстов пользовательского интерфейса, механизм, позволяющий разработчикам расширений определить точные условия, при которых активируется контекст пользовательского интерфейса и загружаются связанные пакеты VSPackage.

## <a name="rule-based-ui-context"></a>Контекст пользовательского интерфейса на основе правил

«Правило» состоит из нового контекста пользовательского интерфейса (GUID) и логическое выражение, которое ссылается на один или несколько «условия» в сочетании с логического «и», «или», «not» операции. «Условия» вычисляются динамически во время выполнения и выражение оценивается каждый раз, когда любой из его изменения условия. Когда выражение принимает значение true, активируется связанный контекст пользовательского интерфейса. В противном случае контекст пользовательского интерфейса является активным.

Контекст пользовательского интерфейса на основе правил можно использовать различными способами:

1. Задать ограничения видимости для команд и окон инструментов. Можно скрыть команды и средства windows, пока не будет выполнено правило контекст пользовательского интерфейса.

2. Как автоматически ограничений нагрузки: нагрузки автоматически пакеты только в том случае, когда правило соблюдается.

3. Как задачу отложенной: задержка загрузки, пока не истечет указанный интервал и по-прежнему соблюдается правило.

   Механизм может использоваться любое расширение Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Создать контекст пользовательского интерфейса на основе правил
 Предположим, что у вас есть расширение TestPackage, который включает команду меню, применяется только к файлам с *.config* расширения. До выхода Visual Studio 2015, лучшим вариантом было загрузить TestPackage при <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> контекст пользовательского интерфейса был активирован. Загрузка TestPackage таким образом не эффективен, так как загруженное решение не может даже содержать *.config* файл. Ниже показано, как на основе правил контекст пользовательского интерфейса можно использовать для активации контекст пользовательского интерфейса, только если файл с *.config* расширение выбран и загрузить TestPackage при активации этого контекста пользовательского интерфейса.

1. Определить новый идентификатор GUID UIContext и добавьте к классу VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> и <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Например, предположим, новый UIContext «UIContextGuid» будет добавляться. Идентификатор GUID, созданный (Создать GUID можно, щелкнув **средства** > **создать GUID**) — «8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B». Затем добавьте следующее объявление в класс пакета:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Для атрибутов добавьте следующие значения: (Сведения об этих атрибутов будет показано ниже)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Эти метаданные определяют новый идентификатор GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) и выражение, ссылающееся на один термин, «DotConfig». Термин «DotConfig» возвращает значение true, каждый раз, когда текущее выделение в активной иерархии имеет имя, которое соответствует шаблону регулярного выражения "\\.config$» (заканчивается *.config*). Значение (по умолчанию) определяет необязательное имя для правила полезны для отладки.

    Pkgdef, созданные во время сборки, затем добавляются значения атрибута.

2. В файл VSCT для команды TestPackage добавьте флаг «DynamicVisibility» соответствующие команды:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. В области видимости VSCT привязать соответствующие команды для нового UIContext GUID, определенный в #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. В разделе "символы" добавьте определение параметра UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Теперь команды контекстного меню  *\*.config* файлы будут видны только элемент, выбранный в обозревателе решений при *.config* пакет будет не удается загрузить файл пока один из них выбран команды.

   Затем используйте отладчик, чтобы подтвердить, что пакет загружается, только когда это должно происходить его. Чтобы выполнить отладку TestPackage:

5. Установите точку останова в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.

6. Построение TestPackage и начните отладку.

7. Создайте проект или откройте его.

8. Выберите любой файл с расширением, отличное от *.config*. Не должна быть достигнута точка останова.

9. Выберите *App.Config* файл.

   TestPackage загружает и останавливается в точке останова.

## <a name="add-more-rules-for-ui-context"></a>Добавить дополнительные правила для контекста пользовательского интерфейса
 Так как правила контекст пользовательского интерфейса — это логические выражения, можно добавить больше ограничений, правил для контекста пользовательского интерфейса. Например в выше контекст пользовательского интерфейса, можно указать, что правило применяется, только если загружено решение с проектом. Таким образом, команды, не отображаются открыв *.config* файл как отдельный файл, а не как часть проекта.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Теперь выражение ссылается на три условия. Первые два термины, «SingleProject» и «MultipleProjects», относятся другие стандартные контексты пользовательского интерфейса (по идентификаторам GUID). Третий термин «DotConfig» является контекст пользовательского интерфейса на основе правил, определенных ранее в этой статье.

## <a name="delayed-activation"></a>Задержки активации
 Правила могут иметь необязательно «задержка». Задержка измеряется в миллисекундах. Если он имеется, задержка приводит к активации или деактивации контекста пользовательского интерфейса правило быть пришло в течение этого интервала времени. Если правило изменения обратно до истечения интервала задержки, ничего не происходит. Этот механизм можно использовать «управлять временем» инициализация - особенно однократную инициализацию, не полагаясь на таймеры или регистрация для получения уведомлений простоя.

 Например можно указать правила нагрузочного теста иметь с некоторой задержкой 100 миллисекунд:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Типы термин

Ниже приведены различные виды терминов, которые поддерживаются.

|Термин|Описание|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Идентификатор GUID ссылается на контекст пользовательского интерфейса. Термин будет иметь значение true, каждый раз, когда контекст пользовательского интерфейса active и false в противном случае.|
|HierSingleSelectionName:\<шаблон >|Термин будет иметь значение true, каждый раз, когда выделение в активной иерархии является один элемент и имя выбранного элемента соответствует регулярное выражение .net в «pattern».|
|UserSettingsStoreQuery:\<query>|«запрос» представляет собой полный путь в хранилище параметров пользователя, которой должен быть равен ненулевое значение. Запрос состоит из «коллекция» и «propertyName» на последний символ косой черты.|
|ConfigSettingsStoreQuery:\<query>|«запрос» представляет собой полный путь в хранилище параметров конфигурации, в которой должен быть равен ненулевое значение. Запрос состоит из «коллекция» и «propertyName» на последний символ косой черты.|
|ActiveProjectFlavor:\<projectTypeGuid>|Термин будет иметь значение true, каждый раз, когда flavored текущий выбранный проект (Сводное) и имеет flavor, идентификатор GUID типа проекта для данного сопоставления.|
|ActiveEditorContentType:\<contentType >|Термин будет иметь значение true, если выбранный документ — это текстовый редактор с заданным типом содержимого.|
|ActiveProjectCapability:\<выражение >|Термин имеет значение true, если указанного выражения совпадает с возможности активного проекта. Выражение может быть нечто вроде VB &#124; CSharp.|
|SolutionHasProjectCapability:\<выражение >|Аналогично выше, но условие равно true, если решение содержит любой загруженный проект, который соответствует выражению.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Термин будет иметь значение true, каждый раз, когда решение содержит проект, который является flavored (Сводное) и у flavor, идентификатор GUID типа проекта для данного сопоставления.|

## <a name="compatibility-with-cross-version-extension"></a>Совместимость с разными версиями расширения

Контексты пользовательского интерфейса на основе правил — это новая функция в Visual Studio 2015 и не может быть перенесена в более ранних версий. Не перенос кода в более ранних версий создает проблему с помощью расширения или пакетов, предназначенных для нескольких версий Visual Studio. Эти версии пришлось бы быть автоматически загружаются в Visual Studio 2013 и более ранних версий, но может принести из контекстов пользовательского интерфейса на основе правил для предотвращения автоматически загружаются в Visual Studio 2015.

Чтобы обеспечить поддержку таких пакетов, AutoLoadPackages записи в реестре, теперь могут предоставлять флага в его поле значения, чтобы указать, что элемент должен быть пропущен в Visual Studio 2015 и более поздних версий. Это можно сделать, добавив возможность флаги <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Теперь можно добавить пакеты VSPackage **SkipWhenUIContextRulesActive** возможность их <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> для указания того, записи должны игнорироваться в Visual Studio 2015 и более поздних версий.
## <a name="extensible-ui-context-rules"></a>Расширяемая правила контекст пользовательского интерфейса

В некоторых случаях пакеты нельзя использовать статические правила контекст пользовательского интерфейса. Например предположим, что у вас есть пакет, поддерживающих расширяемость, таким образом, что состояние команды основано на редактор типов, которые поддерживаются поставщиками импортированных MEF. Команда включена в том случае, если имеется расширение поддержки текущий тип изменения. В таких случаях сам пакет невозможно использовать правило статический контекст пользовательского интерфейса, поскольку условия мог измениться в зависимости от того, MEF, какие расширения доступны.

Чтобы обеспечить поддержку таких пакетов, контексты пользовательского интерфейса на основе правил поддерживаются выражения жестко «*», указывающий всех приведенных далее условий он объединяется с или. Это позволяет определить известные контекст пользовательского интерфейса на основе правил и привязать его состояния команд к этому контексту главный пакет. После этого любое расширение MEF, нацеленное на главный пакет можно добавить условия для редакторов, поддерживаемых без влияния на другие термины или выражение, из главного.

Конструктор <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> документации показан синтаксис для расширяемого правила контекст пользовательского интерфейса.
