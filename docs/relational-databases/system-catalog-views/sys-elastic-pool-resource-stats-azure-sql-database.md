---
title: sys.elastic_pool_resource_stats (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
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
ms.workload: Inactive
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 815b328154bd3ab4f29de1218d403746fabb21c3
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>sys.elastic_pool_resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает статистику использования ресурсов для всех пулов эластичных баз данных в логическом сервере. Для каждого пула эластичной базы данных имеется одна строка для каждого 15 секунд reporting окна (четыре строки в минуту). Сюда входят ЦП, ввода-ВЫВОДА, журнала, использование хранилища и использования параллельных запросов или сеанса используется всеми базами данных в пуле. Эти данные можно сохранить для 14 дней. 
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] версии 12.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Время в формате UTC, указывающее начало отчетного интервала интервал 15 секунд.|  
|**end_time**|**datetime2**|Время в формате UTC, указывающее конец отчетного интервала интервал 15 секунд.|  
|**elastic_pool_name**|**nvarchar(128)**|Имя пула эластичных баз данных.|  
|**avg_cpu_percent**|**Decimal(5,2)**|Среднее использование вычислительной среды в процентах от предела пула.|  
|**avg_data_io_percent**|**Decimal(5,2)**|Среднее использование операций ввода-вывода в процентах от предела для пула.|  
|**avg_log_write_percent**|**Decimal(5,2)**|Среднее использование ресурсов записи в процентах от предела пула.|  
|**avg_storage_percent**|**Decimal(5,2)**|Среднее использование хранилища в процентах от предела хранилища пула.|  
|**max_worker_percent**|**Decimal(5,2)**|Максимальная одновременных рабочих процессов (запросов) в процентах от предела для пула.|  
|**max_session_percent**|**Decimal(5,2)**|Максимальное число одновременных сеансов в процентах от предела для пула.|  
|**elastic_pool_dtu_limit**|**int**|Текущее max эластичного пула DTU значение параметра этот пул эластичных БД в течение этого интервала.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Текущий max эластичного пула предельный размер хранилища для этот пул эластичных БД в мегабайтах в течение этого интервала.|  
  
## <a name="remarks"></a>Замечания  
 Это представление существует в базе данных master логического сервера. Необходимо подключиться к базе данных master для запроса **sys.elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **dbmanager** роли.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает данные об использовании ресурсов, упорядоченные по последнее время для всех пулов эластичных баз данных в текущем логическом сервере.  
  
```  
SELECT * FROM sys.elastic_pool_resource_stats   
ORDER BY end_time DESC;  
```  
  
 В следующем примере подсчитывается средний процент DTU использования для данного пула.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.elastic_pool_resource_stats   
WHERE elastic_pool_name = '<your pool name>'   
ORDER BY end_time DESC;  
```  
  
## <a name="see-also"></a>См. также  
 [Tame взрывоподобный рост эластичных баз данных](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Создание и управление ими пул эластичных баз данных базы данных SQL (Предварительная версия)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [sys.resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [sys.dm_db_resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
