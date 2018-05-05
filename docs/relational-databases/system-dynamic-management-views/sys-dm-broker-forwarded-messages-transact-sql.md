---
title: sys.dm_broker_forwarded_messages (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_forwarded_messages
- dm_broker_forwarded_messages
- sys.dm_broker_forwarded_messages_TSQL
- dm_broker_forwarded_messages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_forwarded_messages dynamic management view
ms.assetid: 5576376d-6364-417a-8475-aa770e060845
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a31e4a932e73b0006de5168ec81b1d75decb980
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmbrokerforwardedmessages-transact-sql"></a>sys.dm_broker_forwarded_messages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по записи на каждое сообщение компонента Service Broker, которое пересылается в данный момент экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**conversation_id**|**uniqueidentifier**|Идентификатор диалога, которому принадлежит это сообщение. Допускает значение NULL.|  
|**is_initiator**|**бит**|Показывает, пришло ли это сообщение от инициатора диалога.  Допускает значение NULL.<br /><br /> 0 = не от инициатора<br /><br /> 1 = от инициатора|  
|**to_service_name**|**nvarchar(512)**|Имя службы, куда посылается сообщение. Допускает значение NULL.|  
|**to_broker_instance**|**nvarchar(512)**|Идентификатор брокера, который управляет службой, пославшей сообщение. Допускает значение NULL.|  
|**from_service_name**|**nvarchar(512)**|Имя службы, отправившей сообщение. Допускает значение NULL.|  
|**from_broker_instance**|**nvarchar(512)**|Идентификатор брокера, у которого расположена служба, пославшая сообщение. Допускает значение NULL.|  
|**adjacent_broker_address**|**nvarchar(512)**|Сетевой адрес назначения для этого сообщения. Допускает значение NULL.|  
|**message_sequence_number**|**bigint**|Порядковый номер сообщения в диалоговом окне. Допускает значение NULL.|  
|**message_fragment_number**|**int**|Если сообщение диалога фрагментировано, тогда это номер фрагмента, содержащегося в транспортном сообщении. Допускает значение NULL.|  
|**hops_remaining**|**tinyint**|Количество попыток повторной передачи сообщения перед его доставкой получателю. Каждый раз, когда сообщение пересылается, это число уменьшается на единицу. Допускает значение NULL.|  
|**time_to_live**|**int**|Максимальное время жизни сообщения. При достижении 0 сообщение удаляется. Допускает значение NULL.|  
|**time_consumed**|**int**|Время, в течение которого активно данное сообщение. Каждый раз, когда сообщение пересылается, это число уменьшается на время, которое заняла пересылка. Не допускает значения NULL.|  
|**message_id**|**uniqueidentifier**|Идентификатор сообщения. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Компонент Service Broker, связанные с динамическим административным представлениям & #40; Transact-SQL & #41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

