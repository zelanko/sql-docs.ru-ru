---
title: sys.dm_exec_text_query_plan (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_text_query_plan
- sys.dm_exec_text_query_plan_TSQL
- dm_exec_text_query_plan_TSQL
- sys.dm_exec_text_query_plan
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_text_query_plan dynamic management function
ms.assetid: 9d5e5f59-6973-4df9-9eb2-9372f354ca57
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e5cd5feeb26a80ad404238d9e10a8b37dfbcefaa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711632"
---
# <a name="sysdmexectextqueryplan-transact-sql"></a>sys.dm_exec_text_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает инструкцию Showplan в текстовом формате для пакета [!INCLUDE[tsql](../../includes/tsql-md.md)] или для определенной инструкции в пакете. План запроса, указанный в дескрипторе плана может быть кэширован или текущей выполняемой. Эта функция с табличным аналогичен [sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md), но имеет следующие отличия:  
  
-   Вывод плана запроса возвращается в текстовом формате.  
  
-   Размер вывода плана запроса не ограничен.  
  
-   Можно указать отдельные инструкции в пакете.  
  
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_exec_text_query_plan   
(   
    plan_handle   
    , { statement_start_offset | 0 | DEFAULT }  
        , { statement_end_offset | -1 | DEFAULT }  
)  
```  
  
## <a name="arguments"></a>Аргументы  
*plan_handle*  
Уникальным образом определяет план запроса для пакета, который находится в кэше или выполняется в данный момент. *plan_handle* — **varbinary(64)**.  
  
Дескриптор плана можно получить из следующих объектов DMO:  
  
-  [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-  [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-  [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
*statement_start_offset* | 0 | ПО УМОЛЧАНИЮ  
Начальная позиция запроса, который описывает строка, в соответствующем тексте пакета или сохраняемом объекте, в байтах. *statement_start_offset* — **int**. Значение 0 обозначает начало пакета. Значение по умолчанию — 0.  
  
Начальное смещение инструкции можно получить из следующих объектов DMO:  
  
-  [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-  [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
*statement_end_offset* | -1 | ПО УМОЛЧАНИЮ  
Конечная позиция запроса, который описывает строка, в соответствующем тексте пакета или сохраняемом объекте, в байтах.  
  
*statement_start_offset* — **int**.  
  
Значение -1 обозначает конец пакета. Значение по умолчанию равно -1.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|Идентификатор базы данных, в контексте которой выполнялась компиляция инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], соответствующей данному плану. Для нерегламентированных и подготовленных инструкций SQL это идентификатор базы данных, в которой происходила компиляция инструкции.<br /><br /> Столбец может содержать значение NULL.|  
|**objectid**|**int**|Идентификатор объекта (например хранимой процедуры или определяемой пользователем функции) для этого плана запроса. Для нерегламентированных и подготовленных пакетов этот столбец содержит **null**.<br /><br /> Столбец может содержать значение NULL.|  
|**номер**|**smallint**|Целое число нумерованных хранимых процедур. Например, группа процедур для **заказы** приложения может называться **orderproc; 1**, **orderproc; 2**, и т. д. Для нерегламентированных и подготовленных пакетов этот столбец содержит **null**.<br /><br /> Столбец может содержать значение NULL.|  
|**Шифрование**|**bit**|Указывает, зашифрована ли соответствующая хранимая процедура.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована<br /><br /> Столбец не может содержать значение NULL.|  
|**query_plan**|**nvarchar(max)**|Содержит представление инструкции Showplan компиляции плана выполнения запроса, которое указано с *plan_handle*. Инструкция Showplan имеет текстовый формат. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план.<br /><br /> Столбец может содержать значение NULL.|  
  
## <a name="remarks"></a>Примечания  
 При следующих условиях вывод инструкции Showplan не возвращается в **план** столбец возвращаемой таблицы для **sys.dm_exec_text_query_plan**:  
  
-   Если план запроса, который задается с помощью *plan_handle* исключен из кэша планов, **query_plan** столбец возвращаемой таблицы имеет значение null. Например, такое условие может возникнуть при наличии задержки между принятием дескриптора плана и когда он использовался с **sys.dm_exec_text_query_plan**.  
  
-   Некоторые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] не кэшируются, к ним относятся инструкции массовых операций, а также инструкции, содержащие строковые литералы размером более 8 КБ. Представление Showplan в формате для таких инструкций нельзя получить с помощью **sys.dm_exec_text_query_plan** так, как они не существуют в кэше.  
  
-   Если [!INCLUDE[tsql](../../includes/tsql-md.md)] пакета или хранимой процедуры содержат вызов определяемой пользователем функции или динамической инструкции SQL, например при помощи EXEC (*строка*), скомпилированная инструкция Showplan XML для определяемой пользователем функции не включается в таблице возвращенный **sys.dm_exec_text_query_plan** для пакета или хранимой процедуры. Вместо этого необходимо отдельно вызвать **sys.dm_exec_text_query_plan** для *plan_handle* , соответствующий определяемой пользователем функции.  
  
Если нерегламентированный запрос использует [простой](../../relational-databases/query-processing-architecture-guide.md#SimpleParam) или [принудительной параметризации](../../relational-databases/query-processing-architecture-guide.md#ForcedParam), **query_plan** столбец будет содержать только текст инструкции, а не фактический план запроса. Чтобы вернуть план запроса, вызовите **sys.dm_exec_text_query_plan** для дескриптора плана подготовленного параметризированного запроса. Можно определить, был ли параметризован запрос, ссылаясь на **sql** столбец [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md) представление или текстовый столбец [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)динамическое административное представление.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения **sys.dm_exec_text_query_plan**, пользователь должен быть членом **sysadmin** предопределенной роли сервера или иметь разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieving-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>A. Получение кэшированного плана запроса для медленно выполняемого запроса или пакета Transact-SQL  
 Если запрос или пакет [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняется длительное время при определенном соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то для определения причины задержки необходимо получить план выполнения для этого запроса или пакета. В следующем примере показано, как получить инструкцию Showplan для медленно выполняемого запроса или пакета.  
  
> [!NOTE]  
> Чтобы выполнить этот пример, замените значения для *session_id* и *plan_handle* значениями, относящимися к серверу.  
  
 Сначала получите идентификатор серверного процесса (SPID) для процесса, выполняющего запрос или пакет, при помощи хранимой процедуры `sp_who`:  
  
```sql  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
 Результирующий набор, возвращаемый процедурой `sp_who`, показывает, что идентификатор SPID равен `54`. Идентификатор SPID можно использовать с динамическим административным представлением `sys.dm_exec_requests` для получения дескриптора плана при помощи следующего запроса:  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 Таблицы, которая возвращается методом **sys.dm_exec_requests** указывает, что дескриптор плана для медленно выполняемого запроса или пакета `0x06000100A27E7C1FA821B10600`. Следующий пример возвращает план запроса для указанного дескриптора плана и использует значения по умолчанию 0 и -1 для возвращения всех инструкций в запросе или пакете.  
  
```sql  
USE master;  
GO  
SELECT query_plan   
FROM sys.dm_exec_text_query_plan (0x06000100A27E7C1FA821B10600,0,-1);  
GO  
```  
  
### <a name="b-retrieving-every-query-plan-from-the-plan-cache"></a>Б. Получение плана каждого запроса из кэша планов  
 Чтобы получить моментальный снимок всех планов запроса, хранимых в кэше планов, необходимо получить дескрипторы планов для всех запросов, хранящихся в кэше, запросив динамическое административное представление `sys.dm_exec_cached_plans`. Дескрипторы планов хранятся в столбце `plan_handle` представления `sys.dm_exec_cached_plans`. Затем воспользуйтесь оператором CROSS APPLY для передачи дескрипторов плана в функцию `sys.dm_exec_text_query_plan`, как показано ниже. Вывод инструкции Showplan для каждого плана, находящегося в кэше планов находится в `query_plan` столбец таблицы, который возвращается.  
  
```sql  
USE master;  
GO  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp   
CROSS APPLY sys.dm_exec_text_query_plan(cp.plan_handle, DEFAULT, DEFAULT);  
GO  
```  
  
### <a name="c-retrieving-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>В. Получение всех планов запросов, для которых сервер собирал статистику запросов, из кэша планов  
 Чтобы получить моментальный снимок всех планов запроса, для которых сервером была собрана статистика и которые в настоящий момент находятся в кэше планов, необходимо получить дескрипторы планов в кэше, запросив динамическое административное представление `sys.dm_exec_query_stats`. Дескрипторы планов хранятся в столбце `plan_handle` представления `sys.dm_exec_query_stats`. Затем воспользуйтесь оператором CROSS APPLY для передачи дескрипторов плана в функцию `sys.dm_exec_text_query_plan`, как показано ниже. Вывод инструкции Showplan для каждого плана находится в столбце `query_plan` возвращаемой таблицы.  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset);  
GO  
```  
  
### <a name="d-retrieving-information-about-the-top-five-queries-by-average-cpu-time"></a>Г. Получение сведений о первых пяти запросах по среднему времени ЦП  
 Следующий пример возвращает планы запросов и среднее время ЦП для пяти первых запросов. **Sys.dm_exec_text_query_plan** функция указывает значения по умолчанию 0 и -1 для возвращения всех инструкций в пакете в плане запроса.  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
Plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, 0, -1)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
