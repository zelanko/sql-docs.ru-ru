---
description: sys.dm_pdw_resource_waits (Transact-SQL)
title: sys.dm_pdw_resource_waits (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/26/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a43ce9a2-5261-41e3-97f0-555ba05ebed9
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: fad0e8410294ecfe477ccf24215772531260bd50
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035227"
---
# <a name="sysdm_pdw_resource_waits-transact-sql"></a>sys.dm_pdw_resource_waits (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Отображает сведения о ожидании для всех типов ресурсов в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] .  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Расположение запроса в списке ожидания.|порядковый номер, основанный на 0. Оно не является уникальным для всех записей ожидания.|  
|session_id|**nvarchar(32)**|Идентификатор сеанса, в котором произошло состояние ожидания.|См. session_id в [sys.dm_pdw_exec_sessions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|тип|**nvarchar(255)**|Тип ожидания, который представляет эта запись.|Возможные значения:<br /><br /> Подключение<br /><br /> Параллельные локальные запросы<br /><br /> Параллелизм распределенных запросов<br /><br /> Параллелизм DMS<br /><br /> Параллелизм резервного копирования|  
|object_type|**nvarchar(255)**|Тип объекта, на который влияет ожидание.|Возможные значения:<br /><br /> **ОБЪЕКТАМИ**<br /><br /> **DATABASE**<br /><br /> **СИСТЕМОЙ**<br /><br /> **SCHEMA**<br /><br /> **ПРИКЛАД**|  
|object_name|**nvarchar (386)**|Имя или идентификатор GUID указанного объекта, на который влияет ожидание.|Таблицы и представления отображаются с именами из трех частей.<br /><br /> Индексы и статистика отображаются с именами из четырех частей.<br /><br /> Имена, участники и базы данных являются строковыми именами.|  
|request_id|**nvarchar(32)**|Идентификатор запроса, для которого произошло состояние ожидания.|Идентификатор Кид запроса.<br /><br /> Идентификатор GUID для запросов загрузки.|  
|request_time|**datetime**|Время запроса блокировки или ресурса.||  
|acquire_time|**datetime**|Время, когда был получен блокировка или ресурс.||  
|Состояние|**nvarchar(50)**|Состояние состояния ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Приоритет ожидающего элемента.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|concurrency_slots_used|**int**|Внутренние|Просмотреть [ресурс Monitor ожидает](#monitor-resource-waits) ниже|  
|resource_class|**nvarchar (20)**|Внутренние |Просмотреть [ресурс Monitor ожидает](#monitor-resource-waits) ниже|  
  
## <a name="monitor-resource-waits"></a>Мониторинг ожиданий ресурсов 
С появлением [групп рабочей нагрузки](/azure/sql-data-warehouse/sql-data-warehouse-workload-isolation)слоты выдачи больше не применяются.  Используйте приведенный ниже запрос и `resources_requested` столбец, чтобы понять ресурсы, необходимые для выполнения запроса.

```sql
select rw.wait_id
      ,rw.session_id
      ,rw.type
      ,rw.object_type
      ,rw.object_name
      ,rw.request_id
      ,rw.request_time
      ,rw.acquire_time
      ,rw.state
      ,resources_requested = s.effective_request_min_resource_grant_percent
      ,r.group_name
  from sys.dm_workload_management_workload_groups_stats s
  join sys.dm_pdw_exec_requests r on r.group_name = s.name collate SQL_Latin1_General_CP1_CI_AS
  join sys.dm_pdw_resource_waits rw on rw.request_id = r.request_id
```

## <a name="see-also"></a>См. также:  
 [Динамические административные представления Azure синапсе Analytics и Параллельное хранилище данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
