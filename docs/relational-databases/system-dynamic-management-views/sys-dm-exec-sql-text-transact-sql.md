---
title: sys.dm_exec_sql_text (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_sql_text
- sys.dm_exec_sql_text
- sys.dm_exec_sql_text_TSQL
- dm_exec_sql_text_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_sql_text dynamic management function
ms.assetid: 61b8ad6a-bf80-490c-92db-58dfdff22a24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 386a582e2d685b30a58f21a2b8938e1ae1698938
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812212"
---
# <a name="sysdmexecsqltext-transact-sql"></a>sys.dm_exec_sql_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает текст SQL, то есть пакета определяется указанным *sql_handle*. Эта функция с табличным значением заменяет системную функцию **fn_get_sql**.  
  
 
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_exec_sql_text(sql_handle | plan_handle)  
```  
  
## <a name="arguments"></a>Аргументы  
*sql_handle*  
Дескриптор SQL искомого пакета. *sql_handle* — **varbinary(64)**. *sql_handle* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_cursors](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cursors-transact-sql.md)  
  
-   [sys.dm_exec_xml_handles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)  
  
-   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  
  
*plan_handle*  
Уникальным образом определяет план запроса для пакета, который находится в кэше или выполняется в данный момент. *plan_handle* — **varbinary(64)**. *plan_handle* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|Идентификатор базы данных.<br /><br /> Для нерегламентированных и подготовленных инструкций SQL это идентификатор базы данных, в которой происходила компиляция инструкции.|  
|**objectid**|**int**|Идентификатор объекта.<br /><br /> Имеет значение NULL для нерегламентированных и подготовленных инструкций SQL.|  
|**номер**|**smallint**|Для пронумерованной хранимой процедуры этот столбец возвращает ее номер. Дополнительные сведения см. в разделе [sys.numbered_procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Имеет значение NULL для нерегламентированных и подготовленных инструкций SQL.|  
|**Шифрование**|**bit**|1 = текст SQL зашифрован.<br /><br /> 0 = текст SQL не зашифрован.|  
|**text**|**nvarchar (max** **)**|Текст SQL-запроса.<br /><br /> Имеет значение NULL для зашифрованных объектов.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="remarks"></a>Примечания  
Для нерегламентированных запросов дескрипторы SQL являются значениями хэша на основе текста SQL, отправляемых на сервер и могут быть получены из любой базы данных. 

Для таких объектов баз данных, как хранимые процедуры, триггеры или функции, дескрипторы SQL создаются на основе идентификатора базы данных, идентификатора объекта, а также номера объекта. 

Дескриптор плана — это значение хэша, производным от скомпилированного плана всего пакета. 

> [!NOTE]
> **DBID** не может быть определена по *sql_handle* для нерегламентированных запросов. Чтобы определить **dbid** для нерегламентированных запросов с помощью *plan_handle* вместо этого.
  
## <a name="examples"></a>Примеры 

### <a name="a-conceptual-example"></a>A. Пример
Ниже приведен простой пример для иллюстрации передачи **sql_handle** напрямую или с помощью **CROSS APPLY**.
  1.  Создание действия.  
Выполните следующий запрос T-SQL в новом окне запроса в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].   
      ```sql
      -- Identify current spid (session_id)
      SELECT @@SPID;
      GO
  
      -- Create activity
        WAITFOR DELAY '00:02:00';
      ```
      
    2.  С помощью **CROSS APPLY**.  
    Sql_handle из **sys.dm_exec_requests** будут переданы **sys.dm_exec_sql_text** с помощью **CROSS APPLY**. Откройте новое окно запроса и передать spid, определенных на шаге 1. В этом примере, может быть идентификатор spid `59`.

        ```sql
        SELECT t.*
        FROM sys.dm_exec_requests AS r
        CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t
        WHERE session_id = 59 -- modify this value with your actual spid
         ```      
 
    2.  Передача **sql_handle** напрямую.  
Получить **sql_handle** из **sys.dm_exec_requests**. Затем передайте **sql_handle** непосредственно к **sys.dm_exec_sql_text**. Откройте новое окно запроса и spid, определенных на шаге 1, чтобы передать **sys.dm_exec_requests**. В этом примере, может быть идентификатор spid `59`. Передать возвращенный **sql_handle** как аргумент **sys.dm_exec_sql_text**.

        ```sql
        -- acquire sql_handle
        SELECT sql_handle FROM sys.dm_exec_requests WHERE session_id = 59  -- modify this value with your actual spid
        
        -- pass sql_handle to sys.dm_exec_sql_text
        SELECT * FROM sys.dm_exec_sql_text(0x01000600B74C2A1300D2582A2100000000000000000000000000000000000000000000000000000000000000) -- modify this value with your actual sql_handle
         ```      
    
  
### <a name="b-obtain-information-about-the-top-five-queries-by-average-cpu-time"></a>Б. Получение сведений о первых пяти запросах по среднему времени ЦП  
 Следующий пример возвращает текст инструкции SQL и среднее время ЦП для пяти первых запросов.  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
    SUBSTRING(st.text, (qs.statement_start_offset/2)+1,   
        ((CASE qs.statement_end_offset  
          WHEN -1 THEN DATALENGTH(st.text)  
         ELSE qs.statement_end_offset  
         END - qs.statement_start_offset)/2) + 1) AS statement_text  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
ORDER BY total_worker_time/execution_count DESC;  
```  
  
### <a name="c-provide-batch-execution-statistics"></a>В. Предоставляют статистику выполнения пакетов  
 Следующий пример возвращает текст запросов SQL, выполняемых в пакетах, и статистические сведения о них.  
  
```sql  
SELECT s2.dbid,   
    s1.sql_handle,    
    (SELECT TOP 1 SUBSTRING(s2.text,statement_start_offset / 2+1 ,   
      ( (CASE WHEN statement_end_offset = -1   
         THEN (LEN(CONVERT(nvarchar(max),s2.text)) * 2)   
         ELSE statement_end_offset END)  - statement_start_offset) / 2+1))  AS sql_statement,  
    execution_count,   
    plan_generation_num,   
    last_execution_time,     
    total_worker_time,   
    last_worker_time,   
    min_worker_time,   
    max_worker_time,  
    total_physical_reads,   
    last_physical_reads,   
    min_physical_reads,    
    max_physical_reads,    
    total_logical_writes,   
    last_logical_writes,   
    min_logical_writes,   
    max_logical_writes    
FROM sys.dm_exec_query_stats AS s1   
CROSS APPLY sys.dm_exec_sql_text(sql_handle) AS s2    
WHERE s2.objectid is null   
ORDER BY s1.sql_handle, s1.statement_start_offset, s1.statement_end_offset;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_cursors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cursors-transact-sql.md)   
 [sys.dm_exec_xml_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)   
 [Использования оператора APPLY](../../t-sql/queries/from-transact-sql.md#using-apply)   
 [sys.dm_exec_text_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)  

