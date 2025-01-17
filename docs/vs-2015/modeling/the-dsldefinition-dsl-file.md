---
title: Файл DslDefinition.dsl | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: f3fc3ed7-2438-4e5a-b3d7-fe7e0e8a134c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 610d371fe288a6582cdf9e6460c339347f60c81a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680821"
---
# <a name="the-dsldefinitiondsl-file"></a>Файл DslDefinition.dsl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описывается структура файла DslDefinition.dsl в проекте Dsl [!INCLUDE[dsl](../includes/dsl-md.md)] решение, которое определяет *предметно ориентированного языка*. Файл DslDefinition.dsl описывает классы и взаимосвязь доменного языка, а также схема, фигуры, соединители, формат сериализации, и **элементов** доменного языка и его средства для изменения. В решении доменного языка код, который определяет эти инструменты, генерируется согласно информации из файла DslDefinition.dsl.  
  
 Как правило, используется *конструктора доменного языка* для редактирования файла DslDefinition.dsl. В необработанном виде файл DslDefinition.dsl представляет собой XML, и его можно открыть в редакторе XML. Это позволит вам понять, какая информация содержится в файле и как она организована в целях отладки и расширения.  
  
 Примеры в данном разделе взяты из шаблона решения "Схема компонентов". Чтобы посмотреть пример, создайте решение доменного языка на основе шаблона решения "Модели компонентов". Как только вы создадите решение, в Конструкторе доменного языка появится файл DslDefinition.dsl. Закройте файл, щелкните правой кнопкой мыши в **обозревателе решений**, пункты **открыть с помощью**, нажмите кнопку **редактор XML**, а затем нажмите кнопку **ОК**.  
  
## <a name="sections-of-the-dsldefinitiondsl-file"></a>Разделы файла DslDefinition.dsl  
 Корневой элемент — \<Dsl > и его атрибуты определяют имя доменного языка, пространство имен, а основной и дополнительный номера версий. Схема `DslDefinitionModel` определяет содержание и структуру действительного файла DslDefinition.dsl.  
  
 Дочерние элементы \<Dsl > корневого элемента, как показано ниже:  
  
 Классы  
 В этом разделе определяется каждый класс домена, который генерирует класс в генерируемом коде.  
  
 Отношения  
 В этом разделе определяются отношения в модели. Источник и цель представляют собой две стороны отношения.  
  
 Типы  
 В этом разделе определяется каждый тип и его пространство имен. Свойства домена бывают двух типов. `DomainEnumerations` определяются в модели и генерируют типы в файле DomainModel.cs. `ExternalTypes` ссылаться на типы, определенные в других местах (таких как `String` или `Int32`) и ничего не генерируют.  
  
 Фигур  
 В этом разделе определяются фигуры, которые описывают внешний вид модели в конструкторе. Геометрические фигуры сопоставляются с классами в модели в разделе "Схема".  
  
 Соединители  
 В этом разделе определяется внешний вид соединителей, присутствующих в конструкторе. Описания стиля геометрических фигур сопоставляются с классами в модели в разделе "Схема".  
  
 XmlSerializationBehavior  
 В этом разделе определяется схема сериализации и предоставляется дополнительная информация о порядке сохранения каждого класса в файл.  
  
 ExplorerBehavior  
 В этом разделе определяется как **обозреватель DSL** появится окно, когда пользователь редактирует модель.  
  
 ConnectionBuilders  
 В этом разделе определяется построитель соединений для каждого инструмента соединения (инструмент устанавливает связи между любыми двумя классами, которые могут быть соединены). В этом разделе определяется возможность соединения класса источника с классом цели.  
  
 Схема  
 В этом разделе определяется схема, которая используется для указания свойств, таких как цвет фона и корневой класс. (Корневой класс — это класс домена, представленный схемой в целом.) Раздел "Схема" также содержит элементы ShapeMap и ConnectorMap, которые указывают, какую фигуру или соединитель представляют каждый класс домена или отношение.  
  
 Designer  
 В этом разделе определяется конструктор (редактор), который объединяет в себе **элементов**, параметры проверки, схему и схему сериализации. Раздел конструктора также определяет корневой класс модели, который обычно является корневым классом схемы.  
  
 Explorer  
 В этом разделе описаны **обозреватель DSL** поведение (определенное в разделе XmlSerializationBehavior).  
  
## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Моникеры в файле DslDefinition.dsl  
 В файле DslDefinition.dsl можно использовать моникеры для создания кросс-ссылок на определенные элементы. Например, каждое определение отношения содержит подразделы "Источник" и "Цель". В каждом подразделе содержится моникер класса объекта, который может быть связан с этим отношением:  
  
