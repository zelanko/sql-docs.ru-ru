---
title: sys.dm_exec_query_profiles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_profiles_TSQL
- sys.dm_exec_query_profiles_TSQL
- dm_exec_query_profiles
- sys.dm_exec_query_profiles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_profiles dynamic management view
ms.assetid: 54efc6cb-eea8-4f6d-a4d0-aa05eeb54081
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 87488f36a4b4b01181cd973a75d6e5c7f2e233d7
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860725"
---
# <a name="sysdmexecqueryprofiles-transact-sql"></a>sys.dm_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

Контролирует ход выполнения запросов в реальном времени. Например, используйте данное динамическое административное представление для определения, какая часть запроса выполняется медленно.  Это динамическое административное представление можно объединять с другими за счет столбцов, определенных в поле описания. Или объедините данное динамическое административное представление с другими счетчиками производительности (такими как Системный Монитор, xperf), используя столбцы меток времени.   
  
## <a name="table-returned"></a>Возвращаемая таблица  
Возвращаемые счетчики есть на каждом операторе и каждом потоке.   Результаты являются динамическими и не соответствовать результатам существующих параметров, таких как `SET STATISTICS XML ON` которой только создают вывод при завершении запроса.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Определяет сеанс, в котором выполняется этот запрос. Ссылка на dm_exec_sessions.session_id.|  
|request_id|**ssNoversion**|Идентифицирует целевой запрос. Ссылка на dm_exec_sessions.request_id.|  
|sql_handle|**varbinary(64)**|— Это маркер, уникально определяющий пакета или хранимой процедуры, частью которого является запрос. Ссылка на dm_exec_query_stats.sql_handle.|  
|plan_handle|**varbinary(64)**|— Это маркер, который уникально идентифицирует план выполнения запроса для запущенного пакета, и ее план находится в кэше планов, или в данный момент. Ссылается на dm_exec_query_stats.plan_handle.|  
|physical_operator_name|**nvarchar(256)**|Имя физического оператора.|  
|node_id|**ssNoversion**|Определяет узел оператора в дереве запросов.|  
|thread_id|**ssNoversion**|Используется для различения потоков (для параллельного запроса), принадлежащих одному узлу оператора запроса.|  
|task_address|**varbinary(8)**|Определяет задачу SQLOS, используемую этим потоком. Ссылка на dm_os_tasks.task_address.|  
|row_count|**BIGINT**|Число строк, возвращенных оператором к настоящему моменту.|  
|rewind_count|**BIGINT**|Число сбросов к текущему моменту.|  
|rebind_count|**BIGINT**|Число повторных привязок к текущему моменту.|  
|end_of_scan_count|**BIGINT**|Количество окончаний просмотров к текущему моменту.|  
|estimate_row_count|**BIGINT**|Предполагаемое количество строк Может быть полезным сравнение estimated_row_count с фактическим row_count.|  
|first_active_time|**BIGINT**|Время, в миллисекундах, когда оператор был вызван первым.|  
|last_active_time|**BIGINT**|Время, в миллисекундах, когда оператор был вызван последним.|  
|open_time|**BIGINT**|Метка времени открытия (в миллисекундах).|  
|first_row_time|**BIGINT**|Метка времени открытия первой строки (в миллисекундах.)|  
|last_row_time|**BIGINT**|Метка времени открытия последней строки (в миллисекундах.)|  
|close_time|**BIGINT**|Метка времени закрытия (в миллисекундах).|  
|elapsed_time_ms|**BIGINT**|Общее затраченное время (в миллисекундах), занятых операциями целевого узла.|  
|cpu_time_ms|**BIGINT**|Общее использование ЦП (в миллисекундах) до сих операциями целевого узла.|  
|database_id|**smallint**|Идентификатор базы данных, которая содержит объект, на котором выполняются операции чтения и записи.|  
|object_id|**ssNoversion**|Идентификатор объекта, на котором выполняются операции чтения и записи. Ссылки на sys.objects.object_id.|  
|index_id|**ssNoversion**|Индекс (если есть), для которого открыт набор строк.|  
|scan_count|**BIGINT**|Количество просмотров таблиц и индексов к текущему моменту.|  
|logical_read_count|**BIGINT**|Количество операций логического считывания к текущему времени.|  
|physical_read_count|**BIGINT**|Количество операций физического считывания к текущему времени.|  
|read_ahead_count|**BIGINT**|Количество операций упреждающего чтения к текущему времени.|  
|write_page_count|**BIGINT**|Число операций записи страниц, вызванных сбросами, к текущему времени.|  
|lob_logical_read_count|**BIGINT**|Количество операций логического считывания LOB к текущему времени.|  
|lob_physical_read_count|**BIGINT**|Количество операций физического считывания LOB к текущему времени.|  
|lob_read_ahead_count|**BIGINT**|Количество операций упреждающего чтения LOB к текущему времени.|  
|segment_read_count|**ssNoversion**|Количество операций упреждающего чтения сегментов к текущему времени.|  
|segment_skip_count|**ssNoversion**|Количество сегментов, пропущенных к текущему времени.| 
|actual_read_row_count|**BIGINT**|Номер строки, считываемые оператор до применения остаточный предикат.| 
|estimated_read_row_count|**BIGINT**|**Применимо к:** Начиная с версии [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] с пакетом обновления 1. <br/>Примерное число строк, считанных оператор до применения остаточный предикат.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Если запрос узла плана не содержит все операции ввода-вывода, все счетчики, относящиеся к я-O, присваивается значение NULL.  
  
 Счетчики, относящиеся к я-O, о которых сообщает это динамическое административное Представление являются более детализированными, чем те, которые сообщаются `SET STATISTICS IO` одним из следующих двух способов:  
  
