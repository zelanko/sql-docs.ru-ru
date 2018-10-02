---
title: Диалоговое окно "Обновление таблицы" (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 12369b0136b949409a81da44a5c40397c55aa53d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752742"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>Диалоговое окно «Обновление таблицы» (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Это диалоговое окно позволяет указать обновляемую таблицу.  
  
Это диалоговое окно появляется, если при изменении типа запроса на запрос обновления на панели диаграмм выведено более одной таблицы.  
  
Выберите обновляемую таблицу и нажмите кнопку **ОК**.  
  
> [!NOTE]  
> Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="see-also"></a>См. также:  
[Создание запросов UPDATE (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)  
  