```  
<DomainRelationship …        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole …>  
       <RolePlayer>  
         <DomainClassMoniker Name="Library" />  
       </RolePlayer>  
     </DomainRole>  
   </Source>  
```  
  
 Обычно пространство имен элемента, на который создается ссылка (в данном примере это класс домена `Library`), совпадает с пространством имен ссылающегося элемента (в данном случае доменная связь LibraryHasMembers). В подобных случаях моникер должен сообщать только имя класса. Если пространства имен отличаются, необходимо использовать полную форму /Namespace/Name:  
  
```  
  
<DomainClassMoniker Name="/ExampleNameSpace/Library" />  
  
```  
  
 Система моникеров требует, чтобы одноуровневые элементы в дереве XML имели разные имена. В связи с этим при попытке сохранить определение доменного языка, содержащее, например, два класса с одинаковым именем, возникнут ошибки проверки. Обязательно исправьте такие ошибки с дублирующими именами, прежде чем сохранить файл DslDefinition.dsl, чтобы потом его можно было правильно перезагрузить.  
  
 У каждого типа есть свой тип моникера: DomainClassMoniker, DomainRelationshipMoniker и т. д.  
  
## <a name="types"></a>Типы  
 В разделе "Типы" определяются все типы, которые файл DslDefinition.dsl содержит в качестве типов и свойств. Эти типы делятся на две категории: внешние типы, такие как System.String, и типы перечисления.  
  
### <a name="external-types"></a>Внешние типы  
 В примере схемы компонентов приводится список стандартных примитивных типов, хотя используются только некоторые из них.  
  
 Каждое определение внешнего типа состоит только из имени и пространства имен, например String и System:  
  
```  
<ExternalType Name="String" Namespace="System" />  
```  
  
 Полные имена типов используются вместо эквивалентов ключевых слов компилятора, таких как string.  
  
 Внешние типы не ограничиваются стандартной библиотекой типов.  
  
### <a name="enumerations"></a>Перечисления  
 Стандартная спецификация перечислений выглядит следующим образом:  
  
```  
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">  
  <Literals>  
    <EnumerationLiteral Name="Start" Value="1"/>  
    <EnumerationLiteral Name="Decision" Value="2"/>  
  </Literals>  
</DomainEnumeration>  
```  
  
 Атрибут `IsFlags` следит за тем, чтобы сгенерированному коду предшествовал атрибут `[Flags]` среды CLR, определяющий, могут ли значения перечисления комбинироваться по битам. Если этот атрибут имеет значение true, необходимо указать значения power-of-two для литералов.  
  
## <a name="classes"></a>Классы  
 Большинство элементов в любом определении доменного языка прямо или косвенно являются экземплярами `DomainClass`. Подклассы `DomainClass` включают `DomainRelationship`, `Shape`, `Connector` и `Diagram`. В разделе `Classes` файла DslDefinition.dsl перечисляются классы доменов.  
  
 Каждый класс имеет набор свойств и может иметь базовый класс. В примере схемы компонентов `NamedElement` является абстрактным классом со свойством `Name` типа строка:  
  
```  
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">  
  <Properties>  
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
</DomainClass>  
```  
  
 `NamedElement` является базовым для других классов, таких как `Component`, который имеет собственные свойства в дополнение к `Name` свойство, которое он наследуется от `NamedElement`. Дочерний узел BaseClass содержит ссылку на моникер. Так как класс, на который задана ссылка, находится в том же пространстве имен, в моникере указывается только его имя:  
  
```  
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">  
  <BaseClass>  
    <DomainClassMoniker Name="NamedElement" />  
  </BaseClass>  
  <Properties>  
    <DomainProperty Name="Kind" DisplayName="Kind" >  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
```  
  
 Каждый класс домена (включая отношения, фигуры, соединители и схемы) может иметь следующие атрибуты и дочерние узлы.  
  
- **Идентификатор.** Этот атрибут является GUID. Если вы не укажете значение в файле, Конструктор доменного языка создаст значение сам. (Для экономии места в иллюстрациях к данному документу этот атрибут обычно опускается.)  
  
- **Имя и пространство имен.** Эти атрибуты указывают имя и пространство имен класса в генерируемом коде. Они должны быть уникальными в пределах доменного языка.  
  
- **InheritanceModifier.** Данный атрибут является "абстрактным", "запечатанным" или пустым.  
  
