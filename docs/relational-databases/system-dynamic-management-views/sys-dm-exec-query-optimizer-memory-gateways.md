---
title: "sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL) | Документы Microsoft"
description: "Возвращает текущее состояние ресурса семафоры позволяет регулировать оптимизации параллельных запросов"
ms.custom: 
ms.date: 04/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_memory_gateways_TSQL
- dm_exec_query_optimizer_memory_gateways
- sys.dm_exec_query_optimizer_memory_gateways_TSQL
- sys.dm_exec_query_optimizer_memory_gateways
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_query_optimizer_memory_gateways dynamic management view
author: josack
ms.author: josack
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cf31a066798e1c88d0d6d475edda87f2df08ba05
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Возвращает текущее состояние ресурса семафоры позволяет регулировать оптимизации параллельных запросов.

|Столбец|Тип|Description|  
|----------|---------------|-----------------|  
|**pool_id**|**int**|Идентификатор пула ресурсов в группе регулятора ресурсов|  
|**name**|**sysname**|Скомпилируйте имя шлюза (небольшой шлюз, средний, большой шлюза)|
|**максимальный счетчик**|**int**|Заданного максимального количества одновременных компилирует|
|**active_count**|**int**|Текущий активный число компилирует в этот шлюз|
|**waiter_count**|**int**|Количество ожидающих в этот шлюз|
|**threshold_factor**|**bigint**|Коэффициент порогового значения, который определяет часть максимальный объем памяти, используемой оптимизации запроса.  Для небольших шлюза threshold_factor указывает оптимизатор максимальное использование памяти в байтах для одного запроса, прежде, чем это требуется для доступа в небольших шлюза.  Для шлюза средних и больших threshold_factor показана часть памяти всего сервера для данного шлюза. Он используется в качестве делителя при вычислении порогового значения использования памяти для шлюза.|
|**Пороговое значение**|**bigint**|Далее пороговое значение памяти в байтах.  Запрос должен получить доступ к этому шлюзу, если памяти достигает порогового значения.  «-1», если запрос не требуется для доступа к этому шлюзу.|
|**is_active**|**bit**|Для передачи текущего шлюза, или не требуется ли запрос.|


## <a name="permissions"></a>Permissions  
SQL Server необходимо разрешение VIEW SERVER STATE на сервере.

База данных SQL Azure требуется разрешение VIEW DATABASE STATE в базе данных.


## <a name="remarks"></a>Замечания  
SQL Server использует подход, многоуровневых шлюза будет регулировать количество разрешенных параллельных компиляций.  Используются три шлюзы, включая малых, средних и большие. Шлюзы предотвращения исчерпания общего объема ресурсов памяти потребители памяти требует большего компиляции.

Ожидает результат шлюза в отложенной компиляции. Помимо задержки в компиляции регулируемые запросы будут иметь связанный RESOURCE_SEMAPHORE_QUERY_COMPILE накопления типа ожидания. Тип ожидания RESOURCE_SEMAPHORE_QUERY_COMPILE может означать, запросы используют большой объем памяти для компиляции и что память будет исчерпан, или в качестве альтернативы имеется достаточный объем памяти в целом, однако доступных единиц в определенном шлюз исчерпаны. Выходные данные **sys.dm_exec_query_optimizer_memory_gateways** можно использовать для исправления ситуации, когда недостаточно памяти для компиляции плана выполнения запроса.  

## <a name="examples"></a>Примеры  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. Просмотр статистики семафоры ресурсов  
Что такое текущую статистику шлюза оптимизатор памяти для данного экземпляра SQL Server

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](./system-dynamic-management-views.md)   
 [&#40; динамические административные представления и функции, связанные с выполнением Transact-SQL &#41;](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[Использование команды DBCC MEMORYSTATUS для мониторинга использования памяти в SQL Server 2005](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[компиляции запроса имеет большой размер ожидает RESOURCE_SEMAPHORE_QUERY_COMPILE в SQL Server 2014](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
