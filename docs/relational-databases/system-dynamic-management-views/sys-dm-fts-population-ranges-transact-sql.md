---
title: sys.dm_fts_population_ranges (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_population_ranges
- sys.dm_fts_population_ranges_TSQL
- dm_fts_population_ranges_TSQL
- dm_fts_population_ranges
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_population_ranges dynamic management view
ms.assetid: 58d8564b-9c43-4965-a31c-2893890334ef
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c5eb63770e5a27321dc9312dfd82897b322372e3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmftspopulationranges-transact-sql"></a>Динамическое административное представление sys.dm_fts_population_ranges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о конкретных диапазонах, соответствующих выполняемому в настоящий момент заполнению полнотекстового индекса.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**адрес_памяти**|**varbinary(8)**|Адрес буферов памяти, выделенных на текущей стадии полнотекстового заполнения индекса.|  
|**parent_memory_address**|**varbinary(8)**|Адрес буферов памяти, в которых хранится родительский объект для всех диапазонов полнотекстового заполнения индекса.|  
|**is_retry**|**бит**|Если значение равно 1, то этот поддиапазон обеспечивает повторную обработку строк, в которых возникли ошибки.|  
|**session_id**|**smallint**|Идентификатор сеанса, в данный момент выполняющего указанную задачу.|  
|**processed_row_count**|**int**|Количество строк, обработанных в этом диапазоне. Ход выполнения сохраняется и подсчитывается каждые 5 минут, а не во время фиксации каждого пакета.|  
|**error_count**|**int**|Количество строк, в которых обнаружены ошибки в этом диапазоне. Ход выполнения сохраняется и подсчитывается каждые 5 минут, а не во время фиксации каждого пакета.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
 
## <a name="physical-joins"></a>Физические соединения  
 ![Существенные соединения данного динамического административного представления](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "существенные соединения данного динамического административного представления")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
  [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

