---
title: sys.dm_xtp_system_memory_consumers (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_xtp_system_memory_consumers
- sys.dm_xtp_system_memory_consumers_TSQL
- sys.dm_xtp_system_memory_consumers
- dm_xtp_system_memory_consumers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_system_memory_consumers dynamic management view
ms.assetid: 9eb0dd82-7920-42e0-9e50-7ce6e7ecee8b
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3363fa2208f735c38ebd696b782fced80e5c49ce
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34468640"
---
# <a name="sysdmxtpsystemmemoryconsumers-transact-sql"></a>sys.dm_xtp_system_memory_consumers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Сообщает о потребителях памяти системного уровня в [!INCLUDE[hek_2](../../includes/hek-2-md.md)]. Память для этих потребителей поступает из пула по умолчанию (если выделение находится в контексте потока пользователя) или из внутреннего пула (если выделение находится в контексте системного потока).  
  
```  
-- system memory consumers @ instance  
select * from sys.dm_xtp_system_memory_consumers  
```  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|memory_consumer_id|**bigint**|Внутренний идентификатор потребителя памяти.|  
|memory_consumer_type|**int**|Целое число, представляющее тип потребителя памяти с помощью одного из следующих значений:<br /><br /> 0 — он не должен отображаться. Суммирует использование памяти для двух или более потребителей.<br /><br /> 1 — АССОЦИАТИВНОГО: Отслеживает потребление памяти для резервного блока памяти системы.<br /><br /> 2 - VARHEAP: Отслеживает потребление памяти для кучи переменной длины.<br /><br /> 4 - пул страниц ввода-ВЫВОДА: отслеживает потребление памяти для системного пула страниц, используемых для операций ввода-ВЫВОДА.|  
|memory_consumer_type_desc|**nvarchar(16) в формате**|Описание типа потребителя памяти.<br /><br /> 0 — он не должен отображаться.<br /><br /> 1 — LOOKASIDE<br /><br /> 2 — VARHEAP<br /><br /> 4 — PGPOOL|  
|memory_consumer_desc|**nvarchar(64)**|Описание экземпляра потребителя памяти.<br /><br /> VARHEAP: <br />Системная куча. Общее назначение. В настоящее время используется только для выделения рабочих элементов сборки мусора.<br />-ИЛИ-<br />Куча резервного блока памяти. Используется резервными блоками памяти, когда количество элементов в списке достигает определенного предела (обычно около 5000 элементов).<br /><br /> PGPOOL: Для системы ввода-ВЫВОДА пулы существует — три разного размера пула страниц системы 4 КБ, 64K системного пула страниц и пул страниц 256 КБ.|  
|lookaside_id|**bigint**|Идентификатор поставщика конкретных потоков локальной памяти резервного блока.|  
|pagepool_id|**bigint**|Идентификатор поставщика памяти пула страниц локального потока.|  
|allocated_bytes|**bigint**|Число байтов, зарезервированных для этого потребителя памяти.|  
|used_bytes|**bigint**|Число байтов, используемых этим потребителем. Применимо только для потребителей памяти varheap.|  
|allocation_count|**int**|Количество выделений.|  
|partition_count|**int**|Только для внутреннего применения.|  
|sizeclass_count|**int**|Только для внутреннего применения.|  
|min_sizeclass|**int**|Только для внутреннего применения.|  
|max_sizeclass|**int**|Только для внутреннего применения.|  
|memory_consumer_address|**varbinary**|Внутренний адрес потребителя памяти.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимы разрешения VIEW SERVER STATE на сервере.  
  
## <a name="user-scenario"></a>Пользовательский сценарий  
  
```  
-- system memory consumers @ instance  
selectmemory_consumer_type_desc,   
allocated_bytes/1024 as allocated_bytes_kb,   
used_bytes/1024 as used_bytes_kb, allocation_count  
from sys.dm_xtp_system_memory_consumers  
```  
  
 Вывод показывает всех потребителей памяти на уровне системы. Например, имеются потребители для резервных блоков памяти транзакции.  
  
```  
memory_consumer_type_name           memory_consumer_desc                           allocated_bytes_kb   used_bytes_kb        allocation_count  
-------------------------------          ---------------------                          -------------------  --------------        ----------------  
VARHEAP                                  Lookaside heap                                 0                    0                    0  
VARHEAP                                  System heap                                    768                  0                    2  
LOOKASIDE                                GC transaction map entry                       64                   64                   910  
LOOKASIDE                                Redo transaction map entry                     128                  128                  1260  
LOOKASIDE                                Recovery table cache entry                     448                  448                  8192  
LOOKASIDE                                Transaction recent rows                        3264                 3264                 4444  
LOOKASIDE                                Range cursor                                   0                    0                    0  
LOOKASIDE                                Hash cursor                                    3200                 3200                 11070  
LOOKASIDE                                Transaction save-point set entry               0                    0                    0  
LOOKASIDE                                Transaction partially-inserted rows set        704                  704                  1287  
LOOKASIDE                                Transaction constraint set                     576                  576                  1940  
LOOKASIDE                                Transaction save-point set                     0                    0                    0  
LOOKASIDE                                Transaction write set                          704                  704                  672  
LOOKASIDE                                Transaction scan set                           320                  320                  156  
LOOKASIDE                                Transaction read set                           704                  704                  343  
LOOKASIDE                                Transaction                                    4288                 4288                 1459  
PGPOOL                                   System 256K page pool                          5120                 5120                 20  
PGPOOL                                   System 64K page pool                           0                    0                    0  
PGPOOL                                   System 4K page pool                            24                   24                   6  
```  
  
 Чтобы определить общий объем памяти, потребляемой блоками распределения системы, выполните следующие действия.  
  
```  
select sum(allocated_bytes)/(1024*1024) as total_allocated_MB, sum(used_bytes)/(1024*1024) as total_used_MB   
from sys.dm_xtp_system_memory_consumers  
  
total_allocated_MB   total_used_MB  
-------------------- --------------------  
2                    2  
```  
  
## <a name="see-also"></a>См. также  
 [Оптимизированные для памяти динамические административные представления таблиц &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
