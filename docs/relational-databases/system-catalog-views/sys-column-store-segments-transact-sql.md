---
title: sys.column_store_segments (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1b4247266c2b6ff16529eb6468211d6b746b6a39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Возвращает по одной строке для каждого сегмента столбца в индексе columnstore. Имеется один сегмент столбца для каждого столбца группы строк. Например таблица с 10 групп строк и столбцов 34 возвращает 340 строки. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Указывает идентификатор секции. Уникален в базе данных.|  
|**hobt_id**|**bigint**|Идентификатор кучи или индекс сбалансированного дерева (hobt) для таблицы, в которой содержится индекс columnstore.|  
|**column_id**|**int**|Идентификатор столбца columnstore.|  
|**segment_id**|**int**|Идентификатор группы строк. Для обеспечения обратной совместимости имя столбца по-прежнему вызываться segment_id, несмотря на то, что это идентификатор группы строк Можно однозначно определить сегмент с помощью \<hobt_id partition_id, column_id >, < segment_id >.|  
|**version**|**int**|Версия формата сегмента столбца.|  
|**encoding_type**|**int**|Тип кодировки, используемой для этого сегмента:<br /><br /> 1 = VALUE_BASED - строка/недвоичные с словарь (очень похоже на 4 с некоторые варианты внутренний)<br /><br /> 2 = VALUE_HASH_BASED - не строки или двоичного столбца с общими значениями в словаре<br /><br /> 3 = STRING_HASH_BASED - строка и двоичный столбец с общими значениями в словаре<br /><br /> 4 = STORE_BY_VALUE_BASED - строка/недвоичные с словарь<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - строка и двоичный файл с словарь<br /><br /> Все кодировки воспользоваться бит упаковки и длин кодирования, когда это возможно.|  
|**row_count**|**int**|Число строк в группе строк.|  
|**has_nulls**|**int**|Значение 1, если сегмент столбца содержит значения NULL.|  
|**base_id**|**bigint**|Идентификатор базового значения, если используется тип кодирования 1.  Если тип кодирования 1 не используется, значение base_id устанавливается равным -1.|  
|**Величина**|**float**|Значение величины, если используется тип кодирования 1.  Если тип кодирования 1 не используется, величина имеет значение -1.|  
|**primary_dictionary_id**|**int**|Значение 0 представляет словарь глобального. Значение-1 соответствует без глобального словарь, созданный для этого столбца.|  
|**secondary_dictionary_id**|**int**|Ненулевое значение указывает на локальный словарь для данного столбца в текущем сегменте (т. е. группу строк). Значение -1 указывает, что отсутствует локальный словарь для этого сегмента.|  
|**min_data_id**|**bigint**|Минимальный идентификатор данных в сегменте столбца.|  
|**max_data_id**|**bigint**|Максимальный идентификатор данных в сегменте столбца.|  
|**null_value**|**bigint**|Значение, используемое для представления значений NULL.|  
|**on_disk_size**|**bigint**|Размер сегмента в байтах.|  
  
## <a name="remarks"></a>Замечания  
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
 Все столбцы требуется по крайней мере **VIEW DEFINITION** разрешение на таблицу. Следующие столбцы возвращают значение null, если у пользователя также нет **ВЫБЕРИТЕ** разрешение: has_nulls, base_id, magnitude, min_data_id, max_data_id и null_value.  
  
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
  
  

