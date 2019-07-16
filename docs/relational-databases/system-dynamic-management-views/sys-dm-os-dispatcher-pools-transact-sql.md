---
title: sys.dm_os_dispatcher_pools (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0bd8d9ae347615053b542c684dedc026f6e549ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900270"
---
# <a name="sysdmosdispatcherpools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о пулах диспетчера сеансов. Пулы диспетчеров представляют собой пулы потоков, используемые системными компонентами для фоновой обработки.  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_dispatcher_pools**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary(8)**|Адрес пула диспетчеров. значение dispatcher_pool_address уникально. Не допускает значение NULL.|  
|type|**nvarchar(256)**|Тип пула диспетчеров. Не допускает значение NULL. Существует два типа пулов диспетчеров:<br /><br /> DISP_POOL_XE_ENGINE;<br /><br /> DISP_POOL_XE_SESSION.<br /><br /> Запрос динамического административного Представления полный список|  
|name|**nvarchar(256)**|Имя пула диспетчеров. Не допускает значение NULL.|  
|dispatcher_count|**int**|Число активных потоков диспетчеров. Не допускает значение NULL.|  
|dispatcher_ideal_count|**int**|Число потоков диспетчеров, которые могут быть задействованы по мере роста пула диспетчеров. Не допускает значение NULL.|  
|dispatcher_timeout_ms|**int**|Время в миллисекундах, в течение которого диспетчер будет ожидать нового задания, прежде чем завершить работу. Не допускает значение NULL.|  
|dispatcher_waiting_count|**int**|Число бездействующих потоков диспетчеров. Не допускает значение NULL.|  
|queue_length|**int**|Число рабочих элементов, ожидающих обработки пулом диспетчеров. Не допускает значение NULL.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
В [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] необходимо разрешение `VIEW DATABASE STATE` для базы данных.   

## <a name="see-also"></a>См. также  
  
  


