---
title: sys.elastic_pool_resource_stats
titleSuffix: Azure SQL Database
ms.date: 01/28/2019
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: reference
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
author: stevestein
ms.author: sstein
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0712785a5af3e8cc3c606a597ba02e0075c88dd9
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843874"
---
# <a name="syselastic_pool_resource_stats-azure-sql-database"></a>sys. elastic_pool_resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает статистику использования ресурсов для всех эластичных пулов на сервере базы данных SQL. Для каждого пула эластичных БД существует одна строка для каждого 15-секундного окна отчетов (четыре строки в минуту). Сюда входят ЦП, ввод-вывод, журнал, использование хранилища и одновременный запрос/сеанс по всем базам данных в пуле. Эти данные сохранены в течение 14 дней. 
  
||  
|-|  
|**Применимо к**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Время в формате UTC, обозначающее начало 15 секунд отчетного интервала.|  
|**end_time**|**datetime2**|Время в формате UTC, указывающее Окончание интервала составления отчета за 15 секунд.|  
|**elastic_pool_name**|**nvarchar(128)**|Имя пула эластичных баз данных.|  
|**avg_cpu_percent**|**Decimal (5, 2)**|Среднее использование вычислений в процентах от предела пула.|  
|**avg_data_io_percent**|**Decimal (5, 2)**|Среднее использование операций ввода-вывода в процентах в зависимости от ограничения пула.|  
|**avg_log_write_percent**|**Decimal (5, 2)**|Среднее использование ресурсов записи в процентах от предела пула.|  
|**avg_storage_percent**|**Decimal (5, 2)**|Средний уровень использования хранилища в процентах от предела хранилища пула.|  
|**max_worker_percent**|**Decimal (5, 2)**|Максимальное число одновременных рабочих процессов (запросов) в процентах на основе ограничения пула.|  
|**max_session_percent**|**Decimal (5, 2)**|Максимальное количество одновременных сеансов в процентах на основе ограничения пула.|  
|**elastic_pool_dtu_limit**|**int**|Текущее значение максимального числа DTU эластичного пула для этого эластичного пула в течение этого интервала.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Текущее значение максимального размера хранилища эластичного пула для этого пула эластичных БД в мегабайтах за этот интервал.|
|**avg_allocated_storage_percent**|**Decimal (5, 2)**|Процент пространства данных, выделенного всеми базами данных в эластичном пуле.  Это отношение пространства данных, выделенного для максимального размера данных для эластичного пула.  Дополнительные сведения см. [в разделе Управление файловым пространством в базе данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management) .|  
  
## <a name="remarks"></a>Remarks

 Это представление существует в базе данных master сервера базы данных SQL. Чтобы запросить представление **sys. elastic_pool_resource_stats**, необходимо подключиться к базе данных master.  
  
## <a name="permissions"></a>Разрешения

 Требуется членство в роли **DBManager** .  
  
## <a name="examples"></a>Примеры

 В следующем примере возвращаются данные об использовании ресурсов, упорядоченные по последнему времени для всех пулов эластичных баз данных на текущем сервере базы данных SQL.  
  
```sql
SELECT * FROM sys.elastic_pool_resource_stats
ORDER BY end_time DESC;  
```

 В следующем примере вычисляется средний процент использования DTU для заданного пула.  

```sql
SELECT start_time, end_time,
  (SELECT Max(v)
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]
FROM sys.elastic_pool_resource_stats
WHERE elastic_pool_name = '<your pool name>'
ORDER BY end_time DESC;  
```

## <a name="see-also"></a>См. также статью

 [Рост окончании образом взрывной с помощью эластичных баз данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Создание пула эластичных баз данных SQL и управление им (Предварительная версия)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [sys. resource_stats &#40;базы&#41; данных SQL Azure](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [sys. dm_db_resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
