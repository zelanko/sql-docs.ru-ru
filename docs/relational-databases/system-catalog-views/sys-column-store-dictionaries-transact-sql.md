---
title: sys.column_store_dictionaries (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: fd497326f278dcc01b4fa81a0e64da6a93cbe8cd
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52518814"
---
# <a name="syscolumnstoredictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого словаря, используемого в индексах columnstore, оптимизированных для памяти xVelocity. Словари используются для кодирования некоторых, но не всех типов данных, поэтому не все столбцы в индексе columnstore имеют словари. Словарь может существовать в качестве основного словаря (для всех сегментов) и, возможно, для других вспомогательных словарей, используемых для подмножества сегментов столбца.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|Идентификатор кучи или индекс сбалансированного дерева (hobt) для таблицы, в которой содержится индекс columnstore.|  
|**column_id**|**int**|Идентификатор столбца columnstore, начиная с 1. Первый столбец имеет идентификатор = 1, второй столбец с Идентификатором = 2, и т.д.|  
|**dictionary_id**|**int**|Может существовать два вида словарей: глобальные и локальные, связанные с сегмента столбца. Dictionary_id 0 представляет глобальный словарь, общей для всех сегментов (по одному для каждой из групп строк) для этого столбца.|  
|**version**|**int**|Версия формата словаря.|  
|**type**|**int**|Тип словаря:<br /><br /> 1 - hash, словарь, содержащий **int** значения<br /><br /> 2 - не используется<br /><br /> 3 — хэш-словарь, содержащий строковые значения<br /><br /> 4 - словарь, содержащий hash **float** значения<br /><br /> Дополнительные сведения о словарях см. в разделе [руководство по индексам Columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md).|  
|**last_id**|**int**|Последний идентификатор данных в словаре.|  
|**entry_count**|**bigint**|Количество записей в словаре.|  
|**on_disc_size**|**bigint**|Размер словаря в байтах.|  
|**partition_id**|**bigint**|Указывает идентификатор секции. Уникален в базе данных.|  
  
## <a name="permissions"></a>Разрешения  
 Для всех столбцов требуется как минимум разрешение VIEW DEFINITION на таблицу. Следующие столбцы возвращают значение null, если у пользователя также нет **ВЫБЕРИТЕ** разрешение: last_id, entry_count, data_ptr.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Руководство по индексам columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Руководство по индексам columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

