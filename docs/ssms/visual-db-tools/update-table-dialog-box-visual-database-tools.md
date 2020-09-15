---
description: Диалоговое окно «Обновление таблицы» (визуальные инструменты для баз данных)
title: Диалоговое окно "Обновить таблицу"
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 93c0ed1368325ec27ff9ebb640f48ee45f7de8ea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88369180"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>Диалоговое окно «Обновление таблицы» (визуальные инструменты для баз данных)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Это диалоговое окно позволяет указать обновляемую таблицу.

Это диалоговое окно появляется, если при изменении типа запроса на запрос обновления на панели диаграмм выведено более одной таблицы.  

Выберите обновляемую таблицу и нажмите кнопку **ОК**.

> [!NOTE]
> Если таблица опубликована для репликации, то изменения схемы следует проводить при помощи инструкции языка Transact-SQL [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) или объектов SMO. При изменении схемы с помощью конструктора таблиц или конструктора диаграмм баз данных конструктор пытается удалить и затем вновь создать таблицу. Но поскольку удалять опубликованные объекты нельзя, изменения схемы не будут применены.

## <a name="see-also"></a>См. также:

[Создание запросов на обновление](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)
