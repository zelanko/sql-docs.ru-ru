---
title: sys.dm_pdw_os_event_logs (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3311090840a2373652239e03f125b86030030a9d
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>sys.dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о различных событий Windows, журналы на разных узлах.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Узел устройства извлекается этот журнал.<br /><br /> pdw_node_id и имя_журнала формируют ключ для этого представления.||  
|имя_журнала|**nvarchar(255)**|Имя журнала событий Windows.<br /><br /> pdw_node_id и имя_журнала формируют ключ для этого представления.||  
|log_source|**nvarchar(255)**|Имя источника журнала событий Windows.||  
|event_id|**int**|Идентификатор события. Не уникален.||  
|event_type|**nvarchar(255)**|Тип события, определяющее серьезность.|«Сведения», «Предупреждение», «Ошибка»|  
|event_message|**nvarchar(4000)**|Дополнительные сведения о событии.||  
|generate_time|**datetime**|Время создания события.||  
|write_time|**datetime**|Время, когда событие было фактически записанных в журнал.||  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении, обратитесь к разделу максимальные значения представление системы в [минимальное и максимальное значения (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) раздела.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
