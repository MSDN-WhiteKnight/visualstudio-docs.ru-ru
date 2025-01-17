---
title: Практическое руководство. Создание и изменение конфигураций | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 35cda86854bede07c8f1d4830f05607b7fab3643
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680415"
---
# <a name="how-to-create-and-edit-configurations"></a>Практическое руководство. Создание и изменение конфигураций
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете создать несколько конфигураций сборки для решения. Например, можно настроить отладочную сборку, которую ваши тест-инженеры могут использовать для поиска и устранения неполадок, или настроить разные типы сборок, которые можно передавать разным клиентам.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-build-configurations"></a>Создание конфигураций сборки  
 Диалоговое окно **Диспетчер конфигураций** служит для выбора или изменения существующих конфигураций сборки, а также для создания новых.  
  
#### <a name="to-open-the-configuration-manager-dialog-box"></a>Открытие диалогового окна "Диспетчер конфигураций"  
  
- В **обозревателе решений** откройте контекстное меню для решения и выберите пункт **Диспетчер конфигураций**.  
  
  > [!NOTE]
  > Если пункт **Диспетчер конфигураций** не отображается в контекстном меню, он должен отображаться в меню **Сборка** в строке меню. Если его нет в обоих меню, в строке меню выберите **Сервис**, **Параметры**, а затем в левой области диалогового окна **Параметры** разверните узел **Проекты и решения**, **Общие** и в области справа установите флажок **Показывать дополнительные конфигурации построения**.  
  
   В диалоговом окне **Диспетчер конфигураций** в раскрывающемся списке **Активная конфигурация решения** можно выбрать конфигурацию сборки для всего решения, изменить существующую или создать новую конфигурацию. Раскрывающийся список **Активная платформа решения** можно использовать для выбора платформы, для которой предназначена конфигурация, или для добавления новой платформы. В области **Конфигурации проектов** перечислены все проекты в решении. Для каждого проекта можно выбрать конфигурацию и платформу проекта, изменить уже существующую или создать новую конфигурацию или добавить новую платформу. Кроме того, можно установить флажки, которые указывают, включается ли конкретный проект при использовании конфигурации на уровне решения для сборки или развертывания решения.  
  
  После настройки необходимых конфигураций можно задать свойства проекта, которые подходят для этих конфигураций.  
  
#### <a name="to-set-properties-based-on-configurations"></a>Задание свойств на основе конфигураций  
  
- В **обозревателе решений** откройте контекстное меню для проекта и выберите пункт **Свойства**.  
  
     Откроется окно **Страницы свойств**.  
  
     Можно задать свойства для конфигураций. Например, для конфигурации выпуска можно задать оптимизацию кода при сборке решения, а для конфигурации отладки — указать, что включен символ условной компиляции `DEBUG`. См. подробнее о параметрах страницы свойств в статье [Знакомство с конструктором проектов](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## <a name="creating-and-modifying-project-configurations"></a>Создание и изменение конфигураций проектов  
  
#### <a name="to-create-a-project-configuration"></a>Создание конфигурации проекта  
  
1. Откройте диалоговое окно **Диспетчер конфигураций**.  
  
2. Выберите проект в столбце **Проект**.  
  
3. В раскрывающемся списке **Конфигурация** для этого проекта выберите **Создать**.  
  
     Откроется диалоговое окно **Создание конфигурации проекта**.  
  
4. В поле **Имя** введите имя новой конфигурации.  
  
5. Чтобы использовать значения свойств из существующей конфигурации проекта, в раскрывающемся списке **Копировать параметры из** выберите конфигурацию.  
  
6. Чтобы одновременно создать конфигурацию на уровне решения, установите флажок **Создать новую конфигурацию решения**.  
  
#### <a name="to-rename-a-project-configuration"></a>Переименование конфигурации проекта  
  
1. Откройте диалоговое окно **Диспетчер конфигураций**.  
  
2. В столбце **Проект** выберите проект, который содержит нужную конфигурацию проекта.  
  
3. В раскрывающемся списке **Конфигурация** для этого проекта выберите **Изменить**.  
  
     Откроется диалоговое окно **Изменение конфигураций проекта**.  
  
4. Выберите имя конфигурации проекта, которую требуется изменить.  
  
5. Выберите **Переименовать**, а затем введите новое имя.  
  
## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Создание и изменение конфигураций сборки на уровне решения  
  
#### <a name="to-create-a-solution-wide-build-configuration"></a>Создание конфигурации сборки на уровне решения  
  
1. Откройте диалоговое окно **Диспетчер конфигураций**.  
  
2. В раскрывающемся списке **Активная конфигурация решения** выберите **Создать**.  
  
     Откроется диалоговое окно **Создание конфигурации решения**.  
  
3. В текстовом поле **Имя** введите имя новой конфигурации.  
  
4. Чтобы использовать параметры из существующей конфигурации решения, в раскрывающемся списке **Копировать параметры из** выберите конфигурацию.  
  
5. Если вы хотите одновременно создать конфигурации проекта, установите флажок **Создать новые конфигурации проекта**.  
  
#### <a name="to-rename-a-solution-wide-build-configuration"></a>Переименование конфигурации сборки на уровне решения  
  
1. Откройте диалоговое окно **Диспетчер конфигураций**.  
  
2. В раскрывающемся списке **Активная конфигурация решения** выберите **Изменить**.  
  
     Откроется диалоговое окно **Изменение конфигураций решения**.  
  
3. Выберите имя конфигурации решения, которую требуется изменить.  
  
4. Выберите **Переименовать**, а затем введите новое имя.  
  
#### <a name="to-modify-a-solution-wide-build-configuration"></a>Изменение конфигурации сборки на уровне решения  
  
1. Откройте диалоговое окно **Диспетчер конфигураций**.  
  
2. В раскрывающемся списке **Активная конфигурация решения** выберите нужную конфигурацию.  
  
3. В области **Конфигурации проектов** для каждого проекта выберите нужную **конфигурацию** и **платформу**, а также выберите, требуется ли выполнять его **сборку** и **развертывание**.  
  
## <a name="see-also"></a>См. также раздел  
 [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)   
 [Building and Cleaning Projects and Solutions in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)  (Построение и очистка проектов и решений в Visual Studio)  
 [NIB. Практическое руководство. Изменение свойств проекта и параметров конфигурации](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
