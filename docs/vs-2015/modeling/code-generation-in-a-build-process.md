---
title: Создание кода в процессе построения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 57114789ce9f0505423e8463f90117619bfc717b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687048"
---
# <a name="code-generation-in-a-build-process"></a>Создание кода в процессе построения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Преобразование текста может вызываться как часть процесса построения решения Visual Studio. Имеются задачи сборки, которые специализируются на преобразовании текста. Задачи сборки T4 запускают выполнение текстовых шаблонов времени разработки, а также компилируют текстовые шаблоны времени выполнения (предварительно обработанные).

Возможности задач построения несколько отличаются в зависимости от используемого обработчика сборки. При построении решения в Visual Studio текстового шаблона можно получить доступ к API Visual Studio (EnvDTE) Если [hostspecific = «true»](../modeling/t4-template-directive.md) атрибут имеет значение. Однако это не так при сборке решения из командной строки или при запуске с помощью Visual Studio сборки на сервере. В таких случаях сборка выполняется в MSBuild и используется другой узел T4.

Это означает, что доступ к таким параметрам, как имена файлов проекта, не может производиться таким же образом, как при сборке текстового шаблона в MSBuild. Тем не менее, вы можете [передать данные среды в текстовые шаблоны и процессоры директив с помощью параметров сборки](#parameters).

## <a name="buildserver"></a> Настройка компьютеров

Задачи сборки на компьютере разработчика, установите [пакет SDK моделирования для Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148).

Если [сервер сборки](https://msdn.microsoft.com/library/788443c3-0547-452e-959c-4805573813a9) работает на компьютере, на котором не установлена Visual Studio, скопируйте следующие файлы на компьютер построения с компьютера разработки. Замените символ "*" номером последней версии.

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    - Microsoft.TextTemplating.Build.Tasks.dll

    - Microsoft.TextTemplating.targets

- $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    - Microsoft.VisualStudio.TextTemplating.*.0.dll

    - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (several files)

    - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Изменение файла проекта

Необходимо изменить файл проекта для настройки некоторых функций в MSBuild.

В обозревателе решений выберите **Unload** в контекстном меню проекта. Это позволит изменить CSPROJ- или VBPROJ-файл в редакторе XML.

После завершения редактирования, выберите **перезагрузить**.

## <a name="import-the-text-transformation-targets"></a>Импорт целевых объектов преобразования текста

В VBPROJ- или CSPROJ-файле найдите строку, аналогичную следующей:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- или -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

После этой строки вставьте директиву импорта текстового шаблона:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version – defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transforming-templates-in-a-build"></a>Преобразование шаблонов в сборке

Предусмотрено несколько свойств, которые можно вставлять в файл проекта для управления задачей преобразования.

- Выполнять задачу преобразования в начале каждой сборки:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Перезаписывать файлы, доступные только для чтения (например, потому что они не извлечены):

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Каждый раз преобразовывать все шаблоны:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     По умолчанию задача MSBuild T4 заново генерирует выходной файл, если он старше своего файла шаблона, любого из включенных файлов или любого файла, который ранее считывался шаблоном или используемым им процессором директив. Обратите внимание, что это намного более мощная проверка зависимостей, чем используемая в команде "Преобразовать все шаблоны" в Visual Studio, которая только сравнивает даты шаблона и выходного файла.

Чтобы выполнить только преобразования текста в проекте, вызовите задачу TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Чтобы преобразовать определенный текстовый шаблон:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

В команде TransformFile можно использовать символы подстановки:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Система управления версиями

Не существует специальной встроенной интеграции с системой управления версиями. Однако можно добавить собственные расширения, например, для извлечения и возврата созданного файла. По умолчанию задача преобразования текста избегает перезаписи файла, помеченного как доступный только для чтения, и если такой файл встречается, в список ошибок Visual Studio записывается информация об ошибке и выполнение задачи завершается неудачей.

Чтобы указать, что доступные только для чтения файлы следует перезаписывать, вставьте такое свойство:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Если не настроить шаг постобработки, при перезаписи файла в список ошибок будет записываться информация об ошибке.

## <a name="customizing-the-build-process"></a>Настройка процесса построения

Преобразование текста производится перед выполнением других задач в процессе сборки. Задачи, которые вызываются до и после преобразования, можно задавать, устанавливая свойства `$(BeforeTransform)` и `$(AfterTransform)`.

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

В свойстве `AfterTransform` можно указывать списки файлов:

- GeneratedFiles – список файлов, сгенерированных данным процессом. Для тех файлов, которые перезаписывают имеющиеся доступные только для чтения файлы, свойство %(GeneratedFiles.ReadOnlyFileOverwritten) будет иметь значение true. Эти файлы можно извлекать из системы управления версиями.

- NonGeneratedFiles – список доступных только для чтения файлов, которые не были перезаписаны.

  Например, можно определить задачу для извлечения GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath и OutputFileName

Эти свойства используются только в MSBuild. Они не влияют на создание кода в Visual Studio. Они перенаправляют созданный выходной файл в другую папку или файл. Целевая папка должна уже существовать.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Для перенаправления может быть полезна папка `$(IntermediateOutputPath).`

Если указано имя выходного файла, оно получает приоритет над расширением, определенным в директиве output в шаблонах.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Не рекомендуется указывать свойства OutputFileName или OutputFilePath, если преобразование шаблонов также выполняется в VS с помощью команды "Преобразовать все" или при запуске генератора единственного файла. В результате путь к файлу будет зависеть от способа запуска преобразования. Это может быть очень неудобно.

## <a name="adding-reference-and-include-paths"></a>Добавление путей для ссылок и включаемых файлов

Узел имеет набор путей по умолчанию, по которым производится поиск сборок, указанных в шаблонах. Для добавления в этот набор:

```
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Чтобы задать папки, в которых будет производиться поиск включаемых файлов, укажите список через точку с запятой. Обычно производится добавление в существующий список папок.

```
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a> Передача данных контекста сборки в шаблоны

Можно задать значения параметров в файле проекта. Например, можно передать свойства построения и [переменные среды](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

В текстовом шаблоне задайте атрибут `hostspecific` в директиве template. Используйте [параметр](../modeling/t4-parameter-directive.md) директиву, чтобы получить значения:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

## <a name="msbuild"></a> Использование свойств проекта в сборке и директив #include

Макросы Visual Studio, такие как $(SolutionDir), не работают в MSBuild. Вместо этого можно использовать свойства проекта.

Измените CSPROJ- или VBPROJ-файл для определения свойства проекта. В этом примере определяется свойство с именем `myLibFolder`.

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Теперь можно использовать ваше свойство проекта в директивах assembly и include:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

 Эти директивы получают значения из T4parameterValues как в узлах MSBuild, так и в узлах Visual Studio.

## <a name="q--a"></a>Вопросы и ответы

**Зачем преобразование шаблонов на сервере сборки? Я уже преобразовал шаблоны в Visual Studio до возврата в моем коде.**

При обновлении включенного файла или другого файл, считываемого шаблоном, Visual Studio не преобразует файл автоматически. Преобразование шаблонов в процессе сборки гарантирует обновление всех компонентов.

**Какие другие варианты есть для преобразования текстовых шаблонов?**

- [Служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) можно использовать в командных сценариев. В большинстве случаев удобнее использовать MSBuild.

- [Вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Во время разработки текстовые шаблоны](../modeling/design-time-code-generation-by-using-t4-text-templates.md) преобразуются в Visual Studio.

- [Текстовые шаблоны времени выполнения](../modeling/run-time-text-generation-with-t4-text-templates.md) преобразуется во время выполнения в приложении.

## <a name="read-more"></a>Дополнительные сведения

Хорошее руководство содержится в шаблоне MSbuild T4, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets

- [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)
- [Визуализации и моделирования пакета SDK для Visual Studio](http://go.microsoft.com/fwlink/?LinkID=185579)
- [Олег Сыч: Основные сведения об интеграции T4:MSBuild](https://github.com/olegsych/T4Toolbox)