-   `SET STATISTICS IO` Группирует счетчики для всех операций ввода-вывода для данной таблицы вместе. С помощью этого динамического административного Представления вы получите раздельные счетчики для каждого узла в плане запроса, выполняющего операции ввода-вывода в таблицу.  
  
-   Если есть параллельное сканирование, данное динамическое административное представление выдает счетчики для каждого из параллельных потоков, выполняющих сканирование.
 
Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, *инфраструктуру профилирования статистики выполнения запросов стандарта* существует side-by-side, с помощью *инфраструктуру профилирования статистики выполнения упрощенных запросов* . `SET STATISTICS XML ON` и `SET STATISTICS PROFILE ON` всегда используйте *инфраструктуру профилирования статистики выполнения запросов стандарта*. Для `sys.dm_exec_query_profiles` для заполнения, профилирование инфраструктур запроса необходимо включить один. Дополнительные сведения см. в разделе [Инфраструктура профилирования запросов](../../relational-databases/performance/query-profiling-infrastructure.md).    

>[!NOTE]
> Запрос в процессе исследования должен начать **после** метод включен в запрос, инфраструктуры профилирования, включения после начала запросов не даст результатов в `sys.dm_exec_query_profiles`. Дополнительные сведения о включении профилирования инфраструктур запросов см. в разделе [инфраструктуры профилирования запросов](../../relational-databases/performance/query-profiling-infrastructure.md).

## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
   
## <a name="examples"></a>Примеры  
 Шаг 1. Войдите в сеанс, в котором вы планируете выполнить запрос, вы будете анализировать с помощью `sys.dm_exec_query_profiles`. Настройка запроса для профильного использования `SET STATISTICS PROFILE ON`. Выполните ваш запрос в данном сеансе.  
  
```sql  
--Configure query for profiling with sys.dm_exec_query_profiles  
SET STATISTICS PROFILE ON;  
GO  

--Or enable query profiling globally under SQL Server 2016 SP1 or above (not needed in SQL Server 2019)  
DBCC TRACEON (7412, -1);  
GO 
  
--Next, run your query in this session, or in any other session if query profiling has been enabled globally 
```  
  
 Шаг 2. Войдите во второй сеанс, отличным от того, в котором выполняется ваш запрос.  
  
 Следующее выражение суммирует состояние, достигнутое текущим запросом в сеансе 54.  Для этого оно рассчитывает общее число выходных строк со всех потоков для каждого узла, и сравнивает его с ожидаемым числом выходных строк для этого узла.  
  
```sql  
--Run this in a different session than the session in which your query is running. 
--Note that you may need to change session id 54 below with the session id you want to monitor.
SELECT node_id,physical_operator_name, SUM(row_count) row_count, 
  SUM(estimate_row_count) AS estimate_row_count, 
  CAST(SUM(row_count)*100 AS float)/SUM(estimate_row_count)  
FROM sys.dm_exec_query_profiles   
WHERE session_id=54
GROUP BY node_id,physical_operator_name  
ORDER BY node_id;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
 
