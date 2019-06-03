---
title: DROP EVENT NOTIFICATION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP EVENT NOTIFICATION
- DROP_EVENT_NOTIFICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event notifications [SQL Server], removing
- deleting event notifications
- dropping event notifications
- DROP EVENT NOTIFICATION statement
- removing event notifications
ms.assetid: 0ffd8f47-4ea3-4238-9e73-c318df710cf7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 852662f66b3989cfec15392218346d792be8b835
ms.sourcegitcommit: 9388dcccd6b89826dde47b4c05db71274cfb439a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270215"
---
# <a name="drop-event-notification-transact-sql"></a>DROP EVENT NOTIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет триггер уведомления о событии из данной базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP EVENT NOTIFICATION notification_name [ ,...n ]  
ON { SERVER | DATABASE | QUEUE queue_name }  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *notification_name*  
 Имя удаляемого уведомления о событии. Можно указать несколько уведомлений о событии. Список созданных уведомлений о событии см. в [sys.event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md).  
  
 SERVER  
 Показывает область уведомления о событии, относящемся к данному серверу. Параметр SERVER необходимо указать в том случае, если он был указан при создании уведомления о событии.  
  
 DATABASE  
 Показывает область уведомления о событии, относящемся к данной базе данных. Параметр DATABASE необходимо указать в том случае, если он был указан при создании уведомления о событии.  
  
 QUEUE *queue_name*  
 Показывает область уведомления о событии, относящемся к очереди, указанной аргументом *queue_name*. Аргумент QUEUE должен быть указан, если он был указан при создании уведомления о событии. Аргумент *queue_name* является именем очереди и также должен быть указан.  
  
## <a name="remarks"></a>Примечания  
 Если уведомление о событии возникает и удаляется в одной и той же транзакции, то вначале происходит отправка экземпляра уведомления о событии, а затем удаление этого уведомления.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы удалить уведомление о событии, относящемся к уровню базы данных, пользователь должен быть, как минимум, владельцем уведомления о событии или обладать разрешением ALTER ANY DATABASE EVENT NOTIFICATION в данной базе данных.  
  
 Чтобы удалить уведомление о событии, относящемся к уровню сервера, пользователь должен быть, как минимум, владельцем уведомления о событии или иметь разрешение ALTER ANY EVENT NOTIFICATION в данной базе данных.  
  
 Чтобы удалить уведомление о событии из определенной очереди, пользователь должен быть, как минимум, владельцем уведомления о событии или обладать разрешением ALTER на родительскую очередь.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается уведомление о событии, существующее в пределах базы данных, а затем оно удаляется.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE EVENT NOTIFICATION NotifyALTER_T1  
ON DATABASE  
FOR ALTER_TABLE  
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984';  
GO  
DROP EVENT NOTIFICATION NotifyALTER_T1  
ON DATABASE;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE EVENT NOTIFICATION (Transact-SQL)](../../t-sql/statements/create-event-notification-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.event_notifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)   
 [sys.event (Transact-SQL)](../../relational-databases/system-catalog-views/sys-events-transact-sql.md)  
  
  
