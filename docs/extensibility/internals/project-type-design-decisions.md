---
title: Проект проектные решения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 697b09ff5725de954963f7583271ac9ebd6814a8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328122"
---
# <a name="project-type-design-decisions"></a>Проектные решения для типа проекта
Прежде чем создавать новый тип проекта, нужно принять несколько решений проектирования, касающиеся типа проекта. Необходимо решить, какие типы элементов, которые будет содержать проекты, как будут сохранены файлы проекта и какие обязательства модели будет использоваться.

## <a name="project-items"></a>Элементы проекта
 Проект будет использовать файлы или абстрактных объектов? Если вы используете файлы, они будут основано на ссылке или на основе directory файлов? -Файлы или абстрактных объектов, которые попадают в быть локальным или удаленным?

 Элементы в проекте может быть файлы, или их можно более абстрактные объекты, такие как объекты в репозиторий или данных подключения к базе данных через Интернет. Если они есть файлы, проект может быть основано на ссылке или проекта на основе каталогов.

 В проектах на основе ссылок элементы могут находиться более одного проекта. Тем не менее фактический файл, который представляет элемент находится в одном каталоге только. В проектах на основе каталогов все элементы проекта существует в структуре каталогов.

 Локальные элементы хранятся на том же компьютере, где установлено приложение. Удаленных элементов могут храниться на отдельном сервере в локальной сети или в другом месте в Интернете.

## <a name="project-file-persistence"></a>Сохранение файла проекта
 Данные сохраняются в распространенных систем неструктурированного файла или в структурированном виде? Будет открыт файлы с помощью стандартного редактора или редактора определенного проекта?

 Чтобы сохранить свои данные, большинство приложений сохранить свои данные в файле и затем считываются обратно в том случае, когда пользователю необходимо просмотреть или изменить сведения.

 Структурированного хранилища, также называется составные файлы обычно используется, когда требуется несколько объектов модели объектов компонента (COM) хранят свои данные, сохраненные в один файл. Со структурированным хранилищем файл одного диска можно использовать несколько различных программных компонентов.

 У вас есть несколько вариантов, которые следует учитывать при сохраняемости для элементов в проекте. Можно выполнить одно из следующих вариантов:

- Сохраните каждый файл по отдельности, когда он был изменен.

- Записать число транзакций в одном **Сохранить** операции.

- Сохранение файлов в локальной среде и опубликовать на сервере или использовать другой подход к сохранение элементов проекта, если элемент представляет подключение данных к удаленному объекту.

  Дополнительные сведения о постоянном хранении см. в разделе [сохранение проекта](../../extensibility/internals/project-persistence.md) и [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Модель проекта обязательств
 Материализованные объекты данных открывается в режиме прямого подключения или режиме транзакций?

 При открытии объектов данных в режиме прямого подключения, изменения, внесенные в данные вносятся немедленно, или когда пользователь вручную сохраняет файл.

 При открытии объекты данных с помощью режима транзакций, изменения будут сохранены во временное расположение в памяти и не фиксируются до вручную не выбран для сохранения файла. В этот момент все изменения должны происходить вместе или не будут изменены.

## <a name="see-also"></a>См. также
- [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)
- [Сохранение проекта](../../extensibility/internals/project-persistence.md)
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)
- [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)
- [Создание типов проектов](../../extensibility/internals/creating-project-types.md)