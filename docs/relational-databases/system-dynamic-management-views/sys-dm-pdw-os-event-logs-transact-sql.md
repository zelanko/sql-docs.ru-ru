---
title: sys. dm_pdw_os_event_logs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ed27e25a1aa977c8fc78186ae2bc9f96ee0e231e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82819362"
---
# <a name="sysdm_pdw_os_event_logs-transact-sql"></a>sys. dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о различных журналах событий Windows на разных узлах.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Узел устройства, из которого находится этот журнал.<br /><br /> pdw_node_id и log_name формируют ключ для этого представления.||  
|log_name|**nvarchar(255)**|Имя журнала событий Windows.<br /><br /> pdw_node_id и log_name формируют ключ для этого представления.||  
|log_source|**nvarchar(255)**|Имя источника журнала событий Windows.||  
|event_id|**int**|Идентификатор события. Не является уникальным.||  
|event_type|**nvarchar(255)**|Тип события, определяющий серьезность.|"Information", "warning", "Error"|  
|event_message|**nvarchar(4000)**|Сведения о событии.||  
|generate_time|**datetime**|Время создания события.||  
|write_time|**datetime**|Время фактической записи события в журнал.||  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе метаданные статьи [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) . 
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
