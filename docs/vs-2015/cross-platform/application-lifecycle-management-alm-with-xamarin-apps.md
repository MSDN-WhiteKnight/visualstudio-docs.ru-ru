---
title: Управление жизненным циклом приложений (ALM) для приложений Xamarin | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: 258b9fcb8b36be1d179d9f907ef2da16ff1c3037
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696253"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Управление жизненным циклом приложений (ALM) для приложений Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Платформа Xamarin позволяет создавать кроссплатформенные мобильные приложения, предназначенные для Android, iOS и Windows, с помощью C#, .NET и Visual Studio. Платформа Xamarin дает возможность совместного использования большей части кода разными платформами, при этом лишь небольшая его часть должна соответствовать конкретной платформе. Дополнительные сведения о самой платформе Xamarin см. в разделе [Visual Studio и Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Разработка приложений для современных платформ включает гораздо больше, чем просто написание кода. Эти действия, называемые DevOps (разработка + операции), охватывают весь жизненный цикл приложения и включают планирование и отслеживание работы, проектирование и реализацию кода, управление репозиторием исходного кода, выполнение сборок, управление непрерывной интеграцией и развертываниями, тестирование (включая модульные тесты и тесты пользовательского интерфейса), выполнение всевозможной диагностики в средах разработки и рабочих средах и отслеживание производительности приложения и поведения пользователей в режиме реального времени с помощью телеметрии и анализа.  
  
 Visual Studio (совместно с Visual Studio Team Services и Team Foundation Server) предоставляет широкий набор возможностей DevOps (которое также называется "управлением жизненным циклом приложений", или ALM). Многие из функций набора полностью применимы к кроссплатформенным проектам.  
  
 Это особенно справедливо в отношении приложений Xamarin, так как они создаются с помощью C# и .NET, на которых также основаны некоторые средства ALM. Другие средства требуют тесной интеграции со средами сборки и выполнения. Поскольку приложения Xamarin выполняются в платформах, отличных от Windows, и используют реализацию Mono среды .NET, Xamarin предоставляет специальные средства для определенных потребностей.  
  
 В таблицах ниже указано, какие возможности Visual Studio ALM будут эффективно работать в проекте Xamarin, а какие имеют ограничения. Дополнительные сведения о самих функциях см. в документации по ссылкам.  
  
## <a name="agile-tools"></a>Средства Agile  
 Ссылка для справки: **[Рабочие](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)**  (с помощью Visual Studio Team Services или TFS, включая Team Explorer Everywhere)  
  
 Общий комментарий: все возможности планирования и отслеживания не зависят от типа проекта и языков программирования.  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|Управление невыполненной работой и спринтами|Да||  
|Отслеживание трудозатрат|Да||  
|Совместная работа в комнате команды|Да||  
|Канбан-доски|Да||  
|Визуализация хода выполнения и отчеты о ходе выполнения|Да||  
  
## <a name="modeling"></a>Моделирование  
 Ссылка для справки: **[Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)**  
  
 Функции разработки не зависят от языка программирования или работы с языками .NET, такими как C#. Аспекты, связанные с кодом, описаны в статье [Роли архитектуры и схем моделирования в разработке программного обеспечения](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools).  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|Схемы последовательностей|Да||  
|Графы зависимости|Да||  
|Иерархия вызовов|Да||  
|Конструктор классов|Да||  
|Обозреватель архитектуры|Да||  
|UML-схемы (вариант использования, действие, класс, компонент, последовательность и DSL)|Да||  
|Схемы слоев|Да||  
|Проверка слоев|Да||  
  
## <a name="code"></a>Код  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|[Используйте управление версиями в Team Foundation](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) или Visual Studio Team Services|Да||  
|[Приступая к работе с Git в Team Services](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Да||  
|[Анализ кода/повышение качества кода (ссылки, предлагаемые изменения и т. д.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Да||  
|[Поиск изменений кода и других журналов](../ide/find-code-changes-and-other-history-with-codelens.md)|Да|Кроме выхода за границы конкретной платформы, где реализация не разрешается до времени выполнения.|  
|[Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)|Да||  
  
## <a name="build"></a>Построить  
 Ссылка для справки: **[Сборки](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|Локальный сервер TFS|Да|На компьютерах для сборки должна быть установлена платформа Xamarin; кроме того, они могут быть связаны с компьютером OSX для сборки приложений для iOS. См. раздел [Настройка TFS для Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (веб-сайт Xamarin)|  
|Локальный сервер сборки, связанный с Visual Studio Team Services|Да|Инструкции см. в разделе [Сервер сборки](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c).|  
|Служба размещенного контроллера Visual Studio Team Services|Да|См. [Сборка приложения Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin).|  
|Определения сборки с сценариями до и после сборки|Да||  
|Непрерывная интеграция, включая условный возврат|Да|Условный возврат доступен только для TFVC, так как Git работает с моделью запроса на включение внесенных изменений, а не с возвратом.|  
  
## <a name="testing"></a>Тестирование  
 Ссылка для справки: **[Тестирование приложения](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|Планирование тестов, создание тестовых случаев и организация наборов тестов|Да||  
|Тестирование вручную|Да||  
|Test Manager (запись и воспроизведение тестов)|Да|Только устройства Windows и эмуляторы Android из Visual Studio. Возможна запись для всех устройств с помощью [Средства записи тестов Xamarin](https://www.xamarin.com/test-cloud/recorder).|  
|Покрытие кода|Н/Д||  
|[Модульное тестирование кода](../test/unit-test-your-code.md)|Да|Для целевых платформ Windows и Android можно использовать встроенные средства MSTest. Для выполнения модульных тестов в Windows, iOS и Android Xamarin рекомендует использовать NUnit. См. раздел [Настройка TFS для Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (веб-сайт Xamarin).|  
|[Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)|Только для Windows|Средства записи тестов пользовательского интерфейса Visual Studio предназначено только для Windows. Средства для других платформ описаны в разделе [Средство записи тестов Xamarin](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Улучшите качество кода  
 Ссылка для справки: **[Улучшение качества кода](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|[Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Да||  
|[Поиск повторяющегося кода с помощью обнаружения клонов кода](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Да||  
|[Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Да||  
|[Обозреватель производительности](../profiling/performance-explorer.md)|Нет|Вместо этого используйте [профилировщик Xamarin](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) в Xamarin Studio. Обратите внимание, что профилировщик Xamarin находится в режиме предварительной версии и пока не работает для целевых платформ Windows.|  
|[Анализ проблем с памятью .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Нет|Инструменты Visual Studio не имеют обработчиков в платформе Mono для профилирования.|  
  
## <a name="release-management"></a>Управление выпуском  
 Ссылка для справки: **[Автоматизирование развертываний с помощью Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|Управление процессами выпуска|Да||  
|Развертывание на серверах для загрузки неопубликованных приложений через сценарии|Да||  
|Отправка в магазин приложений|Partial|Доступны расширения, которые автоматизируют этот процесс для некоторых магазинов приложений.  См. раздел [Расширения для Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), например, [расширение для Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Мониторинг с HockeyApp  
 Ссылка для справки: **[Мониторинг с HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Функция|Поддерживается в Xamarin|Дополнительные комментарии|  
|-------------|----------------------------|-------------------------|  
|Анализ сбоев, телеметрия и бета-распределение|Да||
