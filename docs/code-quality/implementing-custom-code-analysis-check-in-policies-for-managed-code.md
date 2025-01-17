---
title: Пользовательский код анализа политик возврата для управляемого кода
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6619e3bb988a555fba5718f609ff3a5f0584063b
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260841"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Реализация настраиваемых политик возврата с анализом кода для управляемого кода

Политика возврата с анализом кода задает набор правил, которые члены проекта DevOps в Azure необходимо запустить на исходный код, прежде чем он возвращается систему управления версиями. Корпорация Майкрософт предоставляет набор стандартных *наборов правил* этой группы правил анализа кода в функциональных областей. *Пользовательские политики возврата наборов правил* указать набор правил анализа кода, относящиеся к проекту. Набор правил хранится в RULESET-файл.

Политики возврата задаются на уровне проекта DevOps в Azure и заданной расположением RULESET-файла в дерево системы управления версиями. Существуют ограничения на расположение элемента управления версии набора настраиваемых правил политики группы отсутствуют.

Анализ кода настраивается для отдельных проектов кода в окне «Свойства» для каждого проекта. Пользовательский набор правил для проекта кода задается физическое расположение RULESET-файла на локальном компьютере. Если заданный RULESET-файл, расположенный на том же диске, что и проект кода, Visual Studio использует относительный путь к файлу в конфигурации проекта.

Предлагаемый принцип создания Azure DevOps, проект настраиваемый набор правил рекомендуется хранить RULESET-файла политики возврата в специальную папку, которая не является частью любого кода проекта. Если файл хранится в соответствующей папке, можно применить разрешения, ограничивающие, которым разрешено редактировать файл правил и можно легко переместить структуру каталогов, содержащий проекта в другой каталог или компьютера.

## <a name="create-the-project-custom-check-in-rule-set"></a>Создание набора настраиваемых правил проекта

Чтобы создать настраиваемый набор правил для проекта DevOps в Azure, сначала создать особую папку для политики возврата набору правил в **обозреватель управления исходным кодом**. Создать файл набора правил и добавьте его в систему управления версиями. Наконец указываются как политика анализа кода возврата для проекта набор правил.

> [!NOTE]
> Чтобы создать папку в проекте Azure DevOps, сначала необходимо сопоставить корневую папку проекта в папку на локальном компьютере.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Чтобы создать папку системы управления версиями для набора правил политики возврата

1. В командном обозревателе разверните узел проекта и нажмите кнопку **системы управления версиями**.

2. В **папки** панели, щелкните правой кнопкой мыши проект и выберите команду **новую папку**.

3. В основной области системы управления версиями, щелкните правой кнопкой мыши **новую папку**, нажмите кнопку **Переименовать**и введите имя для папки набора правил.

### <a name="to-create-the-check-in-policy-rule-set"></a>Чтобы создать набор правил политики возврата

1. На **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **файл**.

2. В **категории** выберите **Общие**.

3. В **шаблоны** дважды щелкните **набор правил анализа кода**.

4. [Укажите правила](../code-quality/how-to-create-a-custom-rule-set.md) необходимо включить в набор правил, а затем сохранить правило установите файл в папке набора правил, который вы создали.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Чтобы добавить правило установите файл в системе управления версиями

1. В **обозреватель управления исходным кодом**, щелкните правой кнопкой мыши новую папку и нажмите кнопку **добавить элементы в папку**.

     Дополнительные сведения см. в разделе [Git и репозитории Azure](/azure/devops/repos/git/overview?view=vsts).

2. Щелкните созданный файл набора правил, а затем щелкните **Готово**.

     Файл добавляется в систему управления версиями и извлечен вами.

3. В **обозреватель управления исходным кодом** окне сведений щелкните правой кнопкой мыши имя файла и нажмите кнопку **Возврат ожидающих изменений**.

4. В **возврат** диалоговом окне вы можете добавить комментарий, а затем нажмите кнопку **вернуть**.

    > [!NOTE]
    > Если вы уже настроили политику возврата с анализом кода для проекта DevOps в Azure и выбора **включить возврат файлов, которые являются частью текущего решения**, вы получите предупреждение о нарушении политики. В диалоговом окне ошибки политики выберите **переопределить сбой политики и продолжить возврат**. Добавьте необходимое примечание и нажмите кнопку **ОК**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Чтобы задать правило настроить файл как политики возврата

1. На **Team** последовательно выберите пункты **параметры проекта**, а затем нажмите кнопку **системы управления версиями**.

2. Нажмите кнопку **политики возврата**, а затем нажмите кнопку **добавить**.

3. В **политики возврата** дважды щелкните **анализа кода**и убедитесь, что **включить анализ кода для управляемого кода** установлен флажок.

4. В **выполнить этот набор правил** выберите  **\<выбрать набор правил из системы управления версиями >** .

5. Введите путь к файлу набора правил политики возврата в системе управления версиями.

     Путь должен соответствовать следующему синтаксису:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Можно скопировать путь с помощью одного из следующих процедур в **обозреватель управления исходным кодом**:

    - В **папки** панели, щелкните папку, содержащую файл набора правил. Скопируйте путь папки, которая отображается в системе управления версиями **источника** и вручную введите имя файла набора правил.

    - В окне «Подробности» щелкните правой кнопкой мыши файл набора правил, а затем нажмите кнопку **свойства**. На **Общие** вкладке, скопируйте значение в **имя сервера**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Синхронизации проектов кода в набор правил политики возврата

Указывается набор правил политики возврата проекта как набор правил анализа кода, конфигурации проекта кода в диалоговом окне "Свойства" проекта. Если набор правил расположен на том же диске, что и проект кода, чтобы указать набор правил, при выборе пути из диалогового окна файла используется относительный путь. Относительный путь позволяет значения свойств проекта, которую можно переносить на другие компьютеры, использующие аналогично локальной версии структуры элементов управления.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Чтобы задать правило проекта настроить как набор правил проекта кода

1. При необходимости извлеките папку набора правил политики возврата и файл из системы управления версиями.

   Можно выполнять этот шаг в **обозреватель управления исходным кодом** щелкните правой кнопкой мыши набора правил и выбрав команду **получить последнюю версию**.

2. В **обозревателе решений**, щелкните правой кнопкой мыши проект кода и нажмите кнопку **свойства**.

3. **Нажмите кнопку Анализ кода**.

4. При необходимости щелкните соответствующие пункты в **конфигурации** и **платформы** перечислены.

5. Чтобы запустить анализ кода при каждом построении проекта код с помощью указанной конфигурации, выберите **включить анализ кода в построении (определяет константу CODE_ANALYSIS)** "флажок".

6. Чтобы пропускать код в компонентах, от других компаний, установите **подавлять результаты из созданного кода** "флажок".

7. В **выполнить этот набор правил** выберите  **\<Обзор... >** .

8. Укажите локальную версию файла набора правил политики возврата.