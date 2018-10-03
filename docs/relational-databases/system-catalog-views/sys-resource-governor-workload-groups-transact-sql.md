---
title: sys.resource_governor_workload_groups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_workload_groups
- resource_governor_workload_groups_TSQL
- sys.resource_governor_workload_groups_TSQL
- resource_governor_workload_groups
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_workload_groups catalog view
ms.assetid: 619ba4b7-868f-4784-b527-ec1dfd703c4f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d24885b194f8614e393c7529fac0dc34eb3e15fd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857232"
---
# <a name="sysresourcegovernorworkloadgroups-transact-sql"></a>sys.resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает хранимую в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] конфигурацию группы рабочей нагрузки. Каждая группа рабочей нагрузки может иметь подписку только на один и только один пул ресурсов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|group_id|**int**|Уникальный идентификатор группы рабочей нагрузки. Не допускает значение NULL.|  
|name|**sysname**|Имя группы рабочей нагрузки. Не допускает значение NULL.|  
|importance|**sysname**|**Примечание:** важность применима только к группам рабочей нагрузки в одном пуле ресурсов.<br /><br /> Относительная важность запроса в данной группе рабочей нагрузки. Важность принимает одно из следующих, со СРЕДНИМИ используется по умолчанию: низкий, средний, высокий уровень.<br /><br /> Не допускает значение NULL.|  
|request_max_memory_grant_percent|**int**|Максимальный объем предоставляемой памяти, в процентах, для отдельного запроса. Значение по умолчанию — 25. Не допускает значение NULL.<br /><br /> **Примечание:** Если этот параметр имеет более 50 процентов, большие запросы будут выполняться по одному. Поэтому повышается риск возникновения ошибки нехватки памяти при выполнении запроса.|  
|request_max_cpu_time_sec|**int**|Максимально допустимое использование ЦП, в секундах, для отдельного запроса. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.<br /><br /> **Примечание:** Дополнительные сведения см. в разделе [класс событий превышает пороговое значение ЦП](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|request_memory_grant_timeout_sec|**int**|Время ожидания предоставления памяти, в секундах, для отдельного запроса. Для значения по умолчанию 0 используется внутреннее вычисление, основанное на стоимости запроса. Не допускает значение NULL.|  
|max_dop|**int**|Максимальная степень параллелизма для группы рабочей нагрузки. Для значения по умолчанию 0 используются глобальные параметры. Не допускает значение NULL.<br /><br /> **Узел:** этим параметром переопределяется параметр запроса **maxdop**.|  
|group_max_requests|**int**|Максимальное число параллельных запросов. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.|  
|pool_id|**int**|Идентификатор пула ресурсов, используемого данной группой рабочей нагрузки.|  
|external_pool_id|**int**|**Применимо к**: с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор внешнего пула ресурсов, использующий данной группе рабочей нагрузки.|  
  
## <a name="remarks"></a>Примечания  
 Представление каталога отображает хранимые метаданные. Чтобы увидеть конфигурации, хранимой в памяти, используйте соответствующее динамическое административное представление [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md).  
  
 Сохраненная конфигурация и конфигурация, хранимая в памяти, могут различаться, если конфигурация регулятора ресурсов была изменена, но инструкция ALTER RESOURCE GOVERNOR RECONFIGURE не применялась.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешение VIEW ANY DEFINITION для просмотра содержимого и разрешение CONTROL SERVER для изменения содержимого.  
  
## <a name="see-also"></a>См. также  
 [sys.dm_resource_governor_workload_groups (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога регулятора ресурсов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)  
  
  
