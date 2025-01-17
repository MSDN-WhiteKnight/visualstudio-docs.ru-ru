---
title: Страница "Службы" в конструкторе проектов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2ee4201871830a3bb1b9f14c47e9d11bbc4d83fc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689552"
---
# <a name="services-page-project-designer"></a>Страница "Службы" в конструкторе проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Службы клиентских приложений предоставляют упрощенный доступ к службам входа, ролей и профилей [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] из приложений Windows Forms и Windows Presentation Foundation (WPF). Вы можете использовать страницу **Службы** **конструктора проектов**, чтобы включать и настраивать службы клиентских приложений для своего проекта.  
  
 Благодаря службам клиентских приложений можно использовать централизованный сервер для проверки подлинности пользователей, определения ролей, назначенных каждому из пользователей, а также хранения индивидуальных параметров приложений, которые можно совместно использовать в рамках всей сети. Дополнительные сведения см. в разделе [Службы клиентских приложений](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Чтобы открыть страницу **Службы**, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. Когда откроется окно **Конструктор проектов**, перейдите на вкладку **Службы**.  
  
> [!NOTE]
> Для служб клиентских приложений требуется полная версия .NET Framework, и они не поддерживаются в клиентском профиле .NET Framework. Если флажок **Включить службы клиентского приложения** снят, убедитесь, что **Целевая рабочая среда** имеет значение .NET Framework 3.5 или более поздней версии. Чтобы просмотреть значение параметра **Целевая рабочая среда** в C#, откройте конструктор проектов и щелкните страницу **Приложение**. Чтобы просмотреть значение параметра **Целевая рабочая среда** в Visual Basic, откройте конструктор проектов, щелкните страницу **Компиляция** и выберите **Дополнительные параметры компиляции**.  
  
## <a name="task-list"></a>список задач  
 [Практическое руководство. Настройка служб клиентских приложений](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Конфигурация**  
 Этот элемент управления нельзя изменить на этой странице. Описание этого элемента управления см. в разделе [Страница "Компиляция" в конструкторе проектов (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) или [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Платформа**  
 Этот элемент управления нельзя изменить на этой странице. Описание этого элемента управления см. в разделе [Страница "Компиляция" в конструкторе проектов (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) или [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Включить службы клиентских приложений**  
 Выберите, чтобы включить службы клиентских приложений. Требуется указать расположения служб на странице **Службы**, чтобы использовать службы клиентских приложений.  
  
 **Использование проверки подлинности Windows**  
 Указывает, что поставщик проверки подлинности будет использовать проверку подлинности Windows, то есть удостоверение, предоставленное операционной системой Windows.  
  
 **Использовать проверку подлинности с помощью форм**  
 Указывает, что поставщик проверки подлинности будет использовать проверку подлинности с помощью форм. Это означает, что приложение должно предоставить пользовательский интерфейс для входа. Дополнительные сведения см. в разделе [Практическое руководство. Реализация входа пользователя с помощью служб клиентских приложений](https://msdn.microsoft.com/library/5431a671-eb02-4e18-a651-24764fccec9a).  
  
 **Местонахождение службы аутентификации**  
 Используется только для проверки подлинности на основе форм. Задает расположение службы проверки подлинности.  
  
 **Дополнительно. Поставщик учетных данных**  
 Используется только для проверки подлинности на основе форм. Указывает реализацию <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>, которую служба аутентификации будет использовать для вывода диалогового окна входа в систему, если приложение вызывает метод `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> и передает пустые строки или `null` в качестве параметров. Если оставить это поле пустым, необходимо передать допустимое имя пользователя и пароль в метод <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. Поставщиков учетных данных следует задать как имя типа с указанием сборки. Дополнительные сведения см. в разделах <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> и [Имена сборок](https://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e). В простейшем виде имя типа сборки выглядит примерно так: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Местонахождение службы ролей**  
 Указывает расположение службы ролей.  
  
 **Местонахождение службы веб-параметров**  
 Указывает расположение службы профилей (веб-параметры).  
  
 **Дополнительно**  
 Открывает диалоговое окно [Дополнительные параметры служб](../../ide/reference/advanced-settings-for-services-dialog-box.md), с помощью которого можно переопределить поведение по умолчанию. Например, с его помощью можно задать базу данных для автономного хранилища вместо использования локальной файловой системы. Дополнительные сведения см. в разделе [Расширенные параметры для диалогового окна служб](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>См. также  
 [Службы клиентских приложений](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Диалоговое окно "Дополнительные параметры служб"](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Практическое руководство. Настройка служб клиентских приложений](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Страница "Компиляция" в конструкторе проектов (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md)   
 [Знакомство с конструктором проектов](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)
