---
title: sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL) | Документация Майкрософт
description: Возвращает текущее состояние ресурса семафоры, позволяет регулировать оптимизации параллельных запросов
ms.custom: ''
ms.date: 04/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_memory_gateways_TSQL
- dm_exec_query_optimizer_memory_gateways
- sys.dm_exec_query_optimizer_memory_gateways_TSQL
- sys.dm_exec_query_optimizer_memory_gateways
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_memory_gateways dynamic management view
author: josack
ms.author: josack
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cf134f630e4112f0cef87b7138b92fc83959e230
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097673"
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>sys.dm_exec_query_optimizer_memory_gateways (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Возвращает текущее состояние ресурса семафоры, позволяет регулировать оптимизации параллельных запросов.

|Столбец|Type|Описание|  
|----------|---------------|-----------------|  
|**pool_id**|**int**|Идентификатор пула ресурсов в группе регулятора ресурсов|  
|**name**|**sysname**|Скомпилируйте имя шлюза (небольшой шлюз, средний, большой шлюз)|
|**max_count**|**int**|Заданного максимального количества одновременных компиляции|
|**active_count**|**int**|Текущий активный число компилируется в этом шлюзе|
|**waiter_count**|**int**|Количество ожидающих в этом шлюзе|
|**threshold_factor**|**bigint**|Коэффициент порогового значения, который определяет область максимальный объем памяти, используемый оптимизации запроса.  Для малого шлюза threshold_factor указывает оптимизатор максимальное использование памяти в байтах для одного запроса, прежде чем он необходим для доступа в малого шлюза.  Для средних и больших шлюза threshold_factor показана часть общего объема памяти сервера для данного шлюза. Он используется в качестве делителя при вычислении порог использования памяти для шлюза.|
|**Пороговое значение**|**bigint**|Далее пороговое значение памяти в байтах.  Запрос должен получить доступ к этим шлюзом, если памяти достигает этого порогового значения.  «-1», если запрос не требуется для получения доступа к этим шлюзом.|
|**is_active**|**bit**|Для передачи текущего шлюз или не требуется ли запрос.|


## <a name="permissions"></a>Разрешения  
SQL Server требуется разрешение VIEW SERVER STATE на сервере.

База данных SQL Azure требуется разрешение VIEW DATABASE STATE в базе данных.


## <a name="remarks"></a>Примечания  
SQL Server использует подход многоуровневых шлюза будет регулировать количество разрешенных параллельных компиляций.  Используются три шлюзов, включая малый, средний и крупный. Шлюзы предотвратить отвода общую ресурсов памяти потребителями большего размера компиляции требуется памяти.

Ожидает результат шлюза в отложенной компиляции. Помимо задержки в компиляции регулируемые запросы будут иметь связанные RESOURCE_SEMAPHORE_QUERY_COMPILE накопления тип ожидания. Тип ожидания RESOURCE_SEMAPHORE_QUERY_COMPILE может означать, что запросы используют большой объем памяти для компиляции и что память будет исчерпан или также имеется достаточный объем памяти в целом, тем не менее доступных единиц в определенной шлюз закончатся. Выходные данные **sys.dm_exec_query_optimizer_memory_gateways** можно использовать для устранения неполадок сценариев там, где недостаточно памяти для компиляции плана выполнения запроса.  

## <a name="examples"></a>Примеры  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. Просмотр статистики ресурсов семафоры  
Что такое текущую статистику шлюза оптимизатор памяти для данного экземпляра SQL Server

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](./system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[Как использовать для мониторинга использования памяти на SQL Server 2005 команды DBCC MEMORYSTATUS](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[компиляцию большого запроса ожидает RESOURCE_SEMAPHORE_QUERY_COMPILE в SQL Server 2014](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
