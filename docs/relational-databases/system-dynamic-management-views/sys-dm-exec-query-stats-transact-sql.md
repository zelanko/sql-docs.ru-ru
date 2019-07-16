---
title: sys.dm_exec_query_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_stats_TSQL
- dm_exec_query_stats
- sys.dm_exec_query_stats
- sys.dm_exec_query_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_stats dynamic management view
ms.assetid: eb7b58b8-3508-4114-97c2-d877bcb12964
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4811d27e00336f6e02d62d9dd6c346d26400f129
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936931"
---
# <a name="sysdmexecquerystats-transact-sql"></a>sys.dm_exec_query_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает суммарную статистику производительности для кэшированных планов запросов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представление содержит по одной строке для каждой инструкции запроса в плане в кэше, а время жизни строк связано с самим планом. Когда план удаляется из кэша, соответствующие строки исключаются из представления.  
  
> [!NOTE]
> Начальный запрос представления **sys.dm_exec_query_stats** может выдавать неточные результаты, если рабочая нагрузка в данный момент на сервере. Более точные результаты могут быть получены при повторном выполнении запроса.  
  
> [!NOTE]
> Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_exec_query_stats**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**sql_handle**|**varbinary(64)**  |— Это маркер, уникально определяющий пакета или хранимой процедуры, частью которого является запрос.<br /><br /> **sql_handle**вместе с **statement_start_offset** и **statement_end_offset**, можно использовать для получения текста SQL запроса путем вызова **sys.dm_exec_sql_ текст** функции динамического управления.|  
|**statement_start_offset**|**int**|Начальная позиция запроса, описываемого строкой, в соответствующем тексте пакета или сохраняемом объекте, в байтах, начиная с 0.|  
|**statement_end_offset**|**int**|Конечная позиция запроса, описываемого строкой, в соответствующем тексте пакета или сохраняемом объекте, в байтах, начиная с 0. Для версий младше [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], значение -1 указывает конец пакета. Конечные комментарии больше не будут включать.|  
|**plan_generation_num**|**bigint**|Порядковый номер, который может использоваться для проведения различия между экземплярами планов после рекомпиляции.|  
|**plan_handle**|**varbinary(64)**|— Это маркер, который уникально идентифицирует план выполнения запроса для запущенного пакета, и ее план находится в кэше планов, или в данный момент. Это значение может быть передан [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md) функции динамического управления для получения плана запроса.<br /><br /> Значение всегда равно 0x000, если скомпилированная в собственном коде хранимая процедура запрашивает оптимизированную для памяти таблицу.|  
|**creation_time**|**datetime**|Время компиляции плана.|  
|**last_execution_time**|**datetime**|Время начала последнего выполнения плана.|  
|**execution_count**|**bigint**|Количество выполнений плана с момента последней компиляции.|  
|**total_worker_time**|**bigint**|Общее время ЦП, затраченное на выполнение плана с момента компиляции, в микросекундах (но с точностью до миллисекунды).<br /><br /> Для скомпилированных в собственном коде хранимых процедур функция **total_worker_time** может быть неточной, если за время меньше миллисекунды выполняется большое количество хранимых процедур.|  
|**last_worker_time**|**bigint**|Время ЦП, затраченное на последнее выполнение плана, в микросекундах (но с точностью до миллисекунды). <sup>1</sup>|  
|**min_worker_time**|**bigint**|Минимальное время ЦП, когда-либо затраченное на выполнение плана, в микросекундах (но с точностью до миллисекунды). <sup>1</sup>|  
|**max_worker_time**|**bigint**|Максимальное время ЦП, когда-либо затраченное на выполнение плана, в микросекундах (но с точностью до миллисекунды). <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Общее количество операций физического считывания при выполнении плана с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_physical_reads**|**bigint**|Количество операций физического считывания за время последнего выполнения плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_physical_reads**|**bigint**|Минимальное количество операций физического считывания за одно выполнение плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_physical_reads**|**bigint**|Максимальное количество операций физического считывания за одно выполнение плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_writes**|**bigint**|Общее количество операций логической записи при выполнении плана с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_writes**|**bigint**|Количество страниц в буферном пуле, измененных во время последнее выполнение плана.<br /><br />После чтения страницы, страница становится "грязных" только в первый раз, его изменения. Когда страница становится "грязные", этот номер увеличивается. Последующие изменения уже "грязные" страницы не влияют на этот номер.<br /><br />Это число всегда будет равно 0, при запросе оптимизированной для памяти таблицы.|  
|**min_logical_writes**|**bigint**|Минимальное количество операций логической записи за одно выполнение плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_writes**|**bigint**|Максимальное количество операций логической записи за одно выполнение плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_logical_reads**|**bigint**|Общее количество операций логического считывания при выполнении плана с момента его компиляции.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**last_logical_reads**|**bigint**|Количество операций логического считывания за время последнего выполнения плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**min_logical_reads**|**bigint**|Минимальное количество операций логического считывания за одно выполнение плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**max_logical_reads**|**bigint**|Максимальное количество операций логического считывания за одно выполнение плана.<br /><br /> Значение всегда равно 0 при запросе оптимизированной для памяти таблицы.|  
|**total_clr_time**|**bigint**|Время, в микросекундах (но с точностью до миллисекунды), внутри [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] общеязыковая среда выполнения (CLR) объекты при выполнении плана с момента его компиляции. Объекты среды CLR могут быть хранимыми процедурами, функциями, триггерами, типами и статистическими выражениями.|  
|**last_clr_time**|**bigint**|Время, затраченное на последнее выполнение плана внутри объектов [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] среды CLR в микросекундах (но с точностью до миллисекунды). Объекты среды CLR могут быть хранимыми процедурами, функциями, триггерами, типами и статистическими выражениями.|  
|**min_clr_time**|**bigint**|Минимальное время, когда-либо затраченное на выполнение плана внутри объектов [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] среды CLR, в микросекундах (но с точностью до миллисекунды). Объекты среды CLR могут быть хранимыми процедурами, функциями, триггерами, типами и статистическими выражениями.|  
|**max_clr_time**|**bigint**|Максимальное время, когда-либо затраченное на выполнение плана внутри среды CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], в микросекундах (но с точностью до миллисекунды). Объекты среды CLR могут быть хранимыми процедурами, функциями, триггерами, типами и статистическими выражениями.|  
|**total_elapsed_time**|**bigint**|Общее время, затраченное на выполнение плана, в микросекундах (но с точностью до миллисекунды).|  
|**last_elapsed_time**|**bigint**|Время, затраченное на последнее выполнение плана, в микросекундах (но с точностью до миллисекунды).|  
|**min_elapsed_time**|**bigint**|Минимальное время, когда-либо затраченное на выполнение плана, в микросекундах (но с точностью до миллисекунды).|  
|**max_elapsed_time**|**bigint**|Максимальное время, когда-либо затраченное на выполнение плана, в микросекундах (но с точностью до миллисекунды).|  
|**query_hash**|**binary(8)**|Двоичное хэш-значение рассчитывается для запроса и используется для идентификации запросов с аналогичной логикой. Можно использовать хэш запроса для определения использования статистических ресурсов для запросов, которые отличаются только своими литеральными значениями.|  
|**query_plan_hash**|**binary(8)**|Двоичное хэш-значение рассчитывается для плана выполнения запроса и используется для идентификации аналогичных планов выполнения запросов. Можно использовать хэш плана запроса для нахождения совокупной стоимости запросов со схожими планами выполнения.<br /><br /> Значение всегда равно 0x000, если скомпилированная в собственном коде хранимая процедура запрашивает оптимизированную для памяти таблицу.|  
|**total_rows**|**bigint**|Общее число строк, возвращаемых запросом. Не может иметь значение null.<br /><br /> Значение всегда равно 0, если скомпилированная в собственном коде хранимая процедура запрашивает оптимизированную для памяти таблицу.|  
|**last_rows**|**bigint**|Число строк, возвращенных последним выполнением запроса. Не может иметь значение null.<br /><br /> Значение всегда равно 0, если скомпилированная в собственном коде хранимая процедура запрашивает оптимизированную для памяти таблицу.|  
|**min_rows**|**bigint**|Минимальное количество строк, когда-либо возвращенных при выполнении запроса во время одного выполнения. Не может иметь значение null.<br /><br /> Значение всегда равно 0, если скомпилированная в собственном коде хранимая процедура запрашивает оптимизированную для памяти таблицу.|  
|**Max_Rows**|**bigint**|Максимальное число строк, когда-либо возвращенных при выполнении запроса во время одного выполнения. Не может иметь значение null.<br /><br /> Значение всегда равно 0, если скомпилированная в собственном коде хранимая процедура запрашивает оптимизированную для памяти таблицу.|  
|**statement_sql_handle**|**varbinary(64)**|**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Заполнены значениями отличное от NULL только в том случае, если включен Query Store и сбор статистики для данного конкретного запроса.|  
|**statement_context_id**|**bigint**|**Применимо к**: с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Заполнены значениями отличное от NULL только в том случае, если включен Query Store и сбор статистики для данного конкретного запроса.|  
|**total_dop**|**bigint**|Этот план общую сумму степень параллелизма и использовать с момента его компиляции. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_dop**|**bigint**|Степень параллелизма, если время последнего выполнения этого плана. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_dop**|**bigint**|Минимальная степень параллелизма этот план когда-либо используется во время одного выполнения. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_dop**|**bigint**|Максимальная степень параллелизма этот план когда-либо используется во время одного выполнения. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_grant_kb**|**bigint**|Общий объем зарезервированной памяти в КБ предоставить этот план, полученных с момента его компиляции. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_grant_kb**|**bigint**|Объем памяти, зарезервированный предоставляет в КБ, когда время последнего выполнения этого плана. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_grant_kb**|**bigint**|Минимальный объем зарезервированной памяти в КБ предоставить этот план когда-либо получено во время выполнения одного. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_grant_kb**|**bigint**|Максимальный объем зарезервированной памяти в КБ предоставить этот план когда-либо получено во время выполнения одного. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_used_grant_kb**|**bigint**|Общий объем зарезервированной памяти в КБ предоставить этот план, используемый с момента его компиляции. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_used_grant_kb**|**bigint**|Объем grant используемой памяти в КБ, если время последнего выполнения этого плана. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_used_grant_kb**|**bigint**|Минимальный объем используемой памяти в КБ предоставить этот план, использовали во время выполнения одного. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_used_grant_kb**|**bigint**|Максимальный объем используемой памяти в КБ предоставить этот план, использовали во время выполнения одного. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_ideal_grant_kb**|**bigint**|Общий объем grant идеальная память в КБ, Оценка этого плана с момента его компиляции. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_ideal_grant_kb**|**bigint**|Объем памяти, идеальный предоставляет в КБ, когда время последнего выполнения этого плана. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_ideal_grant_kb**|**bigint**|Минимальный объем памяти идеально предоставить этот план когда-либо оценка во время выполнения одной базы Знаний. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_ideal_grant_kb**|**bigint**|Максимальный объем памяти идеально предоставить этот план когда-либо оценка во время выполнения одной базы Знаний. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_reserved_threads**|**bigint**|Общую сумму зарезервированные параллельных потоков этот план когда-либо с момента его компиляции. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_reserved_threads**|**bigint**|Число зарезервированных параллельных потоков, когда время последнего выполнения этого плана. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_reserved_threads**|**bigint**|Минимальное число зарезервированных параллельных потоков использовали во время выполнения одного плана.  Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_reserved_threads**|**bigint**|Максимальное число зарезервированных параллельных потоков, использовали во время выполнения одного плана. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_used_threads**|**bigint**|Общая сумма используется параллельных потоков этот план когда-либо с момента его компиляции. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**last_used_threads**|**bigint**|Число используемых параллельных потоков, когда время последнего выполнения этого плана. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**min_used_threads**|**bigint**|Минимальное число используемых параллельных потоков, этот план когда-либо используется во время одного выполнения. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**max_used_threads**|**bigint**|Максимальное число используемых параллельных потоков, этот план когда-либо используется во время одного выполнения. Он всегда будет равно 0, для запроса к таблице, оптимизированной для памяти.<br /><br /> **Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**total_columnstore_segment_reads**|**bigint**|Общая сумма сегментов columnstore, считанных запросом. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_reads**|**bigint**|Число сегментов columnstore прочитан последнего выполнения запроса. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_reads**|**bigint**|Минимальное количество сегментов columnstore, когда-либо считанных запросом, во время одного выполнения. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_reads**|**bigint**|Максимальное количество сегментов columnstore, когда-либо считанных запросом, во время одного выполнения. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**total_columnstore_segment_skips**|**bigint**|Общая сумма сегментов columnstore пропущена по запросу. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**last_columnstore_segment_skips**|**bigint**|Количество сегментов columnstore, пропущенных последнего выполнения запроса. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**min_columnstore_segment_skips**|**bigint**|Минимальное количество сегментов columnstore, когда-либо пропущена по запросу во время одного выполнения. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|    
|**max_columnstore_segment_skips**|**bigint**|Максимальное количество сегментов columnstore, когда-либо пропущена по запросу во время одного выполнения. Не может иметь значение null.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|
|**total_spills**|**bigint**|Общее число страниц, сброшенных при выполнении этого запроса с момента его компиляции.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|Число страниц, сброшенных последнего выполнения запроса.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|Минимальное число страниц, которые когда-либо этот запрос вытеснены за одно выполнение.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|Максимальное число страниц, которые когда-либо этот запрос вытеснены за одно выполнение.<br /><br /> **Область применения**: Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**pdw_node_id**|**int**|Идентификатор для узла, это распределение является на.<br /><br /> **Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]| 
|**total_page_server_reads**|**bigint**|Общее число удаленных страницы сервера операций считывания при выполнении плана с момента его компиляции.<br /><br /> **Применимо к:** Гипермасштабируемый базы данных Azure SQL |  
|**last_page_server_reads**|**bigint**|Количество операций считывания страницы удаленного сервера выполнять последнего выполнения плана.<br /><br /> **Область применения:** Гипермасштабируемый базы данных Azure SQL |  
|**min_page_server_reads**|**bigint**|Минимальное число сервера удаленной странице считывает, что этот план операций за одно выполнение.<br /><br /> **Область применения:** Гипермасштабируемый базы данных Azure SQL |  
|**max_page_server_reads**|**bigint**|Максимальное количество серверов удаленной странице считывает, что этот план операций за одно выполнение.<br /><br /> **Область применения:** Гипермасштабируемый базы данных Azure SQL |  
> [!NOTE]
> <sup>1</sup> для скомпилированных хранимых процедур при включении сбора статистики накопленное время рабочей роли собираются в миллисекундах. Если запрос выполняется в менее одной миллисекунды, значение будет равно 0.  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
В [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] необходимо разрешение `VIEW DATABASE STATE` для базы данных.   
   
