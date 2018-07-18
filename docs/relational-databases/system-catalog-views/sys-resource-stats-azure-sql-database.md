---
title: sys.resource_stats (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: c2f8a0e0cebcf64bedac33861184e806f322d7d1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038853"
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает загрузку ЦП и данные хранилища для базы данных SQL Azure. Эти данные собираются и объединяются с пятиминутными интервалами. Для каждой пользовательской базы данных существует одна строка для каждого пятиминутного окна отчетности без изменения потребления ресурсов. Данные, возвращенные включает использование ЦП, изменение размера хранилища или базы данных изменения номера SKU. Для простаивающих баз данных без изменения строки могут отсутствовать для каждые пять минут. Данные предыстории хранятся приблизительно в течение 14 суток.  
  
 **Sys.resource_stats** представление имеет разные определения в зависимости от версии сервера базы данных SQL Azure, с которой связан базы данных. Рассмотрим эти различия и все изменения, которые требуются приложению при обновлении до новой версии сервера.  
  
 В следующей таблице описываются столбцы, доступные на сервере v12.  
  
|Столбцы|Тип данных|Описание|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Время в формате UTC, указывающее начало отчетного интервала до пяти минут.|  
|end_time|**datetime**|Время в формате UTC, указывающее окончание 5 минутными отчетного интервала.|  
|database_name|**varchar**|Имя пользовательской базы данных.|  
|sku|**varchar**|Уровень служб базы данных. Допустимы следующие значения:<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium<br /><br />Общее назначение<br /><br />Критические задачи для бизнеса|  
|storage_in_megabytes|**float**|Максимальный размер хранилища в мегабайтах за период времени, включая базы данных, индексы, хранимые процедуры и метаданные.|  
|avg_cpu_percent|**numeric**|Средний уровень использования вычислительных мощностей в процентах от предела для уровня службы.|  
|avg_data_io_percent|**numeric**|Средний уровень использования операций ввода-вывода в процентах от предела для уровня службы.|  
|avg_log_write_percent|**numeric**|Средний уровень использования ресурсов записи в процентах от предела для уровня службы.|  
|max_worker_percent|**Decimal(5,2)**|Максимальное количество одновременных рабочих ролей (запросов) в процентах от предела для уровня службы базы данных.<br /><br /> Максимум в настоящее время вычисляется для интервала до пяти минут, на основании выборки 15 секунд количества параллельных рабочих.|  
|max_session_percent|**Decimal(5,2)**|Максимальное число одновременных сеансов в процентах от предела для уровня службы базы данных.<br /><br /> В настоящее время максимальное вычисляется для интервала до пяти минут, основанного на 15 секунд примеры количество одновременных сеансов.|  
|dtu_limit|**int**|Max настройки текущей базы данных DTU для этой базы данных во время этого интервала. |  
  
> [!TIP]  
>  Дополнительные сведения об этих ограничениях и уровней обслуживания см. в разделах [уровней обслуживания](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/).  
    
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
## <a name="remarks"></a>Примечания  
 Данные, возвращаемые **sys.resource_stats** выражается в процентах от максимально разрешенных ограничений для службы уровня или уровня производительности, которые выполняются.  
  
 Если базы данных входит в пул эластичных баз данных, статистики ресурсов, представленными в виде значений процентов представляют собой процент используемой емкости, доступной для баз данных как в пуле эластичных баз данных конфигурации.  
  
 Для более детального представления этих данных, используйте **sys.dm_db_resource_stats** динамического административного представления в базе данных пользователя. Это представление сохраняет данные каждые 15 секунд и сохраняет исторические данные в течение 1 часа.  Дополнительные сведения см. в разделе [sys.dm_db_resource_stats &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

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
 [Уровни служб](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Служба возможности и ограничения уровней](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
