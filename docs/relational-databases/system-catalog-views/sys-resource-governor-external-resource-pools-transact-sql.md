---
title: sys.resource_governor_external_resource_pools (Трансакт-СЗЛ) Документы Майкрософт
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_external_resource_pools
- sys.resource_governor_external_resource_pools_TSQL
- resource_governor_external_resource_pools
- resource_governor_external_resource_pools_TSQL
helpviewer_keywords:
- sys.resource_governor_external_resource_pools
- resource_governor_external_resource_pools
ms.assetid: 75063e36-a91b-496f-9936-88f3d57bd447
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4751cb9164d5ca11cfdaca4365fa7156c2c2425e
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "80663002"
---
# <a name="sysresource_governor_external_resource_pools-transact-sql"></a>sys.resource_governor_external_resource_pools (Трансакт-СЗЛ)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Область применения:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] и [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Возвращает сохраненную конфигурацию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]внешнего пула ресурсов в . Каждая строка представления определяет конфигурацию пула.
  
|Имя столбца|Тип данных|Описание|
|-----------------|---------------|-----------------|
|external_pool_id|**Int**|Уникальный идентификатор пула ресурсов. Не допускает значение NULL.|
|name|**sysname**|Имя пула ресурсов. Не допускает значение NULL.|
|max_cpu_percent|**Int**|Максимальная средняя пропускная способность ЦП, разрешенная для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Не допускает значение NULL.|
|max_memory_percent|**Int**|Процентная доля от общего объема памяти сервера, который может использоваться для запросов в данном пуле ресурсов. Не допускает значение NULL. Эффективный максимум зависит от минимальных значений для пула. Например, значение max_memory_percent можно установить в 100, но реальный максимум будет ниже.|
|max_processes|**Int**|Максимальное количество параллельных внешних процессов. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.|
|version|**Bigint**|Внутренний номер версии.|
  
## <a name="permissions"></a>Разрешения

Необходимо разрешение VIEW SERVER STATE.

## <a name="see-also"></a>См. также

[Управление ресурсами для машинного обучения в SQL Server](../../machine-learning/administration/resource-governor.md)

[Каталог ресурсного губернатора просматривает &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)

[sys.dm_resource_governor_resource_pools (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)

[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;&#41;"Трансакт-СЗЛ"](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Параметр конфигурации сервера external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
