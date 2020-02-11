---
title: sys. dm_fts_semantic_similarity_population (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 280ab197ef9347c6a209be7ef05e8f1ce2dfd23e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900875"
---
# <a name="sysdm_fts_semantic_similarity_population-transact-sql"></a>sys.dm_fts_semantic_similarity_population (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке сведений о состоянии заполнения индекса подобия документов для каждого индекса подобия в каждой таблице, имеющей связанный семантический индекс.  
  
 Шаг заполнения следует за шагом извлечения. Сведения о состоянии шага извлечения подобия см. в разделе [sys. dm_fts_index_population &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
    
||||  
|-|-|-|  
|**Имя столбца**|**Тип**|**Описание**|  
|**database_id**|**int**|Идентификатор базы данных, в которой содержится заполняемый полнотекстовый индекс.|  
|**catalog_id**|**int**|Идентификатор полнотекстового каталога, в котором содержится полнотекстовый индекс.|  
|**table_id**|**int**|Идентификатор таблицы, в которой содержится заполняемый полнотекстовый индекс.|  
|**document_count**|**int**|Общее количество документов в заполнении.|  
|**document_processed_count**|**int**|Число документов, обработанных с начала этого цикла заполнения|  
|**completion_type**|**int**|Состояние завершения данного заполнения.|  
|**completion_type_description**|**nvarchar (120)**|Описание типа завершения.|  
|**worker_count**|**int**|Число рабочих потоков, связанных с извлечением данных о подобии|  
|**состояние**|**int**|Состояние операции заполнения. Примечание. Некоторые состояния являются временными. Это может быть:<br /><br /> 3 = запускается<br /><br /> 5 = выполняется нормально<br /><br /> 7 = обработка остановлена<br /><br /> 11 = заполнение прервано|  
|**status_description**|**nvarchar (120)**|Описание состояния заполнения.|  
|**start_time**|**datetime**|Время начала заполнения.|  
|**incremental_timestamp**|**TIMESTAMP**|Для полного заполнения содержит отметку времени его начала. Для остальных типов заполнения содержит последнюю зафиксированную контрольную точку (это значение отражает процесс заполнения).|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в разделе [Управление семантическим поиском и наблюдение за](../../relational-databases/search/manage-and-monitor-semantic-search.md)ним.  
  
## <a name="metadata"></a>Метаданные  
 Дополнительные сведения о состоянии семантического индексирования см. в статье [sys. dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как запросить состояние заполнений индекса подобия документов для всех таблиц, имеющих связанный семантический индекс:  
  
```  
SELECT * FROM sys.dm_fts_semantic_similarity_population;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Управление и наблюдение за семантическим поиском](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
