---
title: sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
caps.latest.revision: 8
author: jeannt
ms.author: edmaca
manager: craigg
ms.openlocfilehash: abee195d109b751df856c720264a42241bf861f9
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34466580"
---
# <a name="sysdmresourcegovernorexternalresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Применимо к:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] и [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Возвращает сведения о схожести ЦП о текущей конфигурации пула внешних ресурсов.
  
|Имя столбца|Тип данных|Описание|
|----------------|---------------|-----------------|
|pool_id|**int**|Идентификатор для внешнего пула ресурсов. Не допускает значение NULL.|
|processor_group|**smallint**|Идентификатор логической группы процессоров Windows. Не допускает значение NULL.|
|cpu_mask|**bigint**|Двоичная маска, представляющая процессоры, связанные с этим пулом. Не допускает значение NULL.|
  
## <a name="remarks"></a>Примечания

Пулы, которые созданы со сходством `AUTO` не отображаются в данном представлении, так как они не имеют сходства. Дополнительные сведения см. в разделе [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) и [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) инструкции.

## <a name="permissions"></a>Разрешения

Требуется разрешение `VIEW SERVER STATE`.

## <a name="see-also"></a>См. также:

[Управление ресурсами для машинного обучения в SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[представление sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Параметр конфигурации сервера «external scripts enabled»](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
