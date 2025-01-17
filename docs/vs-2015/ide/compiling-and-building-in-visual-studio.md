---
title: Компилирование и сборка
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bfee16abf522284471baf4c8dc8b3c47468a032e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701483"
---
# <a name="compiling-and-building-in-visual-studio"></a>Компиляция и сборка в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio можно использовать для построения приложений и создания сборок и исполняемых программ через короткие интервалы во время цикла разработки. Частой сборкой кода можно определить ошибки времени компиляции, например неверный синтаксис, неправильно писанные ключевые слова и несоответствия типов, раньше. Кроме того, вы можете найти и исправить ошибки во время выполнения, например логические и семантические ошибки, с помощью частой сборки и запуска отладочных версий кода.

 Когда у вас будет полностью доработанный и отлаженный проект или решение, вы сможете скомпилировать его компоненты в сборку выпуска. По умолчанию сборка выпуска оптимизирована и реализована так, чтобы быть меньше и быстрее, чем отладочная версия кода. Дополнительные сведения см. в разделе [Пошаговое руководство: сборка приложения](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Выбор метода построения
 Для создания приложения можно использовать заданные по умолчанию параметры построения в интегрированной среде разработки, командную строку или воспользоваться Team Foundation Build. В каждом их этих вариантов в качестве базовой технологии применяется MSBuild, и каждый подход имеет определенные преимущества, как показано в следующей таблице.

|Метод построения|Преимущества|Дополнительные сведения|
|------------------|--------------|--------------------------|
|Использование интегрированной среды разработки|— Можно легко создавать сборки и сразу же их выполнять.<br />— Можно выполнять многопроцессорные сборки для проектов C, C++ и C#.<br />— Можно настраивать некоторые области системы сборки.|[Построение и очистка проектов и решений в Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Запуск MSBuild из командной строки|— Можно создавать проекты без установки Visual Studio.<br />— Можно выполнять многопроцессорные сборки для всех типов проектов.<br />— Можно настраивать большинство областей системы сборки.|[MSBuild](../msbuild/msbuild.md)|
|Использование Team Foundation Build|— Можно автоматизировать процесс сборки. Например, можно создавать один или более проектов каждую ночь или всякий раз при возврате кода. Можно также собирать проекты на общих серверах сборки, а не только на компьютере разработчика.<br />— Можно быстро указывать код, который требуется создать, тесты, которые нужно выполнить, и другие общие параметры.<br />— Можно изменять рабочий процесс сборки и при необходимости создавать действия сборки для выполнения настраиваемых задач.|[Построение приложения](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|

## <a name="building-from-the-ide"></a>Создание в интегрированной среде разработки
 При создании проекта для него уже определены конфигурации сборок по умолчанию, и ему назначается конфигурация сборки решения для предоставления контекста для сборки. Конфигурации решения определяют способы сборки и развертывания проектов в решении. Конфигурации проектов — это набор свойств проектов, которые являются уникальными для типа платформы сборки (например, выпуск Win32). Эти заданные по умолчанию конфигурации можно редактировать. Можно также создавать собственные конфигурации. Дополнительные сведения см. в разделе [Знакомство с конструктором проектов](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) и [ПРАКТИЧЕСКОЕ руководство: Изменение свойств проекта и параметров конфигурации](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 В интегрированной среде разработки можно выполнять следующие дополнительные задачи.

- [Изменять выходной каталог сборки](../ide/how-to-change-the-build-output-directory.md).

- [Определять проекты, зависящие от выходных данных другого проекта, для правильного построения](../ide/how-to-create-and-remove-project-dependencies.md).

- [Изменять объем сведений, включенных в журнал сборки или окно вывода для сборок](../ide/how-to-view-save-and-configure-build-log-files.md).

- [Скрывать отдельные предупреждения компилятора для Visual C#, Visual C++ или Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

- [Указывать настраиваемые действия, выполняемые до и после компиляции](../ide/specifying-custom-build-events-in-visual-studio.md).

- Улучшить производительность построения с помощью параллельных сборок. Дополнительные сведения см. в статье [Параллельное построение нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) или в записи блога [Настройка параллелизма построения C++](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx).

## <a name="see-also"></a>См. также
 [Пошаговое руководство: Построение приложения](../ide/walkthrough-building-an-application.md) [основные сведения о конфигурации построения](../ide/understanding-build-configurations.md) [платформы построения понимание](../ide/understanding-build-platforms.md) [построение (компиляция) проектов веб-сайт](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [ Инструкции: Создание и удаление зависимостей проекта](../ide/how-to-create-and-remove-project-dependencies.md)
