---
title: sys. dm_broker_activated_tasks (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_activated_tasks
- sys.dm_broker_activated_tasks_TSQL
- dm_broker_activated_tasks
- dm_broker_activated_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_activated_tasks dynamic management view
ms.assetid: 17e6f87f-8f56-489d-9aed-216afc8ef310
author: stevestein
ms.author: sstein
ms.openlocfilehash: f80ec78e37707058a354a03bb2605a38abdfa803
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68099192"
---
# <a name="sysdm_broker_activated_tasks-transact-sql"></a>sys.dm_broker_activated_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждой хранимой процедуры, активированной компонентом Service Broker.  
 

|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**spid**|**int**|Идентификатор сеанса активированной хранимой процедуры. Допускает значение NULL.|  
|**database_id**|**smallint**|Идентификатор базы данных, в которой определена очередь. Допускает значение NULL.|  
|**queue_id**|**int**|Идентификатор объекта очереди, для которого была активирована хранимая процедура. Допускает значение NULL.|  
|**procedure_name**|**nvarchar (650)**|Имя активированной хранимой процедуры. Допускает значение NULL.|  
|**execute_as**|**int**|Идентификатор пользователя, под именем которого выполняется хранимая процедура. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="physical-joins"></a>Физические соединения  
 ![Соединения для sys.dm_broker_activated_tasks](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-activated-tasks-1.gif "Соединения для sys.dm_broker_activated_tasks")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|С|Кому|Связь|  
|----------|--------|------------------|  
|dm_broker_activated_tasks.spid|dm_exec_sessions.session_id|Один к одному|  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker связанные динамические административные представления &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

