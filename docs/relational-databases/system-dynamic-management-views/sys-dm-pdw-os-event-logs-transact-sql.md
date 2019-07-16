---
title: sys.dm_pdw_os_event_logs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 819b38bce871bd1a43b3d259d23b2c95fb6dfdd3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086215"
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>sys.dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о различных событий Windows, журналы на разных узлах.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Устройство узла извлекается этот журнал.<br /><br /> pdw_node_id и имя_журнала формируют ключ для этого представления.||  
|имя_журнала|**nvarchar(255)**|Имя журнала событий Windows.<br /><br /> pdw_node_id и имя_журнала формируют ключ для этого представления.||  
|log_source|**nvarchar(255)**|Имя источника журнала событий Windows.||  
|event_id|**int**|Идентификатор события. Не уникален.||  
|event_type|**nvarchar(255)**|Тип события, определяющее уровень серьезности.|«Сведения», «Предупреждение», «Ошибка»|  
|event_message|**nvarchar(4000)**|Дополнительные сведения о событии.||  
|generate_time|**datetime**|Время создания события.||  
|write_time|**datetime**|Время, когда событие фактически было записано в журнал.||  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе метаданных в [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) раздела. 
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
