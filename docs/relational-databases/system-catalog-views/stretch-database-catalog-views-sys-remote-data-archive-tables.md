---
title: sys.remote_data_archive_tables (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d94d4788c071a9c5acc006afad9fe119bc0e9c77
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425563"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivetables"></a>Stretch Database представления каталога - sys.remote_data_archive_tables
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой удаленной таблицы, в которой хранятся данные из локальной таблицы с поддержкой Stretch.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта локальной таблицы, совместимых со Stretch.|  
|**remote_database_id**|**int**|Автоматически созданный локальный идентификатор удаленной базы данных.|  
|**remote_table_name**|**sysname**|Имя таблицы в удаленной базе данных, соответствующий локальной таблицы, совместимых со Stretch.|  
|**filter_predicate**|**nvarchar(max)**|Предикат фильтра, если таковые имеются, для идентификации строк в таблице для миграции. Если значение равно NULL, всю таблицу можно переносить.<br /><br /> Дополнительные сведения см. в разделе [включить Stretch Database для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) и [Выбор строк для миграции с помощью предиката фильтра](~/sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).|  
|**migration_direction**|**tinyint**|Направление, в котором в настоящее время выполняется перенос данных. Ниже перечислены доступные значения.<br/>1 (исходящий трафик)<br/>2 (входящий трафик)|  
|**migration_direction_desc**|**nvarchar(60)**|Описание направление, в котором в настоящее время выполняется перенос данных. Ниже перечислены доступные значения.<br/>исходящее (1)<br/>входящих подключений (2)|  
|**is_migration_paused**|**bit**|Указывает, приостановлен ли миграции.|  
|**is_reconciled**|**bit**| Указывает, синхронизированы ли удаленной таблицы и таблицы SQL Server.<br/><br/>Если значение **is_reconciled** -1 (true), в удаленной таблице и таблице SQL Server находятся в синхронизированном и вы можете выполнять запросы, включающие удаленные данные.<br/><br/>Если значение **is_reconciled** равно 0 (false), в удаленной таблице и таблице SQL Server не синхронизированы. Недавно перенесенных строк требуется переносить еще раз. Это происходит при восстановлении удаленной базы данных Azure, или если вручную удалить строки из удаленной таблицы. Пока выверить таблицы нельзя запускать запросы, включающие удаленные данные. Чтобы согласовать в таблицах, запустите [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md). |  
  
## <a name="see-also"></a>См. также  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

