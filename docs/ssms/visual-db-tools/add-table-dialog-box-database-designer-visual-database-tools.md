---
title: Диалоговое окно "Добавление таблицы" (конструктор базы данных)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 9c005a61a742a0c589cf5ccc26f818b8479b6a14
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000760"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a>Диалоговое окно «Добавление таблицы» (конструктор базы данных) (визуальные инструменты для баз данных)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Позволяет добавлять таблицы в конструкторе базы данных.  
  
> [!NOTE]  
> Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.  
  
## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса  
**Обновить**  
Обновляет список таблиц для соответствия текущему состоянию базы данных.  
  
**Добавление**  
Добавляет выбранную таблицу или таблицы.  
  
> [!NOTE]  
> Если нужно добавить несколько таблиц к диаграмме, можно выбрать их все, а затем нажать кнопку **Добавить**. Или можно дважды щелкнуть каждую таблицу, которую нужно добавить, а затем, по окончании, нажать кнопку **Закрыть** .  
  
**Закрыть**  
Закрывает диалоговое окно без дальнейшего добавления таблиц.  
  
## <a name="see-also"></a>См. также:  
[Добавление таблиц в диаграммы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