- **DisplayName.** Этот атрибут имеет имя, отображаемое в **свойства** окна. Атрибут DisplayName может содержать пробелы и другие знаки препинания.  
  
- **GeneratesDoubleDerived.** Если этот атрибут имеет значение true, генерируются два класса, где один является подклассом второго. Все сгенерированные методы включаются в базовый класс, а конструкторы — в подкласс. Настроив данный атрибут, можно переопределить любой сгенерированный метод в пользовательском коде.  
  
- **HasCustomConstructor**. Если этот атрибут имеет значение true, конструктор в генерируемом коде опускается. Это позволяет написать собственную версию кода.  
  
- **Атрибуты**. Это атрибут содержит CLR-атрибуты сгенерированного класса.  
  
- **BaseClass**. Если вы указываете базовый класс, он должен быть того же типа. Например, базовым классом для класса домена должен быть другой класс домена, а для фигуры секции — другая фигура секции. Если базовый класс не указан, то в генерируемом коде используется класс, производный от стандартного класса платформы. Например, класс домена берется из `ModelElement`.  
  
- **Свойства**. Данный атрибут содержит свойства, которые поддерживаются элементом управления транзакциями, и запоминается при сохранении модели.  
  
- **ElementMergeDirectives**. Каждая директива слияния элементов контролирует, каким образом другой экземпляр другого класса добавляется к экземпляру родительского класса. Дополнительную информацию о директивах слияния элементов вы найдете ниже.  
  
- Класс языка C# генерируется для каждого класса домена, который указан в разделе `Classes`. Классы языка C# создаются в файле Dsl\GeneratedCode\DomainClasses.cs.  
  
### <a name="properties"></a>Свойства  
 Каждое свойство домена имеет имя и тип. Имя должно быть уникальным в пределах класса домена и его переходных основ.  
  
 Тип должен ссылаться на один из указанных в разделе `Types`. Обычно моникер должен содержать пространство имен.  
  
```  
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
  <Type>  
    <ExternalTypeMoniker Name="/System/String" />  
  </Type>  
</DomainProperty>  
```  
  
 Каждое свойство домена может также иметь следующие атрибуты:  
  
- **IsBrowsable**. Данный атрибут определяет, будет ли свойство отображаться в **свойства** окно, когда пользователь выберет объект родительского класса.  
  
- **IsUIReadOnly**. Данный атрибут определяет, может ли пользователь изменять свойство в **свойства** окно или с помощью декоратора, в котором представлено это свойство.  
  
- **Тип**. Этот атрибут может иметь значение Normal, Calculated или CustomStorage. Если атрибуту присваивается значение Calculated, необходимо создать пользовательский код, который определит значение, а само свойство будет доступно только для чтения. Если атрибуту присваивается значение CustomStorage, необходимо создать код, который будет как получать, так и устанавливать значения.  
  
- **IsElementName**. Если этот атрибут имеет значение true, при создании экземпляра родительского класса ему автоматически присваивается уникальное значение. Этот атрибут может иметь значение true только для одного свойства в каждом классе, причем это свойство должно быть строкового типа. В примере схемы компонентов свойство `Name` в `NamedElement` атрибуте `IsElementName` имеет значение true. Если пользователь создает элемент `Component` (который наследуется от `NamedElement`), ему автоматически присваивается имя вида Component6.  
  
- `DefaultValue`. Если данный атрибут указан, то указанное значение назначается этому атрибуту в новых экземплярах данного класса. Если атрибут `IsElementName` установлен, то атрибут DefaultValue указывает первоначальную часть новой строки.  
  
- **Категория** — заголовок, под которой свойство отображается в **свойства** окна.  
  
## <a name="relationships"></a>Отношения  
 В разделе `Relationships` перечисляются все отношения в доменном языке. Каждая `Domain Relationship` является бинарной и направленной. Она связывает членов класса источника с членами целевого класса. Классы источника и цели обычно являются классами доменов, но связи с другими отношениями также допускаются.  
  
 Например, отношение соединения связывает членов класса OutPort с членами класса InPort. Каждый экземпляр связи отношения соединяет экземпляр OutPort с экземпляром InPort. Поскольку отношение относится к типу многий-ко-многим, то каждый экземпляр OutPort может иметь много связей соединения с его источниками, а каждый экземпляр InPort — много связей соединения с целевыми объектами.  
  
### <a name="source-and-target-roles"></a>Роли источника и цели.  
 Каждое отношение содержит роли источника и цели со следующими атрибутами.  
  
- Атрибут `RolePlayer` создает ссылки на класс домена из связанных экземпляров: OutPort для источника, InPort для цели.  
  
