---
title: sys.dm_exec_query_plan (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_plan_TSQL
- sys.dm_exec_query_plan
- dm_exec_query_plan
- sys.dm_exec_query_plan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_plan dynamic management function
ms.assetid: e26f0867-9be3-4b2e-969e-7f2840230770
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b76d583cf73b035024e57ba1cb66e63c76d1ad23
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797192"
---
# <a name="sysdmexecqueryplan-transact-sql"></a>sys.dm_exec_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает события инструкции Showplan в XML-формате для пакета, указанного в дескрипторе плана. План, указанный в дескрипторе плана может быть кэширован или выполняться в данный момент.  
  
 Схема XML для Showplan опубликованные, так и найти по адресу [веб-узле Microsoft](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409). Эта схема также доступна в папке установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_exec_query_plan ( plan_handle )  
```  
  
## <a name="arguments"></a>Аргументы  
 *plan_handle*  
 Уникальным образом определяет план запроса для пакета, который находится в кэше или выполняется в данный момент.  
  
 *plan_handle* — **varbinary(64)**. *plan_handle* можно получить из следующих объектов DMO:  
  
 [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
 [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
 [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|Идентификатор базы данных, в контексте которой выполнялась компиляция инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], соответствующей данному плану. Для нерегламентированных и подготовленных инструкций SQL это идентификатор базы данных, в которой происходила компиляция инструкции.<br /><br /> Столбец может содержать значение NULL.|  
|**objectid**|**int**|Идентификатор объекта (например хранимой процедуры или определяемой пользователем функции) для этого плана запроса. Для нерегламентированных и подготовленных пакетов этот столбец содержит **null**.<br /><br /> Столбец может содержать значение NULL.|  
|**номер**|**smallint**|Целое число нумерованных хранимых процедур. Например, группа процедур для **заказы** приложения может называться **orderproc; 1**, **orderproc; 2**, и т. д. Для нерегламентированных и подготовленных пакетов этот столбец содержит **null**.<br /><br /> Столбец может содержать значение NULL.|  
|**Шифрование**|**bit**|Указывает, зашифрована ли соответствующая хранимая процедура.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована<br /><br /> Столбец не может содержать значение NULL.|  
|**query_plan**|**xml**|Содержит представление инструкции Showplan компиляции плана выполнения запроса, которое указано с *plan_handle*. Представление Showplan имеет формат XML. Для каждого пакета, содержащего, например нерегламентированные инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], вызовы хранимых процедур и вызовы определяемых пользователем функций, формируется один план.<br /><br /> Столбец может содержать значение NULL.|  
  
## <a name="remarks"></a>Примечания  
 При следующих условиях вывод инструкции Showplan не возвращается в **query_plan** столбец возвращаемой таблицы для **sys.dm_exec_query_plan**:  
  
-   Если план запроса, который задается с помощью *plan_handle* исключен из кэша планов, **query_plan** столбец возвращаемой таблицы имеет значение null. Например, такое условие может возникнуть при наличии задержки между принятием дескриптора плана и когда он использовался с **sys.dm_exec_query_plan**.  
  
-   Некоторые инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] не кэшируются, к ним относятся инструкции массовых операций, а также инструкции, содержащие строковые литералы размером более 8 КБ. Представление Showplan в формате XML для таких инструкций нельзя получить с помощью **sys.dm_exec_query_plan** Если пакет выполняется в данный момент, так как они не существуют в кэше.  
  
-   Если [!INCLUDE[tsql](../../includes/tsql-md.md)] пакета или хранимой процедуры содержат вызов определяемой пользователем функции или динамической инструкции SQL, например при помощи EXEC (*строка*), скомпилированная инструкция Showplan XML для определяемой пользователем функции не включается в таблице возвращенный **sys.dm_exec_query_plan** для пакета или хранимой процедуры. Вместо этого необходимо отдельно вызвать **sys.dm_exec_query_plan** для дескриптора плана, который соответствует определяемой пользователем функции.  
  
 Если нерегламентированный запрос использует простую или принудительную параметризацию, **query_plan** столбец будет содержать только текст инструкции, а не фактический план запроса. Чтобы вернуть план запроса, вызовите **sys.dm_exec_query_plan** для дескриптора плана подготовленного параметризированного запроса. Можно определить, был ли параметризован запрос, ссылаясь на **sql** столбец [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md) представление или текстовый столбец [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)динамическое административное представление.  
  
 Из-за ограничения количества уровней вложенности, допустимых в **xml** тип данных, **sys.dm_exec_query_plan** не может возвратить планы запросов, которые соответствуют или превосходят 128 уровней вложенных элементов. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это условие предназначалось для предотвращения возврата плана запроса и формирования ошибки 6335. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 и более поздних версиях **query_plan** столбец возвращает значение NULL. Можно использовать [sys.dm_exec_text_query_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md) функции динамического управления для возврата плана запроса в текстовом формате.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения **sys.dm_exec_query_plan**, пользователь должен быть членом **sysadmin** предопределенной роли сервера или иметь разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры показывают, как использовать **sys.dm_exec_query_plan** динамическое административное представление.  
  
 Чтобы просмотреть представление Showplan в формате XML, выполните следующие запросы в редакторе запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], затем нажмите кнопку **ShowPlanXML** в **query_plan** столбец таблицы, возвращаемой функцией **sys.dm_ exec_query_plan**. Представление Showplan в формате XML отображается на сводной панели среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Чтобы сохранить данные XML Showplan в файл, щелкните правой кнопкой мыши **ShowPlanXML** в **query_plan** столбец, нажмите кнопку **сохранить результаты как**, назовите файл в формате \< *имя_файла*> .sqlplan; например, MyXMLShowplan.sqlplan.  
  
### <a name="a-retrieve-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>A. Получение кэшированного плана запроса для медленно выполняемого запроса или пакета Transact-SQL  
 Планы запросов для различных типов пакетов [!INCLUDE[tsql](../../includes/tsql-md.md)], в том числе нерегламентированных пакетов, хранимых процедур и определяемых пользователем функций, кэшируются в области памяти, называемой кэшем планов. Каждый кэшированный план запроса идентифицируется при помощи уникального идентификатора, дескриптора плана. Можно указать дескриптор плана при помощи **sys.dm_exec_query_plan** динамическое административное представление, чтобы получить план выполнения для какого-либо [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса или пакета.  
  
 Если запрос или пакет [!INCLUDE[tsql](../../includes/tsql-md.md)] выполняется длительное время при определенном соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то для определения причины задержки необходимо получить план выполнения для этого запроса или пакета. В следующем примере показано, как получить представление Showplan в формате XML для медленно выполняемого запроса или пакета.  
  
> [!NOTE]  
>  Чтобы выполнить этот пример, замените значения для *session_id* и *plan_handle* значениями, относящимися к серверу.  
  
 Сначала получите идентификатор серверного процесса (SPID) для процесса, выполняющего запрос или пакет, при помощи хранимой процедуры `sp_who`:  
  
```  
USE master;  
GO  
exec sp_who;  
GO  
```  
  
 Результирующий набор, возвращаемый процедурой `sp_who`, показывает, что идентификатор SPID равен `54`. Идентификатор SPID можно использовать с динамическим административным представлением `sys.dm_exec_requests` для получения дескриптора плана при помощи следующего запроса:  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 Таблицы, которая возвращается методом **sys.dm_exec_requests** указывает, что дескриптор плана для медленно выполняемого запроса или пакета `0x06000100A27E7C1FA821B10600`, который можно указать в качестве *plan_handle* аргумент с `sys.dm_exec_query_plan` Чтобы получить план выполнения в формате XML следующим образом. План выполнения в формате XML для медленно выполняемого запроса или пакета содержится в **query_plan** столбец таблицы, возвращаемой функцией `sys.dm_exec_query_plan`.  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_plan (0x06000100A27E7C1FA821B10600);  
GO  
```  
  
### <a name="b-retrieve-every-query-plan-from-the-plan-cache"></a>Б. Получение плана каждого запроса из кэша планов  
 Чтобы получить моментальный снимок всех планов запроса, хранимых в кэше планов, необходимо получить дескрипторы планов для всех запросов, хранящихся в кэше, запросив динамическое административное представление `sys.dm_exec_cached_plans`. Дескрипторы планов хранятся в столбце `plan_handle` представления `sys.dm_exec_cached_plans`. Затем воспользуйтесь оператором CROSS APPLY для передачи дескрипторов плана в функцию `sys.dm_exec_query_plan`, как показано ниже. Вывод инструкции Showplan в формате XML для каждого плана, находящегося в кэше планов, находится в столбце `query_plan` возвращаемой таблицы.  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_cached_plans cp CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
GO  
```  
  
### <a name="c-retrieve-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>В. Получение всех планов запросов, для которых сервер собрал статистику запросов из кэша планов  
 Чтобы получить моментальный снимок всех планов запроса, для которых сервером была собрана статистика и которые в настоящий момент находятся в кэше планов, необходимо получить дескрипторы планов в кэше, запросив динамическое административное представление `sys.dm_exec_query_stats`. Дескрипторы планов хранятся в столбце `plan_handle` представления `sys.dm_exec_query_stats`. Затем воспользуйтесь оператором CROSS APPLY для передачи дескрипторов плана в функцию `sys.dm_exec_query_plan`, как показано ниже. Вывод инструкции Showplan в формате XML для каждого плана, который находится в кэше планов и для которого сервер собирал статистику, находится в столбце `query_plan` возвращаемой таблицы.  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_stats qs CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle);  
GO  
```  
  
### <a name="d-retrieve-information-about-the-top-five-queries-by-average-cpu-time"></a>Г. Получение сведений о первых пяти запросах по среднему времени ЦП  
 Следующий пример возвращает планы и среднее время ЦП для пяти первых запросов.  
  
```  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
Plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Справочник по логическим и физическим операторам Showplan](../../relational-databases/showplan-logical-and-physical-operators-reference.md)   
 [sys.dm_exec_text_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)  
  
  

