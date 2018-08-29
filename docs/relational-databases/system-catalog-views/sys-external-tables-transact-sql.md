---
title: sys.external_tables (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ceaaa2c3a5005b9adec32fecd3b8a63600416652
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43094631"
---
# <a name="sysexternaltables-transact-sql"></a>sys.external_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Содержит по строке для каждой внешней таблицы в текущей базе данных.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|\<наследуемые столбцы >||Список столбцов, наследуемых этим представлением, см. в разделе [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).||  
|max_column_id_used|**int**|Максимальный идентификатор использовали для этой таблицы.||  
|uses_ansi_nulls|**bit**|Таблица была создана при установленном параметре SET ANSI_NULLS = ON.||  
|data_source_id|**int**|Идентификатор объекта для внешнего источника данных.||  
|file_format_id|**int**|Для внешних таблиц на внешнем источнике данных HADOOP это идентификатор объекта для формата внешнего файла.||  
|location|**nvarchar(4000)**|Для внешних таблиц на внешнем источнике данных HADOOP это путь к внешним данным в HDFS.||  
|Если задано reject_type|**tinyint**|Для внешних таблиц на внешнем источнике данных HADOOP это способ, отклоненных строк учитываются при запросе внешних данных.|ЗНАЧЕНИЕ — число отклоненных строк.<br /><br /> ПРОЦЕНТ — процент отклоненных строк.|  
|reject_value|**float**|Для внешних таблиц на внешнем источнике данных HADOOP:<br /><br /> Для *reject_type =* значение, это количество отклонений строки, чтобы разрешить до ошибок в запросе.<br /><br /> Для *reject_type* = percentage, это процент отклонения строки, чтобы прежде чем он остановит запрос.||  
|reject_sample_value|**int**|Для *reject_type* = percentage, это число строк, загружаемых, успешного или неуспешного входа, до расчета Процент отклоненных строк.|Значение NULL, если reject_type = VALUE.|  
|distribution_type|**int**|Для внешних таблиц через источник внешних данных SHARD_MAP_MANAGER это распределение данных строк для базовых таблиц.|0 — Sharded<br /><br /> 1 — репликация<br /><br /> 2 — циклический перебор|  
|distribution_desc|**nvarchar(120)**|Для внешних таблиц через источник внешних данных SHARD_MAP_MANAGER это тип распределения, отображаемый в виде строки.||  
|sharding_column_id|**int**|Для внешних таблиц через источник внешних данных SHARD_MAP_MANAGER и сегментированную распространения это идентификатор столбца, столбца, который содержит значения ключа сегментирования.||  
|remote_schema_name|**sysname**|Для внешних таблиц через источник внешних данных SHARD_MAP_MANAGER это схема, где находится базовая таблица к удаленным базам данных (если он отличается от схемы, в которой определена внешняя таблица).||  
|remote_object_name|**sysname**|Для внешних таблиц через SHARD_MAP_MANAGER внешнего источника данных это имя базовой таблицы к удаленным базам данных (если оно отличается от имени внешней таблицы).||  
  
## <a name="permissions"></a>Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
