---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65846423"
---

1. Закройте и снова откройте консоль управления IIS, чтобы отобразить обновленные параметры конфигурации в пользовательском интерфейсе.

2. В службах IIS щелкните правой кнопкой мыши элемент **Веб-сайт по умолчанию** и выберите **Развернуть** > **Включить публикацию веб-развертывания**.

    ![Настройка конфигурации веб-развертывания](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. Просмотрите параметры в диалоговом окне **Включить публикацию веб-развертывания**.

4. Щелкните **Настройка**.

    Выходные данные в панели **Результаты** показывают, что права доступа предоставлены конкретному пользователю, а в указанном в диалоговом окне месте был создан файл с расширением *.publishsettings*.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    В зависимости от конфигурации Windows Server и служб IIS в XML-файле будут представлены разные значения. Ниже описываются некоторые значения, которые могут вам встретиться.

   * Файл *msdeploy.axd*, на который ссылается атрибут `publishUrl`, представляет собой динамически создаваемый файл обработчика HTTP для веб-развертывания. (В целях тестирования, как правило, можно использовать `http://myhostname:8172`.)
   * Порту `publishUrl` присваивается значение 8172, которое по умолчанию используется для веб-развертывания.
   * Порту `destinationAppUrl` присваивается значение 80, которое по умолчанию используется для служб IIS.
   * Если вам не удается подключиться к удаленному узлу в Visual Studio с использованием имени узла (на последующих шагах), попробуйте использовать вместо имени узла IP-адрес.

     > [!NOTE]
     > Если вы выполняете публикацию в службах IIS, работающих на виртуальной машине Azure, необходимо открыть порты для веб-развертывания и служб IIS в группе безопасности сети. Дополнительные сведения см. в статье [Установка и запуск служб IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Скопируйте этот файл на компьютер, на котором выполняется среда Visual Studio.
