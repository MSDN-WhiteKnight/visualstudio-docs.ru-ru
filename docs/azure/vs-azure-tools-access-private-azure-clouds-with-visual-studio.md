---
title: Доступ к частным облакам Azure
description: Узнайте, как получить доступ к ресурсам частного облака с помощью Visual Studio.
author: ghogen
manager: jillfra
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 57226c032e20871baf36c97a8caede6907567bbf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140745"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Доступ к частным облакам Azure с помощью Visual Studio

По умолчанию Visual Studio поддерживает конечные точки REST облаков Azure. В этой статье вы узнаете, как использовать сертификат частного облака для доступа к частному облаку и взаимодействия с ним через Visual Studio.

1. Скачайте файл параметров публикации с портала Azure для частного облака или запросите этот файл у администратора. (Файл с расширением `.publishsettings`.)

1. В **обозревателе сервера** Visual Studio щелкните правой кнопкой мыши узел **Azure**, а затем выберите **Manage and Filter Subscriptions** (Управление подписками и их фильтрация).

    ![Команда "Управление подписками"](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. В диалоговом окне **Управление подписками Microsoft Azure** выберите вкладку **Сертификаты**, затем нажмите кнопку **Импорт**.

    ![Импорт сертификатов Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. В диалоговом окне **Импорт подписок Microsoft Azure** нажмите кнопку **Обзор**.

    ![Кнопка "Обзор" в диалоговом окне "Импорт подписок Microsoft Azure"](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. В диалоговом окне **Открытие** найдите каталог, в котором вы сохранили PUBLISHSETTINGS-файл, выберите его, а затем нажмите кнопку **Открыть**.

    ![Выбор PUBLISHSETTINGS-файла](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Вернувшись в диалоговое окно **Импорт подписок Microsoft Azure** нажмите кнопку **Импорт**.

    ![Импорт PUBLISHSETTINGS-файла](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Сертификаты импортируются из PUBLISHSETTINGS-файла в Visual Studio, и теперь вы можете работать с ресурсами частного облака.