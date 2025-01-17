---
title: Практическое руководство. Подписание приложения и манифесты развертывания | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: 61
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6dbcc6f74d39353ae38b7298851cb1bab5fb0fe0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685424"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Практическое руководство. Подписание приложения и манифесты развертывания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы хотите опубликовать приложение с помощью развертывания ClickOnce, манифесты приложения и развертывания должны быть подписаны парой из открытого и закрытого ключей с использованием технологии Authenticode. Манифесты можно подписать с помощью сертификата из хранилища сертификатов Windows или файла ключа.  
  
 Дополнительные сведения о развертывании ClickOnce см. в разделе [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
 Подписывание манифестов ClickOnce для приложений на базе EXE является необязательным. Дополнительные сведения см. в разделе "Создание неподписанных манифестов" этого документа.  
  
 Сведения о создании файлов ключей см. в статье [Практическое руководство. Создание пары открытого и закрытого ключей](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] поддерживает только файлы ключей для обмена личной информацией (PFX). Тем не менее, можно выбрать другие типы сертификатов из хранилища сертификатов текущего пользователя Windows, щелкнув **Выбрать из хранилища** на странице **Подписывание** свойств проекта.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>Подписывание манифестов развертывания и приложения с помощью сертификата  
  
1. Откройте окно свойств проекта (щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите пункт **Свойства** либо введите **свойства проекта** в окне **Быстрый запуск** либо нажмите клавиши ALT+ВВОД в **обозревателе решений**). На вкладке **Подписывание** установите флажок **Подписать манифесты ClickOnce**.  
  
2. Нажмите кнопку **Выбрать из хранилища**.  
  
     Появляется диалоговое окно **Выбор сертификата** с содержимым хранилища сертификатов Windows.  
  
    > [!TIP]
    > Если щелкнуть элемент **Щелкните здесь, чтобы просмотреть свойства сертификата**, открывается диалоговое окно **Сведения о сертификате**. Это диалоговое окно содержит подробные сведения о сертификате и дополнительные параметры. Можно щелкнуть элемент **Сертификаты** для просмотра дополнительных справочных сведений.  
  
3. Выберите сертификат, который хотите использовать для подписи манифестов.  
  
4. Кроме того, можно указать адрес сервера меток времени в текстовом поле **URL-адрес сервера меток времени**. Этот сервер предоставляет метку времени, указывающую, когда был подписан манифест.  
  
### <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Подписывание манифестов развертывания и приложения с помощью существующего файла ключа  
  
1. На странице **Подписывание** установите флажок **Подписать манифесты ClickOnce**.  
  
2. Нажмите кнопку **Выбрать из файла**.  
  
     Открывается диалоговое окно **Выбор файла**.  
  
3. В диалоговом окне **Выбор файла** найдите требуемый файл ключа (PFX) и нажмите кнопку **Открыть**.  
  
    > [!NOTE]
    > Этот параметр поддерживает только файлы с расширением PFX. При наличии файла ключа или сертификата в другом формате сохраните его в хранилище сертификатов Windows и выберите сертификат, описанный в предыдущей процедуре. Назначение выбранного сертификата должно включать в себя подписывание кода.  
  
     Отображается диалоговое окно **Ввод пароля для открытия файла**. (Если PFX-файл уже находится в хранилище сертификатов Windows или не защищен паролем, вы не получите запрос на ввод пароля.)  
  
4. Введите пароль для доступа к файлу ключа и нажмите клавишу ВВОД.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Подписывание манифестов развертывания и приложения с помощью тестового сертификата  
  
1. На странице **Подписывание** установите флажок **Подписать манифесты ClickOnce**.  
  
2. Чтобы создать сертификат для тестирования, нажмите кнопку **Создание тестового сертификата**.  
  
3. В диалоговом окне **Создание тестового сертификата** введите пароль для защиты тестового сертификата.  
  
## <a name="generating-unsigned-manifests"></a>Создание неподписанных манифестов  
 Подписывание манифестов ClickOnce для приложений на базе EXE является необязательным. Следующие процедуры демонстрируют создание неподписанных манифестов ClickOnce.  
  
> [!IMPORTANT]
> Неподписанные манифесты позволяют упростить разработку и тестирование приложения. Однако неподписанные манифесты представляют большую угрозу безопасности в рабочей среде. Используйте неподписанные манифесты, только если приложение ClickOnce выполняется на компьютерах в интрасети, которая полностью изолирована от Интернета или других источников вредоносного кода.  
  
 По умолчанию ClickOnce автоматически создает подписанные манифесты, если только один или несколько файлов специально не исключаются из создаваемого хэша. Другими словами, публикация приложения дает подписанные манифесты, если все файлы включены в хэш, даже если флажок **Подписать манифесты ClickOnce** снят.  
  
#### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Создание неподписанных манифестов и включение всех файлов в создаваемый хэш  
  
1. Для создания неподписанных манифестов, которые включают все файлы в хэш, нужно сначала опубликовать приложение вместе с подписанными манифестами. Таким образом, сначала подпишите манифесты ClickOnce, выполнив одну из предыдущих процедур, а затем опубликуйте приложение.  
  
2. На странице **Подписывание** снимите флажок **Подписать манифесты ClickOnce**.  
  
3. Выполните сброс версии публикации, чтобы доступной была только одна версия приложения. По умолчанию Visual Studio автоматически увеличивает номер редакции для версии публикации при каждой публикации приложения. Дополнительные сведения см. в разделе [Практическое руководство. Установка ClickOnce версии публикации](../deployment/how-to-set-the-clickonce-publish-version.md).  
  
4. Опубликуйте приложение.  
  
#### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Создание неподписанных манифестов и исключение одного или нескольких файлов из создаваемого хэша  
  
1. На странице **Подписывание** снимите флажок **Подписать манифесты ClickOnce**.  
  
2. Откройте диалоговое окно **Файлы приложения** и присвойте параметру **Хэш** значение **Исключить** для файлов, которые требуется исключить из создаваемого хэша.  
  
    > [!NOTE]
    > Исключение файла из хэша настраивает ClickOnce на отключение автоматической подписи манифестов, поэтому вам не нужно сначала публиковать приложение с подписанными манифестами, как описано в предыдущей процедуре.  
  
3. Опубликуйте приложение.  
  
## <a name="see-also"></a>См. также  
 [Сборки со строгими именами](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Практическое руководство. Создание пары открытого и закрытого ключей](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)   
 [Страница "Подписывание" в конструкторе проектов](../ide/reference/signing-page-project-designer.md)   
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)