- У атрибута `Multiplicity` может быть четыре значения (ZeroMany, ZeroOne, One и OneMany). Он указывает количество связей данного отношения, которые могут быть связаны с одним исполнителем роли.  
  
- Атрибут `PropertyName` указывает имя, которое используется в классе исполнения роли для осуществления доступа к объектам на другом конце. Это имя используется в шаблоне или пользовательском коде для перебора отношения. Например, если атрибут `PropertyName` роли источника имеет значение `Targets`, срабатывает следующий код:  
  
    ```  
    OutPort op = …; foreach (InPort ip in op.Targets) ...  
    ```  
  
     Как правило, если атрибут кратности имеет значение ZeroMany или OneMany, имена свойств указываются во множественном числе.  
  
     Кратность роли показывает, сколько противоположных ролей могут быть связаны с каждым экземпляром этой роли. Например, если в отношении ComponentHasPorts атрибут `RolePlayer` целевой роли имеет значение Port, атрибут `PropertyName` — значение Component, а атрибут `Multiplicity` — значение ZeroOne, код для использования этой роли будет выглядеть следующим образом:  
  
    ```  
    ComponentPort p = …; Component c = p.Component; if (c != null) …  
    ```  
  
- Атрибут роли `Name` — это имя, которое используется в пределах класса отношения для создания ссылок на другой конец связи. Как правило, имя роли всегда указывается в единственном числе, так как каждая связь имеет по одному экземпляру с каждой стороны. Используется следующий код:  
  
    ```  
    Connection connectionLink = …; OutPort op = connectionLink.Source;  
    ```  
  
- По умолчанию атрибут `IsPropertyGenerator` имеет значение true. Если ему будет присвоено значение false, свойство в классе исполнителя роли создано не будет. (В этом случае `op.Targets`, например, работать не будет.) Однако можно использовать пользовательский код для перебора отношения или получения доступа к связям, если пользовательский код использует отношение явно:  
  
    ```  
    OutPort op = …; foreach (InPort ip in Connection.GetTargets(op)) …  
    foreach (Connection link in Connection.GetLinksToTargets(op)) …  
    ```  
  
### <a name="relationship-attributes"></a>Атрибуты отношений  
 В дополнение к атрибутам и дочерним узлам, доступным для всех классов, каждое отношение имеет также следующие атрибуты.  
  
- **IsEmbedding**. Этот логические атрибут определяет, является ли отношение частью дерева внедрения. Каждая модель должна формировать дерево с отношениями внедрения, а каждый класс домена должен быть целевым объектом хотя бы для одного отношения внедрения, если только это не корневой класс модели.  
  
- **AllowsDuplicates**. Этот логические атрибут по умолчанию имеет значение false и применяется только к отношениям со значением кратности many как в источнике, так и в цели. Он определяет, могут ли пользователи языка соединять одну пару элементов источника и цели больше чем одной связью в одном и том же отношении.  
  
## <a name="designer-and-toolbox-tabs"></a>Конструктор и вкладки панели элементов  
 Основная часть **конструктор** раздел файла DslDefinition.dsl **ToolboxTab** элементов. Один конструктор может иметь несколько таких элементов, каждый из которых представляет собой раздел с заголовком в сгенерированной конструктором **элементов**. Каждый **ToolboxTab** элемент может содержать один или несколько **ElementTool** элементов, **ConnectionTool** элементов, или оба.  
  
 Инструменты элементов могут создавать экземпляры определенного класса домена. Когда пользователь перетаскивает элемент на схему, результат определяется директивами слияния элементов, как описано ниже в данном разделе.  
  
 Каждый инструмент соединения может вызывать определенный построитель соединения. Один построитель соединения может создавать больше одного типа отношений в зависимости от того, где пользователь щелкает мышкой, как описано в разделе о построителях соединений.  
  
 Ни один из типов инструментов не создает фигуры или соединители напрямую. Каждый из них создает класс домена или доменную связь, а затем разметка фигур и соединителей определяет порядок отображения этого класса домена или доменной связи.  
  
