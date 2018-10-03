---
title: Создание шаблонов проектов и элементов | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e288329637c6a6f421a5b32f19084897a31e5f22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572324"
---
# <a name="creating-project-and-item-templates"></a>Создание шаблонов проектов и элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Создание проектов и шаблонов элементов](https://docs.microsoft.com/visualstudio/ide/creating-project-and-item-templates).  
  
Шаблоны проектов и элементов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляют многократно используемые заглушки, обеспечивающие пользователям определенный базовый код и структуры, которые можно использовать в своих целях.  
  
## <a name="visual-studio-templates"></a>Шаблоны Visual Studio  
 При установке [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] устанавливается ряд предопределенных шаблонов проектов и элементов. Шаблоны приложений Windows Forms и библиотек классов [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] и [!INCLUDE[csprcs](../includes/csprcs-md.md)], доступные в диалоговом окне **Новый проект**, являются примерами шаблонов проектов. Установленные шаблоны элементов доступны в диалоговом окне **Добавление нового элемента** и включают в себя такие элементы, как файлы кода, XML-файлы, HTML-страницы и таблицы стилей.  
  
 Для пользователей эти шаблоны представляют собой отправную точку, с которой можно начать создание новых проектов или расширение текущих проектов. Шаблоны проектов предоставляют файлы, необходимые для конкретного типа проекта, включая стандартные ссылки на сборки, задают свойства проекта и параметры компилятора по умолчанию. По сложности шаблоны элементов могут варьироваться от одного пустого файла с правильным расширением до элемента из нескольких файлов, содержащего, например, файлы исходного кода, которые содержат код заглушек, файлы сведений о конструкторе и внедренные ресурсы.  
  
 Кроме использования установленных шаблонов в диалоговых окнах **Новый проект** и **Добавление нового элемента**, вы можете создавать собственные шаблоны, а также скачивать и использовать шаблоны, созданные сообществом. Дополнительные сведения см. в статьях [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md) и [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md).  
  
## <a name="contents-of-a-template"></a>Содержимое шаблона  
 Все шаблоны проектов и элементов, установленные вместе с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] или созданные пользователем, работают на основе одних и тех же принципов и имеют схожее содержимое. Все шаблоны содержат следующие элементы:  
  
-   Файлы, создаваемые при использовании шаблона. Сюда входят файлы с исходным кодом, внедренные ресурсы, файлы проекта и т. д.  
  
-   Один VSTEMPLATE-файл. Этот файл содержит метаданные, которые предоставляют [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] сведения, необходимые для отображения шаблона в диалоговых окнах **Новый проект** и **Добавление нового элемента**, а также для создания проекта или элемента из шаблона. Дополнительные сведения о VSTEMPLATE-файлах см. в статье [Параметры шаблона](../ide/template-parameters.md).  
  
 Если эти файлы сжаты в ZIP-файл и помещены в соответствующую папку, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически отображает их. Шаблоны проектов отображаются в разделе **Мои шаблоны** диалогового окна **Новый проект**, а шаблоны элементов — в диалоговых окнах **Добавление нового элемента**. Дополнительные сведения о папках шаблонов см. в статье [Практическое руководство. Размещение и упорядочение шаблонов](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="starter-kits"></a>Наборы для начинающих  
 Начальные наборы являются усовершенствованными шаблонами, которые можно использовать совместно с другими членами сообщества. Начальный набор содержит компилируемые образцы кода, документацию и другие ресурсы, помогающие пользователям освоить новые инструменты и методы программирования во время разработки полезных реальных приложений. В начальных наборах используются те же основные процедуры и содержимое, что и в обычных шаблонах. Дополнительные сведения см. в статье [Практическое руководство. Создание начальных наборов](../ide/how-to-create-starter-kits.md).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md)   
 [Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)   
 [Практическое руководство. Создание начальных наборов](../ide/how-to-create-starter-kits.md)


