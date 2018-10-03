---
title: sys.dm_fts_semantic_similarity_population (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_semantic_similarity_population_TSQL
- sys.dm_fts_semantic_similarity_population
- dm_fts_semantic_similarity_population
- sys.dm_fts_semantic_similarity_population_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_semantic_similarity_population dynamic management view
ms.assetid: 33666f28-c370-47e2-a932-190316ed5f69
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d65ba08739cde5dede23745c1a891246a6194360
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644242"
---
# <a name="sysdmftssemanticsimilaritypopulation-transact-sql"></a>sys.dm_fts_semantic_similarity_population (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке сведений о состоянии заполнения индекса подобия документов для каждого индекса подобия в каждой таблице, имеющей связанный семантический индекс.  
  
 Шаг заполнения следует за шагом извлечения. Сведения о состоянии данных шагом извлечения подобия, см. в разделе [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
    
||||  
|-|-|-|  
|**Имя столбца**|**Тип**|**Описание**|  
|**database_id**|**int**|Идентификатор базы данных, в которой содержится заполняемый полнотекстовый индекс.|  
|**catalog_id**|**int**|Идентификатор полнотекстового каталога, в котором содержится полнотекстовый индекс.|  
|**table_id**|**int**|Идентификатор таблицы, в которой содержится заполняемый полнотекстовый индекс.|  
|**document_count**|**int**|Общее количество документов в заполнении.|  
|**document_processed_count**|**int**|Число документов, обработанных с начала этого цикла заполнения|  
|**completion_type**|**int**|Состояние завершения данного заполнения.|  
|**completion_type_description**|**nvarchar(120)**|Описание типа завершения.|  
|**worker_count**|**int**|Число рабочих потоков, связанных с извлечением данных о подобии|  
|**status**|**int**|Состояние операции заполнения. Примечание: некоторые из состояний являются временными. Это может быть:<br /><br /> 3 = запускается<br /><br /> 5 = выполняется нормально<br /><br /> 7 = обработка остановлена<br /><br /> 11 = заполнение прервано|  
|**status_description**|**nvarchar(120)**|Описание состояния заполнения.|  
|**start_time**|**datetime**|Время начала заполнения.|  
|**incremental_timestamp**|**timestamp**|Для полного заполнения содержит отметку времени его начала. Для остальных типов заполнения содержит последнюю зафиксированную контрольную точку (это значение отражает процесс заполнения).|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в разделе [управление и мониторинг семантического поиска](../../relational-databases/search/manage-and-monitor-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Дополнительные сведения о состоянии семантического индексирования, запросите [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как запросить состояние заполнений индекса подобия документов для всех таблиц, имеющих связанный семантический индекс:  
  
```  
SELECT * FROM sys.dm_fts_semantic_similarity_population;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Управление семантическим поиском и наблюдение за ним](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
