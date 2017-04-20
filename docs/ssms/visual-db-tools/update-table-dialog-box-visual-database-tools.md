---
title: "Диалоговое окно &quot;Обновление таблицы&quot; (визуальные инструменты для баз данных) | Документация Майкрософт"
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
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e0abd8866fecfd845e56cd1ea26eabfc87b1e3b5
ms.lasthandoff: 04/11/2017

---
# <a name="update-table-dialog-box-visual-database-tools"></a>Диалоговое окно «Обновление таблицы» (визуальные инструменты для баз данных)
Это диалоговое окно позволяет указать обновляемую таблицу.  
  
Это диалоговое окно появляется, если при изменении типа запроса на запрос обновления на панели диаграмм выведено более одной таблицы.  
  
Выберите обновляемую таблицу и нажмите кнопку **ОК**.  
  
> [!NOTE]  
> Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="see-also"></a>См. также:  
[Создание запросов UPDATE (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)  
  