## <a name="paths"></a>Пути  
 Пути доменов отображаются в файле DslDefinition.dsl в нескольких расположениях. Эти пути указывают на серии связей от одного элемента в модели (т. е. экземпляра доменного языка) к другому. Синтаксис пути простой, но многословный.  
  
 Пути отображаются в файле DslDefinition.dsl в тегах `<DomainPath>…</DomainPath>`. Несмотря на то, что пути могут проходить через несколько связей, на практике в большинстве случаев каждый путь проходит только через одну.  
  
 Путь состоит из последовательности сегментов. Каждый сегмент представляет собой прыжок от объекта к связи или от связи к объекту. В связи с этим прыжки обычно сменяют друг друга, образуя собой длинный путь. Первый прыжок осуществляется от объекта к связи, второй — от объекта к другому концу связи, третий прыжок — к следующей связи и т. д. Редкое исключение в данной последовательности возникает, когда взаимосвязь является источником или целью для другой взаимосвязи.  
  
 Каждый сегмент начинается с имени взаимосвязи. В прыжке связи объекта связи предшествует точка и имя свойства: "`Relationship . Property`«. В прыжке объект связи связь предшествует восклицательный знак и имя роли: "`Relationship ! Role`«.  
  
 Пример схемы компонентов содержит путь в элементе ParentElementPath элемента ShapeMap для класса InPort. Этот путь запускается следующим образом:  
  
```  
    ComponentHasPorts.Component  
```  
  
 В данном примере InPort является подклассом ComponentPort и имеет отношение с классом ComponentHasPorts. Свойство называется Component.  
  
 При написании C# для данной модели, можно перепрыгивать через связь за один шаг, с помощью свойства, которое генерируется отношением на каждый из классов, которым они относятся:  
  
```  
     InPort port; ...  Component c = port.Component;  
```  
  
 При этом необходимо явно включить оба прыжка в синтаксис пути. Из-за этого требования получение доступа к промежуточной связи можно упростить. Следующий код завершает прыжок из связи в свойство Component.  
  
```  
    ComponentHasPorts.Component / ! Component  
```  
  
 (Можно опустить имя отношения, если оно такое же, как в предыдущем сегменте.)  
  
## <a name="element-merge-directives"></a>Директивы слияния элементов  
 Когда пользователь языка перетаскивает элемент из **элементов** на схему, создается экземпляр класса этого средства. Кроме того, создаются связи между данным экземпляром и существующими элементами модели. Некоторые элементы, такие как компоненты или комментарии, создаются в том случае, когда пользователь языка перетаскивает их из **элементов** фигуру на пустую часть схемы. Другие элементы создаются, когда пользователь языка перетаскивает их на другие размещенные элементы. Например, OutPort или InPort создаются, когда пользователь перетаскивает их на компонент.  
  
 Потенциальный класс для размещения, такой как Component, принимает новый элемент, только если класс размещения имеет директиву слияния элементов для класса нового элемента. Например, узел DomainClass с параметром Name="Component" содержит следующее:  
  
```  
<DomainClass Name="Component" …> …  
    <ElementMergeDirective>  
      <Index>  
        <DomainClassMoniker Name="ComponentPort" />  
      </Index>  
      <LinkCreationPaths>  
        <DomainPath>ComponentHasPorts.Ports</DomainPath>  
      </LinkCreationPaths>  
    </ElementMergeDirective> …  
```  
  
 Моникер класса, находящийся под узлом Index, ссылается на класс элемента, который может быть принят. В данном случае, ComponentPort является абстрактным базовым классом элементов InPort и OutPort. Таким образом, любой из этих элементов может быть принят.  
  
 ComponentModel, корневой класс языка, имеет директивы слияния элементов для компонентов и комментариев. Пользователь может перетаскивать элементы для этих классов прямо на схему, так как пустые части схемы представляют собой корневой класс. У класса ComponentModel нет директивы слияния элементов для ComponentPort, а значит, пользователь не может перетаскивать элементы InPorts или OutPorts прямо на схему.  
  
 Директива слияния элементов определяет, какая связь или связи будут создаваться для того, чтобы новый элемент мог интегрироваться или войти в существующую модель. Для ComponentPort создается экземпляр ComponentHasPorts. DomainPath определяет как взаимосвязь, так и свойство родительского класса Ports, к которому будет добавлен элемент.  
  
 Можно создать несколько связей для директивы слияния элементов, включив несколько путей создания связи. Один из путей должен быть встроенным.  
  
 В пути создания связи можно использовать несколько сегментов. В данном случае последний сегмент определяет, какую связь необходимо создать. Предшествующие сегменты идут от родительского класса к объекту, из которого будет создана новая связь.  
  
 Например, можно добавить эту директиву слияния элементов к классу Component:  
  
