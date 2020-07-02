---
title: sys. dm_broker_forwarded_messages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e72a67d74fb6147f9710490254b752cc838b55cd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754307"
---
# <a name="sysdm_broker_forwarded_messages-transact-sql"></a>sys.dm_broker_forwarded_messages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по записи на каждое сообщение компонента Service Broker, которое пересылается в данный момент экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**conversation_id**|**uniqueidentifier**|Идентификатор диалога, которому принадлежит это сообщение. Допускает значение NULL.|  
|**is_initiator**|**bit**|Показывает, пришло ли это сообщение от инициатора диалога.  Допускает значение NULL.<br /><br /> 0 = не от инициатора<br /><br /> 1 = от инициатора|  
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
 [Динамические административные представления и функции &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с компонентом Service Broker (Transact-SQL)](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

