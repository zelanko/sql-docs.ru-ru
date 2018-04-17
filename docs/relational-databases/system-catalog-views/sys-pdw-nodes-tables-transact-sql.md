---
title: sys.pdw_nodes_tables (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 473b5d14-171b-4a16-9195-acf36d3f786c
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 79ab5f34c5d079076d3c54bffa201e03f48ac7ad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwnodestables-transact-sql"></a>sys.pdw_nodes_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого объекта таблицы, которыми владеет участник или на который участник были предоставлены разрешения.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|\<Унаследованные столбцы >||Список столбцов, наследуемых этим представлением см. в разделе [sys.objects](http://msdn.microsoft.com/en-us/c36fa71e-549a-4533-a6cd-1314d26f533f).||  
|lob_data_space_id|**int**||Значение всегда равно 0.|  
|filestream_data_space_id|**int**|Идентификатор пространства данных для файловой группы FILESTREAM или [!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**int**|Идентификатор столбца, максимальное, использованный в таблице.||  
|lock_on_bulk_load|**бит**|Таблица заблокирована при массовой загрузке.|TBD|  
|uses_ansi_nulls|**бит**|Таблица была создана при установленном параметре SET ANSI_NULLS = ON.|1|  
|is_replicated|**бит**|1 = таблица опубликована путем репликации.|0; репликация не поддерживается.|  
|has_replication_filter|**бит**|1 = для таблицы имеется фильтр репликации.|0|  
|is_merge_published|**бит**|1 = таблица опубликована путем репликации слиянием.|0; не поддерживается.|  
|is_sync_tran_subscribed|**бит**|1 = таблица используется в немедленно обновляемой подписке.|0; не поддерживается.|  
|has_unchecked_assembly_data|**бит**|1 = таблица содержит материализованные данные, зависящие от сборки, определение которых изменилось во время последней операции ALTER ASSEMBLY. Будет сброшено в значение 0 после следующей успешной операции DBCC CHECKDB или DBCC CHECKTABLE.|0; отсутствует поддержка среды CLR.|  
|text_in_row_limit|**int**|0 = параметр текста в строке не установлен.|Значение всегда равно 0.|  
|large_value_types_out_of_row|**бит**|1 = типы больших значений хранятся вне строк.|Значение всегда равно 0.|  
|is_tracked_by_cdc|**бит**|1 = таблица включена для отслеживания измененных данных|Всегда равно 0; отсутствует поддержка CDC.|  
|lock_escalation|**tinyint**|Значение параметра LOCK_ESCALATION для таблицы: 2 = AUTO|Всегда 2.|  
|lock_escalation_desc|**nvarchar(60)**|Текстовое описание параметра lock_escalation.|Всегда ꞌAUTOꞌ.|  
|pdw_node_id|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|NOT NULL|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
