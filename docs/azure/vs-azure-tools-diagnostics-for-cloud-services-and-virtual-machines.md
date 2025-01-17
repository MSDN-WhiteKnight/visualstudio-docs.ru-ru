---
title: Система диагностики для Облачных служб и виртуальных машин Azure
description: Узнайте, как настраивать систему диагностики для отладки облачных служб и виртуальных машин Azure в Visual Studio.
author: ghogen
manager: jillfra
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.openlocfilehash: 0b212ee44809f925bb4d2d78efc972a4986602a5
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177329"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Настройка системы диагностики для облачных служб и виртуальных машин Azure
Чтобы устранить неполадки в облачных службах или виртуальных машинах Azure, можно использовать Visual Studio для быстрой настройки системы диагностики Azure. Система диагностики собирает системные данные и данные журналов, поступающие от виртуальных машин и их экземпляров, на которых работает ваша облачная служба. Данные диагностики переносятся в указанную вами учетную запись хранения. Дополнительные сведения о ведении журнала диагностики см. в статье [Включение ведения журнала диагностики для веб-приложений в службе приложений Azure](/azure/app-service/web-sites-enable-diagnostic-log).

Эта статья содержит сведения о том, как использовать Visual Studio, чтобы включить и настроить систему диагностики Azure до и после развертывания. Узнайте, как настроить систему диагностики на виртуальных машинах Azure, а также как выбирать типы данных диагностики для их сбора и просматривать информацию после сбора.

Для настройки системы диагностики Azure можно использовать один из следующих вариантов:

* Измените параметры диагностики в диалоговом окне **конфигурации диагностики** в Visual Studio. Параметры сохраняются в файл с именем diagnostics.wadcfgx (в пакете SDK Azure версии 2.4 и более ранних файл назывался diagnostics.wadcfg). Вы также можете напрямую изменить файл конфигурации. Если вы измените файл вручную, изменения конфигурации вступят в силу после следующего развертывания облачной службы в Azure или следующего запуска службы в эмуляторе.
* Изменить параметры диагностики для работающей облачной службы или виртуальной машины можно с помощью Cloud Explorer или обозревателя сервера в Visual Studio.

## <a name="azure-sdk-26-diagnostics-changes"></a>Изменение в системе диагностики пакета SDK Azure 2.6
Для проектов в Visual Studio, использующих пакет SDK Azure версии 2.6 и более поздних:

* Локальный эмулятор теперь поддерживает систему диагностики. Это означает, что на этапе разработки и тестирования в Visual Studio вы можете собирать диагностические данные. Это позволит вам убедиться, что приложение создает правильные трассировки. При запуске проекта облачной службы в Visual Studio строка подключения `UseDevelopmentStorage=true` включает сбор диагностических данных с помощью эмулятора хранения Azure. Все диагностические данные собираются в учетную запись хранения (хранилище разработки).
* Строка подключения учетной записи хранения для диагностики `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` хранится в файле конфигурации службы (CSCFG). В пакете Azure SDK версии 2.5 учетная запись хранения диагностических данных указывается в файле diagnostics.wadcfgx.

Строка подключения в некоторых ключевых случаях работает иначе в пакете SDK Azure версии 2.6 и выше, чем в пакете SDK Azure 2.4 и предыдущих версиях.

