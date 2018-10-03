---
title: Изменение изолированной оболочки с помощью. Файл Vsct | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0606d28f151f0d9c85980121e3129bd9204c61b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573060"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Изменение изолированной оболочки с помощью. Файл Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [изменение изолированной оболочки с помощью. Файл Vsct](https://docs.microsoft.com/visualstudio/extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file).  
  
Проект пользовательского интерфейса для проекта изолированной оболочки Visual Studio содержит vsct-файл, который позволяет указать, какие группы приложений и отдельных команд доступны в приложении. Ниже приведен отрывок из файла .vsct без изменений.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 По умолчанию включены большинство команд и группы команд. Чтобы исключить команды или группы команд, просто удалите комментарий этого команды или группы.  
  
 Например, чтобы удалить область следующего и предыдущего панели команд, раскомментируйте `No_PaneNextPaneCommand` и `No_PanePrevPaneCommand` записи:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Более подробный пример эти настройки, см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Файлы, на которую указывает ссылка  
 Vsct-файл по умолчанию, для приложения ссылается на следующие файлы. Эти файлы расположены в подкаталоге \VisualStudioIntegration\Common\Inc\ каталога установки Visual Studio SDK.  
  
|Файл|Описание|  
|----------|-----------------|  
|wbids.h|Удостоверения пользовательского интерфейса для пакета Обзор Web.|  
|AppIDCmdUsed.vsct|Таблицы команд для основных элементов пользовательского интерфейса Visual Studio.|  
|EmulatorCmdUsed.vsct|Таблицы команд для Emacs и краткое описание элементов пользовательского интерфейса эмуляции редактора.|  
|Vsdebugguids.h|Определяет идентификаторы GUID команды, страница "Параметры" и другие функции отладчика Visual Studio.|  
|VsDbgCmdUsed.vsct|Таблицы команд отладчика.|  
  
 Файл AppIDCmdUsed.vsct включает в себя элементы пользовательского интерфейса Visual Studio на основании символов, определенных в vsct-файл приложения.  
  
 Дополнительные сведения см. в разделе [проектирование таблицы команд XML (. Файлы Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) и [Справочник по схемам VSCT XML](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)
