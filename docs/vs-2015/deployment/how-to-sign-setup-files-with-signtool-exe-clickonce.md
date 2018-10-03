---
title: 'Практическое: входа файлов установки с помощью SignTool.exe (ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ad234b1c21030032428265e9c03528a165cba8c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571462"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Практическое руководство. Подписывание файлов установки с помощью программы SignTool.exe (ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: подписывание файлов установки с SignTool.exe (ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/how-to-sign-setup-files-with-signtool-exe-clickonce).  
  
Чтобы подписать программу установки (setup.exe), можно использовать SignTool.exe. Этот процесс позволяет проверить, не установлены ли на компьютер конечного пользователя измененные злоумышленниками файлы.  
  
 По умолчанию ClickOnce включает подписанные манифесты и подписанную программу установки. Если вы собираетесь изменить параметры программы установки в дальнейшем, ее следует подписать позже. Если вы измените параметры после того, как программа установки будет подписана, подпись будет повреждена.  
  
 В ходе описанной ниже процедуры генерируются неподписанные манифесты и неподписанная программа установки. После этого в Visual Studio станет доступна процедура подписи приложений ClickOnce, позволяющая сгенерировать подписанные манифесты. Программа установки остается неподписанной, чтобы клиент смог подписать исполняемый файл своим собственным сертификатом.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Генерирование неподписанной программы установки и ее последующая подпись  
  
1.  На компьютере разработчика установите сертификат для подписи манифестов.  
  
2.  Выберите проект в **обозревателе решений**.  
  
3.  На **проекта** меню, щелкните *имя_проекта* **свойства**.  
  
4.  В **подписывание** странице снимите **подписать манифесты ClickOnce**.  
  
5.  В **публикации** щелкните **предварительные требования**.  
  
6.  Убедитесь, что выбраны все необходимые компоненты и нажмите кнопку **ОК**.  
  
7.  В **публикации** странице, проверьте настройки публикации и нажмите кнопку **Опубликовать сейчас**.  
  
     Решение опубликует неподписанный манифест приложения, неподписанный манифест развертывания, файлы конкретной версии и неподписанную программу установки в расположение папки для публикации.  
  
8.  В **публикации** щелкните **предварительные требования**.  
  
9. В **предварительные требования** снимите флажок **создать программу установки для необходимых компонентов**.  
  
10. В **публикации** странице, проверьте настройки публикации и нажмите кнопку **Опубликовать сейчас**.  
  
     Решение опубликует подписанный манифест приложения, подписанный манифест развертывания и файлы конкретной версии в расположение папки для публикации. Неподписанная программа установки в процессе публикации не переписывается.  
  
11. На сайте клиента откройте командную строку.  
  
12. Перейдите в каталог, содержащий файл .EXE.  
  
13. Введите следующую команду, чтобы подписать файл .EXE:  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Например, для подписи программы установки используются следующие команды:  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md)


