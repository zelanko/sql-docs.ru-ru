---
title: sys.dm_pdw_nodes_exec_query_profiles (Transact-SQL) | Документация Майкрософт
description: Динамическое административное представление, которое можно использовать для мониторинга хода выполнения запросов хранилища данных в реальном времени во время выполнения запроса.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest
ms.openlocfilehash: c5c908d8db988e83d682bbf636de08ef86a8223a
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644071"
---
# <a name="sysdm_pdw_nodes_exec_query_profiles-transact-sql"></a>sys.dm_pdw_nodes_exec_query_profiles (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Отслеживает ход выполнения запросов в хранилище данных в реальном времени, пока запрос выполняется.   
  
## <a name="table-returned"></a>Таблица возвращена
  
Возвращаемые счетчики есть на каждом операторе и каждом потоке.   Результаты являются динамическими и не соответствуют результатам существующих параметров, например `SET STATISTICS XML ON` , которые создают выходные данные только после завершения запроса.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Уникальный числовой идентификатор, связанный с узлом.|
|session_id|**smallint**|Определяет сеанс, в котором выполняется этот запрос. Ссылка на dm_exec_sessions.session_id.|  
|request_id|**int**|Идентифицирует целевой запрос. Ссылка на dm_exec_sessions.request_id.|  
|sql_handle|**varbinary (64)**|Токен, однозначно определяющий пакет или хранимую процедуру, частью которой является запрос. Ссылка на dm_exec_query_stats.sql_handle.|  
|plan_handle|**varbinary (64)**|Токен, однозначно определяющий план выполнения запроса для пакета, который был выполнен, а его план находится в кэше планов или в данный момент выполняется. Ссылается на dm_exec_query_stats. plan_handle.|  
|physical_operator_name|**nvarchar(256)**|Имя физического оператора.|  
|node_id|**int**|Определяет узел оператора в дереве запросов.|  
|thread_id|**int**|Используется для различения потоков (для параллельного запроса), принадлежащих одному узлу оператора запроса.|  
|task_address|**varbinary(8)**|Определяет задачу SQLOS, используемую этим потоком. Ссылка на dm_os_tasks.task_address.|  
|row_count|**bigint**|Число строк, возвращенных оператором к настоящему моменту.|  
|rewind_count|**bigint**|Число сбросов к текущему моменту.|  
|rebind_count|**bigint**|Число повторных привязок к текущему моменту.|  
|end_of_scan_count|**bigint**|Количество окончаний просмотров к текущему моменту.|  
|estimate_row_count|**bigint**|Предполагаемое количество строк Может быть полезным сравнение estimated_row_count с фактическим row_count.|  
|first_active_time|**bigint**|Время, в миллисекундах, когда оператор был вызван первым.|  
|last_active_time|**bigint**|Время, в миллисекундах, когда оператор был вызван последним.|  
|open_time|**bigint**|Метка времени открытия (в миллисекундах).|  
|first_row_time|**bigint**|Метка времени открытия первой строки (в миллисекундах.)|  
|last_row_time|**bigint**|Метка времени открытия последней строки (в миллисекундах.)|  
|close_time|**bigint**|Метка времени закрытия (в миллисекундах).|  
|elapsed_time_ms|**bigint**|Общее затраченное время (в миллисекундах), используемое операциями целевого узла до сих пор.|  
|cpu_time_ms|**bigint**|Общее время ЦП (в миллисекундах), используемое операциями целевого узла до сих пор.|  
|database_id|**smallint**|Идентификатор базы данных, которая содержит объект, на котором выполняются операции чтения и записи.|  
|object_id|**int**|Идентификатор объекта, на котором выполняются операции чтения и записи. Ссылки на sys.objects.object_id.|  
|index_id|**int**|Индекс (если есть), для которого открыт набор строк.|  
|scan_count|**bigint**|Количество просмотров таблиц и индексов к текущему моменту.|  
|logical_read_count|**bigint**|Количество операций логического считывания к текущему времени.|  
|physical_read_count|**bigint**|Количество операций физического считывания к текущему времени.|  
|read_ahead_count|**bigint**|Количество операций упреждающего чтения к текущему времени.|  
|write_page_count|**bigint**|Число операций записи страниц, вызванных сбросами, к текущему времени.|  
|lob_logical_read_count|**bigint**|Количество операций логического считывания LOB к текущему времени.|  
|lob_physical_read_count|**bigint**|Количество операций физического считывания LOB к текущему времени.|  
|lob_read_ahead_count|**bigint**|Количество операций упреждающего чтения LOB к текущему времени.|  
|segment_read_count|**int**|Количество операций упреждающего чтения сегментов к текущему времени.|  
|segment_skip_count|**int**|Количество сегментов, пропущенных к текущему времени.| 
|actual_read_row_count|**bigint**|Число строк, считанных оператором перед применением остаточного предиката.| 
|estimated_read_row_count|**bigint**|**Применимо к:** Начиная с с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] пакетом обновления 1. <br/>Количество строк, которое должно быть считано оператором перед применением остаточного предиката.|  
  
## <a name="remarks"></a>Комментарии

Те же примечания в [sys.dm_exec_query_profiles](./sys-dm-exec-query-profiles-transact-sql.md) применяются.  

## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  

## <a name="see-also"></a>См. также раздел

 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
   

 ## <a name="next-steps"></a>Дальнейшие действия 

Обзор разработки Azure синапсе Analytics] (/Азуре/скл-Дата-варехаусе/скл-Дата-варехаусе-овервиев-Девелоп).