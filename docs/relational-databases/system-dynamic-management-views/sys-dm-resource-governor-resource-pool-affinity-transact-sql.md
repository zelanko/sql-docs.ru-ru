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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 649bb3d5278337db4bda4b3f3622823bd3b35a17
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784889"
---
# <a name="sysdm_resource_governor_resource_pool_affinity-transact-sql"></a>Представление sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отслеживает сходство пула ресурсов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|Идентификатор пула ресурсов. Не допускает значение NULL.|  
|Processor_group|**smallint**|Идентификатор логической группы процессоров Windows. Не допускает значение NULL.|  
|Scheduler_mask|**bigint**|Двоичная маска, представляющая планировщики, связанные с этим пулом. Не допускает значение NULL.|  
  
## <a name="remarks"></a>Примечания  
 Пулы, которые созданы со сходством AUTO, не будут появляться в этом представлении, поскольку не имеют сходства. Дополнительные сведения см. в статьях [Создание пула ресурсов &#40;Transact-sql&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md) и [изменение пула ресурсов &#40;инструкций transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md) .  
  
## <a name="see-also"></a>См. также  
 [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
