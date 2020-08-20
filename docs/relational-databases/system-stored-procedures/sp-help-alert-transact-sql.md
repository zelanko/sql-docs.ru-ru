---
description: sp_help_alert (Transact-SQL)
title: sp_help_alert (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_alert
- sp_help_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_alert
ms.assetid: 850cef4e-6348-4439-8e79-fd1bca712091
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ce66505585fa7e7ed49919c5cb54b94ffd205500
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469349"
---
# <a name="sp_help_alert-transact-sql"></a>sp_help_alert (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Выдает сведения о предупреждениях, определенных для данного сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_alert [ [ @alert_name = ] 'alert_name' ]   
     [ , [ @order_by = ] 'order_by' ]   
     [ , [ @alert_id = ] alert_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @legacy_format = ] legacy_format ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @alert_name = ] 'alert_name'` Имя оповещения. *alert_name* имеет тип **nvarchar (128)**. Если параметр *alert_name* не указан, возвращаются сведения обо всех оповещениях.  
  
`[ @order_by = ] 'order_by'` Порядок сортировки, используемый для создания результатов. Аргумент *order_by*имеет тип **sysname**и значение по умолчанию N "*Name*".  
  
`[ @alert_id = ] alert_id` Идентификационный номер предупреждения для передачи сведений о. *alert_id*имеет **тип int**и значение по умолчанию NULL.  
  
`[ @category_name = ] 'category'` Категория оповещения. *Category* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @legacy_format = ] legacy_format` Указывает, следует ли создавать результирующий набор прежних версий. *legacy_format* имеет **бит**и значение по умолчанию **0**. Если *legacy_format* равен **1**, **sp_help_alert** возвращает результирующий набор, возвращенный **sp_help_alert** в Microsoft SQL Server 2000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если ** \@ legacy_format** равен **0**, **sp_help_alert** создает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Присвоенный системой уникальный целочисленный идентификатор.|  
|**name**|**sysname**|Имя предупреждения (например, "демонстрация": полный журнал **msdb** ).|  
|**event_source**|**nvarchar (100)**|Источник события. Это всегда будет **MSSQLServer** для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7,0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Код ошибки сообщения, который определен для предупреждения (Обычно соответствует номеру ошибки в таблице **sysmessages** ). Если для определения предупреждения используется серьезность, **message_id** имеет значение **0** или null.|  
|**severity**|**int**|Уровень серьезности (от **9** до **25**, **110**, **120**, **130**или **140**), определяющий оповещение.|  
|**доступной**|**tinyint**|Состояние того, включено ли оповещение (**1**) или нет (**0**). Отправка отключенных предупреждений не производится.|  
|**delay_between_responses**|**int**|Время ожидания (в секундах) между ответами на предупреждение.|  
|**last_occurrence_date**|**int**|Дата последнего возникновения предупреждения.|  
|**last_occurrence_time**|**int**|Время последнего возникновения предупреждения.|  
|**last_response_date**|**int**|Дата последнего ответа на предупреждение от службы **SQLServerAgent** .|  
|**last_response_time**|**int**|Время последнего ответа на предупреждение службой **SQLServerAgent** .|  
|**notification_message**|**nvarchar(512)**|Необязательное дополнительное сообщение, отправляемое оператору по электронной почте или на пейджер.|  
|**include_event_description**|**tinyint**|Указывает, следует ли включить в текст уведомления описание ошибки SQL Server из журнала приложений Microsoft Windows.|  
|**database_name**|**sysname**|База данных, ошибка в которой приводит к появлению предупреждения. Если имя базы данных равно значению NULL, предупреждение появляется независимо от места возникновения ошибки.|  
|**event_description_keyword**|**nvarchar (100)**|Описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в журнале приложений Windows, которое должно соответствовать указанной последовательности символов.|  
|**occurrence_count**|**int**|Количество раз возникновения предупреждения.|  
|**count_reset_date**|**int**|Дата последнего сброса **occurrence_count** .|  
|**count_reset_time**|**int**|Время последнего сброса **occurrence_count** .|  
|**job_id**|**uniqueidentifier**|Идентификационный номер задания, выполняющегося при срабатывании данного предупреждения.|  
|**job_name**|**sysname**|Имя задания, выполняющегося при срабатывании данного предупреждения.|  
|**has_notification**|**int**|Ненулевое значение, если один или более операторов уведомлены данным предупреждением. Результат логической операции OR одного или нескольких следующих значений:<br /><br /> **1**= имеется уведомление по электронной почте<br /><br /> **2**= имеется уведомление на пейджер<br /><br /> **4**= содержит уведомление **net send** .|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performance_condition**|**nvarchar(512)**|Если **тип** имеет значение **2**, в этом столбце отображается определение условия производительности. в противном случае столбец имеет значение NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0 всегда будет иметь значение «[Без категорий]».|  
|**wmi_namespace**|**sysname**|Если **тип** имеет значение **3**, в этом столбце отображается пространство имен для события WMI.|  
|**wmi_query**|**nvarchar(512)**|Если **тип** — **3**, в этом столбце отображается запрос для события WMI.|  
|**type**|**int**|Тип события:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оповещение о событии 1<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предупреждение о производительности<br /><br /> **3** = предупреждение о событии WMI|  
  
 Если ** \@ legacy_format** равен **1**, **sp_help_alert** создает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Присвоенный системой уникальный целочисленный идентификатор.|  
