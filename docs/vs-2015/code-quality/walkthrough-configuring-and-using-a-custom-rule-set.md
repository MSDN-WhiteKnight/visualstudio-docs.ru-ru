---
title: Пошаговое руководство. Настройка и использование настраиваемого набора правил | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fa3a91df779094e3e11722dfc7bfc03c58bcea7e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383420"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Пошаговое руководство. Настройка и использование набора настраиваемых правил
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как использовать средства анализа кода, которые были настроены для использования настраиваемый *набор правил* для библиотеки классов. Можно выбрать набор правил, к которому относится тип проекта, который вы указали для решения, или выбрать другие наборы правил в соответствии с конкретными потребностями, такие как сканирование устаревшего кода для проблем, которые могут быть исправлены является критическим. В любом случае наборы правил можно также настроить настраивать в соответствии с требованиями проекта.  
  
 В этом пошаговом руководстве приводится пошаговое описание следующих процессов:  
  
- Создайте библиотеку классов.  
  
- Выберите **базовые правила и рекомендации по разработке Microsoft** набора правил анализа кода.  
  
- Добавьте собственный код в класс.  
  
- Запустите анализ кода.  
  
- Настройка набора правил.  
  
- Запустить анализ кода и см. в разделе поведения настроек набора правил.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]или [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>Использование наборов правил для анализа кода  
 Во-первых можно создайте простую библиотеку классов.  
  
#### <a name="create-a-class-library"></a>Создание библиотеки классов  
  
1. В меню **Файл** последовательно выберите пункты **Создать** и **Проект**.  
  
2. В **новый проект** диалогового **типы проектов**, нажмите кнопку **Visual C#** .  
  
3. В разделе **Visual C#** выберите **библиотеки классов**.  
  
4. В **имя** текстовое поле, тип **Пример_набора_правил** и нажмите кнопку **ОК**.  
  
   После этого вы сможете выбрать **базовые правила и рекомендации по разработке Microsoft** набор правил и сохраните его с проектом.  
  
#### <a name="select-a-code-analysis-rule-set"></a>Выберите набор правил анализа кода  
  
1. На **анализ** меню, щелкните **Настройка анализа кода для Пример_набора_правил**.  
  
    Параметры конфигурации для анализа кода отображаются.  
  
2. В **выполнить этот набор правил** стрелку раскрывающегося списка выберите **все правила Майкрософт**.  
  
    Дополнительные сведения о доступных наборах правил см. в разделе [Справочник по набору правил анализа кода](../code-quality/code-analysis-rule-set-reference.md).  
  
    В меню «Файл» выберите **сохранить выбранные элементы** обновление файла проекта с информацию о выбранном наборе правил и его параметрах.  
  
   > [!TIP]
   > В реальной ситуации, использование приоритетов какие проблемы, вы будете работать с анализом кода рекомендуется начать с **минимальные рекомендуемые правила** набор правил и исправьте необходимые проблемы и затем постепенно добавлять Дополнительные правила или правило задает для нахождения и исправления дополнительные проблемы.  
  
   Далее добавим код в библиотеку классов, которая будет использоваться для демонстрации нарушений CA1704 «Идентификаторы должны иметь правильное правописание» правила анализа кода. Дополнительные сведения см. в разделе [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### <a name="add-your-own-code"></a>Добавьте свой код  
  
- В обозревателе решений откройте файл Class1.cs и замените существующий код следующим:  
  
  ```  
  using System;  
  using System.Collections.Generic;  
  using System.Text;  
  
  namespace RuleSetSample  
  {  
      public class Class1  
      {  
          //The variable parameter names "a" and "b" will cause  
          //the warning CA 1704 Microsoft.Naming "Consider   
          //providing a more meaningful name" to fire  
          public int AddIntegers(int a, int b)  
          {  
  
              int sum = a + b;  
  
              return (sum);  
          }  
      }  
  }  
  
  ```  
  
  Теперь можно запустить анализ кода для проекта Пример_набора_правил и найдите все ошибки и предупреждения, созданные в окне списка ошибок.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Запустить анализ кода для проекта Пример_набора_правил  
  
1. На **анализ** меню, щелкните **запустить анализ кода на Пример_набора_правил**.  
  
2. В окне «Список ошибок» щелкните **предупреждения** и нажмите кнопку **описание** заголовок столбца для сортировки предупреждений буквенно-цифровом порядке.  
  
    В реальном приложении бы исправить любые нарушения правил, требующая исправления на этом этапе, или при необходимости отключите или подавления правила в том случае, если определено, что она не требующая исправления. Дополнительные сведения см. в разделе [Подавление предупреждений при помощи атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3. Обратите внимание на предупреждения CA1704. Эти нарушения этого правила указывают, что вы должны «подберите более значимое имя для параметров.» Удалось устранить проблему в коде или отключить правило, как описано в следующей процедуре.  
  
   Далее надо настроить правило, задать, чтобы исключить предупреждение CA1704:, «Идентификаторы должны иметь правильное правописание».  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Настройка набора правил для проекта, чтобы отключить определенное правило  
  
1. На **анализ** меню, щелкните **Настройка анализа кода для Пример_набора_правил**.  
  
2. В **выполнить этот набор правил** выберите в раскрывающемся списке, убедитесь, что **все правила Майкрософт** правила, по-прежнему выбран набор, а затем нажмите кнопку **откройте**. Отображается страница набора правил.  
  
3. Разверните узел категории Microsoft.Naming и выберите предупреждение CA1704.  
  
4. В разделе **действие** столбец, выберите **None.** Это предотвращает CA1704 отображении в виде предупреждения или ошибки в окне списка ошибок.  
  
    Теперь будет подходящий момент, чтобы поэкспериментировать с различными кнопками панели инструментов и параметры, чтобы ознакомиться с их фильтрации. Например, можно использовать **Group By** стрелку раскрывающегося списка, чтобы найти определенные правила или категории правил. Другой пример —, которые можно использовать **Скрыть отключенные правила** кнопку в страницах наборов правил Чтобы скрыть или отобразить все правила с **действие** столбец значение **None**. Это может быть полезно в том случае, если вы хотите найти все правила, которые вы отключали функцию, чтобы убедиться, что по-прежнему требуется, чтобы их отключить.  
  
5. В меню «Вид» щелкните окно "Свойства". Тип **Мой настраиваемый набор правил** в поле "имя" Свойства окна инструментов. Это изменяет отображаемое имя набора правил в [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] интегрированной среды разработки.  
  
6. На **файл** меню, щелкните **сохранить все Rules.ruleset Microsoft** чтобы сохранить настраиваемые правила набор. Перейдите в корневую папку проекта. В **имя файла** текстовое поле, тип **"Мой_настраиваемый_набор_правил"** . Теперь можно одновременно выбрать настраиваемый набор правил для использования с проектом.  
  
   Благодаря создан новый набор правил теперь вам нужно настроить параметры проекта, чтобы указать, что вы хотите использовать набор с ним.  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Укажите новый набор правил для использования с проектом  
  
1. В обозревателе решений щелкните правой кнопкой мыши проект и выберите **свойства**.  
  
2. В **свойства** щелкните **анализа кода**.  
  
    В **выполнить этот набор правил** стрелку раскрывающегося списка, щелкните  **\<Обзор... >** . Перейдите в корневую папку проекта кода, а затем выберите **MyCustomRuleSet.ruleset**. Это новый набор правил, созданный в предыдущей процедуре.  
  
3. На **файл** меню, щелкните **Сохранить** чтобы сохранить конфигурацию проекта. Теперь настраиваемый набор правил можно использовать с проектом.  
  
   Наконец будет выполняться снова с помощью правил Мой_настраиваемый_набор_правил анализа кода. Обратите внимание на то, что окно списка ошибок не отображает нарушение правила производительности CA1704.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Запустить анализ кода для проекта Пример_набора_правил во второй раз  
  
1. На **анализ** меню, щелкните **запустить анализ кода на Пример_набора_правил**.  
  
2. В окне списка ошибок, обратите внимание, что при нажатии кнопки **предупреждения**, больше нет нарушений предупреждения CA1704 для правила «Идентификаторы должны иметь правильное правописание».  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Справочник по набору правил анализа кода](../code-quality/code-analysis-rule-set-reference.md)
