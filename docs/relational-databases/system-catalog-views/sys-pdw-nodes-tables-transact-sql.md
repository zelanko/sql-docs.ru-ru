---
description: sys.pdw_nodes_tables (Transact-SQL)
title: sys.pdw_nodes_tables (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 473b5d14-171b-4a16-9195-acf36d3f786c
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a115b3ff132658dcfc2746fc9899fcfafce411ae
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035776"
---
# <a name="syspdw_nodes_tables-transact-sql"></a>sys.pdw_nodes_tables (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Содержит по одной строке для каждого объекта таблицы, который владеет участником или на который участник предоставил какое-либо разрешение.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|\<inherited columns>||Список столбцов, наследуемых этим представлением, см. в разделе [sys. Objects](../system-catalog-views/sys-objects-transact-sql.md).||  
|lob_data_space_id|**int**||Всегда равно 0.|  
|filestream_data_space_id|**int**|Идентификатор пространства данных для файловой группы FILESTREAM или [!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**int**|Максимальный идентификатор столбца, используемый этой таблицей.||  
|lock_on_bulk_load|**bit**|Таблица заблокирована при массовой загрузке.|TBD|  
|uses_ansi_nulls|**bit**|Таблица была создана при установленном параметре SET ANSI_NULLS = ON.|1|  
|is_replicated|**bit**|1 = таблица опубликована с помощью репликации.|0,0 Репликация не поддерживается.|  
|has_replication_filter|**bit**|1 = для таблицы имеется фильтр репликации.|0|  
|is_merge_published|**bit**|1 = таблица опубликована путем репликации слиянием.|0,0 не поддерживается.|  
|is_sync_tran_subscribed|**bit**|1 = таблица используется в немедленно обновляемой подписке.|0,0 не поддерживается.|  
|has_unchecked_assembly_data|**bit**|1 = таблица содержит материализованные данные, зависящие от сборки, определение которых изменилось во время последней операции ALTER ASSEMBLY. Будет сброшено в значение 0 после следующей успешной операции DBCC CHECKDB или DBCC CHECKTABLE.|0,0 без поддержки CLR.|  
|text_in_row_limit|**int**|0 = параметр текста в строке не установлен.|Всегда равно 0.|  
|large_value_types_out_of_row|**bit**|1 = типы больших значений хранятся вне строк.|Всегда равно 0.|  
|is_tracked_by_cdc|**bit**|1 = таблица включена для отслеживания измененных данных|Всегда равно 0; без поддержки CDC.|  
|lock_escalation|**tinyint**|Значение параметра LOCK_ESCALATION для таблицы: 2 = AUTO.|Всегда 2.|  
|lock_escalation_desc|**nvarchar(60)**|Текстовое описание параметра lock_escalation.|Всегда черта AUTO черта.|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|NOT NULL|  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога Azure Synapse Analytics и Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
