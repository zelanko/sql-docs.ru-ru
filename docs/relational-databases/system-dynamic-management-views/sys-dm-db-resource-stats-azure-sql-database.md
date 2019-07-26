---
title: sys. DM _db_resource_stats (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 05/21/2019
ms.service: sql-database
ms.reviewer: ''
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
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 71efbc5abad150c599a674ea66409207fc2bf628
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471087"
---
# <a name="sysdmdbresourcestats-azure-sql-database"></a>sys.dm_db_resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения об использовании ЦП, ввода-вывода и памяти для базы данных [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Существует одна строка для каждых 15 секунд, даже если в базе данных не выполняется никаких действий. Исторические данные хранятся в течение одного часа.  
  
|Столбцы|Тип данных|Описание|  
|-------------|---------------|-----------------|  
|end_time|**datetime**|Время в формате UTC, указывающее окончание текущего отчетного интервала.|  
|avg_cpu_percent|**Decimal (5, 2)**|Средний уровень использования вычислительных мощностей в процентах от предела для уровня службы.|  
|avg_data_io_percent|**Decimal (5, 2)**|Среднее использование операций ввода-вывода данных в процентах от ограничения уровня службы.|  
|avg_log_write_percent|**Decimal (5, 2)**|Среднее число операций записи в журнал транзакций (в Мбит/с) в процентах от пределов уровня службы.|  
|avg_memory_usage_percent|**Decimal (5, 2)**|Средний уровень использования памяти в процентах от предела для уровня службы.<br /><br /> Сюда входит память, используемая для страниц буферного пула и хранения объектов OLTP в памяти.|  
|xtp_storage_percent|**Decimal (5, 2)**|Использование хранилища для выполняющейся в памяти OLTP в процентах от ограничения уровня службы (в конце интервала отчетности). Сюда входит память, используемая для хранения следующих объектов OLTP в памяти: оптимизированных для памяти таблиц, индексов и табличных переменных. Он также включает память, используемую для обработки операций ALTER TABLE.<br /><br /> Возвращает 0, если выполняющаяся в памяти OLTP не используется в базе данных.|  
|max_worker_percent|**Decimal (5, 2)**|Максимальное число одновременных рабочих процессов (запросов) в процентах от предела уровня служб базы данных.|  
|max_session_percent|**Decimal (5, 2)**|Максимальное число одновременных сеансов в процентах от ограничения уровня служб базы данных.|  
|dtu_limit|**int**|Текущее максимальное значение DTU базы данных для этой базы данных в течение этого интервала. Для баз данных, использующих модель на основе виртуальное ядро, этот столбец имеет значение NULL.|
|cpu_limit|**Decimal (5, 2)**|Число виртуальных ядер для этой базы данных в течение этого интервала. Для баз данных, использующих модель на основе DTU, этот столбец имеет значение NULL.|
|avg_instance_cpu_percent|**Decimal (5, 2)**|Средний уровень использования ЦП базы данных в процентах от процесса SQL DB.|
|avg_instance_memory_percent|**Decimal (5, 2)**|Средний объем использования памяти базы данных в процентах от процесса SQL DB.|
|avg_login_rate_percent|**Decimal (5, 2)**|Указано только в ознакомительных целях. Не поддерживается. Совместимость с будущими версиями не гарантируется.|
|replica_role|**int**|Представляет роль текущей реплики с 0 в качестве первичной, 1 в качестве вторичной и 2 в качестве сервера пересылки (основной сервер геореплики). Вы увидите "1" при соединении с намерением ReadOnly для всех доступных для чтения вторичных реплик. Если при подключении к геовторичному серверу не задано намерение ReadOnly, вы увидите "2" (подключение к серверу пересылки).|
|||
  
> [!TIP]  
>  Дополнительные сведения об этих ограничениях и уровнях служб см. в разделах [уровни служб](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) и [возможности и ограничения уровня](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)служб.  
  
## <a name="permissions"></a>Разрешения  
 Для этого представления необходимо разрешение VIEW DATABASE STATE.  
  
## <a name="remarks"></a>Примечания  
 Данные, возвращаемые **sys. DM _db_resource_stats** , выражаются в процентном отношении к максимально допустимому уровню обслуживания или уровня производительности, который вы используете.
 
 Если база данных переключилась на другой сервер за последние 60 минут, представление будет возвращать только данные за то время, в течение которого она была базой данных-источником с момента отработки отказа.  
  
 Для менее детального представления этих данных используйте представление каталога **sys. resource_stats** в базе данных **master** . Это представление сохраняет данные каждые 5 минут и сохраняет исторические данные в течение 14 дней.  Дополнительные сведения см. в статье [sys. &#40;Resource_stats Azure SQL&#41;Database](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md).  
  
 Если база данных является членом эластичного пула, то статистика ресурсов, представленная в виде процентных значений, выражается в процентах от максимального предела для баз данных, как указано в конфигурации эластичного пула.  
  
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
    AVG(avg_log_write_percent) AS 'Average Log Write I/O Throughput Utilization In Percent',   
    MAX(avg_log_write_percent) AS 'Maximum Log Write I/O Throughput Utilization In Percent',   
    AVG(avg_memory_usage_percent) AS 'Average Memory Usage In Percent',   
    MAX(avg_memory_usage_percent) AS 'Maximum Memory Usage In Percent'   
FROM sys.dm_db_resource_stats;  
  
```  
  
## <a name="see-also"></a>См. также  
 [sys. resource_stats &#40;база данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [Уровни служб](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Возможности и ограничения уровня службы](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