```  
<DomainClass Name="Component" …> …  
  <ElementMergeDirective>  
    <Index>  
       <DomainClassMoniker Name="Comment"/>  
    </Index>  
    <LinkCreationPaths>  
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>  
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>  
    </LinkCreationPaths>  
  </ElementMergeDirective>  
```  
  
 После этого пользователи смогут перетаскивать комментарий на компонент, в случае чего будет автоматически создан новый комментарий, связанный с компонентом.  
  
 Первый путь создания связи идет от `Component` к `ComponentModel`, а затем создает экземпляр отношения внедрения `ComponentModelHasComments`. Второй путь создания связи создает связь отношения со ссылкой CommentsReferenceComponents из элемента размещения Component с новым элементом Comment. Все пути создания связи начинаются с класса размещения и должны заканчиваться на связи, которая переходит к созданному классу.  
  
## <a name="xmlclassdata"></a>XmlClassData  
 Каждый класс домена (включая отношения и другие подтипы) может содержать дополнительную информацию, предоставленную в узле `XmlClassData`, который отображается в разделе `XmlSerializationBehavior` файла DslDefinition.dsl. Эта информация, в частности, определяет сохранение экземпляров класса в сериализованной форме при сохранении модели в файл.  
  
 Большая часть сгенерированного кода, на который влияет `XmlSerializationBehavior`, находится в файле `Dsl\GeneratedCode\Serializer.cs`.  
  
 Каждый узел `XmlClassData` включает следующие дочерние узлы и атрибуты.  
  
- Узел моникера, ссылающийся на класс, к которому применяются данные.  
  
- **XmlPropertyData** для каждого свойства, определенного в классе.  
  
- **XmlRelationshipData** для каждого отношения, созданного из класса. (У отношений также есть собственные узлы XmlClassData.)  
  
- **TypeName** строковый атрибут, который определяет имя вспомогательного класса сериализации, в созданном коде.  
  
- **ElementName** строка, определяющая XML-тэг сериализованных экземпляров этого класса. Как правило, ElementName совпадает с именем класса за тем исключением, что начинается со строчной буквы. Например, файл образца модели начинается следующим образом:  
  
    ```  
    <componentModel …  
    ```  
  
- **MonikerElementName** в файлах сериализованной модели пользователя. Данный атрибут вводит моникер, который ссылается на этот класс.  
  
- **MonikerAttributeName**, определяющий имя XML-атрибута в моникере. В этом фрагменте сериализованного файла пользователя автор доменного языка определенные **MonikerElementName** как «inPortMoniker» и **MonikerAttributeName** как «путь»:  
  
    ```  
    <inPortMoniker path="//Component2/InPort1" />  
    ```  
  
### <a name="connectionbuilders"></a>ConnectionBuilders  
 Построитель соединения определяется для каждого средства соединения. Каждый построитель соединения состоит из одного или нескольких элементов LinkConnectDirective, каждый из которых содержит один или несколько элементов SourceDirective. Выбрав средство соединения, пользователь может начать соединение с любой фигуры, сопоставленной с элементом модели из списка элементов SourceDirective. Соединение может быть завершено на фигуре, сопоставленной с элементом из списка элементов TargetDirective. Создаваемый класс отношения зависит от элемента LinkConnectDirective, который определяется в соответствии с местом создания соединения.  
  
### <a name="xmlpropertydata"></a>XmlPropertyData  
 Объект **DomainPropertyMoniker** атрибутов определяет свойство, к которому относится данные. Данный атрибут должен быть свойством включающего класса ClassData.  
  
 **XmlName** атрибут предоставляет соответствующее имя атрибута, которое должно отображаться в XML. Как правило, эта строка совпадает с именем свойства за тем исключением, что начинается со строчной буквы.  
  
 По умолчанию **представление** атрибут имеет значение атрибута. Если **представление** имеет значение Element, дочерний узел создается в XML. Если **представление** имеет значение Ignore, свойство не сериализуется.  
  
 **IsMonikerKey** и **IsMonikerQualifier** атрибуты предоставляют свойство роли в идентификационных экземплярах родительского класса. Можно задать **IsMonikerKey** значение true для одного свойства, определенного или наследуемого классом. Этот атрибут определяет отдельный экземпляр родительского класса. Свойство, для которого устанавливается значение `IsMonikerKey`, обычно является именем или другим ключевым идентификатором. Например, строковое свойство `Name` является ключом моникера для NamedElement и его производных классов. Когда пользователь сохраняет модель в файл, этот атрибут должен содержать уникальные значения для каждого экземпляра одноуровневых элементов в дереве отношений внедрения.  
  
 В сериализованном файле модели полный моникер элемента представляет собой путь от корня модели вниз по дереву отношений внедрения со ссылками на ключ моникера на каждой точке. Например, элементы InPort внедряются в компоненты, которые, в свою очередь, внедряются в корень модели. Таким образом, правильный моникер выглядит так:  
  
