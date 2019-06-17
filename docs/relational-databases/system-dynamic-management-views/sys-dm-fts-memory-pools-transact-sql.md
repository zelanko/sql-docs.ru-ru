---
title: sys.dm_fts_memory_pools (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools
- dm_fts_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_pools dynamic management view
ms.assetid: 24747239-cd78-4d55-a00a-19233a457f42
author: pmasl
ms.author: pelopes
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8af495b77a6a6d1cba9198237a40e87168c16e69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947252"
---
# <a name="sysdmftsmemorypools-transact-sql"></a>sys.dm_fts_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о пулах общей памяти, доступных компоненту полнотекстового сборщика данных для полнотекстового сканирования или диапазона полнотекстового сканирования.  
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|Идентификатор выделенного пула памяти.<br /><br /> 0 = небольшие буферы<br /><br /> 1 = большие буферы|  
|**buffer_size**|**int**|Размер каждого распределенного буфера в пуле памяти.|  
|**min_buffer_limit**|**int**|Минимальное количество буферов, допустимых в пуле памяти.|  
|**max_buffer_limit**|**int**|Максимальное количество буферов, допустимых в пуле памяти.|  
|**buffer_count**|**int**|Текущее количество общих буферов памяти в пуле памяти.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
 
## <a name="physical-joins"></a>Физические соединения  
 ![Существенные соединения данного динамического административного представления](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-pools-1.gif "существенные соединения данного динамического административного представления")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|«многие к одному»|  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о суммарном объеме общей памяти, принадлежащей компоненту полнотекстового сборщика данных ([!INCLUDE[msCoName](../../includes/msconame-md.md)]) процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT SUM(buffer_size * buffer_count) AS "total memory"   
    FROM sys.dm_fts_memory_pools;  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
