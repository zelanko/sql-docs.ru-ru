---
title: "sys.remote_data_archive_tables (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_tables
- sys.remote_data_archive_tables_TSQL
- remote_data_archive_tables
- remote_data_archive_tables_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.remote_data_archive_tables catalog view
ms.assetid: 765069b7-60fd-414c-875f-3455460b75cd
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b41baab19da3d1c42653fb397270ca74f4a54828
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stretch-database-catalog-views---sysremotedataarchivetables"></a>Растянуть представления каталога базы данных - sys.remote_data_archive_tables
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой удаленной таблицы, которая хранит данные из локальной таблицы с поддержкой Stretch.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта в локальной таблице с включенным Stretch.|  
|**remote_database_id**|**int**|Автоматически созданный локальный идентификатор удаленной базы данных.|  
|**remote_table_name**|**sysname**|Имя таблицы в удаленной базе данных, соответствующий локальной таблицы с включенным Stretch.|  
|**filter_predicate**|**nvarchar(max)**|Предикат фильтра, если таковые имеются, для идентификации строк в таблице для миграции. Если значение равно NULL, всю таблицу можно переносить.<br /><br /> Дополнительные сведения см. в разделе [включения базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) и [Выбор строк для миграции с помощью предиката фильтра](~/sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).|  
|**migration_direction**|**tinyint**|Направление, в котором в настоящее время выполняется перенос данных. Ниже перечислены доступные значения.<br/>1 (исходящий)<br/>2 (входящий трафик)|  
|**migration_direction_desc**|**nvarchar(60)**|Описание направление, в котором в настоящее время выполняется перенос данных. Ниже перечислены доступные значения.<br/>исходящее (1)<br/>входящих подключений (2)|  
|**is_migration_paused**|**bit**|Указывает ли миграции в настоящий момент приостановлена.|  
|**is_reconciled**|**bit**| Указывает, синхронизированы ли удаленной таблицы в таблицу SQL Server.<br/><br/>Если значение **is_reconciled** -1 (true), удаленной таблицей и таблицей SQL Server находятся в синхронизированном состоянии и выполнении запросов, содержащих удаленные данные.<br/><br/>Если значение **is_reconciled** равно 0 (false), в удаленной таблице и таблице SQL Server не синхронизированы. Недавно перенесенные строки нужно перенести еще раз. Это происходит при восстановлении удаленной базы данных Azure, или когда вручную удалить строки из удаленной таблицы. Пока выверить таблицы нельзя запускать запросы, включающие удаленных данных. Чтобы согласовать таблиц, запустите [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md). |  
  
## <a name="see-also"></a>См. также:  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

