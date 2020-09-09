---
description: sys. dm_pdw_os_event_logs (Transact-SQL)
title: sys. dm_pdw_os_event_logs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fb4194b866595009b46aea888f600488b6a1cc3b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89530807"
---
# <a name="sysdm_pdw_os_event_logs-transact-sql"></a>sys. dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Содержит сведения о различных журналах событий Windows на разных узлах.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
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
  
  
