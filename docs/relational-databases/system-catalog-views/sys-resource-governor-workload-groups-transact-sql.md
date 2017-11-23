---
title: "sys.resource_governor_workload_groups (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_workload_groups
- resource_governor_workload_groups_TSQL
- sys.resource_governor_workload_groups_TSQL
- resource_governor_workload_groups
dev_langs: TSQL
helpviewer_keywords: sys.resource_governor_workload_groups catalog view
ms.assetid: 619ba4b7-868f-4784-b527-ec1dfd703c4f
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b5bb4505558ebc20107257acd30d57543f356e6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysresourcegovernorworkloadgroups-transact-sql"></a>sys.resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает хранимую в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] конфигурацию группы рабочей нагрузки. Каждая группа рабочей нагрузки может иметь подписку только на один и только один пул ресурсов.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|group_id|**int**|Уникальный идентификатор группы рабочей нагрузки. Не допускает значение NULL.|  
|имя|**sysname**|Имя группы рабочей нагрузки. Не допускает значение NULL.|  
|importance|**sysname**|**Примечание:** важность применима только к группам рабочей нагрузки в том же пуле ресурсов.<br /><br /> Относительная важность запроса в данной группе рабочей нагрузки. Важность принимает одно из следующих, со СРЕДНИМ используется по умолчанию: низкий, средний, ВЫСОКИЙ.<br /><br /> Не допускает значение NULL.|  
|request_max_memory_grant_percent|**int**|Максимальный объем предоставляемой памяти, в процентах, для отдельного запроса. Значение по умолчанию — 25. Не допускает значение NULL.<br /><br /> **Примечание:** Если этот параметр имеет более 50 процентов, большие запросы будут выполняться по одному. Поэтому повышается риск возникновения ошибки нехватки памяти при выполнении запроса.|  
|request_max_cpu_time_sec|**int**|Максимально допустимое использование ЦП, в секундах, для отдельного запроса. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.<br /><br /> **Примечание:** Дополнительные сведения см. в разделе [класс событий превышает пороговое значение ЦП](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|request_memory_grant_timeout_sec|**int**|Время ожидания предоставления памяти, в секундах, для отдельного запроса. Для значения по умолчанию 0 используется внутреннее вычисление, основанное на стоимости запроса. Не допускает значение NULL.|  
|max_dop|**int**|Максимальная степень параллелизма для группы рабочей нагрузки. Для значения по умолчанию 0 используются глобальные параметры. Не допускает значение NULL.<br /><br /> **Узел:** этот параметр переопределяет параметр запроса **maxdop**.|  
|group_max_requests|**int**|Максимальное число параллельных запросов. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.|  
|pool_id|**int**|Идентификатор пула ресурсов, используемого данной группой рабочей нагрузки.|  
|external_pool_id|**int**|**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор для внешнего пула ресурсов, использующего данную группу рабочей нагрузки.|  
  
## <a name="remarks"></a>Замечания  
 Представление каталога отображает хранимые метаданные. Для просмотра конфигурации, в памяти, используйте соответствующее динамическое административное представление [sys.dm_resource_governor_workload_groups &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md).  
  
 Сохраненная конфигурация и конфигурация, хранимая в памяти, могут различаться, если конфигурация регулятора ресурсов была изменена, но инструкция ALTER RESOURCE GOVERNOR RECONFIGURE не применялась.  
  
## <a name="permissions"></a>Permissions  
 Требует разрешение VIEW ANY DEFINITION для просмотра содержимого и разрешение CONTROL SERVER для изменения содержимого.  
  
## <a name="see-also"></a>См. также:  
 [sys.dm_resource_governor_workload_groups &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога регулятора ресурсов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)  
  
  
