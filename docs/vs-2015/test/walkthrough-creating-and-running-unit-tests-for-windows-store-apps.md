---
title: Пошаговое руководство. Создание и запуск модульных тестов для приложений Windows Store | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1f74502472a72416d33bcf48e473977d694e545f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695112"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>Пошаговое руководство. Создание и запуск модульных тестов для приложений Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio включает поддержку модульного тестирования управляемых приложений [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] и шаблоны библиотек модульных тестов для Visual C#, Visual Basic и Visual C++.  
  
> [!TIP]
> Дополнительные сведения о разработке приложений [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] см. в разделе [Начало работы с приложениями Магазина Windows](http://go.microsoft.com/fwlink/?LinkID=241410).  
  
 Visual Studio предоставляет следующие возможности модульного тестирования:  
  
- [Создание проектов модульных тестов](#CreateAndRunUnitTestWin8Tailored_Create)  
  
- [Правка манифеста для проекта модульного теста](#CreateAndRunUnitTestWin8Tailored_Manifest)  
  
- [Создание кода модульного теста](#CreateAndRunUnitTestWin8Tailored_Code)  
  
- [Запуск модульных тестов](#CreateAndRunUnitTestWin8Tailored_Run)  
  
  В следующих процедурах описаны этапы создания, выполнения и отладки модульных тестов для управляемого приложения Windows 8 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)].  
  
## <a name="prerequisites"></a>Предварительные требования  
 Visual Studio  
  
## <a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Создание проектов модульных тестов  
  
#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Создание проектов модульных тестов для приложения Магазина Windows  
  
1. В меню **Файл** выберите пункт **Создать проект**.  
  
     Откроется диалоговое окно "Создать проект".  
  
2. В разделе "Шаблоны" выберите язык программирования, на котором требуется создать модульный тест, а затем выберите связанную библиотеку модульных тестов [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Например, выберите **Visual C#** , затем выберите **Магазин Windows**, а затем **Библиотека модульных тестов (приложения для Магазина Windows)**.  
  
    > [!NOTE]
    > Visual Studio включает шаблоны библиотек модульных тестов для Visual C#, Visual Basic и Visual C++.  
  
3. (Необязательно) В текстовом поле **Имя** введите имя, которое будет использоваться для проекта модульного теста [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)].  
  
4. (Необязательно) Измените путь, по которому нужно создать проект, введя его в текстовом поле **Расположение** или с помощью кнопки **Обзор** .  
  
5. (Необязательно) В текстовом поле имени **Решение** введите имя, которое будет использоваться для решения.  
  
6. Оставьте флажок **Создать каталог для решения** установленным и нажмите кнопку **ОК** .  
  
     ![Адаптированная библиотека модульных тестов](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")  
  
     В обозревателе решений появляется ваш новый проект модульного теста [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], а в редакторе кода отображается модульный тест по умолчанию с именем UnitTest1.  
  
     ![Новый адаптированный проект модульных тестов](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")  
  
## <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Правка манифеста для проекта модульного теста  
 Может потребоваться изменить манифест для проекта модульного теста, чтобы предоставить необходимые возможности запуска приложения.  
  
#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Изменение файла манифеста приложения для Магазина Windows проекта модульного теста  
  
1. В обозревателе решений в новом проекте модульного теста [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] щелкните правой кнопкой мыши файл Package.appxmanifest и выберите **Открыть**.  
  
     Конструктор манифеста открывается для редактирования.  
  
2. В конструкторе манифеста выберите вкладку **Возможности** .  
  
3. В списке в разделе **Возможности**выберите возможности, необходимые для модульного теста и тестируемого кода. Например, установите флажок **Интернет** , если модульный тест и проверяемый им код требуют возможности получения доступа к Интернету.  
  
    > [!NOTE]
    > Выбранные функции должны включать только возможности, необходимые для правильного функционирования модульного теста [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Эти возможности никогда не должны включать функции, которые не входят в состав тестируемого приложения [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], и обычно должны представлять собой подмножество функций, определенных для тестируемого приложения [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)].  
  
     См. дополнительные сведения о [настройке пакета приложения Windows 8.1 с помощью конструктора манифеста](https://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).  
  
     ![Манифест модульного теста](../test/media/unit-test-win8.png "Unit_Test_Win8_")  
  
## <a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Создание кода модульного теста  
  
#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Кодирование модульного теста для приложения Магазина Windows  
  
1. В редакторе кода добавьте модульный тест и включите необходимые утверждения и логику.  
  
     Дополнительные сведения см. в статье [Использование классов утверждений](http://go.microsoft.com/fwlink/?LinkID=224991) в библиотеке MSDN.  
  
## <a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Запуск модульных тестов  
  
#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Сборка решения и выполнение модульного теста с помощью обозревателя тестов  
  
1. В меню **Тест** выберите **Windows**, а затем **Обозреватель тестов**.  
  
     Отображается обозреватель тестов без вашего теста.  
  
2. В меню **Построение** выберите пункт **Построить решение**.  
  
     Модульный тест теперь присутствует в списке.  
  
    > [!NOTE]
    > Необходимо собрать решение, чтобы обновить список модульных тестов в обозревателе тестов.  
  
    > [!WARNING]
    > Известная проблема Visual Studio: Необходимо открыть обозреватель тестов до создания тестового проекта.  
  
3. В обозревателе тестов выберите созданный модульный тест.  
  
    > [!TIP]
    > Обозреватель тестов содержит ссылку на исходный код рядом с надписью **Источник:**.  
  
4. Выберите **Запустить все**.  
  
     ![Обозреватель модульных тестов — запуск модульного теста](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")  
  
    > [!TIP]
    > Можно выбрать один или несколько модульных тестов, перечисленных в обозревателе, а затем щелкнуть правой кнопкой мыши и выбрать **Запуск выбранных тестов**.  
    >   
    >  Кроме того, можно выбрать **Отладить выбранные тесты**, **Открыть тест**и использовать параметр **Свойства** .  
    >   
    >  ![Обозреватель модульных тестов — контекстное меню модульного теста](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")  
  
     Выполняется модульный тест. По завершении обозреватель тестов отображает состояние теста, затраченное время и содержит ссылку на источник.  
  
     ![Обозреватель модульных тестов — тест завершен](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
### <a name="videos"></a>Видеоролики  
 [Канал 9. Модульное тестирование приложений Windows Store, созданных с помощью XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Форумы  
 [Модульное тестирование Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="msdn-library"></a>Библиотека MSDN  
 [Библиотека MSDN. Создание и запуск модульных тестов для существующего кода (Visual Studio 2010)](http://go.microsoft.com/fwlink/?LinkID=223683)  
  
## <a name="see-also"></a>См. также  
 [Тестирование приложений Магазина с помощью Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Сборка и тестирование приложений для магазина Windows с использованием Team Foundation Build](https://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)
