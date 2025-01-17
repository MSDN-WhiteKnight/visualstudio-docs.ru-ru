---
title: Анализ энергопотребления приложениями Магазина | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2b25d0fa57659b3081b54c51b7493621423188f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696992"
---
# <a name="analyze-energy-use-in-store-apps"></a>Анализ энергопотребления приложениями Магазина
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Профилировщик **Расход энергии** Visual Studio позволяет анализировать расход энергии приложениями Магазина Windows на планшетных устройствах с низким энергопотреблением, постоянно или периодически работающих на своих аккумуляторах. На устройстве, работающем от аккумулятора, приложение с большим энергопотреблением может вызывать такое недовольство пользователя, что он в конце концов удалит его. Оптимизация расхода энергии позволяет улучшить восприятие приложения пользователями и повысить степень его использования.  
  
## <a name="BKMK_What_the_Energy_Consumption_tool_is__how_it_works__and_what_it_measures"></a> Что такое профилировщик "Расход энергии", как он работает и что измеряет  
 Во время сеанса профилирования профилировщик расхода энергии фиксирует операции дисплея, центрального процессора и сетевых подключений устройства. Затем он оценивает мощность, затраченную при выполнении этих операций, и общую энергию, израсходованную в течение сеанса профилирования.  
  
> [!NOTE]
> Профилировщик расхода энергии оценивает потребляемую мощность и расход энергии с помощью программной модели стандартного оборудования эталонного устройства, представляющего планшетные устройства с низким энергопотреблением, на которых может работать приложение. Для получения наилучших оценок рекомендуется осуществлять сбор данных профилирования на планшетном устройстве с низким энергопотреблением.  
>   
> Хотя данная модель предоставляет хорошие оценки для различных устройств с низким энергопотреблением, фактические значения профилируемого устройства будут, скорее всего, другими. Используйте эти значения для поиска тех дисплейных, процессорных и сетевых операций, которые приводят к большему расходу энергии, чем использование других ресурсов, и поэтому могут быть хорошими кандидатами для оптимизации.  
  
 Для профилировщика расхода энергии используются следующие определения *мощности* и *энергии*.  
  
- *Мощность* — это интенсивность использования силы для выполнения работы в течение определенного периода времени. В электротехнике стандартной единицей мощности является *Ватт*. Эта единица определяется как интенсивность, с которой выполняется работа при прохождении тока величиной один ампер через разность потенциалов один вольт. На диаграмме **Энергопотребление** единицы представляются в милливаттах ( **мВт** ). Один милливатт — это одна тысячная ватта.  
  
   Поскольку мощность представляет собой интенсивность, она имеет направление (объем работы может увеличиваться или уменьшаться в определенном промежутке времени) и скорость (величина, на которую возрастает или уменьшается объем работы).  
  
