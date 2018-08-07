---
title: Отслеживание производительности хранимых процедур, скомпилированных в собственном коде | Документация Майкрософт
ms.custom: ''
ms.date: 04/03/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 55548cb2-77a8-4953-8b5a-f2778a4f13cf
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 6a7566bb3d86885872f4b0dba9cf79aaae13460f
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39554504"
---
# <a name="monitoring-performance-of-natively-compiled-stored-procedures"></a>Отслеживание производительности скомпилированных в собственном коде хранимых процедур
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этой статье показано, как наблюдать за производительностью хранимых процедур, скомпилированных в собственном коде, а также других скомпилированных в собственном коде модулей T-SQL.  
  
## <a name="using-extended-events"></a>Использование расширенных событий  
 Для трассировки выполнения запроса используйте расширенное событие **sp_statement_completed** . Создайте сеанс с этим событием, при этом можно использовать фильтр в object_id для определенной хранимой процедуры, скомпилированной в собственном коде. Расширенное событие вызывается после выполнения каждого запроса. Время ЦП и время существования, указанные расширенным событием, показывают объем ресурсов ЦП, который потребовался на выполнение запроса, и время его выполнения. Скомпилированная в собственном коде хранимая процедура, которая потребляет значительное время ЦП, может сталкиваться с проблемами производительности.  
  
 **line_number**вместе с **object_id** в расширенном событии можно использовать для анализа запросов. Следующий запрос может использоваться для получения определения процедуры. Номер строки можно использовать для поиска запроса в определении.  
  
```sql  
select [definition] from sys.sql_modules where object_id=object_id  
```  
  
 Дополнительные сведения о расширенном событии **sp_statement_completed** см. в статье [Как получить инструкцию, которая вызвала событие](http://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx).  
  
## <a name="using-data-management-views-and-query-store"></a>Использование динамических административных представлений и хранилища запросов
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] поддерживают сбор статистики выполнения для скомпилированных в собственном коде хранимых процедур как на уровне процедуры, так и на уровне запроса. Из-за влияния на производительность сбор статистики выполнения по умолчанию не используется.  

Статистика выполнения отражается в системных представлениях [sys.dm_exec_procedure_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md) и [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md), а также в [хранилище запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).

### <a name="enabling-procedure-level-execution-statistics-collection"></a>Включение сбора статистики на уровне процедуры

**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: включите или отключите сбор статистики для скомпилированных в собственном коде хранимых процедур на уровне процедуры с помощью [sys.sp_xtp_control_proc_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).  Следующая инструкция включает сбор статистики выполнения на уровне процедуры для всех скомпилированных в собственном коде модулей T-SQL текущего экземпляра:
```sql
EXEC sys.sp_xtp_control_proc_exec_stats 1
```

**[!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]**: включите или отключите сбор статистики для скомпилированных в собственном коде хранимых процедур на уровне процедуры с помощью [database-scoped configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md), используя параметр `XTP_PROCEDURE_EXECUTION_STATISTICS`. Следующая инструкция включает сбор статистики выполнения на уровне процедуры для всех скомпилированных в собственном коде модулей T-SQL текущей базы данных:
```sql
ALTER DATABASE SCOPED CONFIGURATION SET XTP_PROCEDURE_EXECUTION_STATISTICS = ON
```

### <a name="enabling-query-level-execution-statistics-collection"></a>Включение сбора статистики на уровне запроса

**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: включите или отключите сбор статистики для скомпилированных в собственном коде хранимых процедур на уровне запроса с помощью [sys.sp_xtp_control_query_exec_stats (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  Следующая инструкция включает сбор статистики выполнения на уровне запроса для всех скомпилированных в собственном коде модулей T-SQL текущего экземпляра:
```sql
EXEC sys.sp_xtp_control_query_exec_stats 1
```

**[!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]**: включите или отключите сбор статистики для скомпилированных в собственном коде хранимых процедур на уровне инструкции с помощью [database-scoped configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md), используя параметр `XTP_QUERY_EXECUTION_STATISTICS`. Следующая инструкция включает сбор статистики выполнения на уровне запроса для всех скомпилированных в собственном коде модулей T-SQL текущей базы данных:
```sql
ALTER DATABASE SCOPED CONFIGURATION SET XTP_QUERY_EXECUTION_STATISTICS = ON
```

## <a name="sample-queries"></a>Примеры запросов

 После того как статистика выполнения хранимых процедур, скомпилированных в собственном коде, будет собрана, запросить ее для определенной процедуры можно будет с помощью [sys.dm_exec_procedure_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md), а для запросов — с помощью [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md).  
 
  
 После сбора статистики следующий запрос возвращает имена и статистику выполнения скомпилированных в собственном коде хранимых процедур в текущей базе данных.  
  
```sql  
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
  
```sql  
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

## <a name="query-execution-plans"></a>Планы выполнения запросов

 Скомпилированные в собственном коде хранимые процедуры поддерживают SHOWPLAN_XML (предполагаемый план выполнения). С помощью предполагаемого плана выполнения можно проверять план запроса с целью выявления проблем. Общие причины появления некачественных планов.  
  
-   Статистика не была обновлена перед созданием процедуры.  
  
-   Отсутствующие индексы  
  
 Для получения Showplan XML выполняется следующая инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
```sql  
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
  
  
