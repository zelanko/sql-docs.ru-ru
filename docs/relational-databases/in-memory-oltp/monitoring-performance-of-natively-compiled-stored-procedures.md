---
title: "Отслеживание производительности хранимых процедур, скомпилированных в собственном коде | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55548cb2-77a8-4953-8b5a-f2778a4f13cf
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d8db102af60a736dd0e971a1799508188a8332dc
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="monitoring-performance-of-natively-compiled-stored-procedures"></a>Отслеживание производительности скомпилированных в собственном коде хранимых процедур
  В этом разделе показано, как наблюдать за производительностью хранимых процедур, скомпилированных в собственном коде  
  
## <a name="using-extended-events"></a>Использование расширенных событий  
 Для трассировки выполнения запроса используйте расширенное событие **sp_statement_completed** . Создайте сеанс с этим событием, при этом можно использовать фильтр в object_id для определенной хранимой процедуры, скомпилированной в собственном коде. Расширенное событие вызывается после выполнения каждого запроса. Время ЦП и время существования, указанные расширенным событием, показывают объем ресурсов ЦП, который потребовался на выполнение запроса, и время его выполнения. Скомпилированная в собственном коде хранимая процедура, которая потребляет значительное время ЦП, может сталкиваться с проблемами производительности.  
  
 **line_number**вместе с **object_id** в расширенном событии можно использовать для анализа запросов. Следующий запрос может использоваться для получения определения процедуры. Номер строки можно использовать для поиска запроса в определении.  
  
```tsql  
select [definition] from sys.sql_modules where object_id=object_id  
```  
  
 Дополнительные сведения о расширенном событии **sp_statement_completed** см. в статье [Как получить инструкцию, которая вызвала событие](http://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx).  
  
## <a name="using-data-management-views"></a>Использование динамических административных представлений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает сбор статистики выполнения для скомпилированных в собственном коде хранимых процедур как на уровне процедуры, так и на уровне запроса. Из-за влияния на производительность сбор статистики выполнения по умолчанию не используется.  
  
 Включать и отключать сбор статистики для скомпилированных в собственном коде хранимых процедур можно с помощью [sys.sp_xtp_control_proc_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).  
  
 Если сбор статистики включен с помощью процедуры [sys.sp_xtp_control_proc_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md), можно с помощью [sys.dm_exec_procedure_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md) выполнять мониторинг производительности скомпилированной в собственном коде хранимой процедуры.  
  
 Если сбор статистики включен с помощью процедуры [sys.sp_xtp_control_query_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md), можно с помощью [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) выполнять мониторинг производительности скомпилированной в собственном коде хранимой процедуры.  
  
 Прежде всего включите сбор статистики. Затем выполните скомпилированную в собственном коде хранимую процедуру. После завершения сбора статистики отключите его. Затем проанализируйте статистику выполнения, которая была возвращена динамическими административными представлениями.  
  
 После того как статистика выполнения хранимых процедур, скомпилированных в собственном коде, будет собрана, запросить ее для определенной процедуры можно будет с помощью [sys.dm_exec_procedure_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md), а для запросов — с помощью [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md).  
  
> [!NOTE]  
>  Если сбор статистики включен, то накопленное время рабочей роли для скомпилированных в собственном коде хранимых процедур указывается в миллисекундах. Если запрос выполняется за время меньше миллисекунды, это значение будет равно 0. Для скомпилированных в собственном коде хранимых процедур функция **total_worker_time** может быть неточной, если за время меньше миллисекунды выполняется большое количество хранимых процедур.  
  
 После сбора статистики следующий запрос возвращает имена и статистику выполнения скомпилированных в собственном коде хранимых процедур в текущей базе данных.  
  
```tsql  
select object_id,  
       object_name(object_id) as 'object name',  
       cached_time,  
       last_execution_time,  
       execution_count,  
       total_worker_time,  
       last_worker_time,  
       min_worker_time,  
       max_worker_time,  
       total_elapsed_time,  
       last_elapsed_time,  
       min_elapsed_time,  
       max_elapsed_time   
from sys.dm_exec_procedure_stats  
where database_id=db_id() and object_id in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by total_worker_time desc  
```  
  
 Следующий запрос возвращает текст запроса, а также статистику выполнения всех запросов из скомпилированных в собственном коде хранимых процедур в текущей базе данных, для которой были собраны статистические данные. Статистика при этом упорядочивается по общему времени рабочей роли в убывающем порядке.  
  
```tsql  
select st.objectid,   
       object_name(st.objectid) as 'object name',   
       SUBSTRING(st.text, (qs.statement_start_offset/2) + 1, ((qs.statement_end_offset-qs.statement_start_offset)/2) + 1) as 'query text',   
       qs.creation_time,  
       qs.last_execution_time,  
       qs.execution_count,  
       qs.total_worker_time,  
       qs.last_worker_time,  
       qs.min_worker_time,  
       qs.max_worker_time,  
       qs.total_elapsed_time,  
       qs.last_elapsed_time,  
       qs.min_elapsed_time,  
       qs.max_elapsed_time  
from sys.dm_exec_query_stats qs cross apply sys.dm_exec_sql_text(sql_handle) st  
where  st.dbid=db_id() and st.objectid in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by qs.total_worker_time desc  
```  
  
 Скомпилированные в собственном коде хранимые процедуры поддерживают SHOWPLAN_XML (предполагаемый план выполнения). С помощью предполагаемого плана выполнения можно проверять план запроса с целью выявления проблем. Общие причины появления некачественных планов.  
  
-   Статистика не была обновлена перед созданием процедуры.  
  
-   Отсутствующие индексы  
  
 Для получения Showplan XML выполняется следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
```tsql  
SET SHOWPLAN_XML ON  
GO  
EXEC my_proc   
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 Кроме того, в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выберите имя процедуры и щелкните **Показать предполагаемый план выполнения**.  
  
 Предполагаемый план выполнения для скомпилированных в собственном коде хранимых процедур показывает операторы и выражения для запросов из процедуры. [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] не поддерживает все атрибуты SHOWPLAN_XML для скомпилированных в собственном коде хранимых процедур. Например, атрибуты, связанные с оценкой затрат оптимизатора запросов, не являются частью SHOWPLAN_XML для процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
