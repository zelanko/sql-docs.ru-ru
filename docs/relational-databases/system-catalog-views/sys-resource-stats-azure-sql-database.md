---
title: "sys.resource_stats (база данных SQL Azure) | Документы Microsoft"
ms.custom: 
ms.date: 05/23/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
caps.latest.revision: "28"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dad039b91c30e4c8d89168dd90d549ec6507c750
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает загрузку ЦП и данные хранилища для базы данных SQL Azure. Эти данные собираются и объединяются с пятиминутными интервалами. Для каждой пользовательской базы данных существует одна строка для каждого пятиминутного окна отчетности без изменения потребления ресурсов. Это может быть изменение загрузки ЦП, размера хранилища и номер SKU базы данных. Для простаивающих баз данных без изменений строки для каждого пятиминутного интервала могут отсутствовать. Данные предыстории хранятся приблизительно в течение 14 суток.  
  
 **Sys.resource_stats** представление имеет разные определения в зависимости от версии сервера базы данных SQL Azure, связанный с базы данных. Рассмотрим эти различия и все изменения, которые требуются приложению при обновлении до новой версии сервера.  
  
 В следующей таблице описываются столбцы, доступные на сервере v12.  
  
|Столбцы (сервер v12)|Тип данных|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Время в формате UTC, указывающее начало 5-минутного отчетного интервала.|  
|end_time|**datetime**|Время в формате UTC, указывающее окончание 5-минутного периода составления отчетов.|  
|database_name|**varchar**|Имя пользовательской базы данных.|  
|sku|**varchar**|Уровень служб базы данных. Допустимы следующие значения:<br /><br /> Basic<br /><br /> Standard Edition<br /><br /> Premium|  
|storage_in_megabytes|**float**|Максимальный объем хранилища в мегабайтах в течение периода времени, в том числе данные базы данных, индексы, хранимые процедуры и метаданные.|  
|avg_cpu_percent|**numeric**|Средний уровень использования вычислительных мощностей в процентах от предела для уровня службы.|  
|avg_data_io_percent|**numeric**|Средний уровень использования операций ввода-вывода в процентах от предела для уровня службы.|  
|avg_log_write_percent|**numeric**|Средний уровень использования ресурсов записи в процентах от предела для уровня службы.|  
|max_worker_percent|**Decimal(5,2)**|Максимальная одновременных рабочих процессов (запросов) в процентах от предела для уровня службы базы данных.<br /><br /> В настоящее время максимальное рассчитывается для 5-минутный интервал, на основании 15 второй выборки, количества параллельных рабочих.|  
|max_session_percent|**Decimal(5,2)**|Максимальное число одновременных сеансов в процентах от предела для уровня службы базы данных.<br /><br /> В настоящее время максимальное рассчитывается для 5-минутный интервал, на основании 15 второй выборки, количества одновременных сеансов.|  
|dtu_limit|**int**|Max настройки текущей базы данных DTU для этой базы данных в течение этого интервала.|  
  
> [!TIP]  
>  Дополнительный контекст об этих ограничениях и уровней обслуживания см. в разделах [уровней обслуживания](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) и [уровня возможности и ограничения службы](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
 В следующей таблице описываются столбцы, доступные на сервере v11.  
  
|Столбцы (сервер v11)|Тип данных|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Время в формате UTC, указывающее начало 5-минутного отчетного интервала.|  
|end_time|**datetime**|Время в формате UTC, указывающее окончание 5-минутного периода составления отчетов.|  
|database_name|**nvarchar**|Имя базы данных.|  
|sku|**nvarchar**|Уровень служб базы данных. Допустимы следующие значения:<br /><br /> Web Edition<br /><br /> Business Edition<br /><br /> Basic<br /><br /> Standard Edition<br /><br /> Premium|  
|usage_in_seconds|**int**|*Примечание: Этот столбец является устаревшим для v11 и его значение всегда равно 0.*<br /><br /> Время ЦП, использованное с момента последнего измерения.<br /><br /> Для измерения ЦП рекомендуется использовать **avg_cpu_cores_used** столбца, а не этот столбец.|  
|storage_in_megabytes|**decimal**|Максимальный объем хранилища в мегабайтах в течение периода времени, в том числе данные базы данных, индексы, хранимые процедуры и метаданные.|  
|avg_cpu_cores_used|**decimal**|*Примечание: Этот столбец является устаревшим для v11 и его значение всегда равно 0.*<br /><br /> Среднее число ядер ЦП, используемых в этом интервале.|  
|avg_physical_read_iops|**decimal**|*Примечание: Этот столбец является устаревшим для v11 и его значение всегда равно 0.*<br /><br /> Среднее число операций IOPS чтения в этом интервале.|  
|avg_physical_write_iops|**decimal**|*Примечание: Этот столбец является устаревшим для v11 и его значение всегда равно 0.*<br /><br /> Среднее число операций IOPS записи в этом интервале.|  
|active_memory_used_kb|**bigint**|*Примечание: Этот столбец является устаревшим для v11 и его значение всегда равно 0.*<br /><br /> Активный объем памяти, используемый в конце интервала.|  
|active_session_count|**int**|Количество активных сеансов в конце интервала.|  
|active_worker_count|**int**|Количество активных исполнителей в конце интервала.|  
|avg_cpu_percent|**decimal**|Средний уровень использования вычислительных мощностей в процентах от предела для уровня службы.|  
|avg_physical_data_read_percent|**decimal**|Средний уровень использования операций ввода-вывода в процентах от предела для уровня службы.|  
|avg_log_write_percent|**decimal**|Средний уровень использования ресурсов записи в процентах от предела для уровня службы.|  
  
## <a name="permissions"></a>Permissions  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
## <a name="remarks"></a>Замечания  
 Данные, возвращенные **sys.resource_stats** выражается в процентах от максимально разрешенных ограничений DTU для уровня производительности или уровня службы, которые выполняются для баз данных Basic, Standard и Premium.  Для уровней Web и Business эти числа указывают проценты в условиях уровня производительности Standard S2.  Например, если при выполнении в базе данных Web значение avg_cpu_percent возвращает 70 %, это означает 70 % лимита уровня S2. Кроме того, для уровней Web и Business проценты могут отражать количество сверх 100 %, что также основывается на ограничении уровня S2.  
  
 Когда база данных является членом эластичного пула, Статистика ресурсов, представленный в виде процента значений выражаются в виде процентов максимальные значения DTU для баз данных, как указано в конфигурации пула эластичных БД.  
  
 Для более детального представления данных, используйте **sys.dm_db_resource_stats** динамического административного представления в базе данных пользователя. Это представление сохраняет данные каждые 15 секунд и сохраняет исторические данные в течение 1 часа.  Дополнительные сведения см. в разделе [sys.dm_db_resource_stats &#40; База данных Azure SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все базы данных с усреднением по меньшей мере для 80 % использования вычислительной мощности за последнюю неделю.  
  
```  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
  
 В следующем примере подсчитывается средний процент DTU использования для заданной базы данных. (Этот запрос работает только при выполнении на сервере v11.)  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
   FROM (VALUES (avg_cpu_percent), (avg_physical_data_read_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.resource_stats   
WHERE database_name = '<your db name>'   
ORDER BY end_time DESC;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Уровни обслуживания](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Возможности уровня службы и ограничения](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
