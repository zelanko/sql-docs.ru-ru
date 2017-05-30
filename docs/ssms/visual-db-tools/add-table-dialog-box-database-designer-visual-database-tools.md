---
title: "Диалоговое окно &quot;Добавление таблицы&quot; в конструкторе базы данных (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 275f2120bd76147916f1ba6d24d59dc450ed7c8b
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Диалоговое окно «Добавление таблицы» (конструктор базы данных) (визуальные инструменты для баз данных)
Позволяет добавлять таблицы в конструкторе базы данных.  
  
> [!NOTE]  
> Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
**Обновить**  
Обновляет список таблиц для соответствия текущему состоянию базы данных.  
  
**Добавить**  
Добавляет выбранную таблицу или таблицы.  
  
> [!NOTE]  
> Если нужно добавить несколько таблиц к диаграмме, можно выбрать их все, а затем нажать кнопку **Добавить**. Или можно дважды щелкнуть каждую таблицу, которую нужно добавить, а затем, по окончании, нажать кнопку **Закрыть** .  
  
**Закрыть**  
Закрывает диалоговое окно без дальнейшего добавления таблиц.  
  
## <a name="see-also"></a>См. также:  
[Добавление таблиц в диаграммы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  

