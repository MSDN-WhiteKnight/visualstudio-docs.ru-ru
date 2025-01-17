---
title: Шаблоны поддержки веб-сайтов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e9229a2614d2d797a5a2159df5b18a92850edbd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323274"
---
# <a name="web-site-support-templates"></a>Шаблоны поддержки веб-сайтов
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Веб-сайт шаблонов проектов и элементов предоставляют многократно используемых и настраиваемые веб-узел проектов и элементов, позволяющую ускорить процесс разработки, избавляя от необходимости создание новых проектов веб-сайта и элементов с нуля. Дополнительные сведения о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] шаблонов, см. в разделе [Создание проектов и шаблонов элементов](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Папка шаблонов проекта
 Шаблоны веб-проектов обычно устанавливаются на [*путь установки Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, каждый во вложенной папке с именем после выполнения веб-язык программирования.

## <a name="project-file"></a>Файл проекта
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) требуется расширение файла проекта в качестве способа сопоставления шаблона к типу нужный проект. Поскольку веб-проектов не имеют файл проекта, с расширением WEBPROJ фиктивный проект расширение файла регистрируется для сопоставления шаблона с типом проекта.

 При необходимости можно добавить строку имени языковой в шаблон, чтобы задать язык по умолчанию в системе проектов Web **Добавление нового элемента** диалоговое окно для элементов на основе шаблона. Строка должна быть первая строка файла. Он должен соответствовать как имя, зарегистрированное в группе AddItemLanguageName в регистрации обработчик IntelliSense, так и имя, зарегистрированное в группе Subtype(VsTemplate) проекта. Дополнительные сведения см. в разделе [атрибуты поддержки веб-сайт](../../extensibility/internals/web-site-support-attributes.md).

 Если строка не существует, веб-проекта системы пытается определить язык по умолчанию, в зависимости от расширения атрибута и файл языка страниц, добавлены в веб-проект с помощью шаблона проекта.

## <a name="project-templates"></a>Шаблоны проектов
 Шаблоны проекта веб-узлов используются для создания нового веб-сайтов в ответ на **новый веб-сайт** команды **файл** меню. В настоящее время поддерживаются три типа проектов веб-сайта:

- Пустой веб-узел проектов

- Проекты веб-сайта

- Проекты веб-службы

### <a name="empty-web-site-projects"></a>Пустой веб-узел проектов
 Эти файлы создавать новый пустой веб-сайт в ответ на **пустой веб-сайт** команды, которая доступна после выбора **файл** > **новый веб-сайт**:

- EmptyWeb.vstemplate

     Файл шаблона, который помогает создавать новый пустой веб-сайт.

- EmptyWeb.webproj

     Этот файл — это артефакт системы шаблона проекта. Он соответствует свойству ссылку на файл проекта в файле EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Проекты веб-сайта
 Эти файлы создать новый веб-сайт в ответ на **веб-сайт ASP.NET** команды, которая доступна после выбора **файл** > **новый веб-сайт**:

- Default.aspx

     Домашняя страница по умолчанию для новых веб-сайта. Атрибут Language задает язык фонового кода, и атрибут CodeFile указывает зависимый файл, содержащий код фонового кода, связанный с этой страницей.

- Default.aspx. *расширения*

     Зависимый файл, содержащий код фонового кода для домашней страницы по умолчанию. Язык фонового кода определяет *расширение* этого файла.

- web.config.

     Корневой файл конфигурации web.site.

- WebApplication.vstemplate

     Файл шаблона, который определяет содержимое решения веб-сайта и принудительно создает папку App_Data.

- WebApplication.webproj

     Этот файл — это артефакт системы шаблона проекта. Он соответствует свойству ссылку на файл проекта в файле WebApplication.vstemplate.

### <a name="web-service-projects"></a>Проекты веб-службы
 Эти файлы создать новый веб-сайт в ответ на **веб-службы ASP.NET** команды, которая доступна после выбора **файл** > **новый веб-сайт**:

- Service.asmx

     Страницу HTML для новой веб-службы. Атрибут Language задает язык фонового кода, с указанием атрибут CodeBehind зависимый файл, содержащий код фонового кода, связанный с этой службой.

- Служба. *Расширение*

     Зависимый файл, который реализует класс службы. Язык фонового кода определяет *расширение* этого файла.

- web.config.

- Корневой файл конфигурации web.site.

- WebService.vstemplate

     Файл шаблона, который определяет содержимое решения веб-сайта и принудительно создает папки App_Data и App_Code. Служба. *расширение* файл копируется в папку App_Code.

- WebService.webproj

     Этот файл — это артефакт системы шаблона проекта. Он соответствует свойству ссылку на файл проекта в файле WebService.vstemplate.

## <a name="project-item-template-folder"></a>Папка шаблонов элемента проекта
 Веб-шаблонов элементов проекта, обычно устанавливаются в [*путь установки Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, каждый во вложенной папке с именем после его веб-программирования языка.

## <a name="project-item-templates"></a>Шаблоны элементов проекта
 Шаблоны элементов проекта веб-сайта можно использовать для добавления новых веб-страниц на веб-сайт в ответ на **добавить существующий элемент** команды. В настоящее время поддерживаются следующие виды веб-страниц:

- Новый класс

- Новая страница HTML

- Новый веб-формы

- Новую эталонную страницу

### <a name="new-class"></a>Новый класс
 Этот шаблон создает новый исходный файл, который определяет пустой класс в ответ на **Добавление нового класса** команды.

- Класс. *Расширение*

     Исходный файл, который реализует пустой класс. Язык фонового кода определяет *расширение* этого файла.

- Class.vstemplate

     Файл шаблона, который создает исходный файл и определяет его содержимое.

### <a name="new-html-page"></a>Новая страница HTML
 Этот шаблон создает новый веб-страницы в ответ на **добавить новый HTML-страницу** команды.

- HTMLPage.htm

     Начальный содержимое веб-страницы. Эту веб-страницу обычно не имеет связанного фонового кода зависимого файла. Чтобы создать смарт-страницу с файлом связанные фонового кода, используйте шаблон веб-форма.

- HTMLPage.vstemplate

     Файл шаблона, который создает веб-страницы и определяет его содержимое.

### <a name="new-webform"></a>Новый веб-форма
 Этот шаблон создает новый смарт-веб-страницы в ответ на **Добавление новой веб-формы** команды.

 Чтобы создать файл с исходным зависимые фонового кода, выберите **поместите код в отдельный файл**. В противном случае создается один веб-страницы, содержит пустой блок сценариев и не содержит \<% Page % > директивы подключить зависимого файла.

 Чтобы создать страницу содержимого для выбранного главной страницы, выберите **выбрать главную страницу**.

- WebForm.aspx

     Начальный содержимое веб-страницы. Эта веб-страница не имеет связанного фонового кода зависимые файла.

- WebForm_cb.aspx

     Начальный содержимое веб-страницы. Этот веб-странице есть файл зависимые связанные фонового кода.

- Фонового кода. *Расширение*

     Зависимый файл, который реализует класс веб-форма. Язык фонового кода определяет *расширение* этого файла.

- ContentPage.aspx

     Начальный содержимое веб-страницы странице содержимого. Эта веб-страница не имеет связанного фонового кода зависимые файла.

- ContentPage_cb.aspx

     Начальный содержимое веб-страницы странице содержимого. Этот веб-странице есть файл зависимые связанные фонового кода.

- WebForm.vstemplate

     Файл шаблона, который определяет содержимое новой веб-страницы и ее зависимый файл, если таковые имеются.

### <a name="new-master-page"></a>Создание главной страницы
 Этот шаблон создает новой главной страницы в ответ на **добавить Создание главной страницы** команды.

 Чтобы создать файл с исходным зависимые фонового кода, выберите **поместите код в отдельный файл**. В противном случае создается один веб-страницы, содержит пустой блок сценариев и не содержит \<% Page % > директивы подключить зависимого файла.

- MasterPage.master

     Начальный содержимое главной страницы. Эта главная страница не имеет связанного фонового кода зависимого файла.

- MasterPage_cb.master

     Начальный содержимое главной страницы. Эта главная страница имеет файл зависимые связанные фонового кода.

- Фонового кода. *расширения*

     Зависимый файл, который реализует класс главной страницы. Язык фонового кода определяет *расширение* этого файла.

- MasterPage.vstemplate

     Файл шаблона, который определяет содержимое главной страницы Обновить и ее зависимый файл, если таковые имеются.

## <a name="see-also"></a>См. также
- [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)