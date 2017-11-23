---
title: "sys.dm_pdw_os_threads (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: ddc12f05-edeb-4848-b6d7-e851684cf044
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ca9c5f015c5818348de45d69df84416ca8a2b25
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwosthreads-transact-sql"></a>sys.dm_pdw_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Идентификатор соответствующего узла.<br /><br /> pdw_node_id и thread_id формируют ключ для этого представления.|В разделе node_id в [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|thread_id|**int**|pdw_node_id и thread_id формируют ключ для этого представления.||  
|process_id|**int**|||  
|имя|**nvarchar(255)**|||  
|priority|**int**|||  
|start_time|**datetime**|||  
|state|**nvarchar(32)**|||  
|wait_reason|**nvarchar(32)**|||  
|total_processor_elapsed_time|**bigint**|Общее время ядра используемые потоком.||  
|total_user_elapsed_time|**bigint**|Общее время пользователя используемые потоком||  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
