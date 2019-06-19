---
title: sys.column_store_segments (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: df7698d222c2c2f0f68138eaa5f6289106b97659
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62799880"
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Возвращает по одной строке для каждого сегмента столбца в индексе columnstore. Имеется один сегмент столбца для каждого столбца в каждой группе строк. Например таблица с 10 групп строк и столбцов 34 возвращает 340 строки. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Указывает идентификатор секции. Уникален в базе данных.|  
|**hobt_id**|**bigint**|Идентификатор кучи или индекс сбалансированного дерева (hobt) для таблицы, в которой содержится индекс columnstore.|  
|**column_id**|**int**|Идентификатор столбца columnstore.|  
|**segment_id**|**int**|Идентификатор группы строк. Для обеспечения обратной совместимости имя столбца по-прежнему вызываться segment_id, несмотря на то, что это идентификатор группы строк Можно однозначно определить сегмент с помощью \<hobt_id, partition_id, column_id >, < segment_id >.|  
|**version**|**int**|Версия формата сегмента столбца.|  
|**encoding_type**|**int**|Тип кодировки, используемой для этого сегмента:<br /><br /> 1 = VALUE_BASED - строка/недвоичных с словарь (очень схож с 4 с некоторые варианты внутренний)<br /><br /> 2 = VALUE_HASH_BASED - строка/недвоичный столбец с общими значениями в словаре<br /><br /> 3 = STRING_HASH_BASED - двоичные данные строки или столбца с общими значениями в словаре<br /><br /> 4 = STORE_BY_VALUE_BASED - строка/недвоичных с словарь<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - строки или двоичного файла с помощью нет словаря<br /><br /> Все кодировки использовать преимущества упаковки бит и длин кодирования, когда это возможно.|  
|**row_count**|**int**|Число строк в группе строк.|  
|**has_nulls**|**int**|Значение 1, если сегмент столбца содержит значения NULL.|  
|**base_id**|**bigint**|Идентификатор базового значения, если используется тип кодирования 1.  Если тип кодирования 1 не используется, значение base_id устанавливается равным -1.|  
|**абсолютное значение**|**float**|Значение величины, если используется тип кодирования 1.  Если тип кодирования 1 не используется, абсолютное значение устанавливается равным -1.|  
|**primary_dictionary_id**|**int**|Значение 0 представляет глобальный словарь. Значение -1 указывает, что имеется не глобальный словарь, созданный для этого столбца.|  
|**secondary_dictionary_id**|**int**|Ненулевое значение указывает на локальный словарь для данного столбца в текущем сегменте (т. е. группу строк). Значение -1 указывает, что отсутствует локальный словарь для этого сегмента.|  
|**min_data_id**|**bigint**|Минимальный идентификатор данных в сегменте столбца.|  
|**max_data_id**|**bigint**|Максимальный идентификатор данных в сегменте столбца.|  
|**null_value**|**bigint**|Значение, используемое для представления значений NULL.|  
|**on_disk_size**|**bigint**|Размер сегмента в байтах.|  
  
## <a name="remarks"></a>Примечания  
 Следующий запрос возвращает сведения о сегментах индекса columnstore.  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>Разрешения  
 Все столбцы требуется по меньшей мере **VIEW DEFINITION** разрешение на таблицу. Следующие столбцы возвращают значение null, если у пользователя также нет **ВЫБЕРИТЕ** разрешение: has_nulls, base_id, magnitude, min_data_id, max_data_id и null_value.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Руководство по индексам columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

