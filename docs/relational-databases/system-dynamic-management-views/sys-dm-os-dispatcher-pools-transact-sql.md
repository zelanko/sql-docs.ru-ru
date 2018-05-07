---
title: sys.dm_os_dispatcher_pools (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_dispatcher_pools_TSQL
- dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_os_dispatcher_pools DMV
ms.assetid: b9edbc83-c6bc-4753-9bb5-a454cfe7d6bf
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ceaad5d07730720f9aef590762f062cf1832a07
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmosdispatcherpools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о пулах диспетчера сеансов. Пулы диспетчеров представляют собой пулы потоков, используемые системными компонентами для фоновой обработки.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_dispatcher_pools**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary(8)**|Адрес пула диспетчеров. значение dispatcher_pool_address уникально. Не допускает значение NULL.|  
|Тип|**nvarchar(256)**|Тип пула диспетчеров. Не допускает значение NULL. Существует два типа пулов диспетчеров:<br /><br /> DISP_POOL_XE_ENGINE;<br /><br /> DISP_POOL_XE_SESSION.<br /><br /> Запрос динамического административного Представления полный список|  
|имя|**nvarchar(256)**|Имя пула диспетчеров. Не допускает значение NULL.|  
|dispatcher_count|**int**|Число активных потоков диспетчеров. Не допускает значение NULL.|  
|dispatcher_ideal_count|**int**|Число потоков диспетчеров, которые могут быть задействованы по мере роста пула диспетчеров. Не допускает значение NULL.|  
|dispatcher_timeout_ms|**int**|Время в миллисекундах, в течение которого диспетчер будет ожидать нового задания, прежде чем завершить работу. Не допускает значение NULL.|  
|dispatcher_waiting_count|**int**|Число бездействующих потоков диспетчеров. Не допускает значение NULL.|  
|queue_length|**int**|Число рабочих элементов, ожидающих обработки пулом диспетчеров. Не допускает значение NULL.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="see-also"></a>См. также  
  
  


