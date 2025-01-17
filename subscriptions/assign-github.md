---
title: Пакет Visual Studio с GitHub | Документация Майкрософт
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/23/2019
ms.topic: conceptual
description: Управление подписками в пакете Visual Studio с GitHub
searchscope: VS Subscription
ms.openlocfilehash: a775317029db1a2be3b01411955ae197c7df6873
ms.sourcegitcommit: bd519d1da375e374016f94a44c295d3253f61a8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945243"
---
# <a name="managing-visual-studio-subscriptions-with-github-enterprise"></a>Управление подписками Visual Studio с GitHub Enterprise

Клиенты, заключившие с корпорацией Майкрософт соглашения Enterprise (EA), имеют право приобрести новый пакет, в котором объединены стандартные подписки Visual Studio и подписки GitHub Enterprise. Таким образом, подписчики Visual Studio смогут снизить затраты на приобретение GitHub Enterprise. 

Управление подписками Visual Studio с GitHub Enterprise, которые приобретает ваша организация, осуществляется в два этапа.

## <a name="managing-visual-studio-subscriptions"></a>Управление подписками Visual Studio

Если ваша организация приобрела подписки Visual Studio с GitHub Enterprise, относящаяся к Visual Studio часть подписки предоставляется незамедлительно, а подписки становятся доступны для назначения и управления на [портале администрирования подписок](https://manage.visualstudio.com) Visual Studio. 

Дополнительные сведения об управлении подписками см. в следующих разделах:
- [Использование портала администрирования](using-admin-portal.md)
- [Назначение подписок](assign-license.md)
- [Изменение подписок](edit-license.md)
- [Удаление подписок](delete-license.md)
- [Превышение доступности](handle-overclaimed-license.md)

> [!Important]
> Подписки Visual Studio с GitHub Enterprise, которые назначены администраторами подписки Visual Studio и никогда не приобретались, не будут видны администраторам GitHub Enterprise в организации. Чтобы отображать подписки GitHub Enterprise, при первичном назначении подписки необходимо совершить покупку, включающую **как минимум одну** подписку Visual Studio Professional с GitHub Enterprise или Visual Studio Enterprise с GitHub Enterprise.  
>
> В целях соблюдения требований лицензионных соглашений в отношении подписки клиент отвечает за проверку того, что для каждой назначенной таким образом подписки GitHub присутствует соответствующая подписка Visual Studio с GitHub, назначенная на портале управления.

## <a name="managing-github-enterprise-subscriptions"></a>Управление подписками GitHub Enterprise

При приобретении подписок GitHub Enterprise клиенты получают со стороны GitHub помощь в создании и настройке организаций, которые будут получать доступ к GitHub, а также в определении администраторов.  Пользователи, назначенные в качестве администраторов, получат соответствующие уведомления.  

Из-за более высокой сложности процесса полная настройка организаций и администраторов может занимать несколько дней с момента приобретения подписок.

Доступ к GitHub реализуется посредством облака через веб-сайт GitHub.com или с помощью локального сервера GitHub Enterprise Server.  Процессы управления для этих двух версий различаются.  GitHub предлагает множество разделов справки и руководств для администраторов, посвященных управлению подписками GitHub Enterprise.  Ссылки на некоторые из этих ресурсов приводятся ниже.  

### <a name="githubspanspancom"></a>GitHub<span></span>.com 

Дополнительные сведения об управлении на веб-сайте GitHub<span></span>.com см. в следующих разделах [справки по GitHub](https://help.github.com/en).
- [Полный список разделов справки](https://help.github.com/en)
- [Управление членством в вашей организации](https://help.github.com/en/articles/managing-membership-in-your-organization)
> - [Отправка пользователям приглашений присоединиться к вашей организации](https://help.github.com/en/articles/inviting-users-to-join-your-organization)
> - [Удаление пользователей из групп или организаций](https://help.github.com/en/articles/removing-a-member-from-your-organization)
> - [Восстановление бывшего члена вашей организации](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization)
- [Управление доступом на основе ролей](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles)
- [Объединение пользователей в группы](https://help.github.com/en/articles/organizing-members-into-teams)
- [Управление доступом к репозиториям вашей организации](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories)

### <a name="github-enterprise-server"></a>GitHub Enterprise Server

В справке по GitHub представлено множество руководств для администраторов, содержащих ответы на вопросы и рекомендации, которые связаны с управлением сервером GitHub Enterprise Server, внедренным в вашей организации.

- [Посмотреть все руководства для администраторов](https://help.github.com/en/enterprise/2.16/admin)
- [Управление пользователями](https://help.github.com/en/enterprise/2.16/admin/user-management)
> - [Организации и группы](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams)
> > - [Создание организаций](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations)
> > - [Создание групп](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams)
> > - [Добавление пользователей в группы](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams)
> > - [Удаление пользователей из групп и организаций](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations)
> - [Безопасность пользователя](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security)
- [Установка и настройка GitHub Enterprise Server](https://help.github.com/en/enterprise/2.16/admin/installation)


## <a name="support-resources"></a>Ресурсы поддержки
-  В [справке по GitHub](https://help.github.com/en) вы можете найти ответы на самые разные вопросы, связанные с GitHub.
-  Кроме того, вы можете воспользоваться помощью других пользователей GitHub, посетив [форум сообщества GitHub](https://github.community/).
-  По вопросам продаж, использования подписок, учетных записей и выставления счетов для подписок Visual Studio обратитесь в [службу поддержки подписок](https://visualstudio.microsoft.com/subscriptions/support/) Visual Studio.
-  У вас есть вопросы о Visual Studio IDE, Azure DevOps Services или других продуктах или службах Visual Studio?  Перейдите на [страницу поддержки Visual Studio](https://visualstudio.microsoft.com/support/).
-  Обратитесь в [службу технической поддержки](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) для GitHub Enterprise.   

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения об управлении подписками Visual Studio с GitHub Enterprise см. также на [портале администрирования подписок](https://visualstudio.microsoft.com/subscriptions-administration/) Visual Studio.