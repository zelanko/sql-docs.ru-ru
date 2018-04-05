---
title: sys.resource_stats (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 05/23/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
caps.latest.revision: 28
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c6b77fb44d24454b786ef74ed4471b8195619110
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает загрузку ЦП и данные хранилища для базы данных SQL Azure. Эти данные собираются и объединяются с пятиминутными интервалами. Для каждой пользовательской базы данных существует одна строка для каждого пятиминутного окна отчетности без изменения потребления ресурсов. Это может быть изменение загрузки ЦП, размера хранилища и номер SKU базы данных. Для простаивающих баз данных без изменений строки для каждого пятиминутного интервала могут отсутствовать. Данные предыстории хранятся приблизительно в течение 14 суток.  
  
 **Sys.resource_stats** представление имеет разные определения в зависимости от версии сервера базы данных SQL Azure, связанный с базы данных. Рассмотрим эти различия и все изменения, которые требуются приложению при обновлении до новой версии сервера.  
  
 В следующей таблице описываются столбцы, доступные на сервере v12.  
  
|Столбцы|Тип данных|Описание|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Время в формате UTC, указывающее начало 5-минутного отчетного интервала.|  
|end_time|**datetime**|Время в формате UTC, указывающее окончание 5-минутного периода составления отчетов.|  
|database_name|**varchar**|Имя пользовательской базы данных.|  
|sku|**varchar**|Уровень служб базы данных. Допустимы следующие значения:<br /><br /> Basic<br /><br /> Standard Edition<br /><br /> Premium<br /><br />Общего назначения<br /><br />Критический для бизнеса|  
|storage_in_megabytes|**float**|Максимальный объем хранилища в мегабайтах в течение периода времени, в том числе данные базы данных, индексы, хранимые процедуры и метаданные.|  
|avg_cpu_percent|**numeric**|Средний уровень использования вычислительных мощностей в процентах от предела для уровня службы.|  
|avg_data_io_percent|**numeric**|Средний уровень использования операций ввода-вывода в процентах от предела для уровня службы.|  
|avg_log_write_percent|**numeric**|Средний уровень использования ресурсов записи в процентах от предела для уровня службы.|  
|max_worker_percent|**decimal(5,2)**|Максимальная одновременных рабочих процессов (запросов) в процентах от предела для уровня службы базы данных.<br /><br /> В настоящее время максимальное рассчитывается для 5-минутный интервал, на основании 15 второй выборки, количества параллельных рабочих.|  
|max_session_percent|**decimal(5,2)**|Максимальное число одновременных сеансов в процентах от предела для уровня службы базы данных.<br /><br /> В настоящее время максимальное рассчитывается для 5-минутный интервал, на основании 15 второй выборки, количества одновременных сеансов.|  
|dtu_limit|**int**|Max настройки текущей базы данных DTU для этой базы данных в течение этого интервала.|  
  
> [!TIP]  
>  Дополнительный контекст об этих ограничениях и уровней обслуживания см. в разделах [уровней обслуживания](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/).  
    
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
## <a name="remarks"></a>Замечания  
 Данные, возвращенные **sys.resource_stats** выражается в процентах от максимально разрешенных ограничений DTU для уровня производительности или уровня службы, которые выполняются для баз данных Basic, Standard и Premium.  
  
 Когда база данных является членом эластичного пула, Статистика ресурсов, представленный в виде процента значений выражаются в виде процентов максимальные значения DTU для баз данных, как указано в конфигурации пула эластичных БД.  
  
 Для более детального представления данных, используйте **sys.dm_db_resource_stats** динамического административного представления в базе данных пользователя. Это представление сохраняет данные каждые 15 секунд и сохраняет исторические данные в течение 1 часа.  Дополнительные сведения см. в разделе [sys.dm_db_resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все базы данных с усреднением по меньшей мере для 80 % использования вычислительной мощности за последнюю неделю.  
  
```sql  
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
    
## <a name="see-also"></a>См. также  
 [Уровни обслуживания](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Возможности уровня службы и ограничения](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
