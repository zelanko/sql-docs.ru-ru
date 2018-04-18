---
title: sys.dm_fts_active_catalogs (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_active_catalogs_TSQL
- dm_fts_active_catalogs
- dm_fts_active_catalogs_TSQL
- sys.dm_fts_active_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_active_catalogs dynamic management view
ms.assetid: 40ab5453-040c-4d2e-bb49-e340cf90c3ee
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8104491ddcdf6c63e872da7a70374f8475cb1a62
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmftsactivecatalogs-transact-sql"></a>sys.dm_fts_active_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о полнотекстовых каталогах, для которых на сервере выполняются те или иные операции по заполнению.  
  
> [!NOTE]  
>  Следующие столбцы будут удалены в будущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: is_paused, previous_status, previous_status_description, row_count_in_thousands, состояние, status_description и worker_count. Избегайте использовать эти столбцы в новых разработках и запланируйте изменение приложений, где они используются в настоящий момент.  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, содержащей активный полнотекстовый каталог.|  
|**catalog_id**|**int**|Идентификатор активного полнотекстового каталога.|  
|**адрес_памяти**|**varbinary(8)**|Адрес буферов памяти, выделенных для операции заполнения, относящейся к полнотекстовому каталогу.|  
|**name**|**nvarchar(128)**|Имя активного полнотекстового каталога.|  
|**is_paused**|**бит**|Указывает, было ли приостановлено заполнение активного полнотекстового каталога.|  
|**status**|**int**|Текущее состояние полнотекстового каталога. Это может быть:<br /><br /> 0 = инициализация<br /><br /> 1 = готовность<br /><br /> 2 = пауза<br /><br /> 3 = временная ошибка<br /><br /> 4 = необходимость повторного подключения<br /><br /> 5 = выключение<br /><br /> 6 = приостановлен для резервного копирования<br /><br /> 7 = резервное копирование осуществлено через каталог<br /><br /> 8 = каталог поврежден|  
|**status_description**|**nvarchar(120)**|Описание текущего состояния активного полнотекстового каталога.|  
|**previous_status**|**int**|Предыдущее состояние полнотекстового каталога. Это может быть:<br /><br /> 0 = инициализация<br /><br /> 1 = готовность<br /><br /> 2 = пауза<br /><br /> 3 = временная ошибка<br /><br /> 4 = необходимость повторного подключения<br /><br /> 5 = выключение<br /><br /> 6 = приостановлен для резервного копирования<br /><br /> 7 = резервное копирование осуществлено через каталог<br /><br /> 8 = каталог поврежден|  
|**previous_status_description**|**nvarchar(120)**|Описание предыдущего состояния активного полнотекстового каталога.|  
|**worker_count**|**int**|Количество текущих потоков, работающих в этом полнотекстовом каталоге.|  
|**active_fts_index_count**|**int**|Количество полнотекстовых индексов, заполняемых в настоящий момент.|  
|**auto_population_count**|**int**|Количество таблиц, в которых происходит автозаполнение для этого полнотекстового каталога.|  
|**manual_population_count**|**int**|Количество таблиц с выполняющимся заполнением вручную для этого полнотекстового каталога.|  
|**full_incremental_population_count**|**int**|Количество таблиц с выполняющимся полным или добавочным заполнением для этого полнотекстового каталога.|  
|**row_count_in_thousands**|**int**|Оценка числа строк (в тысячах) в полнотекстовых индексах этого полнотекстового каталога.|  
|**is_importing впервые**|**бит**|Указывает, выполняется ли в настоящее время импорт полнотекстового каталога:<br /><br /> 1 = выполняется импорт каталога.<br /><br /> 2 = импорт каталога не выполняется.|  
  
## <a name="remarks"></a>Замечания  
 Столбец is_importing впервые впервые появился в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
   
## <a name="physical-joins"></a>Физические соединения  
 ![Существенные соединения данного динамического административного представления](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-active-catalogs-1.gif "существенные соединения данного динамического административного представления")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_fts_active_catalogs.database_id|dm_fts_index_population.database_id|Один к одному|  
|dm_fts_active_catalogs.catalog_id|dm_fts_index_population.catalog_id|Один к одному|  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает сведения об активных полнотекстовых каталогах в текущей базе данных.  
  
```  
SELECT catalog.name, catalog.is_importing, catalog.auto_population_count,  
  OBJECT_NAME(population.table_id) AS table_name,  
  population.population_type_description, population.is_clustered_index_scan,  
  population.status_description, population.completion_type_description,  
  population.queued_population_type_description, population.start_time,  
  population.range_count   
FROM sys.dm_fts_active_catalogs catalog   
CROSS JOIN sys.dm_fts_index_population population   
WHERE catalog.database_id = population.database_id   
AND catalog.catalog_id = population.catalog_id   
AND catalog.database_id = (SELECT dbid FROM sys.sysdatabases WHERE name = DB_NAME());  
GO  
```  
  
## <a name="see-also"></a>См. также  
 
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
