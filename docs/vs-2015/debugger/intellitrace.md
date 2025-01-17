---
title: IntelliTrace | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ea7378e72d970bf53470b4434222aa4a1a4d9a1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690525"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) .  
  
Сократите затраты времени на отладку приложения, используя IntelliTrace для записи и отслеживания истории выполнения кода. Вы сможете без труда находить ошибки, поскольку IntelliTrace позволяет выполнять следующие задачи.  
  
- Записывать определенные события.  
  
   Просматривать связанный код, данные, отображаемые в окне **Локальные** во время событий отладчика, и данные вызова функции.  
  
- Выполнять отладку ошибок, которые трудно воспроизводимы или возникают в развертывании.  
  
  IntelliTrace можно использовать в выпуске Visual Studio Enterprise (но не в выпусках Professional или Community).  
  
## <a name="what-do-you-want-to-do"></a>Выберите действие  
  
|||  
|-|-|  
|**Отладка приложения с помощью IntelliTrace**<br /><br /> — Отображение прошлых событий.<br />-Show me сведений о вызовах с прошлыми событиями.<br />-Сохранение сеанса IntelliTrace.<br />-Элемент управления данных, собираемых IntelliTrace.|-   [Пошаговое руководство: Использование IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Возможности IntelliTrace](../debugger/intellitrace-features.md)<br />-   [Настройка IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Отладка с ведением журнала](../debugger/historical-debugging.md)|  
|**Сбор данных IntelliTrace во время тестового сеанса в Test Manager**|-   [Сбор дополнительных данных диагностики в ручных тестах](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Сбор данных IntelliTrace из развернутых приложений**|-   [Использование автономного сборщика данных IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Запуск отладки из файла журнала IntelliTrace (файл .iTrace)**|-   [Использование сохраненных данных IntelliTrace](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="IntelliTraceSupport"></a>Какие приложения можно отлаживать с помощью IntelliTrace?  
  
|||  
|-|-|  
|**Поддерживается**|— Приложения Visual Basic и Visual C#, которые используют .NET Framework 2.0 или более поздней версии.<br />     Можно отлаживать большинство приложений, включая ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 и 64-разрядные приложения.<br />     Для отладки приложений SharePoint с помощью IntelliTrace, см. в разделе [Пошаговое руководство: Отладка приложения SharePoint с помощью IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     Отладка приложений Microsoft Azure с помощью IntelliTrace, см. в разделе [отладка опубликованной облачной службы с помощью IntelliTrace и Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Ограниченная поддержка**|- F# приложений в экспериментальном режиме<br />-Поддерживается только для событий приложений Windows Store|  
|**Не поддерживается**|-C++, другие языки и скрипт<br />-Windows служб Silverlight, Xbox, или [!INCLUDE[winmobile](../includes/winmobile-md.md)] приложений|  
  
> [!NOTE]
> Нельзя использовать IntelliTrace для отладки уже выполняемого процесса. Необходимо запустить IntelliTrace при запуске процесса.  
  
## <a name="IntelliTraceVSTraditional"></a> Зачем выполнять отладку с помощью IntelliTrace?  
 Традиционная отладка или отладка *в реальном времени* отображает только текущее состояние приложения с ограниченными данными о прошлых событиях. Необходимо либо сделать вывод об этих событиях на основании текущего состояния приложения, либо создать заново эти события, повторно запустив приложение.  
  
 IntelliTrace расширяет эти традиционные возможности отладки, записывая конкретные события и данные в определенные периоды времени. Это позволяет увидеть, что произошло в приложении, не перезапуская его, особенно если место возникновения ошибки было пропущено. IntelliTrace по умолчанию включается во время традиционной отладки и автоматически и незаметно собирает данные. Это позволяет легко переключаться между традиционной отладкой и отладкой с помощью IntelliTrace для просмотра записанной информации. См. в разделе [возможности IntelliTrace](../debugger/intellitrace-features.md) и [какие данные собирает IntelliTrace?](#WhatData)  
  
 IntelliTrace также может помочь в отладке ошибок, которые трудно воспроизводимы или происходят в развертывании. Можно собирать данные IntelliTrace и сохранять их в файл журнала IntelliTrace (файл .iTrace). Файл .iTrace содержит сведения об исключениях, событиях производительности, запросах через Интернет, тестовых данных, потоках, модулях и другую системную информацию. Можно открыть этот файл в Visual Studio Enterprise, выбрать элемент и начать отладку с помощью IntelliTrace. Это позволяет перейти к любому событию в файле и просматривать конкретные сведения о приложении на этот момент времени.  
  
 Можно сохранять данные IntelliTrace из следующих источников:  
  
- Сеанс IntelliTrace в Visual Studio 2015 Enterprise или более ранних версий Visual Studio Ultimate.  
  
- Сеанс тестирования в Microsoft Test Manager.  
  
- Веб-приложения ASP.NET, размещенные в IIS, или приложения SharePoint 2010 и SharePoint 2013, работающие в развертывании при использовании Microsoft Monitoring Agent, как отдельно, так и вместе с System Center 2012. См. в разделе [использование автономного сборщика данных IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) и [мониторинг с помощью Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465153.aspx).  
  
  Ниже приведено несколько примеров того, как IntelliTrace облегчает отладку.  
  
- Приложение имеет поврежденный файл данных, но вы не знаете, где произошло это событие.  
  
   Без IntelliTrace было бы необходимо просмотреть код, чтобы найти все возможные попытки доступа к файлу, разместить точки останова в этих местах осуществления доступа и перезапустить приложение для поиска места возникновения проблемы. С помощью IntelliTrace можно просмотреть все собранные события доступа к файлу и конкретные сведения о приложении на момент, когда произошло каждое событие.  
  
- Происходит исключение.  
  
   Без IntelliTrace вы получаете сообщение об исключении, но в нем отсутствуют многие сведения о событиях, ставших причиной исключения. Можно проверить стек вызовов, чтобы просмотреть цепочку вызовов, которые привели к возникновению исключения, но невозможно просмотреть последовательность событий, произошедших во время этих вызовов. С помощью IntelliTrace можно просмотреть события, которые случились перед исключением.  
  
- Приложение аварийно завершает работу на тестовом компьютере, но успешно выполняется на компьютере разработчика.  
  
   Можно собирать данные IntelliTrace из Microsoft Test Manager, сохранить эти данные в файле .iTrace и вложить этот файл в рабочий элемент Team Foundation Server для последующего изучения. См. в разделе [сбор дополнительных данных диагностики в ручных тестах](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) и [использование сохраненных данных IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
- В развернутом приложении происходит ошибка или сбой.  
  
   Для приложений на базе Microsoft Azure можно настроить сбор данных IntelliTrace до публикации приложения. Во время работы приложения IntelliTrace сохраняет информацию в ITRACE-файл. Ознакомьтесь со статьей [Отладка опубликованной облачной службы с помощью IntelliTrace и Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   Для веб-приложений ASP.NET, размещенных в IIS 7.0, 7.5 и 8.0, и приложений SharePoint 2010 и SharePoint 2013 используйте Microsoft Monitoring Agent либо отдельно, либо вместе с System Center 2012 для сохранения данных IntelliTrace в ITRACE-файл.  
  
   Этот метод полезен при диагностике проблем с приложениями в развертывании. См. в разделе [использование автономного сборщика данных IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="WhatData"></a> Какие данные собирает IntelliTrace?  
 **Сбор сведений о событиях**  
  
 По умолчанию IntelliTrace записывает только события IntelliTrace — события отладчика, исключения, события .NET Framework и другие системные события, которые помогут вам в процессе отладки. Можно выбрать типы событий IntelliTrace, которые необходимо собирать, за исключением событий отладчика и исключений, которые собираются всегда. См. в разделе [настроить IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **События отладчика**  
  
   IntelliTrace всегда записывает события, которые происходят в отладчике Visual Studio. Например, запуск приложения — это событие отладчика. Другие события отладчика — события остановки, заставляющие приложение прервать исполнение. Например, программа достигает точки останова, точки трассировки или выполняет команду **Шаг**.  
  
   Во избежание проблем с производительностью IntelliTrace не записывает все возможные значения события отладчика. а только следующие:  
  
  - Значения в окне **Локальные**. Оставьте окно **Локальные** открытым, чтобы видеть эти значения.  
  
  - Значения в поле **Видимые**, если окно **Видимые** открыто.  
  
  - Значения в советах DataTips, отображаемые при наведении указателя мыши на переменную в окне исходного кода для просмотра ее значения. IntelliTrace не собирает значения в закрепленных советах DataTips.  
  
- **Исключения**  
  
   IntelliTrace записывает тип исключения и сообщение для:  
  
  - обработанных исключений, если исключение создано и перехвачено;  
  
  - необработанных исключений.  
  
- **События .NET Framework**  
  
   По умолчанию IntelliTrace записывает наиболее распространенные события .NET Framework. Пример:  
  
  - при доступе к файлу IntelliTrace записывает имя файла;  
  
  - Для события установки флажка IntelliTrace собирает состояние и текст флажка.  
  
- **События приложений SharePoint 2010 и SharePoint 2013**  
  
   Можно записать события профиля пользователя и подмножество событий унифицированной системы ведения журнала (ULS) для приложений SharePoint 2010 и 2013, выполняемых вне Visual Studio. Можно сохранить эти события в ITRACE-файле. Требуется Visual Studio Enterprise 2015, предыдущей версии Visual Studio Ultimate или [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) в **трассировки** режим.  
  
   При открытии ITRACE-файла введите идентификатор корреляции SharePoint для поиска соответствующего веб-запроса, просмотра записанных событий и запуска отладки из указанного события. Если файл содержит необработанные исключения, можно выбрать идентификатор корреляции для запуска отладки исключения.  
  
   Пример  
  
  - [Использование автономного сборщика данных IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Использование сохраненных данных IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
  - [Пошаговое руководство: Отладка приложения SharePoint с помощью IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Сбор сведений о вызовах функции**  
  
  Можно настроить IntelliTrace для сбора сведений о вызовах для функций. Эти сведения позволяют просмотреть историю стека вызовов и перемещаться по вызовам в коде вперед и назад. Для каждого вызова функции IntelliTrace записывает следующие данные.  
  
- Имя функции  
  
- Значения простых типов данных, переданные в качестве параметров в точках входа функции и возвращаемые в точках выхода функции.  
  
- Значения автоматических свойств при их чтении или изменении.  
  
- Указатели на дочерние объекты первого уровня без их значений (только информацию о том, являются ли они null или нет).  
  
> [!NOTE]
> IntelliTrace собирает только первые 256 объектов в массивах и первые 256 символов в строках.  
  
 См. в разделе [настроить IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Сбор сведений о модуле**  
  
 Для того, чтобы контролировать размер собираемой IntelliTrace информации о вызовах, укажите только интересующие модули. Это может повысить производительность приложения во время сбора информации. См. в разделе [настроить IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="AffectPerformance"></a> Замедлит ли IntelliTrace работу приложения?  
 По умолчанию IntelliTrace собирает данные только для выбранных событий IntelliTrace. В зависимости от структуры и организации кода возможно замедление работы приложения. Например, частая запись события IntelliTrace может замедлить работу приложения. Также может потребоваться рассмотреть возможность рефакторинга приложения.  
  
 Сбор сведений о вызовах может значительно замедлить выполнение приложения. Это также может увеличить размер любых файлов журнала IntelliTrace (ITRACE-файлов), которые сохраняются на диск. Чтобы свести к минимуму указанные эффекты, собирайте информацию о вызовах только в важных для вас модулях.  Чтобы изменить максимальный размер ITRACE-файлов, последовательно выберите **Сервис**, **Параметры**, **IntelliTrace**, **Дополнительно**. См. в разделе [настроить IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Возможности IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Настройка IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Включение данных диагностической трассировки в сообщения об ошибках, которые трудно воспроизвести](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Диагностика проблем после развертывания](../debugger/diagnose-problems-after-deployment.md)  
  
 [Использование сохраненных данных IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Блоги  
 [Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Форумы  
 [Visual Studio Diagnostics](http://go.microsoft.com/fwlink/?LinkId=262263)