```  
<inPortMoniker name="//Component2/InPort1" />  
```  
  
 Можно задать **IsMonikerQualifier** атрибут для строкового свойства и предоставить дополнительный способ для создания полного имени элемента. Например, в файле DslDefinition.dsl **пространства имен** квалификатором моникера является.  
  
### <a name="xmlrelationshipdata"></a>XmlRelationshipData  
 В сериализованном файле модели связи (как для отношений внедрения, так и для ссылочных отношений) представляются дочерними узлами на стороне источника отношения. В случае отношений внедрения дочерний узел содержит поддерево. В случае ссылочных отношений дочерний узел содержит моникер, который ссылается на другую часть дерева.  
  
 **XmlRelationshipData** атрибут в **XmlClassData** атрибут определяет, точно как дочерние узлы вкладываются в исходный элемент. Каждое отношение, которое является источником в классе домена имеет один **XmlRelationshipData** атрибута.  
  
 **DomainRelationshipMoniker** атрибут определяет одну из связей, источником в классе.  
  
 **RoleElementName** атрибут предоставляет имя тега XML, который заключается дочерний узел в сериализованных данных.  
  
 Например, файл DslDefinition.dsl содержит следующий код:  
  
```  
<XmlClassData ElementName="component" …>  
  <DomainClassMoniker Name="Component" />  
  <ElementData>  
    <XmlRelationshipData RoleElementName="ports">  
      <DomainRelationshipMoniker Name="ComponentHasPorts" />  
    </XmlRelationshipData>  
```  
  
 Таким образом, сериализованный файл следующий код:  
  
```  
<component name="Component1"> <!-- parent ->  
   <ports> <!-- role ->  
     <outPort name="OutPort1"> <!-- child element ->  
       …  
     </outPort>  
   </ports> …  
```  
  
 Если **UseFullForm** атрибут имеет значение true, вводится дополнительный уровень вложенности. Этот слой представляет собой отношение. Если это отношение имеет свойства, данному атрибуту необходимо присвоить значение true.  
  
```  
<XmlClassData ElementName="outPort">  
   <DomainClassMoniker Name="OutPort" />  
   <ElementData>  
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">  
       <DomainRelationshipMoniker Name="Connection" />  
     </XmlRelationshipData>  
   </ElementData>  
 </XmlClassData>  
```  
  
 Сериализованный файл содержит следующий код:  
  
```  
<outPort name="OutPort1">  <!-- Parent ->  
   <targets>  <!-- role ->  
     <connection sourceRoleName="X">  <!-- relationship link ->  
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->  
     </connection>  
    </targets>  
  </outPort>  
```  
  
 (Отношение соединения имеет собственный XML-класс данных, предоставляющий имена для атрибутов и элемента.)  
  
 Если **OmitElement** атрибут имеет значение true, связь роли имя указано, что сокращает сериализованный файл и понимается недвусмысленно при двух классов иметь не более одной связи. Пример:  
  
```  
<component name="Component3">  
  <!-- only one relationship could get here: ->  
  <outPort name="OutPort1">    
     <targets> …  
```  
  
### <a name="serialization-of-a-domain-specific-language-definition"></a>Сериализация определения доменного языка.  
 Файл DslDefinition.dsl сам является сериализованным файлом и соответствует определению доменного языка. Ниже приводятся несколько примеров XML определений сериализации.  
  
- **DSL** является узлом RootClass и классом схемы. DomainClass, DomainRelationship и другие элементы внедрены в `Dsl`.  
  
- **Классы** — **RoleElementName** связи между доменного языка и DomainClass.  
  
```  
<Dsl Name="CmptDsl5" …>  
  <Classes>  
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" …  
```  
  
- **XmlSerializationBehavior** атрибут внедрен в `Dsl` атрибута, но **OmitElement** значением на отношение внедрения. Следовательно, атрибут`RoleElementName` не внедряется. Напротив **ClassData** атрибут `RoleElementName` атрибут отношения внедрения между **XmlSerializationBehavior** атрибут и **XmlClassData** атрибута.  
  
```  
<Dsl Name="CmptDsl5" …> …  
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >  
    <ClassData>  
      <XmlClassData …>…</XmlClassData>  
      <XmlClassData …>…</XmlClassData>  
```  
  
- ConnectorHasDecorators является отношением внедрения между `Connector` и `Decorator`. `UseFullForm` задано таким образом, чтобы имя отношения отображается вместе со списком свойств для каждой связи из объекта соединителя. При этом атрибут `OmitElement` также установлен таким образом, чтобы ни один элемент `RoleElementName` не включал несколько связей, внедренных в `Connector`:  
  
