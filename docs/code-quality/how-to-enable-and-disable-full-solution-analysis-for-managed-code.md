---
title: Включение и отключение полного анализа решения для управляемого кода
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a445439014e3b1f68b634865265089eb68e790a6
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260877"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Практическое руководство. Включение и отключение полного анализа решения для управляемого кода

*Полный анализ решения* — это компонент Visual Studio, позволяет просматривать проблемы анализа кода только в визуальном элементе откройте C# или файлов Visual Basic в решении или в файлах кода, которые были закрыты. По умолчанию — полный анализ решения *включена* в Visual Basic и *отключена* для визуального C#.

Его можно использовать для просмотра всех ошибок во всех файлах, но это также может быть отвлекает. Visual Studio завершает работу при решении очень большой или содержит большое количество файлов. Чтобы ограничить количество показано проблем и повышения производительности Visual Studio, можно отключить полный анализ решения. При необходимости, можно легко включить это средство.

## <a name="to-toggle-full-solution-analysis"></a>Чтобы включить полный анализ решения

1. Чтобы открыть **параметры** диалоговое окно, в строке меню в Visual Studio выберите **средства** > **параметры**.

1. В **параметры** диалоговое окно, выберите **текстовый редактор**  >  **C#** или **основные**  >  **Advanced**.

1. Выберите **включить полный анализ решения** флажок, чтобы включить полный анализ решения или снимите флажок, чтобы отключить его. Выберите **ОК** после завершения.

    ![Установите флажок analysis полное решение.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Результаты Включение и отключение полного анализа решения

На следующем снимке экрана вы увидите результаты при включении полный анализ решения. Все ошибки и проблемы анализа кода в *все* файлов в решении отображается, независимо от того, является ли файлы открыты или нет.

![Полный анализ решения включена.](../code-quality/media/fsa_enabled.png)

На следующем рисунке показан результаты из того же решения после отключения полный анализ решения. Только ошибки и проблемы анализа кода в файлах открытое решение появляются в **список ошибок**.

![Полный анализ решения отключена.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Автоматическое отключение полного анализа решения

Если Visual Studio обнаруживает, что 200 МБ или системной памяти доступен на него, он автоматически отключает полный анализ решения (и некоторые другие функции), если он включен. В этом случае появится предупреждение, информирующее о том, что Visual Studio отключила некоторые функции. Кнопка позволяет включить полный анализ решения, если требуется.

![Текст предупреждения, приостановка полный анализ решения](../code-quality/media/fsa_alert.png)