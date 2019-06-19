---
title: sys.dm_db_xtp_index_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_index_stats
- dm_db_xtp_index_stats
- sys.dm_db_xtp_index_stats_TSQL
- dm_db_xtp_index_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_index_stats dynamic management view
ms.assetid: 8d0a50b8-2015-4576-930f-e3307dfc888e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b80ba01b73dff6810ee9fcfdc08a904ff6ad4697
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62640420"
---
# <a name="sysdmdbxtpindexstats-transact-sql"></a>sys.dm_db_xtp_index_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Содержит статистические данные, собранные со времени последнего перезапуска базы данных.  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP &#40;оптимизация в памяти&#41; ](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md) и [Using Indexes on Memory-Optimized Tables, касающиеся](https://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b).  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|Идентификатор объекта, которому принадлежит данный индекс.|  
|xtp_object_id|**bigint**|Внутренний идентификатор, соответствующий текущей версии объекта.<br /><br /> Примечание. Применяется к [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
|index_id|**bigint**|Идентификатор индекса. Значение index_id уникально только в пределах объекта.|  
|scans_started|**bigint**|Количество выполненных сканирований индексов In-Memory OLTP. Каждая инструкция SELECT, INSERT, UPDATE и DELETE требует сканирования индекса.|  
|scans_retries|**bigint**|Количество сканирований индекса, необходимое для повторной попытки.|  
|rows_returned|**bigint**|Общее количество возвращенных строк с момента создания таблицы или запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_touched|**bigint**|Общее количество строк, к которым был осуществлен доступ, с момента создания таблицы или запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rows_expiring|**bigint**|Только для внутреннего применения.|  
|rows_expired|**bigint**|Только для внутреннего применения.|  
|rows_expired_removed|**bigint**|Только для внутреннего применения.|  
|phantom_scans_started|**bigint**|Только для внутреннего применения.|  
|phatom_scans_retries|**bigint**|Только для внутреннего применения.|  
|phantom_rows_touched|**bigint**|Только для внутреннего применения.|  
|phantom_expiring_rows_encountered|**bigint**|Только для внутреннего применения.|  
|phantom_expired_rows_encountered|**bigint**|Только для внутреннего применения.|  
|phantom_expired_removed_rows_encountered|**bigint**|Только для внутреннего применения.|  
|phantom_expired_rows_removed|**bigint**|Только для внутреннего применения.|  
|object_address|**varbinary(8)**|Только для внутреннего применения.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE на текущую базу данных.  
  
## <a name="see-also"></a>См. также  
 [Оптимизированные для памяти динамические административные представления таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
