---
title: sys.dm_fts_index_population (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_index_population
- dm_fts_index_population
- sys.dm_fts_index_population_TSQL
- dm_fts_index_population_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_population dynamic management view
ms.assetid: 82d1c102-efcc-4b60-9a5e-3eee299bcb2b
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2c97061b08475549b2e8ebccdc75a56f74eb6614
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265930"
---
# <a name="sysdmftsindexpopulation-transact-sql"></a>sys.dm_fts_index_population (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о выполняющемся в настоящее время заполнении полнотекстового индекса и индекса семантических ключевых фраз в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, в которой содержится заполняемый полнотекстовый индекс.|  
|**catalog_id**|**int**|Идентификатор полнотекстового каталога, в котором содержится полнотекстовый индекс.|  
|**table_id**|**int**|Идентификатор таблицы, в которой содержится заполняемый полнотекстовый индекс.|  
|**адрес_памяти**|**varbinary(8)**|Адрес внутренней структуры данных в памяти, используемый, чтобы представлять активное заполнение.|  
|**population_type**|**int**|Тип заполнения. Это может быть:<br /><br /> 1 = полное заполнение;<br /><br /> 2 = добавочное заполнение на основе отметок времени;<br /><br /> 3 = ручное обновление отслеженных изменений;<br /><br /> 4 = фоновое обновление отслеженных изменений.|  
|**population_type_description**|**nvarchar(120)**|Описание типа заполнения.|  
|**is_clustered_index_scan**|**bit**|Указывает, включает ли заполнение просмотр кластеризованных индексов.|  
|**range_count**|**int**|Число поддиапазонов, на которые распараллелена операция заполнения.|  
|**completed_range_count**|**int**|Число диапазонов, для которых обработка завершена.|  
|**счетчик_необработанных_пакетов**|**int**|Число необработанных пакетов для данного заполнения. Дополнительные сведения см. в разделе [sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql.md).|  
|**status**|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Состояние операции заполнения. Примечание: некоторые из состояний являются временными. Это может быть:<br /><br /> 3 = запускается<br /><br /> 5 = выполняется нормально<br /><br /> 7 = обработка остановлена<br /><br /> Например, это состояние появляется в процессе автоматического слияния.<br /><br /> 11 = заполнение прервано<br /><br /> 12 = извлечение данных о семантическом подобии|  
|**status_description**|**nvarchar(120)**|Описание состояния заполнения.|  
|**completion_type**|**int**|Состояние завершения данного заполнения.|  
|**completion_type_description**|**nvarchar(120)**|Описание типа завершения.|  
|**worker_count**|**int**|Это значение всегда равно 0.|  
|**queued_population_type**|**int**|Тип заполнения на основе отслеженных изменений, которое последует за текущим заполнением, если таковое выполняется.|  
|**queued_population_type_description**|**nvarchar(120)**|Описание следующего заполнения, оно должно произойти. Например, при параметре CHANGE TRACKING = AUTO и в процессе первоначального полного заполнения в этом столбце будет отображаться «Самозаполнение».|  
|**start_time**|**datetime**|Время начала заполнения.|  
|**incremental_timestamp**|**timestamp**|Для полного заполнения содержит отметку времени его начала. Для остальных типов заполнения содержит последнюю зафиксированную контрольную точку (это значение отражает процесс заполнения).|  
  
## <a name="remarks"></a>Примечания  
 Если в дополнение к полнотекстовому индексированию включено статистическое семантическое индексирование, то выделение и заполнение семантических ключевых фраз, а также извлечение данных о подобии документов происходит одновременно с полнотекстовым индексированием. Заполнение индекса подобия документов выполняется позже, на втором этапе. Дополнительные сведения см. в разделе [управление и мониторинг семантического поиска](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   
  
## <a name="physical-joins"></a>Физические соединения  
 ![Существенные соединения данного динамического административного представления](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-index-population-1.gif "существенные соединения данного динамического административного представления")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|dm_fts_active_catalogs.database_id|dm_fts_index_population.database_id|Один к одному|  
|dm_fts_active_catalogs.catalog_id|dm_fts_index_population.catalog_id|Один к одному|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|«многие к одному»|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Компонент Full-Text Search и семантический поиск динамические административные представления и функции &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

