---
title: Модульное тестирование
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5682d752ba2c1430d8ab708e3dadda754a1ba757
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461385"
---
# <a name="unit-test-your-code"></a>Модульное тестирование кода

Модульные тесты позволяют разработчикам и тест-инженерам быстро искать логические ошибки в методах классов для проектов на языках C#, Visual Basic и C++.

Средства модульных тестов включают:

* **Обозреватель тестов**&mdash;Вы можете запускать модульные тесты и просматривать их результаты с помощью **обозревателя тестов**. Вы можете использовать любые тестовые платформы, в том числе сторонние платформы, которые имеют адаптер для **обозревателя тестов**.

* **Платформа модульного тестирования Майкрософт для управляемого кода**&mdash;Платформа для тестирования Майкрософт для управляемого кода устанавливается с Visual Studio и предоставляет среду для тестирования кода в .NET.

* **Платформа модульного тестирования Майкрософт для C++**&mdash;Платформа модульного тестирования Майкрософт для C++ устанавливается в составе рабочей нагрузки **Разработка классических приложений на C++**. Эта платформа обеспечивает тестирование машинного кода. Вдобавок включаются платформы Google Test, Boost.Test и CTest, а также сторонние адаптеры для дополнительных платформ тестирования. Дополнительные сведения см. в статье [Создание модульных тестов для C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Инструменты покрытия кода**&mdash;Можно определить объем кода продукта, который покрывают модульные тесты, при помощи одной команды в обозревателе тестов.

* **Платформа изоляции Microsoft Fakes**&mdash;Границы изоляции Microsoft Fakes могут создать постановочные классы и методы для рабочего кода и систем, которые создают зависимости в тестируемом коде. Путем реализации подставных делегатов для функции можно контролировать поведение и возвращаемые значения объекта зависимости.

Кроме того, можно использовать компонент [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md), чтобы изучить код .NET и создать тестовые данные и набор модульных тестов. Для каждого оператора в коде создаются входные данные теста, которые будут выполнять этот оператор. Анализ случая выполняется для каждой условной ветви в коде.

## <a name="key-tasks"></a>Ключевые задачи

Следующие разделы помогут в понимании и создании модульных тестов.

|Задачи|Связанные разделы|
|-|-----------------------|
|**Краткие и пошаговые руководства**. Здесь можно изучить модульное тестирование в Visual Studio на конкретных примерах кода.|- [Пошаговое руководство: создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Краткое руководство. Разработка на основе тестирования с помощью обозревателя тестов](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Практическое руководство. Добавление модульных тестов для приложений на C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Модульное тестирование с помощью обозревателя тестов**. Узнайте, как с помощью обозревателя тестов создавать более производительные и более эффективные модульные тесты.|- [Основные сведения о модульных тестах](../test/unit-test-basics.md)<br />- [Create a unit test project](../test/create-a-unit-test-project.md) (Создание проекта модульного теста)<br />- [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)<br />- [Install third-party unit test frameworks](../test/install-third-party-unit-test-frameworks.md) (Установка платформ модульного тестирования сторонних поставщиков)|
|**Модульное тестирование кода C++**|- [Написание модульных тестов для C и C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Изоляция модульных тестов**|- [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Использование покрытия кода для определения того, какая часть кода проекта тестируется**. Изучите возможности покрытия кода, которые предоставляют средства тестирования Visual Studio.|- [Использование параметра объема протестированного кода для определения объема протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Анализ нагрузки и производительности с помощью нагрузочных тестов**. Вы можете создать нагрузочные тесты, чтобы выявить проблемы с нагрузкой и производительностью в приложении.|- [Краткое руководство. Создание проекта нагрузочного тестирования](../test/quickstart-create-a-load-test-project.md).<br />- [Нагрузочное тестирование (Azure Test Plans и TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Установка системы контроля качества**. Вы можете создать систему контроля качества, чтобы выполнять тесты перед сохранением или объединением кода.|- [Политики возврата (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Задание параметров тестирования**. Сведения о настройке параметров теста, например места, где хранятся результаты теста.|[Настройка модульных тестов с помощью файла .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Справочная документация по API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> описывает пространство имен UnitTesting, предоставляющего атрибуты, исключения, утверждения и другие классы, поддерживающие модульное тестирование.
- В <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> описано пространство имен UnitTesting.Web, расширяющее пространство имен UnitTesting за счет поддержки ASP.NET и модульных тестов веб-службы.

## <a name="see-also"></a>См. также

- [Улучшение качества кода](../test/improve-code-quality.md)
