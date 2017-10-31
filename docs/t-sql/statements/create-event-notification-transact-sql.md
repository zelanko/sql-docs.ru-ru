---
title: "Создание уведомления о СОБЫТИИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_EVENT_NOTIFICATION_TSQL
- NOTIFICATION_TSQL
- EVENT
- NOTIFICATION
- CREATE EVENT NOTIFICATION
- EVENT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EVENT NOTIFICATION statement
- events [SQL Server], notifications
- event notifications [SQL Server], creating
ms.assetid: dbbff0e8-9e25-4f12-a1ba-e12221d16ac2
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 82d4f844c44f92232c8ac9bebd5841460f93051c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-event-notification-transact-sql"></a>CREATE EVENT NOTIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает объект, отправляющий в службу компонента Service Broker данные о событии сервера или базы данных. Уведомления о событиях создаются только при помощи инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE EVENT NOTIFICATION event_notification_name   
ON { SERVER | DATABASE | QUEUE queue_name }   
[ WITH FAN_IN ]  
FOR { event_type | event_group } [ ,...n ]  
TO SERVICE 'broker_service' , { 'broker_instance_specifier' | 'current database' }  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *event_notification_name*  
 Имя уведомления о событии. Имя уведомления о событии должно соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md) и должно быть уникальным в пределах области, в котором они были созданы: сервер, база данных, или *object_name*.  
  
 SERVER  
 Применяет область уведомления о событии к текущему экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если задано это значение, уведомление срабатывает при каждом возникновении события, указанного в предложении FOR, на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
 DATABASE  
 Применяет область уведомления о событии к текущей базе данных. Если задано это значение, уведомление срабатывает при каждом возникновении в текущей базе данных события, указанного в предложении FOR.  
  
 QUEUE  
 Применяет область уведомления о событии к определенной очереди в текущей базе данных. Параметр QUEUE можно указать, только если также указан параметр FOR QUEUE_ACTIVATION или FOR BROKER_QUEUE_DISABLED.  
  
 *имя_очереди*  
 Имя очереди, к которой применяется уведомление о событии. *имя_очереди* можно указать, только если задан параметр QUEUE.  
  
 WITH FAN_IN  
 Служит для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указанием рассылать обозначенным службам только одно сообщение на событие для всех уведомлений о событиях, которые:  
  
-   созданы в том же событии;  
  
-   созданы тем же участником (который определен таким же идентификатором безопасности);  
  
-   Укажите ту же службу и *broker_instance_specifier*.  
  
-   указывают WITH FAN_IN.  
  
 Например, были созданы три уведомления о событии. Все уведомления о событии указывают параметры FOR ALTER_TABLE, WITH FAN_IN, предложение TO SERVICE и созданы тем же идентификатором безопасности. При выполнении инструкции ALTER TABLE сообщения, которые созданы этими тремя уведомлениями о событии, объединяются в одно. Поэтому целевая служба получает только одно сообщение о событии.  
  
 *event_type*  
 Имя типа события, которое вызывает уведомление о событии. *event_type* может быть [!INCLUDE[tsql](../../includes/tsql-md.md)] тип события DDL, тип события трассировки SQL или [!INCLUDE[ssSB](../../includes/sssb-md.md)] тип события. Список уточняющих [!INCLUDE[tsql](../../includes/tsql-md.md)] типов событий DDL, в разделе [DDL-события](../../relational-databases/triggers/ddl-events.md). QUEUE_ACTIVATION и BROKER_QUEUE_DISABLED являются типами событий компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Дополнительные сведения см. в разделе [Event Notifications](../../relational-databases/service-broker/event-notifications.md).  
  
 *event_group*  
 Имя предопределенной группы типов событий [!INCLUDE[tsql](../../includes/tsql-md.md)] или трассировки SQL. Возникновение любого события из группы может привести к срабатыванию уведомления о событии. Список групп событий DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в них события, а также области, по которому можно будет определить, [группы DDL-событий](../../relational-databases/triggers/ddl-event-groups.md).  
  
 *event_group* также выступает в качестве макроса, после завершения инструкции CREATE EVENT NOTIFICATION, добавляя события соответствующих типов он охватывает для **sys.events** представления каталога.  
  
 **"** *broker_service* **"**  
 Указывает целевую службу, получающую данные о событиях экземпляра. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] начинает один или несколько диалогов с целевой службой для уведомления о событии. Данная служба должна поддерживать тип сообщений о событиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и контракт, использованный для отправки сообщения.  
  
 Диалог остается открытым до удаления уведомления о событии. Некоторые ошибки могут привести к досрочному завершению диалогов. Явное завершение всех или некоторых диалогов может помешать конечной службе получать новые сообщения.  
  
 { **"***broker_instance_specifier***"** | **'current database'** }  
 Указывает экземпляр компонента service broker для которой *broker_service* разрешается. Значение для определенного компонента service broker может быть получено путем запроса **service_broker_guid** столбец **sys.databases** представления каталога. Используйте **'current database'** чтобы указать экземпляр компонента service broker в текущей базе данных. **'current database'** — без учета регистра строковый литерал.  
  
> [!NOTE]  
>  Этот параметр недоступен в автономной базе данных.  
  
