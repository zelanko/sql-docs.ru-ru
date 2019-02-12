---
title: sys.dm_pdw_os_performance_counters (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 820027ee5bf893d7df81c51f90b431daa7c0af07
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027345"
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о счетчиках производительности Windows для узлов в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Идентификатор узла, который содержит счетчик.<br /><br /> pdw_node_id и counter_name формируют ключ для этого представления.|См. в разделе node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Имя счетчика производительности Windows.||  
|counter_category|**nvarchar(255)**|Имя категории счетчика производительности Windows.||  
|имя_экземпляра|**nvarchar(255)**|Имя заданного экземпляра счетчика.||  
|counter_value|**Decimal(38,10)**|Текущее значение счетчика.||  
|last_update_time|**Datetime2(3)**|Отметка времени последнего обновления значение.||  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
