---
title: -Command (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a87be2f0b60b02588b5ba73e5837caca1b4bd8ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685847"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Выполняет заданную команду после запуска интегрированной среды разработки (IDE) [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Аргументы  
 `CommandName`  
 Обязательный. Полное имя команды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] или ее псевдоним, заключенные в двойные кавычки. Дополнительные сведения о синтаксисе команд и псевдонимов см. в разделе [Команды Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Примечания  
 После завершения запуска интегрированная среда разработки выполняет именованную команду. При использовании этого параметра среда IDE не отображает начальную страницу [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] при запуске.  
  
 Если надстройка предоставляет команду, этот параметр можно использовать для запуска надстройки из командной строки. Дополнительные сведения см. в разделе [Практическое руководство. Управление надстройками с помощью диспетчера надстроек](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Пример  
 В данном примере запускается [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и автоматически выполняется макрос Open Favorite Files.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