## <a name="remarks"></a>Замечания  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] включает в себя тип сообщений и контракт исключительно для уведомлений о событии. Таким образом служба вызывающей стороны не должен создаваться, так как он уже существует, компонент Service Broker задает следующее имя контракта:`http://schemas.microsoft.com/SQL/Notifications/PostEventNotification`  
  
 Целевая служба, принимающая уведомления о событиях, должна поддерживать такой уже существующий контракт.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] на удаленном сервере, необходимо настроить безопасность диалога. Безопасность диалога должна быть настроена вручную согласно модели полной безопасности. Дополнительные сведения см. в разделе [настроить безопасность диалога для уведомлений о событиях](../../relational-databases/service-broker/configure-dialog-security-for-event-notifications.md).  
  
 Если происходит откат транзакции события, активирующей уведомление, то же происходит и с отправкой уведомления о событии. Уведомления о событиях не срабатывают в результате действий, определенных триггерами, когда происходит завершение или откат транзакции внутри триггера. Учитывая то, что события трассировки не связаны транзакциями, уведомления о событиях, основанные на событиях трассировки, отправляются вне зависимости от того, происходит ли откат активировавшей их транзакции.  
  
 Если диалог между сервером и конечной службой прерывается после срабатывания уведомления о событии, то появляется сообщение об ошибке, а уведомление о событии удаляется.  
  
 На транзакцию события, инициировавшую уведомление, не влияет успешность отправки уведомления о событии.  
  
 Все неудачные попытки отправки уведомления о событии заносятся в журнал.  
  
## <a name="permissions"></a>Permissions  
 Чтобы создать уведомление о событии в области базы данных (ON DATABASE), необходимо разрешение CREATE DATABASE DDL EVENT NOTIFICATION в текущей базе данных.  
  
 Чтобы создать уведомление о событии для инструкции DDL в области сервера (ON SERVER), необходимо разрешение CREATE DDL EVENT NOTIFICATION на сервере.  
  
 Чтобы создать уведомление о событии для события трассировки, необходимо разрешение CREATE TRACE EVENT NOTIFICATION на сервере.  
  
 Чтобы создать уведомление о событии в области очереди, необходимо разрешение ALTER для запроса.  
  
## <a name="examples"></a>Примеры  
  
> [!NOTE]  
>  В примерах A и B, идентификатор GUID, указанный в предложении `TO SERVICE 'NotifyService'` («8140a771-3c4b-4479-8ac0-81008ab17984») специфичен для компьютера, на котором установлен пример. Для этого экземпляра использовался идентификатор GUID для базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
>   
>  Чтобы копировать и запустить эти примеры, необходимо заменить этот идентификатор GUID на идентификатор из вашего компьютера и экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Как описано в разделе «аргументы» выше, можно получить **"***broker_instance_specifier***"** путем запроса столбца service_broker_guid sys.databases представления каталога.  
  
### <a name="a-creating-an-event-notification-that-is-server-scoped"></a>A. Создание уведомления о событии уровня сервера  
 В следующем примере создаются объекты, необходимые для установки целевой службы при помощи компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Конечная служба ссылается на тип сообщения и контракт вызывающей стороны исключительно для уведомлений о событиях. Затем уведомление о событии создается в конечной службе, которая начинает рассылку уведомлений в ответ на событие трассировки `Object_Created` на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```tsql  
--Create a queue to receive messages.  
CREATE QUEUE NotifyQueue ;  
GO  
--Create a service on the queue that references  
--the event notifications contract.  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
([http://schemas.microsoft.com/SQL/Notifications/PostEventNotification]);  
GO  
--Create a route on the service to define the address   
--to which Service Broker sends messages for the service.  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
--Create the event notification.  
CREATE EVENT NOTIFICATION log_ddl1   
ON SERVER   
FOR Object_Created   
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
### <a name="b-creating-an-event-notification-that-is-database-scoped"></a>Б. Создание уведомления о событии уровня базы данных  
 В следующем примере создается уведомление о событии для той же службы, что и в предыдущем примере. Уведомление о событии срабатывает в ответ на событие `ALTER_TABLE` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```tsql  
CREATE EVENT NOTIFICATION Notify_ALTER_T1  
ON DATABASE  
FOR ALTER_TABLE  
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984';  
```  
  
### <a name="c-getting-information-about-an-event-notification-that-is-server-scoped"></a>В. Получение данных об уведомлении о событии уровня сервера  
 В следующем примере у представления каталога `sys.server_event_notifications` запрашиваются метаданные об уведомлении о событии `log_ddl1`, созданном в области сервера.  
  
```  
SELECT * FROM sys.server_event_notifications  
WHERE name = 'log_ddl1';  
```  
  
### <a name="d-getting-information-about-an-event-notification-that-is-database-scoped"></a>Г. Получение сведений об уведомлении о событии уровня базы данных  
 В следующем примере у представления каталога `sys.event_notifications` запрашиваются метаданные об уведомлении о событии `Notify_ALTER_T1`, созданном на уровне базы данных.  
  
```tsql  
SELECT * FROM sys.event_notifications  
WHERE name = 'Notify_ALTER_T1';  
```  
  
## <a name="see-also"></a>См. также:  
 [Уведомления о событиях](../../relational-databases/service-broker/event-notifications.md)   
 [Удаление уведомления о СОБЫТИИ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-event-notification-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.event_notifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)   
 [sys.server_event_notifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)   
 [sys.Events &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-events-transact-sql.md)   
 [sys.server_events &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-events-transact-sql.md)  
  
  

