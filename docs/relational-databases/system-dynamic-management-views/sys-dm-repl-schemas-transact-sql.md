---
title: sys.dm_repl_schemas (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_repl_schemas_TSQL
- dm_repl_schemas
- sys.dm_repl_schemas_TSQL
- sys.dm_repl_schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_schemas dynamic management function
ms.assetid: 6f5fefff-8492-4360-bd5b-a97287367914
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b57aedba448f2ce94f5a5fc7756e3a27d7a95f96
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmreplschemas-transact-sql"></a>sys.dm_repl_schemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о столбцах таблицы, опубликованных в ходе репликации.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artcache_schema_address**|**varbinary(8)**|Внутренний адрес кэшированной структуры схемы в памяти для статьи опубликованной таблицы.|  
|**tabid**|**bigint**|Идентификатор реплицируемой таблицы.|  
|**IndexID**|**smallint**|Идентификатор кластеризованного индекса для опубликованной таблицы.|  
|**idSch**|**bigint**|Идентификатор схемы таблицы.|  
|**tabschema**|**nvarchar(510)**|Имя схемы таблицы.|  
|**ccTabschema**|**smallint**|Длина символов в схеме таблицы.|  
|**tabname**|**nvarchar(510)**|Имя опубликованной таблицы.|  
|**ccTabname**|**smallint**|Длина символов в имени опубликованной таблицы.|  
|**rowsetid_delete**|**bigint**|Идентификатор удаленной строки.|  
|**rowsetid_insert**|**bigint**|Идентификатор вставленной строки.|  
|**num_pk_cols**|**int**|Число первичных ключевых столбцов.|  
|**pcitee**|**binary(8000)**|Указатель на структуру выражения запроса, используемую для получения значения вычисляемого столбца.|  
|**re_numtextcols**|**int**|Число столбцов больших бинарных объектов в реплицируемой таблице.|  
|**re_schema_lsn_begin**|**binary(8000)**|Начальный регистрационный номер транзакции в журнале (LSN) для записи версии схемы в журнале.|  
|**re_schema_lsn_end**|**binary(8000)**|Конечный номер LSN для записи версии схемы в журнале.|  
|**re_numcols**|**int**|Число опубликованных столбцов.|  
|**re_colid**|**int**|Идентификатор столбца на стороне издателя.|  
|**re_awcName**|**nvarchar(510)**|Имя опубликованного столбца.|  
|**re_ccName**|**smallint**|Число символов в имени столбца.|  
|**re_pk**|**tinyint**|Показывает, является ли опубликованный столбец частью первичного ключа.|  
|**re_unique**|**tinyint**|Показывает, является ли опубликованный столбец частью уникального индекса.|  
|**re_maxlen**|**smallint**|Максимальная длина опубликованного столбца.|  
|**re_prec**|**tinyint**|Точность опубликованного столбца.|  
|**re_scale**|**tinyint**|Масштаб опубликованного столбца.|  
|**re_collatid**|**bigint**|Идентификатор параметров сортировки для опубликованного столбца.|  
|**re_xvtype**|**smallint**|Тип опубликованного столбца.|  
|**re_offset**|**smallint**|Смещение опубликованного столбца.|  
|**re_bitpos**|**tinyint**|Битовая позиция опубликованного столбца в байтовом векторе.|  
|**re_fNullable**|**tinyint**|Показывает, поддерживаются ли для опубликованного столбца значения NULL.|  
|**re_fAnsiTrim**|**tinyint**|Показывает, используется ли для опубликованного столбца обрезок ANSI.|  
|**re_computed**|**smallint**|Показывает, является ли опубликованный столбец вычисляемым.|  
|**se_rowsetid**|**bigint**|Идентификатор набора строк.|  
|**se_schema_lsn_begin**|**binary(8000)**|Начальный номер LSN для записи версии схемы в журнале.|  
|**se_schema_lsn_end**|**binary(8000)**|Конечный номер LSN для записи версии схемы в журнале.|  
|**se_numcols**|**int**|Число столбцов.|  
|**se_colid**|**int**|Идентификатор столбца на стороне подписчика.|  
|**se_maxlen**|**smallint**|Максимальная длина столбца.|  
|**se_prec**|**tinyint**|Точность столбца.|  
|**se_scale**|**tinyint**|Масштаб столбца.|  
|**se_collatid**|**bigint**|Идентификатор параметров сортировки для столбца.|  
|**se_xvtype**|**smallint**|Тип столбца.|  
|**se_offset**|**smallint**|Смещение столбца.|  
|**se_bitpos**|**tinyint**|Битовая позиция столбца в байтовом векторе.|  
|**se_fNullable**|**tinyint**|Показывает, поддерживаются ли для столбца значения NULL.|  
|**se_fAnsiTrim**|**tinyint**|Показывает, используется ли для столбца усечение ANSI.|  
|**se_computed**|**smallint**|Показывает, является ли столбец вычисляемым.|  
|**se_nullBitInLeafRows**|**int**|Показывает, равняется ли значение столбца NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение VIEW DATABASE STATE в базе данных публикации на вызов **dm_repl_schemas**.  
  
## <a name="remarks"></a>Замечания  
 Возвращаются сведения только по реплицируемым объектам базы данных, которые загружены в кэш статей репликации.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с репликацией &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  

