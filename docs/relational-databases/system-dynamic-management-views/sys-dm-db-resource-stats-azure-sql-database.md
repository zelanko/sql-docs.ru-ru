---
title: sys.dm_db_resource_stats (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 4e67b2e698440789e954e60c25b7aaeb18d04e41
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmdbresourcestats-azure-sql-database"></a>sys.dm_db_resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает использование ЦП, ввода-вывода и памяти для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] базы данных. Существует одна строка для каждых 15 секунд, даже если в базе данных не выполняется никаких действий. Исторические данные хранятся в течение одного часа.  
  
|Столбцы|Тип данных|Описание|  
|-------------|---------------|-----------------|  
|end_time|**datetime**|Время в формате UTC, указывающее окончание текущего отчетного интервала.|  
|avg_cpu_percent|**Decimal (5,2)**|Средний уровень использования вычислительных мощностей в процентах от предела для уровня службы.|  
|avg_data_io_percent|**Decimal (5,2)**|Среднее использование операций ввода-вывода в процентах от предела для уровня службы данных.|  
|avg_log_write_percent|**Decimal (5,2)**|Средний уровень использования ресурсов записи в процентах от предела для уровня службы.|  
|avg_memory_usage_percent|**Decimal (5,2)**|Средний уровень использования памяти в процентах от предела для уровня службы.<br /><br /> Это включает память, используемая для хранения объектов OLTP в памяти.|  
|xtp_storage_percent|**Decimal (5,2)**|Использование хранилища для OLTP в памяти в процентах от предела для уровня службы (в конце отчетного интервала). Это включает память, используемая для хранения следующих объектов в памяти OLTP: оптимизированные для памяти таблицы, индексы и табличные переменные. Он также включает память, используемая для обработки операции ALTER TABLE.<br /><br /> Возвращает 0, если не используется In-Memory OLTP в базе данных.|  
|max_worker_percent|**Decimal (5,2)**|Максимальная одновременных рабочих процессов (запросов) в процентах от предела для уровня службы базы данных.|  
|max_session_percent|**Decimal (5,2)**|Максимальное число одновременных сеансов в процентах от предела для уровня службы базы данных.|  
|dtu_limit|**int**|Max настройки текущей базы данных DTU для этой базы данных в течение этого интервала. |
|||
  
> [!TIP]  
>  Дополнительный контекст об этих ограничениях и уровней обслуживания см. в разделах [уровней обслуживания](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) и [уровня возможности и ограничения службы](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/).  
  
## <a name="permissions"></a>Разрешения  
 Для этого представления необходимо разрешение VIEW DATABASE STATE.  
  
## <a name="remarks"></a>Замечания  
 Данные, возвращенные **sys.dm_db_resource_stats** выражается в процентах от максимально разрешенных ограничений на уровень производительности и уровня обслуживания, который вы используете.
 
 Если база данных переключилась на другой сервер за последние 60 минут, представление будет возвращать только данные за то время, в течение которого она была базой данных-источником с момента отработки отказа.  
  
 Для получения менее детального представления данных используйте **sys.resource_stats** представление каталога **master** базы данных. Это представление сохраняет данные каждые 5 минут и сохраняет исторические данные в течение 14 дней.  Дополнительные сведения см. в разделе [sys.resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md).  
  
 Когда база данных является членом эластичного пула, Статистика ресурсов, представленный в виде процента значений выражаются в виде процентов максимальное ограничение для баз данных, как указано в конфигурации пула эластичных БД.  
  
## <a name="example"></a>Пример  
  
Следующий пример возвращает данные об использовании ресурсов, упорядоченные по последнему времени для подключенной в текущий момент базы данных.  
  
```  
SELECT * FROM sys.dm_db_resource_stats ORDER BY end_time DESC;  
  
```  
  
 Следующий пример определяет среднее потребление DTU в процентном с как отношение в процентах от максимального разрешенного значения DTU на уровне производительности для пользовательской базы данных за последний час. Рекомендуется увеличивать уровень производительности, когда это значение длительное время близко к 100 %.  
  
```  
SELECT end_time,   
  (SELECT Max(v)    
   FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS    
   value(v)) AS [avg_DTU_percent]   
FROM sys.dm_db_resource_stats;  
  
```  
  
 Следующий пример возвращает среднее и максимальное значения использования ЦП, операций ввода-вывода данных и журналов, а также потребление памяти за последний час.  
  
```  
SELECT    
    AVG(avg_cpu_percent) AS 'Average CPU Utilization In Percent',   
    MAX(avg_cpu_percent) AS 'Maximum CPU Utilization In Percent',   
    AVG(avg_data_io_percent) AS 'Average Data IO In Percent',   
    MAX(avg_data_io_percent) AS 'Maximum Data IO In Percent',   
    AVG(avg_log_write_percent) AS 'Average Log Write Utilization In Percent',   
    MAX(avg_log_write_percent) AS 'Maximum Log Write Utilization In Percent',   
    AVG(avg_memory_usage_percent) AS 'Average Memory Usage In Percent',   
    MAX(avg_memory_usage_percent) AS 'Maximum Memory Usage In Percent'   
FROM sys.dm_db_resource_stats;  
  
```  
  
## <a name="see-also"></a>См. также  
 [sys.resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Уровни обслуживания](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Возможности уровня службы и ограничения](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
