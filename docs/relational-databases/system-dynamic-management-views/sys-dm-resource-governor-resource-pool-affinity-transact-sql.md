---
title: sys. dm_resource_governor_resource_pool_affinity (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_affinity_TSQL
- sys.dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_affinity
- sys.dm_resource_governor_resource_pool_affinity
ms.assetid: a197ec19-a2ba-44f5-a4f2-3eee33ebd77d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b51cd98cd9ef0e6adc3d17d2b1263a62604ab52
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053270"
---
# <a name="sysdm_resource_governor_resource_pool_affinity-transact-sql"></a>Представление sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отслеживает сходство пула ресурсов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|Идентификатор пула ресурсов. Не допускает значение NULL.|  
|Processor_group|**smallint**|Идентификатор логической группы процессоров Windows. Не допускает значение NULL.|  
|Scheduler_mask|**bigint**|Двоичная маска, представляющая планировщики, связанные с этим пулом. Не допускает значение NULL.|  
  
## <a name="remarks"></a>Remarks  
 Пулы, которые созданы со сходством AUTO, не будут появляться в этом представлении, поскольку не имеют сходства. Дополнительные сведения см. в статьях [Создание пула ресурсов &#40;Transact-sql&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md) и [изменение пула ресурсов &#40;инструкций transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md) .  
  
## <a name="see-also"></a>См. также:  
 [sys. dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
