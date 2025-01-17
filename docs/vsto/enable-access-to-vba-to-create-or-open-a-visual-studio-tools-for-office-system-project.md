---
title: VBA доступа, чтобы создать или открыть проект VSTO system
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
titleSuffix: Visual Studio Tools for Microsoft Office
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c85a907b057118c28ea35b8a920337ecdad5ad01
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177653"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Включение доступа к коду VBA, чтобы создать или открыть Visual Studio Tools для системы Microsoft Office проекта

Доступ к Visual Basic для приложений (VBA) система проектов в Microsoft Office необходимо включить явным образом в том случае, прежде чем можно будет создать или открыть Visual Studio Tools для системы Microsoft Office проекта.

 Разработка проектов Microsoft Office требуют доступа к Visual Basic для приложений (VBA) система проектов в Microsoft Office Word и Microsoft Office Excel, несмотря на то, что проекты не используют Visual Basic для приложений. Поддержка элементов управления времени разработки в проектах Visual Basic и C# зависит от системы проектов Visual Basic для приложений.

 Некоторые макровирусы Microsoft Office пытаются автоматизировать систему проектов Visual Basic для приложений как способ своего распространения. Разрешая доступ к системе проектов Visual Basic для приложений, вы отключаете средство защиты, которое позволяет предотвратить распространение макровирусов. Тем не менее, остаются стандартные средства обеспечения безопасности макросов: уровень безопасности макросов и список надежных издателей, поддерживаемый для приложений Office, помогут выявить выполнение макросов на компьютере.

> [!NOTE]
> Это касается только компьютера разработки. Компьютеры конечных пользователей не обязательно включать эту возможность для запуска решений Office.

 Важно отметить, что отключение доступа к системе проектов Visual Basic для приложений само по себе не защитит вас от вирусов, оно просто помогает предотвратить распространение некоторых вирусов в другие документы в случае заражения компьютера макровирусом. Эта возможность отключена по умолчанию, что обеспечивает дополнительный уровень защиты компьютера. Однако ее включение не делает ваш компьютер более подверженным атакам, если вы выполняете рекомендации по обеспечению безопасности.

 Лучший способ защиты от макровирусов Office — выполнение приложений Office с высоким или очень высоким уровнем безопасности, доверять макросам только из проверенных и известных источников и будьте в курсе обновлений и антивирусных программ.

 Можно включить или отключить параметр **Доверять доступ к Visual Basic Project** вручную.

 При появлении ошибок VBA или COM можно восстановить установку Office.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Чтобы включить или отключить доступ к проектам Visual Basic

1. Перейдите на вкладку **Файл** .

2. Щелкните **Параметры**.

3. Нажмите кнопку **Центр управления безопасностью**, а затем нажмите кнопку **параметры центра управления безопасностью**.

4. В **Центр управления безопасностью**, нажмите кнопку **Macro Settings**.

5. Установите или снимите флажок **Доверять доступ к объектной модели project VBA** для включения или отключения доступа к проектам Visual Basic.

6. Нажмите кнопку **ОК**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Чтобы включить или отключить доступ к проектам Visual Basic в выпуске 2007 системы Microsoft Office

1. На **средства** меню в Word или Excel, укажите **макрос**, а затем нажмите кнопку **безопасности**.

2. В **безопасности** диалоговом окне щелкните **Доверенные издатели** вкладки.

3. Выберите для включения или снимите флажок, чтобы отключить, **Доверять доступ к Visual Basic Project**.

4. Нажмите кнопку **ОК**.

## <a name="to-set-your-office-macro-security-level"></a>Настройка уровня безопасности макросов в Office

1. Перейдите на вкладку **Файл** .

2. Щелкните **Параметры**.

3. Нажмите кнопку **Центр управления безопасностью**, а затем нажмите кнопку **параметры центра управления безопасностью**.

4. В **Центр управления безопасностью**, нажмите кнопку **Macro Settings**.

5. В **Macro Settings** выберите нужный параметр.

6. Нажмите кнопку **ОК**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Чтобы задать уровень безопасности макросов Office выпуска 2007 системы Microsoft Office

1. На **средства** меню в Word или Excel, укажите **макрос**, а затем нажмите кнопку **безопасности**.

2. На **уровень безопасности** выберите нужный параметр.

    **Уровень безопасности** вкладка содержит сведения о каждом уровне. Дополнительные сведения см. в разделе "Уровни безопасности макросов" справки Microsoft Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Установка VBA в выпуске 2007 системы Microsoft Office

1. В панели управления запустите **Установка и удаление программ** или **программы и компоненты**.

2. Выберите Office в **установленные программы** списка.

3. Щелкните **Изменить**.

4. Выберите **добавить или удалить компоненты**, а затем нажмите кнопку **Продолжить**.

5. Выберите **Расширенная настройка приложений**, а затем нажмите кнопку **Далее**.

6. Разверните **общие компоненты Office** в **выберите параметры обновления приложений и средств** списка.

7. Откройте раскрывающееся меню рядом с полем **Visual Basic for Applications**, а затем нажмите кнопку **запускать с моего компьютера**.

8. Нажмите кнопку **Продолжить**.

9. Нажмите кнопку **Закрыть**.

## <a name="to-repair-your-installation-of-office"></a>Восстановление установки Office

1. В панели управления запустите **Установка и удаление программ** или **программы и компоненты**.

2. Выберите нужную версию Office в **установленные программы** списка.

3. Щелкните **Изменить**.

4. Выберите **переустановка или восстановление**, а затем нажмите кнопку **Далее**.

5. Выберите **найти и исправить ошибки в установке Office**, а затем нажмите кнопку **установить**.

## <a name="see-also"></a>См. также
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