- *Энергия* — это суммарная мощность (например, энергоемкость аккумулятора), потребленная за определенный период времени. Единица измерения энергии — ватт-час (мощность величиной один ватт, постоянно подаваемая в течение одного часа). На диаграмме **Сводка энергии**единицы представляются в милливаттах в час ( **мВт-ч**).  
  
  ![Запас энергии, израсходованная энергия и общая израсходованная энергия](../profiling/media/energyprof-capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Например, полностью заряженный аккумулятор в планшете имеет определенное количество накопленной энергии. Так как энергия используется для выполнения таких задач, как обмен данными по сети, расчет значений и отображение графики, мощность аккумулятора расходуется с разной интенсивностью. В течение любого периода времени общее количество потребляемой мощности измеряется также с использованием показателя "энергия".  
  
## <a name="BKMK_Identify_scenarios_with_user_marks"></a> Определение сценариев с пользовательскими отметками  
 Можно добавлять *пользовательские деления* в данные профилирования для облегчения идентификации областей на линейке временной шкалы.  
  
 ![Пользовательские метки на временной шкале](../profiling/media/profilers-usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 Отметка отображается в виде оранжевого треугольника на временной шкале в момент выполнения метода. При наведении указателя мыши на отметку отображаются сообщение и время в виде подсказки. Если две или несколько пользовательских отметок расположены рядом друг с другом, отметки и данные их всплывающих подсказок объединяются. Для разделения отметок можно увеличить масштаб изображения временной шкалы.  
  
 **Добавление делений в код C#, Visual Basic, C++**  
  
 Для добавления пользовательского деления в код C#, Visual Basic, C++ сначала создайте объект [Windows.Foundation.Diagnostics LoggingChannel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) . Затем добавьте вызовы методов [LoggingChannel.LogMessage](https://msdn.microsoft.com/library/windows/apps/dn264210.aspx) в тех местах кода, которые требуется отметить. Используйте [LoggingLevel.Information](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) в вызовах.  
  
 При выполнении метода пользовательская отметка добавляется в данные профилирования вместе с сообщением.  
  
> [!NOTE]
> - Windows.Foundation.Diagnostics LoggingChannel реализует интерфейс [Windows.Foundation.IClosable](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iclosable.aspx) (проецируемый как [System.IDisposable](https://msdn.microsoft.com/library/System.IDisposable.aspx) в C# и VB). Чтобы избежать утечки системных ресурсов, вызовите [LoggingChannel.Close](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.close.aspx) ()(Windows.Foundation.Diagnostics.LoggingChannel.Dispose() в C# и VB) после завершения работы с каналом ведения журнала.  
>   - Каждый открытый канал ведения журнала должен иметь уникальное имя. При попытке создать новый канал ведения журнала с тем же именем, что и у существующего канала, вызывается исключение.  
  
 См. пример Windows SDK [LoggingSession Sample](http://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336) .  
  
 **Добавление делений в код JavaScript**  
  
 Для добавления пользовательских делений добавьте следующий код в тех местах кода, которые необходимо отметить:  
  
```  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* — строка, содержащая сообщение, которое будет отображаться в подсказке пользовательского деления.  
  
## <a name="BKMK_Configure_your_environment_for_profiling"></a> Настройка среды для профилирования  
 Для получения точных оценок необходимо профилировать расход энергии приложением на устройстве с низким энергопотреблением, которое работает на своих аккумуляторах. Поскольку Visual Studio не работает на большинстве таких устройств, к устройству потребуется подключить компьютер Visual Studio с помощью инструментов удаленной отладки Visual Studio. Для подключения к удаленному устройству необходимо настроить как проект Visual Studio, так и удаленное устройство. См. дополнительные сведения о [запуске приложений для Магазина Windows на удаленном компьютере](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
> [!TIP]
> - Не рекомендуется выполнять профилирование энергопотребления на имитаторе Магазина Windows и на компьютере Visual Studio. При профилировании на реальном устройстве получаются гораздо более точные данные.  
>   - Выполняйте профилирование при работе целевого устройства на своих аккумуляторах.  
>   - Закройте другие приложения, которые могут использовать те же ресурсы (сеть, центральный процессор или дисплей).  
  
## <a name="BKMK_Collect_energy_profile_data_for_your_app"></a> Сбор данных профилирования расхода энергии приложением  
  
1. В меню **Отладка** выберите **Запуск диагностики без отладки**.  
  
     ![Выбор расхода энергии в концентраторе диагностики](../profiling/media/energyprof-diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2. Выберите **Расход энергии** и нажмите кнопку **Запуск**.  
  
    > [!NOTE]
    > При запуске профилировщика **Расход энергии** может появиться окно **Контроль учетных записей** с запросом на разрешение запуска файла VsEtwCollector.exe. Выберите **Да**.  
  
3. Запустите приложение для сбора данных.  
  
4. Чтобы остановить профилирование, вернитесь в Visual Studio (использовав сочетание клавиш Alt + Tab) и на странице "Концентратор диагностики" выберите **Остановка сбора** .  
  
     ![Остановка сбора данных](../profiling/media/xamlprof-stopcollection.png "XAMLProf_StopCollection")  
  
     Visual Studio анализирует собранные данные и отображает результаты.  
  
## <a name="BKMK_Collect_energy_profile_data_for_an_installed_app"></a> Сбор данных профилирования расхода энергии установленным приложением  
 Инструмент "Расход энергии" можно запускать только в приложениях Магазина Windows 8.1, запущенных из решения Visual Studio или установленных из Магазина Windows. Когда решение открыто в Visual Studio, конечный объект по умолчанию — **Запускаемый проект**. Выбор в качестве конечного объекта установленного приложения.  
  
1. Щелкните **Изм. конечн. объект** и выберите **Установленное приложение**.  
  
2. В списке **Выберите установленный пакет приложения** выберите целевой объект.  
  
3. На странице концентратора диагностики выберите **Расход энергии** .  
  
4. Выберите **Запуск** , чтобы начать профилирование.  
  
   Чтобы остановить профилирование, вернитесь в Visual Studio (использовав сочетание клавиш Alt + Tab) и на странице "Концентратор диагностики" выберите **Остановка сбора** .  
  
## <a name="BKMK_Analyze_energy_profile_data"></a> Анализ данных профилирования расхода энергии  
 Данные профилирования энергопотребления отображаются в окне документа Visual Studio:  
  
 ![Страница отчета профилировщика расхода энергии](../profiling/media/energyprof-all.png "ENERGYPROF_All")  
  
|||  
|-|-|  
|![Шаг 1](../profiling/media/procguid-1.png "ProcGuid_1")|Имя файла отчета — Report*ГГГГММДД-ЧЧММ*.diagsession. При сохранении отчета имя можно изменить.|  
|![Шаг 2](../profiling/media/procguid-2.png "ProcGuid_2")|На временной шкале отображаются продолжительность сеанса профилирования, события активации жизненного цикла приложения и пользовательские отметки.|  
|![Шаг 3](../profiling/media/procguid-3.png "ProcGuid_3")|Отчет можно ограничить частью временной шкалы, перетащив синие панели, чтобы выбрать нужную область временной шкалы.|  
|![Шаг 4](../profiling/media/procguid-4.png "ProcGuid_4")|Диаграмма **Использование энергии** — это линейная диаграмма с несколькими графиками, на которой показывается изменение выходной мощности, вызванное каким-либо ресурсом устройства во время сеанса профилирования. Профилировщик "Расход энергии" отслеживает мощность, потребляемую центральным процессором, сетевыми операциями и дисплеем.|  
|![Шаг 5](../profiling/media/procguid-6.png "ProcGuid_6")|На диаграмме **Ресурсы (Вкл./Выкл.)**  отображаются сведения о затратах энергии для выполнения сетевых операций. На панели **Сеть** показывается время, в течение которого было открыто сетевое подключение. На дочерней панели **Передача данных** указывается время, в течение которого приложение принимало данные из сети или передавало их в сеть.|  
|![Шаг 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|**Сводка потребления энергии** представляет пропорциональное количество общей энергии, использованной в выбранных временных рамках центральным процессором, сетевыми операциями и дисплеем.|  
  
 **Действия для анализа данных профилирования энергопотребления**  
  
 Найдите область с пиковой потребляемой мощностью. Соотнесите пиковую область с функциями приложения. Затем используйте панели элементов управления на временной шкале, чтобы увеличить масштаб данной области. Если интерес представляет использование сети, разверните узел **Сеть** на диаграмме **Ресурсы (Вкл./Выкл.)**  , чтобы сравнить время открытого состояния сетевого подключения с временем, в течение которого приложение принимало или передавало по нему данные. Очень эффективный способ оптимизации — сокращение времени, в течение которого сетевое подключение открыто без необходимости.  
  
## <a name="BKMK_Optimize_energy_use"></a> Оптимизация расхода энергии  
 Помимо расхода энергии на передачу данных, сетевые подключения требуют энергозатрат для своей инициализации, поддержания и закрытия. Некоторые сети поддерживают подключение в течение определенного периода времени после передачи или приема данных, чтобы можно было передать больше данных, используя одно подключение. Для выяснения способа взаимодействия приложения с подключением можно использовать панель **Ресурсы (Вкл./Выкл.)** .  
  
 ![Панель ресурсов (Вкл./Выкл.)](../profiling/media/energyprof-resources.png "ENERGYPROF_Resources")  
  
 Если на панелях **Сеть** и **Передача данных** указывается, что подключение открыто в течение длительных периодов времени для периодической передачи ряда небольших пакетов данных, можно объединить данные для их передачи в одном пакете, сократить время открытого состояния сетевого подключения и снизить тем самым затраты энергии.  
  
 ![Область сводки энергопотребления](../profiling/media/energyprof-summary.png "ENERGYPROF_Summary")  
  
 Для дисплея имеется меньше возможностей управления затратами энергии. Большинству дисплеев требуется больше энергии для отображения светлых цветов, чем темных. Поэтому один из способов снижения затрат — использование темного фона.  
  
## <a name="BKMK_Other_resources"></a> Другие источники  
  
- В разделах **Управление состояниями подключений и затратами** для [C#/VB/C++ и XAML](https://msdn.microsoft.com/0ee0b706-8432-4d49-9801-306ed90764e1) и [JavaScript и HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) в Центре разработки для Windows описываются API-интерфейсы Windows, предоставляющие информацию о сетевых подключениях, которую приложение может использовать для минимизации затрат на сетевой трафик.  
  
     Имитатор Visual Studio для приложений Магазина Windows позволяет имитировать свойства подключений для передачи данных API-интерфейсов, предоставляющих информацию о сети. См. раздел [Run Windows Store apps in the simulator](../debugger/run-windows-store-apps-in-the-simulator.md).  
  
- Инструменты **Время выполнения функций JavaScript** и **Загрузка ЦП** позволяют снизить нагрузку на ЦП, связанную с неэффективными функциями. См. дополнительные сведения об [анализе использования ЦП](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).
