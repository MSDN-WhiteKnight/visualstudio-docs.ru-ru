---
title: Разделение наборов данных и адаптеров таблиц на разные проекты | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bfd6cc62fc93ca3a535fb60c4ea5e1323c720558
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690236"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Разделение наборов данных и TableAdapter на разные проекты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Типизированные наборы данных были усовершенствованы, чтобы [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) и классы наборов данных могут быть созданы в отдельные проекты. Это дает возможность быстро разделять слои приложения и создавать многоуровневые приложения.  
  
 Следующая процедура описывает процесс использования конструктора наборов данных для создания кода набора данных в проект, который отличается от проекта, который содержит созданный `TableAdapter` кода.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets и адаптеров таблиц  
 При разделении набора данных код из `TableAdapter` кода, содержащего код набора данных должен быть расположен в текущем решении. Если этот проект не находится в текущем решении, оно действует в **проект DataSet** в списке **свойства** окна.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Для разделения набора данных на другой проект  
  
1. Откройте решение, которое содержит набор данных (XSD-файл).  
  
   > [!NOTE]
   > Если решение содержит проект, в которую необходимо выделить код набора данных, создать проект или добавить существующий проект в решение.  
  
2. Дважды щелкните файл типизированного набора данных (XSD-файл) в **обозревателе решений** чтобы открыть набор данных в **конструктор наборов данных**.  
  
3. Выберите пустую область **конструктор наборов данных**.  
  
4. В **свойства** окна, найдите **проект DataSet** узла.  
  
5. В **проект DataSet** выберите имя проекта, в который требуется создать код набора данных.  
  
    После выбора проекта, в который требуется создать код набора данных, **файл набора данных** свойство заполняется имя файла по умолчанию. Это имя можно изменить при необходимости. Кроме того, если требуется создать код набора данных в определенный каталог, можно задать **папку проекта** имя папки.  
  
   > [!NOTE]
   > При разделении наборов данных и адаптеров таблиц (задавая **проект DataSet** свойство), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
6. Сохраните набор данных.  
  
    Код набора данных создается в выбранный проект в **проект DataSet** свойство и **TableAdapter** код помещается в текущий проект.  
  
   По умолчанию, после разделения набора данных и `TableAdapter` кода, результат — это отдельные файлы классов в каждом проекте. Исходный проект содержит файл с именем DatasetName.Designer.vb (или DatasetName.Designer.cs), содержащий `TableAdapter` кода. Проект, который определен в **проект Dataset** свойство имеется файл с именем DatasetName.DataSet.Designer.vb (или DatasetName.DataSet.Designer.cs), содержащий код набора данных.  
  
> [!NOTE]
> Чтобы просмотреть файл созданный класс, выберите набор данных или `TableAdapter` проекта. Затем в **обозревателе решений**выберите **Показать все файлы** .  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о данных в N-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)   
 [Пошаговое руководство: Создание данных N-уровневого приложения](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Иерархическое обновление](../data-tools/hierarchical-update.md)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