```  
<Connector Name="AssociationLink" …>  
  <ConnectorHasDecorators Position="TargetTop" …>  
    <TextDecorator Name="TargetRoleName"   />  
  </ConnectorHasDecorators>  
  <ConnectorHasDecorators Position="SourceTop" …>  
    <TextDecorator Name="SourceRoleName"   />  
  </ConnectorHasDecorators>  
</Connector>  
```  
  
## <a name="shapes-and-connectors"></a>Фигуры и соединители  
 Определения фигур и соединителей наследуют атрибуты и дочерние узлы от классов доменов в дополнение к следующим атрибутам:  
  
- Атрибуты `Color` и `Line``Style`.  
  
- **ExposesFillColorAsProperty** и некоторые похожие атрибуты. Эти логические атрибуты позволяют пользователю менять соответствующее свойство. Как правило, когда пользователь выбирает фигуру на диаграмме, свойства, которые отображаются на **свойства** окне зависят от экземпляра класса домена, к которому эта фигура сопоставлена. Если `ExposesFillColorAsProperty` имеет значение true, также отображается свойство фигуры.  
  
- **ShapeHasDecorators**. Экземпляр данного атрибута присутствует в каждом тексте, ярлыке или декораторе расширения и свертывания. (В файле DslDefinition.dsl, `ShapeHasDecorators` является отношением, атрибут `UseFullForm` которого имеет значение true.)  
  
## <a name="shape-maps"></a>Карты фигур  
 Карты фигур определяют, как экземпляры данного класса домена будут выглядеть на экране. Карты фигур и соединителей отображаются в разделе `Diagram` файла DslDefinition.dsl.  
  
 Как и в следующем примере, элементы `ShapeMap` имеют как минимум моникер класса домена, моникер фигуры и элемент `ParentElementPath`:  
  
```  
<ShapeMap>  
  <DomainClassMoniker Name="InPort" />  
  <ParentElementPath>  
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>  
  </ParentElementPath>  
  <PortMoniker Name="InPortShape" />  
</ShapeMap>  
```  
  
 Основная функция элемента `ParentElementPath` состоит в том, что один и тот же класс объектов может в разном контексте выглядеть по-разному. Например, если `InPort` может быть также внедрен в комментарий, в этом качестве `InPort` будет отображаться в виде другой фигуры.  
  
 Кроме того, путь определяет связь между фигурой и ее родительским объектом. Структура внедрения между фигурами и файлом DslDefinition.dsl не определена и должна выводиться из карт фигур. Родительским объектом фигуры является фигура, сопоставленная с элементом домена, которого определяет путь родительского элемента. В данном случае путь определяет компонент, к которому относится `InPort`. В другой карте фигур класс Component сопоставляется с классом с ComponentShape. Следовательно, новая фигура `InPort` создает дочернюю фигуру компонента `ComponentShape`.  
  
 Если вместо этого фигура InPort присоединяется к схеме, пути родительского элемента приходится предпринимать еще один шаг — к модели компонентов, которая сопоставлена со схемой:  
  
```  
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel  
```  
  
 Корень модели не имеет карты фигур. Он ссылается напрямую из схемы, в которой находится элемент `Class`:  
  
```  
<Diagram Name="ComponentDiagram" >  
    <Class>  
      <DomainClassMoniker Name="ComponentModel" />  
    </Class>…  
```  
  
### <a name="decorator-maps"></a>Карты декоратора  
 Карта декоратора объединяет свойство в сопоставленном классе с декоратором в фигуре. Если свойство имеет числовой или логический тип, его значение может определить, будет ли виден декоратор. Если декоратор является текстовым, отображается значение свойства, а пользователь может его редактировать.  
  
### <a name="compartment-shape-maps"></a>Карты фигур секций  
 Карты фигур секций являются подтипами карт фигур.  
  
## <a name="connector-maps"></a>Карты соединителей  
 Минимальная карта соединителя ссылается на соединитель и отношение:  
  
```  
<ConnectorMap>  
  <ConnectorMoniker Name="CommentLink" />  
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />  
</ConnectorMap>  
```  
  
 Карты соединителей могут также содержать карты декораторов.  
  
## <a name="see-also"></a>См. также  
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Способ определения доменного языка](../modeling/how-to-define-a-domain-specific-language.md)   
 [Сведения о моделях, классах и отношениях](../modeling/understanding-models-classes-and-relationships.md)
