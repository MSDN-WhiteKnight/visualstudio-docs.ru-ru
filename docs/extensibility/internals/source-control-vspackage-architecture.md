---
title: Исходная архитектура управления VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c05ae692a364d4e7a81a017d376dd820ade56b73
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322507"
---
# <a name="source-control-vspackage-architecture"></a>Архитектура пакета VSPackage системы управления версиями
Пакет системы управления версиями — пакет VSPackage, который использует службы, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет интегрированную среду разработки. Взамен пакет системы управления версиями обеспечивает его функциональные возможности, что в систему управления версиями. Кроме того, пакет системы управления версиями является альтернативой более гибкими, чем интеграция системы управления версиями в подключаемый модуль системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Подключаемый модуль, который реализует интерфейс API подключаемых модулей управления источника придерживается строгий контракт. Например, подключаемый модуль не может заменить значение по умолчанию [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс (UI). Кроме того API подключаемых модулей управления источника не поддерживает подключаемый модуль реализовать собственную модель управления исходным кодом. Пакет системы управления версиями, однако обходит большую часть этих ограничений. Пакет системы управления версиями имеет полный контроль над опыт управления источника [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользователя. Кроме того пакет системы управления версиями может использовать свою собственную модель управления исходным кодом и логики, и он может определять все интерфейсы пользователя, связанные с управлением версиями источника.

## <a name="source-control-package-components"></a>Компоненты пакета системы управления версиями
 Как показано на схеме архитектуры, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонент с именем заглушкой системы управления версиями — это пакет VSPackage, который объединяет пакет системы управления версиями с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Заглушкой системы управления версиями обрабатывает следующие задачи.

- Предоставляет общий пользовательский Интерфейс, который необходим для регистрации пакета системы управления версиями.

- Загружает пакет системы управления версиями.

- Задает пакет системы управления версиями в качестве активных и неактивных.

  Заглушкой системы управления версиями ищет активной службой для пакета системы управления версиями и направляет все входящие вызовы службы в интегрированной среде разработки для этого пакета.

  Пакет адаптера системы управления версиями — это специальный источник-элемент управления пакета, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет. Этот пакет является основным компонентом для поддержки источника подключаемые модули управления на основе API подключаемого модуля управления источника. Если подключаемый модуль системы управления версиями активного подключаемого модуля, заглушкой системы управления версиями отправляет его события адаптера пакет системы управления версиями. В свою очередь адаптер пакет системы управления версиями взаимодействует с подключаемый модуль системы управления версиями с помощью API подключаемых модулей управления источника, а также предоставляет стандартный пользовательский Интерфейс, который является общим для всех модулей системы управления версиями plug.

  Если включен пакет системы управления версиями active пакета, с другой стороны, заглушкой системы управления версиями напрямую взаимодействует с пакетом с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] интерфейсы пакета системы управления версиями. Пакет системы управления версиями отвечает за размещение свой собственный пользовательский Интерфейс системы управления версиями.

  ![Архитектура управления исходным кодом](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Пакет системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не предоставляет исходный код элемента управления или API для интеграции. Сравните это с помощью подхода, описанный в [Создание подключаемого модуля управления источника](../../extensibility/internals/creating-a-source-control-plug-in.md) где подключаемый модуль системы управления версиями должна реализовать жесткого набора функций и обратные вызовы.

  Как и любой пакет VSPackage, пакет системы управления версиями — это объект COM, которые могут быть созданы с помощью `CoCreateInstance`. VSPackage делает себя доступным для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. При создании экземпляра VSPackage получает указатель сайта и <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейсом, обеспечивающим доступ VSPackage для доступных службах и интерфейсах в интегрированной среде разработки.

  Написание пакет системы управления версиями на основе VSPackage требует более сложных опыт программирования, чем написание, основанная на API подключаемых модулей управления источник подключаемого модуля.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)