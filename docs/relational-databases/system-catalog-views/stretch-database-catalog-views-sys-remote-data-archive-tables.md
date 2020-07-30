---
title: sys. remote_data_archive_tables (Transact-SQL) | Документация Майкрософт
description: Узнайте, как sys. remote_data_archive_tables содержит по одной строке для каждой удаленной таблицы, в которой хранятся данные из локальной таблицы с поддержкой растяжения.
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_tables
- sys.remote_data_archive_tables_TSQL
- remote_data_archive_tables
- remote_data_archive_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_tables catalog view
ms.assetid: 765069b7-60fd-414c-875f-3455460b75cd
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: c4b2b32181360b9974a3acfe85cb166d7ebd515d
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248143"
---
# <a name="stretch-database-catalog-views---sysremote_data_archive_tables"></a>Stretch Database представлений каталога — sys. remote_data_archive_tables
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Содержит по одной строке для каждой удаленной таблицы, в которой хранятся данные из локальной таблицы с поддержкой растяжения.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта локальной таблицы с поддержкой растяжения.|  
|**remote_database_id**|**int**|Автоматически созданный локальный идентификатор удаленной базы данных.|  
|**remote_table_name**|**sysname**|Имя таблицы в удаленной базе данных, которая соответствует локальной таблице, поддерживающей растяжение.|  
|**filter_predicate**|**nvarchar(max)**|Предикат фильтра, если он есть, который определяет строки в таблице для переноса. Если значение равно null, то всю таблицу можно перенести.<br /><br /> Дополнительные сведения см. в разделе [включение Stretch Database для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) и [Выбор строк для миграции с помощью предиката фильтра](~/sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).|  
|**migration_direction**|**tinyint**|Направление, в котором данные переносятся в данный момент. Ниже приведены доступные значения.<br/>1 (исходящий трафик)<br/>2 (входящий трафик)|  
|**migration_direction_desc**|**nvarchar(60)**|Описание направления, в котором данные переносятся в данный момент. Ниже приведены доступные значения.<br/>исходящий трафик (1)<br/>входящий трафик (2)|  
|**is_migration_paused**|**bit**|Указывает, приостановлена ли миграция.|  
|**is_reconciled**|**bit**| Указывает, синхронизирована ли удаленная таблица и SQL Serverная таблица.<br/><br/>Если значение **is_reconciled** равно 1 (true), то удаленная таблица и SQL Serverная таблица синхронизируются, и можно выполнять запросы, включающие удаленные данные.<br/><br/>Если значение **is_reconciled** равно 0 (false), то удаленная таблица и SQL Serverная таблица не синхронизируются. Недавно перенесенные строки необходимо перенести снова. Это происходит при восстановлении удаленной базы данных Azure или при удалении строк вручную из удаленной таблицы. До согласования таблиц нельзя выполнять запросы, содержащие удаленные данные. Чтобы согласовать таблицы, выполните [sys. sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md). |  
  
## <a name="see-also"></a>См. также:  
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)  
  
  