## <a name="remarks"></a>Примечания  
 Статистика в представлении обновляется после завершения выполнения запроса.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-finding-the-top-n-queries"></a>A. Поиск запросов TOP N  
 В следующем примере возвращаются сведения о пяти первых запросах, отсортированных по среднему времени ЦП. В этом примере объединяются запросы в соответствии с хэшем запроса таким образом, чтобы обеспечить группировку логически эквивалентных запросов по их совокупному потреблению ресурсов.  
  
```sql  
SELECT TOP 5 query_stats.query_hash AS "Query Hash",   
    SUM(query_stats.total_worker_time) / SUM(query_stats.execution_count) AS "Avg CPU Time",  
    MIN(query_stats.statement_text) AS "Statement Text"  
FROM   
    (SELECT QS.*,   
    SUBSTRING(ST.text, (QS.statement_start_offset/2) + 1,  
    ((CASE statement_end_offset   
        WHEN -1 THEN DATALENGTH(ST.text)  
        ELSE QS.statement_end_offset END   
            - QS.statement_start_offset)/2) + 1) AS statement_text  
     FROM sys.dm_exec_query_stats AS QS  
     CROSS APPLY sys.dm_exec_sql_text(QS.sql_handle) as ST) as query_stats  
GROUP BY query_stats.query_hash  
ORDER BY 2 DESC;  
```  
  
### <a name="b-returning-row-count-aggregates-for-a-query"></a>Б. Возврат статистического выражения счетчика строк для запроса  
 В следующем примере показан возврат сведений о статистическом выражении счетчика строк (общее число строк, минимальное число строк, максимальное число строк и число строк при последнем выполнении) для запросов.  
  
```sql  
SELECT qs.execution_count,  
    SUBSTRING(qt.text,qs.statement_start_offset/2 +1,   
                 (CASE WHEN qs.statement_end_offset = -1   
                       THEN LEN(CONVERT(nvarchar(max), qt.text)) * 2   
                       ELSE qs.statement_end_offset end -  
                            qs.statement_start_offset  
                 )/2  
             ) AS query_text,   
     qt.dbid, dbname= DB_NAME (qt.dbid), qt.objectid,   
     qs.total_rows, qs.last_rows, qs.min_rows, qs.max_rows  
FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS qt   
WHERE qt.text like '%SELECT%'   
ORDER BY qs.execution_count DESC;  
```  
  
## <a name="see-also"></a>См. также  
[Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)    
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)    
[sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)     
[sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)     
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  