|**name**|**sysname**|Имя предупреждения (например, "демонстрация": полный журнал **msdb** ).|  
|**event_source**|**nvarchar (100)**|Источник события. Это всегда будет **MSSQLServer** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7,0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Код ошибки сообщения, который определен для предупреждения (Обычно соответствует номеру ошибки в таблице **sysmessages** ). Если для определения предупреждения используется серьезность, **message_id** имеет значение **0** или null.|  
|**severity**|**int**|Уровень серьезности (от **9** до **25**, **110**, **120**, **130**или 1**40**), определяющий оповещение.|  
|**доступной**|**tinyint**|Состояние того, включено ли оповещение (**1**) или нет (**0**). Отправка отключенных предупреждений не производится.|  
|**delay_between_responses**|**int**|Время ожидания (в секундах) между ответами на предупреждение.|  
|**last_occurrence_date**|**int**|Дата последнего возникновения предупреждения.|  
|**last_occurrence_time**|**int**|Время последнего возникновения предупреждения.|  
|**last_response_date**|**int**|Дата последнего ответа на предупреждение от службы **SQLServerAgent** .|  
|**last_response_time**|**int**|Время последнего ответа на предупреждение службой **SQLServerAgent** .|  
|**notification_message**|**nvarchar(512)**|Необязательное дополнительное сообщение, отправляемое оператору по электронной почте или на пейджер.|  
|**include_event_description**|**tinyint**|Указывает, следует ли включить в текст сообщения уведомления описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из журнала приложений Windows.|  
|**database_name**|**sysname**|База данных, ошибка в которой приводит к появлению предупреждения. Если имя базы данных равно значению NULL, предупреждение появляется независимо от места возникновения ошибки.|  
|**event_description_keyword**|**nvarchar (100)**|Описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в журнале приложений Windows, которое должно соответствовать указанной последовательности символов.|  
|**occurrence_count**|**int**|Количество раз возникновения предупреждения.|  
|**count_reset_date**|**int**|Дата последнего сброса **occurrence_count** .|  
|**count_reset_time**|**int**|Время последнего сброса **occurrence_count** .|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_name**|**sysname**|Задание по требованию, выполняющееся в ответ на данное предупреждение.|  
|**has_notification**|**int**|Ненулевое значение, если один или более операторов уведомлены данным предупреждением. Значение является результатом логической операции OR над одним или несколькими следующими значениями:<br /><br /> **1**= имеется уведомление по электронной почте<br /><br /> **2**= имеется уведомление на пейджер<br /><br /> **4**= содержит уведомление **net send** .|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)].|  
|**performance_condition**|**nvarchar(512)**|Если **тип** имеет значение **2**, в этом столбце отображается определение условия производительности. Если **тип** — **3**, в этом столбце отображается запрос для события WMI. В противном случае столбец содержит значение NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Всегда будет иметь "**[без категории]**" для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7,0.|  
|**type**|**int**|Тип предупреждения:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оповещение о событии 1<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предупреждение о производительности<br /><br /> **3** = предупреждение о событии WMI|  
  
## <a name="remarks"></a>Комментарии  
 **sp_help_alert** должны запускаться из базы данных **msdb** .  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена предопределенная роль базы данных **SQLAgentOperatorRole** в базе данных **msdb** .  
  
 Дополнительные сведения о **SQLAgentOperatorRole**см. в разделе [Агент SQL Server предопределенных ролей базы данных](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере выдаются сведения о предупреждении `Demo: Sev. 25 Errors`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_add_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
