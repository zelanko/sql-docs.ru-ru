---
title: "sys.pdw_nodes_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 268c77b7-1d71-4197-a2ed-5e2b2b8fc260
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1095ccfc9838062f0612502a422398309242491
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwnodescolumns-transact-sql"></a>sys.pdw_nodes_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Отображаются столбцы для определяемой пользователем таблицы и представления, определяемые пользователем.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Идентификатор объекта, которому принадлежит этот столбец.||  
|имя|**sysname**|Имя столбца. Уникально в объекте.||  
|column_id|**int**|Идентификатор столбца. Уникально в объекте.||  
|system_type_id|**tinyint**|Идентификатор системного типа столбца.||  
|user_type_id|**int**|Идентификатор определенного пользователем типа столбца.||  
|max_length|**smallint**|Максимальная длина столбца (в байтах).|Содержит значение -1 (не является допустимым) для типов столбцов не поддерживается.|  
|precision|**tinyint**|Точность столбца, если он является числовым; в противном случае — 0.||  
|масштаб|**tinyint**|Масштаб значений столбца в случае числового выражения; в противном случае — 0.||  
|collation_name|**sysname**|Имя параметров сортировки столбца, если он символьный; в противном случае — значение NULL.||  
|is_nullable|**bit**|1 = столбец может принимать значение NULL.||  
|is_ansi_padded|**bit**|1 = столбец использует поведение ANSI_PADDING ON, если имеет тип данных character, binary или variant.|Всегда равно 0.|  
|is_rowguidcol|**bit**|1 = столбец объявлен как ROWGUIDCOL.|Всегда равно 0.|  
|is_identity|**bit**|1 = столбец идентификаторов.|Всегда равно 0.|  
|is_computed|**bit**|1 = столбец является вычисляемым.|Всегда равно 0.|  
|is_filestream|**bit**|1 — столбец является столбцом FILESTREAM.|Всегда равно 0.|  
|is_replicated|**bit**|1 = столбец реплицирован.|Всегда равно 0.|  
|is_non_sql_subscribed|**bit**|1 = столбец имеет подписчиков, отличных от SQL.|Всегда равно 0.|  
|is_merge_published|**bit**|1 = столбец публикуется слиянием.|Всегда равно 0.|  
|is_dts_replicated|**bit**|1 = столбец реплицируется с помощью служб SSIS.|Всегда равно 0.|  
|is_xml_document|**bit**|1 = содержимое является готовым XML-документом.|Всегда равно 0.|  
|xml_collection_id|**int**|0 = нет коллекции схем XML.|Всегда равно 0.|  
|default_object_id|**int**|Идентификатор объекта по умолчанию; 0 = нет значения по умолчанию.|Всегда равно 0.|  
|rule_object_id|**int**|Идентификатор изолированного правила, привязанное к столбцу. <br />0 = изолированное правило отсутствует.|Всегда равно 0.|  
|is_sparse|**bit**|1 = столбец является разреженным.|Всегда равно 0.|  
|is_column_set|**bit**|1 = столбец является набором столбцов.|Всегда равно 0.|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|NOT NULL|  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.all_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)  
  
  
