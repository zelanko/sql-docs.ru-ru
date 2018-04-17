---
title: sys.external_tables (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bf4bceb7932cb5f8a5f4f891015efb4e540d6cf9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysexternaltables-transact-sql"></a>sys.external_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Содержит по одной строке для каждой внешней таблицы в текущей базе данных.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|\<Унаследованные столбцы >||Список столбцов, наследуемых этим представлением см. в разделе [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).||  
|max_column_id_used|**int**|Максимальный идентификатор использовали для этой таблицы.||  
|uses_ansi_nulls|**бит**|Таблица была создана при установленном параметре SET ANSI_NULLS = ON.||  
|data_source_id|**int**|Идентификатор объекта для внешнего источника данных.||  
|file_format_id|**int**|Для внешних таблиц через HADOOP внешнего источника данных это идентификатор объекта для формата внешнего файла.||  
|location|**nvarchar(4000)**|Для внешних таблиц через HADOOP внешнего источника данных это путь к внешним данным в HDFS.||  
|reject_type|**tinyint**|Для внешних таблиц через HADOOP внешнего источника данных это способ, отклоненных строк учитываются при запросе внешних данных.|ЗНАЧЕНИЕ — количество отклоненных строк.<br /><br /> ПРОЦЕНТ — процент отклоненных строк.|  
|reject_value|**float**|Для внешних таблиц через HADOOP внешнего источника данных:<br /><br /> Для *reject_type =* значение, это число строк отказы для прежде чем он остановит запрос.<br /><br /> Для *reject_type* = процент, процент отклонения строки для прежде чем он остановит запроса.||  
|reject_sample_value|**int**|Для *reject_type* = процентное значение, число строк, которые необходимо загрузить, успешно или неудачно, вычисление процент отклоненных строк.|Значение NULL, если reject_type = значение.|  
|distribution_type|**int**|Для внешних таблиц через SHARD_MAP_MANAGER внешнего источника данных это распределение данных строк на базовые таблицы.|0 — Sharded<br /><br /> 1 — репликация<br /><br /> 2 — циклический перебор|  
|distribution_desc|**nvarchar(120)**|Для внешних таблиц через SHARD_MAP_MANAGER внешнего источника данных это тип распределения, отображаются в виде строки.||  
|sharding_column_id|**int**|Для внешних таблиц через SHARD_MAP_MANAGER внешнего источника данных и сегментированных распространения это идентификатор столбца, столбца, который содержит значения ключа сегментирования.||  
|remote_schema_name|**sysname**|Для внешних таблиц через SHARD_MAP_MANAGER внешнего источника данных это схема, в которой находится базовая таблица удаленных базах данных (если он отличается от схемы, в которой определен внешней таблицы).||  
|remote_object_name|**sysname**|Для внешних таблиц через SHARD_MAP_MANAGER внешнего источника данных это имя базовой таблицы для удаленных баз данных (если отличается от имени внешней таблицы).||  
  
## <a name="permissions"></a>Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