* В Azure SDK 2.4 и более ранних версиях строка подключения использовалась как среда выполнения подключаемого модуля диагностики, который получал из нее параметры учетной записи хранения для передачи журналов диагностики.
* В Azure SDK 2.6 и более поздних версиях Visual Studio использует строку подключения диагностики для настройки учетной записи хранения в расширении системы диагностики Azure во время публикации. С помощью строки подключения можно указать разные учетные записи хранения для различных конфигураций службы. Visual Studio будет использовать их во время публикации. Но подключаемый модуль диагностики больше не доступен в пакетах Azure SDK, начиная с версии 2.5, поэтому сам CSCFG-файл уже не может настроить расширение диагностики. Вам необходимо настроить расширение отдельно с помощью средств, таких как Visual Studio или PowerShell.
* Выходные данные пакета Visual Studio содержат общедоступный XML-файл конфигурации расширения диагностики для каждой роли. Это позволяет упростить процесс настройки расширения с использованием PowerShell. С помощью строки подключения диагностики Visual Studio получает из общедоступной конфигурации данные учетной записи хранения. Общедоступные файлы конфигурации создаются в папке Extensions. Они используют шаблон именования PaaSDiagnostics.&lt;имя роли\>.PubConfig.xml. Все развертывания с использованием PowerShell могут использовать этот шаблон имени для сопоставления каждой конфигурации с ролью.
* [Портал Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040) использует строку подключения в CSCFG-файле для доступа к данным диагностики. Данные отображаются на вкладке **мониторинга**. Строка подключения позволяет настроить в службе отображение на портале подробных данных мониторинга.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Перенос проектов на Azure SDK версии 2.6 и выше
Когда проект переносится с Azure SDK 2.5 на Azure SDK 2.6 или более новую версию и в WADCFGX-файле указана учетная запись хранения для диагностики, она остается в этом файле. Чтобы воспользоваться преимуществами гибкости использования различных учетных записей хранения для разных конфигураций хранилища, необходимо вручную добавить строку подключения в проект. При переносе проекта на основе пакета SDK для Azure 2.4 или более ранней версии на пакет SDK для Azure 2.6 строки подключения системы диагностики сохраняются. Однако не забывайте, что в пакете SDK Azure 2.6 строки подключения используются иначе, как описано в предыдущем разделе.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Определение учетной записи хранения диагностических данных в Visual Studio
* Если в CSCFG-файле указана строка подключения диагностики, Visual Studio использует ее для настройки расширения диагностики во время публикации, а также при создании общедоступных XML-файлов конфигурации на этапе упаковки.
* Если в CSCFG-файле строка подключения диагностики не указана, Visual Studio использует для этих же целей учетную запись хранения, указанную в WADCFGX-файле.
* Строка подключения диагностики в CSCFG-файле имеет более высокий приоритет, чем учетная запись хранения в WADCFGX-файле. Если в CSCFG-файле присутствует строка подключения диагностики, Visual Studio использует ее, игнорируя учетную запись хранения в WADCFGX-файле.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Что позволяет сделать флажок "Обновлять строки подключения хранилища разработки…"?
Флажок **Обновлять строки подключения хранилища разработки для диагностики и кэширования, используя учетную запись хранилища Microsoft Azure, при публикации в Microsoft Azure** позволяет быстро заменить строку подключения хранилища для разработки учетной записью хранения Azure, указанной во время публикации.

Например, если установить этот флажок, а в строке подключения диагностики указан параметр `UseDevelopmentStorage=true`, то когда вы будете публиковать проект в Azure, Visual Studio автоматически заменит строки подключения диагностики учетной записью хранения, которую вы указали в мастере публикации. Но если в строке подключения диагностики указана реальная учетная запись хранения, будет использоваться именно она.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Функциональные различия диагностики в пакете SDK Azure между более ранними (до 2.4 включительно) и более поздними (с 2.5 включительно) версиями
Обновляя свой проект с пакета SDK Azure 2.4 и более ранних версий на Azure SDK 2.5 или выше, помните о следующих функциональных различиях диагностики.

* **API конфигурации являются устаревшими.** Программная конфигурация диагностики доступна в пакете SDK для Azure 2.4 и более ранних версий, но в дальнейших выпусках, начиная с версии SDK для Azure 2.5, она не используется. Если конфигурация диагностики в вашем проекте определена в коде, после переноса проекта на более новую версию SDK все нужно настроить заново, чтобы диагностика продолжала работать. Пакет SDK Azure 2.4 использует файл конфигурации диагностики diagnostics.wadcfg, а пакет SDK Azure 2.5 и более поздние версии — diagnostics.wadcfgx.
* **Диагностику для приложений облачной службы можно настроить только на уровне роли.** В пакете SDK Azure 2.5 и более поздних версиях диагностику для приложений облачной службы нельзя настроить на уровне экземпляра.
* **Конфигурация диагностики обновляется при каждом развертывании приложения.** Если изменить конфигурацию диагностики в обозревателе сервера Visual Studio и повторно развернуть приложение, могут возникнуть проблемы с контролем четности.
* **В пакете SDK Azure 2.5 и более поздних версиях аварийные дампы настраиваются в файле конфигурации диагностики, а не в коде.** Если вы настроили аварийные дампы в коде проекта, следует вручную перенести параметры из кода в файл конфигурации. При переходе на пакет SDK Azure 2.6 аварийные дампы не переносятся.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Включение диагностики в проектах облачных служб перед их развертыванием
В Visual Studio при запуске службы в эмуляторе перед ее развертыванием можно собирать диагностические данные для ролей, выполняемых в Azure. Все изменения параметров диагностики в Visual Studio сохраняются в файл конфигурации diagnostics.wadcfgx. Эти параметры определяют учетную запись хранения, в которую сохраняются диагностические данные после развертывания облачной службы.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Включение диагностики в Visual Studio перед развертыванием

