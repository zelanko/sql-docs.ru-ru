---
title: sys.elastic_pool_resource_stats (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- Azure SQL Database
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 5f7f13ebb5699fc0fe2174e7ee1af9d6c44bcbfb
ms.sourcegitcommit: b8e2e3e6e04368aac54100c403cc15fd4e4ec13a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45563270"
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>sys.elastic_pool_resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает статистику использования ресурсов для всех пулов эластичных баз данных на логическом сервере. Для каждого пула эластичной базы данных имеется одна строка каждые 15 секунд окна (четыре строки в минуту) отчета. Это включает в себя загрузки ЦП, ввода-ВЫВОДА, журнала, использованный объем хранилища и параллельных запросов и сеансов всеми базами данных в пуле. Эти данные сохраняются в течение 14 дней. 
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] версии 12.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Время в формате UTC, с которой начинается 15 секунд, в течение отчетного интервала.|  
|**end_time**|**datetime2**|Время в формате UTC, указывающий на конец отчетного интервала интервал 15 секунд.|  
|**elastic_pool_name**|**nvarchar(128)**|Имя пула эластичных баз данных.|  
|**avg_cpu_percent**|**Decimal(5,2)**|Среднее использование вычислительных ресурсов в процентах от предела пула.|  
|**avg_data_io_percent**|**Decimal(5,2)**|Среднее использование ввода-вывода в процентах от предела пула.|  
|**avg_log_write_percent**|**Decimal(5,2)**|Среднее использование ресурсов записи в процентах от предела пула.|  
|**avg_storage_percent**|**Decimal(5,2)**|Среднее использование хранилища в процентах от предела пула.|  
|**max_worker_percent**|**Decimal(5,2)**|Максимальное количество одновременных рабочих ролей (запросов) в процентах от предела пула.|  
|**max_session_percent**|**Decimal(5,2)**|Максимальное число одновременных сеансов в процентах от предела пула.|  
|**elastic_pool_dtu_limit**|**int**|Текущее максимальное значение параметра DTU для этого пула эластичных БД в течение этого интервала.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Значение для этого пула эластичных БД в мегабайтах во время этого интервала текущего размера хранилища эластичного пула.|
|**avg_allocated_storage_percent**|**Decimal(5,2)**|Процент пространства данных, выделенной с помощью всех баз данных в эластичном пуле.  Это отношение данных пространства, выделенного для данных максимальный размер для эластичного пула.  Дополнительные сведения см. в разделе: [пространства управление файлами в базе данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|  
  
## <a name="remarks"></a>Примечания  
 Это представление существует в базе данных master логического сервера. Необходимо подключение к базе данных master, к запросу **sys.elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **dbmanager** роли.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает данные об использовании ресурсов, упорядоченные по самой последней времени для всех пулов эластичных баз данных в текущем логическом сервере.  
  
```  
SELECT * FROM sys.elastic_pool_resource_stats   
ORDER BY end_time DESC;  
```  
  
 В следующем примере вычисляется среднее относительное потребление DTU для данного пула.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.elastic_pool_resource_stats   
WHERE elastic_pool_name = '<your pool name>'   
ORDER BY end_time DESC;  
```  
  
## <a name="see-also"></a>См. также  
 [Укротите взрывной рост объемов данных с эластичными базами данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Создание и управление ими в пуле эластичных баз данных баз данных SQL (Предварительная версия)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [sys.resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [sys.dm_db_resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
