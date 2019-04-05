---
title: Устранение неполадок
description: Распространенные проблемы, возникающие у пользователей Visual Studio для Mac, и способы их разрешения.
ms.topic: troubleshooting
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 3a5ea59e6f98891cd113ccad9a74038ca52cccf8
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568196"
---
# <a name="troubleshooting"></a>Устранение неполадок

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Просмотр журналов в Visual Studio для Mac

Журналы можно найти, перейдя в раздел **Справка > Открыть каталог журналов**, как показано ниже:

![Пункт меню "Открыть каталог журналов"](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Просмотр исключений

При перехвате исключения отображается пузырек исключения. Чтобы просмотреть дополнительные сведения, нажмите кнопку **Просмотреть сведения**:

![Просмотр дополнительных сведений об исключении](media/troubleshooting-image2.png)

Отображается диалоговое окно **Показать подробности** с дополнительными сведениями об исключении.

![Диалоговое окно "Показать подробности"](media/troubleshooting-image3.png)

Ниже подробнее описаны упомянутые наиболее важные разделы диалогового окна:

1. Тип исключения, который показывает полное имя для наблюдаемого типа исключения.
2. Сообщение об исключении, показывающее значение свойства Message для объекта исключения.
3. Тип внутреннего исключения, который показывает полное имя типа для выбранного исключения в представлении внутренних исключений в виде дерева.
4. Сообщение внутреннего исключения, которое показывает значение свойства Message для выбранного исключения в представлении внутренних исключений в виде дерева.
5. Представление трассировки стека. Оно может быть свернуто с помощью стрелки и содержит записи кадров стека.
6. Пример записей непользовательского кода.
7. Пример записей пользовательского кода.
8. Представление свойств, показывающее все свойства и поля исключения. Его можно свернуть с помощью стрелки.
9. Представление внутренних исключений в виде дерева. Выбирайте внутренние исключения в этом представлении с помощью клавиш со стрелками ВВЕРХ И ВНИЗ на клавиатуре, мыши или трекпада.
10. По умолчанию состояние этого параметра соответствует настройке **Выполняйте отладку только кода проекта**. Установка этого флажка позволяет свернуть весь непользовательский код в одну строку в трассировке стека.
11. Кнопка для копирования выходных данных `exception.ToString()` в буфер обмена.

Обратите внимание, что некоторые из этих разделов видны только в том случае, когда исключение имеет внутреннее исключение.

## <a name="see-also"></a>См. также

- [Ресурсы для устранения неполадок интегрированной среды разработки (Visual Studio для Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)