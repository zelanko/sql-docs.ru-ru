---
title: sys. dm_resource_governor_external_resource_pool_affinity (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77d0d322139be1f1c6086622855600a7c24fc4c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "80664325"
---
# <a name="sysdm_resource_governor_external_resource_pool_affinity-transact-sql"></a>sys. dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Применимо к:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] и [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Возвращает сведения о сходстве ЦП с текущей конфигурацией внешнего пула ресурсов.
  
|Имя столбца|Тип данных|Описание|
|----------------|---------------|-----------------|
|pool_id|**int**|ИДЕНТИФИКАТОР внешнего пула ресурсов. Не допускает значение NULL.|
|processor_group|**smallint**|Идентификатор логической группы процессоров Windows. Не допускает значение NULL.|
|cpu_mask|**bigint**|Двоичная маска, представляющая процессоры, связанные с этим пулом. Не допускает значение NULL.|
  
## <a name="remarks"></a>Remarks

Пулы, созданные с помощью сходства `AUTO` , не отображаются в этом представлении, так как они не имеют сходства. Дополнительные сведения см. в статьях [Создание пула внешних ресурсов &#40;Transact-sql&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md) и [Изменение внешнего пула ресурсов &#40;инструкций transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) .

## <a name="permissions"></a>Разрешения

Требуется разрешение `VIEW SERVER STATE`.

## <a name="see-also"></a>См. также

[Управление ресурсами для машинного обучения в SQL Server](../../machine-learning/administration/resource-governor.md)

[sys. dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Параметр конфигурации сервера «external scripts enabled»](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
