---
title: Изменение расположения установки в Visual Studio 2017
description: Узнайте, как уменьшить пространство, занимаемое установкой на системном диске, переместив кэш загрузки, общие компоненты, пакеты SDK и средства на разные диски.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0460e61fea7e617e497a46c55f8af811ba2e24fe
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Изменение расположения установки в Visual Studio 2017

**Новые возможности в версии 15.7**. Вы можете уменьшить пространство, занимаемое установкой на системном диске, переместив кэш загрузки, общие компоненты, пакеты SDK и средства на разные диски.

Ниже описывается порядок действий.

1. При установке Visual Studio откройте вкладку **Параметры установки**.

  ![Visual Studio 2017 — изменение расположения установки](media/installation-options-by-location.png "Изменение расположения установки")

  > [!IMPORTANT]
  > Если приостановить установку, а затем возобновить ее, Visual Studio начнет с того места, на котором вы остановились. Иными словами, ход выполнения применяется к оставшейся части загрузки и установки, а предыдущий отсчет не продолжается.

2. В разделе **Visual Studio** примите значение по умолчанию. Будет установлен основной компонент и файлы, относящиеся к этой версии Visual Studio.

 > [!IMPORTANT]
 > Если ваш системный диск — это твердотельный накопитель (SSD), мы рекомендуем принять расположение по умолчанию в системном диске. При работе в Visual Studio вы считываете и записываете большое количество файлов, что приводит к увеличению числа операций ввода-вывода на диске.  Рекомендуется выбрать самый быстрый диск, чтобы справиться с нагрузкой.

2. В разделе **Кэш загрузки** решите, следует ли сохранить кэш загрузки, а затем установите или снимите флажок **Сохранить кэш загрузки**. <br><br>Если вы решили не сохранять кэш загрузки, это расположение будет использоваться временно. Это действие не повлияет на файлы из предыдущей установки и не приведет к их удалению. (Чтобы очистить все пакеты установки, необходимо отдельно изменить предыдущие установки.)

3. В разделе **Кэш загрузки** укажите диск, где будут храниться файлы установки и манифесты. <br><br>Например, при выборе рабочей нагрузки **Разработка классических приложений на C++** потребуется 1,58 ГБ пространства на системном диске, но после завершения установки этот объем будет освобожден.

 > [!NOTE]
 > Файлы сначала загружаются во временную папку на системном диске, а затем удаляются, после того как Visual Studio проверит их и переместит в папку кэша загрузки. Если вы решите сохранить кэш загрузки на другом диске, Visual Studio все равно потребуется объем, эквивалентный размеру кэша загрузки, на системном диске.
 > [!IMPORTANT]
 > Расположение задается во время первой установки. Его нельзя изменить позднее в пользовательском интерфейсе установщика. Вместо этого вы можете [использовать параметры командной строки](use-command-line-parameters-to-install-visual-studio.md) для перемещения кэша загрузки

4. В разделе **Общие компоненты, пакеты SDK и средства** укажите диск, где вы хотите сохранить файлы, используемые совместно параллельными установками Visual Studio. Пакеты SDK и средства, расположение установки которых затем будет изменено установщиком Visual Studio, также сохраняются в этом каталоге.

 > [!NOTE]
 > Некоторые средства и пакеты SDK имеют другие правила расположения установки. Эти средства и пакеты SDK будут установлены на системном диске, даже если вы выбрали другое расположение.

## <a name="get-support"></a>Техническая поддержка

Иногда возникают проблемы. При сбое установки Visual Studio воспользуйтесь инструкцией по [устранению неполадок и исправлению ошибок в ходе установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Вы можете также связаться с нами для помощи по установке в [интерактивном чате](https://www.visualstudio.com/vs/support/#talktous) (только английский язык). Дополнительные сведения см. на [странице Visual Studio "Свяжитесь с нами"](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:

* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio). (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также

* [Установка Visual Studio 2017](install-visual-studio.md)
* [Обновление Visual Studio 2017](update-visual-studio.md)
* [Изменение Visual Studio 2017](update-visual-studio.md)
* [Удаление Visual Studio 2017](uninstall-visual-studio.md)