1. В контекстном меню для роли выберите **Свойства**. В диалоговом окне **Свойства** перейдите на вкладку **Конфигурация**.
2. В разделе **Диагностика** установите флажок **Включить диагностику**.

    ![Доступ к параметру "Включить диагностику"](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Чтобы указать учетную запись хранения для данных диагностики, нажмите кнопку с многоточием (...).

    ![Выбор учетной записи хранения](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. В диалоговом окне **Создание строки подключения к хранилищу** укажите способ подключения, например с помощью эмулятора хранения Azure, подписки Azure или вручную введенных учетных данных.

    ![Диалоговое окно учетной записи хранения](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * Если выбрать **Эмулятор хранилища Microsoft Azure**, строка подключения будет иметь значение `UseDevelopmentStorage=true`.
   * Если выбрать **Ваша подписка**, вы можете выбрать подписку Azure, которую хотите использовать, и ввести имя учетной записи. Чтобы управлять подписками Azure, выберите **Управление учетными записями**.
   * Если вы выберете **Введенные вручную учетные данные**, введите имя и ключ учетной записи Azure, которую хотите использовать.
5. Чтобы просмотреть диалоговое окно **конфигурации диагностики**, выберите **Настройка**. Каждая вкладка (кроме вкладок **Общие** и **Каталоги журналов**) соответствует определенному источнику диагностических данных, которые можно собирать. По умолчанию открывается вкладка **Общие**, где вы можете выбрать следующие режимы сбора диагностических данных: **Только ошибки**, **Все сведения** и **Пользовательский план**. По умолчанию установлен режим **Только ошибки**, для которого требуется наименьший объем хранилища, поскольку в этом режиме предупреждения и сообщения трассировки не передаются. Режим **Все сведения** передает больше всего информации и использует самый большой объем хранилища, поэтому он наиболее затратный.

   > [!NOTE]
   > Для параметра "Квота диска в МБ" минимальный поддерживаемый размер составляет 4 ГБ. Но если выполняется сбор дампов памяти, увеличьте это значение, например до 10 ГБ.
   >

    ![Включение и настройка диагностики Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. В нашем примере мы выберем режим **Пользовательский план**, в котором вы можете настроить собранные данные.
7. В поле **Квота диска в МБ** можно указать, сколько выделить места для диагностических данных в своей учетной записи хранения. Вы можете применить значение по умолчанию или изменить его.
8. На каждой вкладке, которая содержит нужные вам диагностические данные, установите флажок **Включить передачу \<тип_журнала\>** . Например, если вы хотите собирать журналы приложений, на вкладке **Журналы приложений** установите флажок **Включить передачу журналов приложения**. Установите также все остальные параметры, необходимые для каждого типа диагностических данных. Сведения о параметрах на каждой вкладке см. в разделе **Настройка источников диагностических данных** далее в этой статье.
9. Настроив все нужные параметры сбора диагностических данных, нажмите кнопку **ОК**.
10. Теперь запустите проект облачной службы Azure в Visual Studio обычным образом. В процессе использования приложения вся информация, сбор которой вы включили, будет сохраняться в указанной учетной записи хранения Azure.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Включение диагностики на виртуальных машинах Azure
В Visual Studio вы можете собирать диагностические данные для виртуальных машин Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Включение диагностики на виртуальных машинах Azure

1. В обозревателе сервера выберите узел Azure и подключитесь к подписке Azure (если это еще не сделано).
2. Разверните узел **Виртуальные машины** . Вы можете создать виртуальную машину или выбрать имеющийся узел.
3. В контекстном меню нужной виртуальной машины выберите **Настроить**. Откроется диалоговое окно конфигурации виртуальной машины.

    ![Настройка виртуальной машины Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Добавьте расширение Microsoft Monitoring Agent Diagnostics, если оно еще не установлено. Это расширение позволяет собирать диагностические данные для виртуальной машины Azure. В разделе **Установленные расширения** в раскрывающемся списке **Выбрать допустимое расширение** выберите **Microsoft Monitoring Agent Diagnostics**.

    ![Установка расширения виртуальной машины Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > Для виртуальных машин существуют и другие диагностические расширения. Дополнительные сведения см. в разделе [Обзор расширений и компонентов виртуальной машины под управлением Windows](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Чтобы добавить расширение и просмотреть информацию в диалоговом окне **конфигурации диагностики**, выберите **Добавить**.
6. Чтобы указать учетную запись хранения, выберите **Настройка** и нажмите кнопку **ОК**.

    Каждая вкладка (кроме вкладок **Общие** и **Каталоги журналов**) соответствует определенному источнику диагностических данных, которые можно собирать.

    ![Включение и настройка диагностики Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    По умолчанию открывается вкладка **Общие**, где вы можете выбрать следующие режимы сбора диагностических данных: **Только ошибки**, **Все сведения** и **Пользовательский план**. По умолчанию установлен режим **Только ошибки**, для которого требуется наименьший объем хранилища, поскольку в этом режиме предупреждения и сообщения трассировки не передаются. В режиме **Все сведения** передается больше всего информации; это самый затратный по объему хранения вариант.
7. В нашем примере мы выберем режим **Пользовательский план** , в котором вы можете настроить параметры сбора данных.
8. В поле **Квота диска в МБ** вы указываете, сколько хотите выделить места для диагностических данных в своей учетной записи хранения. Значение по умолчанию можно изменять.
9. На каждой вкладке, которая содержит нужные вам диагностические данные, установите флажок **Включить передачу \<тип_журнала\>** .

    Например, если вы хотите собирать журналы приложений, установите флажок **Включить передачу журналов приложения** на вкладке **Журналы приложений**. Установите также все остальные параметры, необходимые для каждого типа диагностических данных. Сведения о параметрах на каждой вкладке см. в разделе **Настройка источников диагностических данных** далее в этой статье.
10. Настроив все нужные параметры сбора диагностических данных, нажмите кнопку **ОК**.
11. Сохраните обновленный проект.

    Сообщение в окне **Журнал действий Microsoft Azure** оповещает о выполненном обновлении виртуальной машины.

## <a name="set-up-diagnostics-data-sources"></a>Настройка источников диагностических данных
Включив сбор диагностических данных, вы можете указать нужные вам источники данных и выбрать конкретную информацию, которую желаете собирать. В следующих подразделах содержатся сведения о вкладках в диалоговом окне **конфигурации диагностики** и описание каждого параметра.

### <a name="application-logs"></a>Журналы приложений
Журналы приложений содержат диагностические данные, сформированные веб-приложением. Если вы хотите собирать журналы приложений, установите флажок **Включить передачу журналов приложения** . Чтобы увеличить или уменьшить интервал между перемещениями журналов приложений в учетную запись хранения, измените значение параметра **Период передачи (мин.)** . Вы можете также изменить объем сведений, сохраняемых в журнале, установив значение **Уровень журнала**. Например, выбрав уровень **Подробный**, вы будете получать подробные сведения, а выбрав уровень **Критический** — только критические ошибки. Если имеется определенный провайдер диагностических данных, создающий журналы приложений, вы можете настроить сбор этих журналов, добавив идентификатор поставщика в поле **GUID поставщика**.

  ![Журналы приложений](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Дополнительные сведения о журналах приложений см. в статье [Включение ведения журнала диагностики для веб-приложений в службе приложений Azure](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Журналы событий Windows
Чтобы собирать журналы событий Windows, установите флажок **Включить перемещение журналов событий Windows**. Чтобы увеличить или уменьшить интервал между перемещениями журналов событий в учетную запись хранения, измените значение параметра **Период передачи (мин.)** . Установите флажки для тех типов событий, которые хотите отслеживать.

![Журналы событий](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Если вы используете пакет SDK Azure 2.6 (или более позднюю версию) и хотите указать пользовательский источник данных, введите его в текстовом поле **\<Имя источника данных\>** , а затем выберите **Добавить**. Источник данных добавляется в файл diagnostics.cfcfg.

Если вы используете Azure SDK 2.5 и хотите указать пользовательский источник данных, вы можете добавить его в файл diagnostics.wadcfgx в раздел `WindowsEventLog`, как показано в следующем примере.

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Счетчики производительности.
Сведения о счетчиках производительности помогут вам найти проблемы в системе и оптимизировать производительность системы и приложений. Дополнительные сведения см. в статье [Создание и использование счетчиков производительности в приложении Azure](https://msdn.microsoft.com/library/azure/hh411542.aspx). Чтобы записать данные счетчика производительности, установите флажок **Включить перемещение счетчиков производительности**. Чтобы увеличить или уменьшить интервал между перемещениями журналов событий в учетную запись хранения, измените значение параметра **Период передачи (мин.)** . Установите флажки для тех счетчиков, которые хотите отслеживать.

![Счетчики производительности.](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Чтобы отслеживать счетчик производительности, который отсутствует в списке, введите его имя, используя предложенный синтаксис, а затем выберите **Добавить**. Список счетчиков производительности, которые можно отслеживать, зависит от операционной системы на виртуальной машине. Дополнительные сведения о синтаксисе см. в статье [Specifying a Counter Path](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx) (Указание пути к счетчику).

### <a name="infrastructure-logs"></a>Журналы инфраструктуры
Журналы инфраструктуры содержат сведения об инфраструктуре диагностики Azure и модулях RemoteAccess и RemoteForwarder. Для сбора данных о журналах инфраструктуры установите флажок **Enable transfer of Infrastructure Logs** (Включить передачу журналов инфраструктуры). Чтобы увеличить или уменьшить интервал между перемещениями журналов инфраструктуры в учетную запись хранения, измените значение параметра **Период передачи (мин.)** .

![Журналы инфраструктуры диагностики](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Дополнительные сведения см. в статье [Включение системы диагностики Azure в облачных службах Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Каталоги журналов
В каталоги журналов собираются данные из выбранных вами папок, а также из каталогов, в которых хранятся журналы запросов к службам IIS и журналы неудачно завершенных запросов. Если вы хотите собирать данные каталогов журналов, установите флажок **Включить перемещение каталогов журналов**. Чтобы увеличить или уменьшить интервал между перемещениями журналов в учетную запись хранения, измените значение параметра **Период передачи (мин.)** .

Установите флажки для журналов, которые хотите собирать, например **журналы IIS** и журналы **неудачно завершенных запросов**. Имена контейнеров хранилища задаются автоматически, но вы можете их изменить.

Вы можете собирать журналы из любой папки. Укажите путь к ней в разделе **Журнал из абсолютного каталога** и выберите **Добавить каталог**. Журналы сохраняются в указанные контейнеры.

![Каталоги журналов](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Журналы трассировки событий Windows
Если вы используете [трассировку событий для Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) и хотите собирать журналы ETW, установите флажок **Включить перемещение журналов трассировки событий Windows**. Чтобы увеличить или уменьшить интервал между перемещениями журналов в учетную запись хранения, измените значение параметра **Период передачи (мин.)** .

События записываются из указанных вами источников событий и манифестов событий. Чтобы указать источник событий, введите его имя в разделе **Источники событий**, а затем выберите **Добавить источник событий**. Аналогичным образом вы можете указать манифест событий в разделе **Манифесты событий** и выбрать **Добавить манифест событий**.

![Журналы трассировки событий Windows](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ASP.NET поддерживает структуру ETW с использованием классов в пространстве имен [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)). Пространство имен Microsoft.WindowsAzure.Diagnostics, которое наследует и расширяет стандартные классы [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)), позволяет использовать [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) как платформу ведения журналов в среде Azure. Дополнительные сведения см. в статьях [Управление протоколированием и трассировкой в Windows Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) и [Включение системы диагностики Azure в облачных службах Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Аварийные дампы
Чтобы собирать сведения об аварийном завершении работы экземпляра роли, установите флажок **Включить перемещение аварийных дампов**. Поскольку ASP.NET обрабатывает большинство исключений, обычно это полезно только для рабочих ролей. Чтобы увеличить или уменьшить процент выделяемого под аварийные дампы места в хранилище, измените значение параметра **Квота каталога (%)** . Вы можете изменить контейнер хранения аварийных дампов, а также выбрать, какой дамп нужно сохранять: **полный** или **мини**.

Все отслеживаемые процессы указаны на снимке экрана ниже. Установите флажки для тех процессов, данные о которых вы хотите собирать. Чтобы добавить в список другой процесс, введите имя процесса и выберите **Добавить процесс**.

![Аварийные дампы](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Дополнительные сведения см. в статьях [Управление протоколированием и трассировкой в Windows Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) и [Диагностика Microsoft Azure, часть 4. Настраиваемые компоненты ведения журналов и изменения в системе диагностики Azure 1.3](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Просмотр диагностических данных
Собранные диагностические данные для облачной службы или виртуальной машины можно просматривать.

### <a name="to-view-cloud-service-diagnostics-data"></a>Просмотр диагностических данных облачной службы
1. Разверните и запустите облачную службу обычным образом.
2. Диагностические данные можно просмотреть в виде отчета, который создает Visual Studio, или в виде таблиц в учетной записи хранения. Чтобы просмотреть данные в отчете, откройте Cloud Explorer или обозреватель сервера, затем откройте контекстное меню интересующего вас узла и выберите **View Diagnostic Data** (Просмотреть диагностические данные).

    ![Просмотр диагностических данных](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Появится отчет по имеющимся данным.

    ![Отчет Диагностики Microsoft Azure в Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    Если в нем не содержатся самые свежие данные, вам следует дождаться завершения очередного периода передачи.

    Для немедленного обновления данных щелкните ссылку **Обновить**. Чтобы данные обновлялись автоматически, выберите интервал в раскрывающемся списке **Автообновление**. Чтобы экспортировать данные об ошибках, нажмите кнопку **Экспорт в CSV**. Будет создан CSV-файл, который вы сможете открыть в виде листа Excel.

    В Cloud Explorer или обозревателе сервера откройте учетную запись хранения, связанную с развертыванием.
3. Откройте диагностические таблицы в средстве просмотра таблиц и изучите собранные данные. Для просмотра пользовательских журналов и журналов служб IIS вы можете открыть контейнер больших двоичных объектов. Указанная ниже таблица содержит список таблиц или контейнеров больших двоичных объектов, содержащих данные для файлов разных журналов. В дополнение к данным соответствующего журнала таблицы содержат поля **EventTickCount**, **DeploymentId**, **Role** и **RoleInstance**. Они помогут вам понять, какая виртуальная машина и роль создали эти данные, а также когда эти данные были созданы.

   | Диагностические данные | ОПИСАНИЕ | Расположение |
   | --- | --- | --- |
   | Журналы приложений |Журналы, которые ваш код создает при вызове класса **System.Diagnostics.Trace**. |WADLogsTable |
   | Журналы событий |Данные, собранные из журналов событий Windows на виртуальных машинах. В этих журналах хранится информация ОС Windows, но приложения и службы также могут записывать в них ошибки или данные. |WADWindowsEventLogsTable |
   | Счетчики производительности. |Вы можете собирать данные с любого счетчика производительности, который доступен на вашей виртуальной машине. Операционная система предоставляет различные счетчики, которые позволяют изучать всевозможную статистику, например использование памяти и загруженность процессора. |WADPerformanceCountersTable |
   | Журналы инфраструктуры |Журналы, которые создает сама инфраструктура диагностики. |WADDiagnosticInfrastructureLogsTable |
   | Журналы IIS |Журналы, которые записывают веб-запросы. Если в облачную службу поступает очень много запросов, эти журналы могут быть длинными. Рекомендуется собирать и хранить эти данные только при необходимости. |Журналы неудачных запросов можно найти в контейнере больших двоичных объектов в папке wad-iis-failedreqlogs, расположенной в каталоге конкретного развертывания, роли и экземпляра. Полные журналы вы найдете в папке wad-iis-logfiles. В таблицу WADDirectories вносятся записи для каждого файла. |
   | Аварийные дампы |Предоставляет двоичные образы процесса облачной службы (обычно рабочей роли). |Контейнер больших двоичных объектов wad-crush-dumps |
   | Файлы пользовательских журналов |Настроенные вами журналы. |Вы можете в коде задать расположение файлов пользовательских журналов в своей учетной записи хранения, например указать для них пользовательский контейнер больших двоичных объектов. |
4. Если данные любого типа усекаются, вы можете попробовать увеличить размер буфера для этого типа данных или уменьшить интервал между передачами данных из виртуальной машины в учетную запись хранения.
5. Время от времени удаляйте данные из учетной записи хранения, чтобы снизить общие затраты на хранение. Это необязательно.
6. Когда вы выполняете полное развертывание, Azure обновляет файл diagnostics.cscfg (diagnostics.wadcfgx в Azure SDK 2.5) и облачная служба принимает все изменения, внесенные в конфигурацию диагностики. Если же вы обновляете существующее развертывание, Azure не обновляет CSCFG-файл. Но вы и в этом случае можете изменить конфигурацию диагностики, выполнив действия, описанные в следующем разделе. Дополнительные сведения о полном развертывании и обновлении существующего развертывания см. в статье [Мастер публикации приложений Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Просмотр диагностических данных виртуальной машины
1. Выберите в контекстном меню виртуальной машины пункт **Просмотр данных диагностики**.

    ![Просмотр диагностических данных на виртуальной машине Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    Отобразится диалоговое окно **Сводка диагностики**.

    ![Сводка по диагностическим данным виртуальной машины](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    Если в нем не содержатся самые свежие данные, вам следует дождаться завершения очередного периода передачи.

    Для немедленного обновления данных щелкните ссылку **Обновить**. Чтобы данные обновлялись автоматически, выберите интервал в раскрывающемся списке **Автообновление**. Чтобы экспортировать данные об ошибках, нажмите кнопку **Экспорт в CSV**. Будет создан CSV-файл, который вы сможете открыть в виде листа Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Настройка диагностики облачной службы после развертывания
Если вы изучаете проблему, возникшую в уже запущенной облачной службе, вам могут потребоваться новые данные, которые не были указаны перед первоначальным развертыванием этой роли. В этом случае вы можете начать сбор новых данных, изменив настройки в обозревателе сервера. Вы можете настроить диагностику для одного или всех экземпляров роли. В первом случае следует открыть диалоговое окно **настройки диагностики** из контекстного меню для экземпляра, а во втором — для роли. Если вы изменяете настройки в узле роли, все вносимые изменения применяются ко всем экземплярам. Если вы изменяете настройки в узле экземпляра, все вносимые изменения применяются только к этому экземпляру.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Настройка диагностики для работающей облачной службы
1. В обозревателе сервера разверните узел **Облачные службы**, а затем разверните список узлов, чтобы найти анализируемую роль или экземпляр (или и то, и другое).

    ![Настройка диагностики](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. В контекстном меню узла экземпляра или роли выберите пункт **Обновить параметры диагностики**, а затем выберите параметры диагностики, которые желаете собирать.

    Сведения о параметрах конфигурации см. в разделе **Настройка источников диагностических данных** в этой статье. Информацию о просмотре диагностических данных см. в разделе **Просмотр диагностических данных** в этой статье.

    Когда вы изменяете настройки сбора данных в обозревателе сервера, эти изменения остаются в силе до следующего полного развертывания облачной службы. Если вы используете стандартные параметры публикации, внесенные изменения не будут перезаписаны. По умолчанию при публикации выполняется обновление имеющегося развертывания, а не полное повторное развертывание. Чтобы очистить эти настройки во время развертывания, перейдите в мастере публикации на вкладку **Дополнительные параметры** и снимите флажок **Обновление развертывания**. При повторном развертывании со снятым флажком параметры снова принимают значения, заданные для роли в WADCFGX- или WADCFG-файле через редактор **свойств**. Если вы обновляете развертывание, Azure сохраняет старые настройки.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Устранение неполадок облачной службы Azure
Если вы столкнетесь с проблемами в проектах облачных служб (например, роль "зависает" в состоянии "занято", постоянно перезапускается или выдает внутреннюю ошибку сервера), вы можете использовать несколько инструментов и методов для диагностики и устранения этой проблемы. Конкретные примеры распространенных проблем и решений, а также общие сведения о концепциях и инструментах для диагностики и устранения ошибок вы найдете в блоге [Windows Azure PaaS Compute Diagnostics Data](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx) (Данные диагностики вычислений Microsoft Azure PaaS).

## <a name="q--a"></a>Вопросы и ответы
**Что такое размер буфера и каким он должен быть?**

Для каждого экземпляра виртуальной машины имеются квоты, которые ограничивают объем хранения диагностических данных в локальной файловой системе. Кроме того, вы определяете размер буфера для каждого доступного типа диагностических данных. Этот буфер выполняет роль индивидуальной квоты для соответствующего типа данных. Чтобы определить общую квоту и объем свободной памяти, просмотрите нижнюю часть диалогового окна для типа диагностических данных. Если вы укажете большие размеры буферов или большее количество типов данных, можно превысить общую квоту. Общую квоту вы можете изменить, отредактировав файл конфигурации diagnostics.wadcfg (или diagnostics.wadcfgx). Диагностические данные хранятся в той же файловой системе, что и данные приложения, поэтому не следует увеличивать общую квоту для диагностики, если приложение использует много места на диске.

**Что такое период передачи и каким он должен быть?**

Период передачи определяет количество времени между последовательными сборами данных. По окончании каждого периода передачи система диагностики перемещает данные из локальной файловой системы виртуальной машины в таблицы в вашей учетной записи хранения. Если до окончания периода передачи объем собираемых данных превысит квоту, старые данные удаляются. Если вы теряете данные из-за превышения размера буфера или общей квоты, советуем уменьшить период передачи.

**Какой часовой пояс используется для отметок времени?**

В отметках времени указан локальный часовой пояс того центра обработки данных, в котором размещена ваша облачная служба. Таблицы журналов содержат такие три столбца отметки времени:

* **PreciseTimeStamp**: отметка времени событий ETW. Это время регистрации события клиентом.
* **TIMESTAMP**: значение для **PreciseTimeStamp** с округлением до ближайшей границы периода передачи. Например, если вы используете период передачи 5 минут, а событие регистрируется в 00:17:12, в поле TIMETAMP установлено значение 00:15:00.
* **Метка времени.** отметка времени создания записи в таблице Azure.

**Как снизить затраты на сбор диагностической информации?**

По умолчанию выбраны значения параметров (**Уровень ведения журнала** имеет значение **Ошибка**, а **Период передачи** имеет значение **1 минута**), которые обеспечивают минимальные затраты. Затраты на вычисления увеличиваются, когда вы собираете больше диагностических данных или уменьшаете период передачи. Не следует собирать больше данных, чем вам действительно нужно. Также не забудьте отключить сбор данных, когда это вам не нужно. Вы всегда можете включить эту функцию снова, даже во время выполнения, как описано ранее в этой статье.

**Как собирать журналы неудачных запросов службы IIS?**

По умолчанию службы IIS не собирают журналы неудачных запросов. Чтобы настроить сбор журналов неудачных запросов в службах IIS, измените файл web.config для веб-роли.

**Я не получаю сведения о трассировке от методов RoleEntryPoint, например OnStart. В чем проблема?**

Методы **RoleEntryPoint** вызываются в контексте WAIISHost.exe, а не IIS. К ним не применяются настройки конфигурации из файла web.config, который обычно включает трассировку. Чтобы устранить эту проблему, добавьте в проект веб-роли CONFIG-файл с именем, которое соответствует имени выходной сборки, в которой размещен код **RoleEntryPoint**. В проекте веб-роли по умолчанию этот файл должен называться WAIISHost.exe.config. Добавьте в этот файл следующие строки.

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

В окне **Свойства** задайте для свойства **Копировать в выходной каталог** значение **Всегда копировать**.

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о ведении журналов диагностики в Azure см. в статьях [Включение системы диагностики Azure в облачных службах Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics) и [Включение ведения журнала диагностики для веб-приложений в службе приложений Azure](/azure/app-service/web-sites-enable-diagnostic-log).
