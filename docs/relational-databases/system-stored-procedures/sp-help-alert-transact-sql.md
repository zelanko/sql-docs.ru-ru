---
title: "sp_help_alert (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_alert
- sp_help_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_alert
ms.assetid: 850cef4e-6348-4439-8e79-fd1bca712091
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f1dc2217a34afadc5a105709ac294325ac9e80a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpalert-transact-sql"></a>sp_help_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [ **@alert_name =**] **'***alert_name***'**  
 Имя предупреждения. *alert_name* — **nvarchar(128)**. Если *alert_name* — не указан, возвращаются сведения обо всех предупреждениях.  
  
 [ **@order_by =**] **'***order_by***'**  
 Порядок сортировки, в котором выдаются результаты. *order_by*— **sysname**, значение по умолчанию N '*имя*".  
  
 [ **@alert_id =**] *alert_id*  
 Идентификационный номер предупреждения, о котором запрашиваются сведения. *alert_id*— **int**, значение по умолчанию NULL.  
  
 [  **@category_name =**] **"***категории***"**  
 Категория предупреждения. *Категория* — **sysname**, значение по умолчанию NULL.  
  
 [ **@legacy_format**=] *legacy_format*  
 Указывает, следует ли выдавать результирующий набор в старом формате. *legacy_format* — **бит**, значение по умолчанию **0**. Когда *legacy_format* — **1**, **sp_help_alert** возвращает результирующий набор, возвращенный **sp_help_alert** в Microsoft SQL Server 2000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Когда  **@legacy_format**  — **0**, **sp_help_alert** возвращает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Присвоенный системой уникальный целочисленный идентификатор.|  
|**name**|**sysname**|Имя предупреждения (например, Демонстрация: полный **msdb** журнала).|  
|**event_source**|**nvarchar(100)**|Источник события. Всегда будет иметь **MSSQLServer** для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Код ошибки сообщения, который определен для предупреждения (Обычно соответствует номеру ошибки в **sysmessages** таблицы). Если уровень важности используется для определения предупреждения, **message_id** — **0** или иметь значение NULL.|  
|**severity**|**int**|Уровень серьезности (от **9** через **25**, **110**, **120**, **130**, или **140**) определяющий оповещение.|  
|**включен**|**tinyint**|Состояние ли в настоящее время включено предупреждение (**1**) или нет (**0**). Отправка отключенных предупреждений не производится.|  
|**delay_between_responses**|**int**|Время ожидания (в секундах) между ответами на предупреждение.|  
|**last_occurrence_date**|**int**|Дата последнего возникновения предупреждения.|  
|**last_occurrence_time**|**int**|Время последнего возникновения предупреждения.|  
|**last_response_date**|**int**|Дата последнего предупреждения ответа от **SQLServerAgent** службы.|  
|**last_response_time**|**int**|Время последнего предупреждения ответа от **SQLServerAgent** службы.|  
|**notification_message**|**nvarchar(512)**|Необязательное дополнительное сообщение, отправляемое оператору по электронной почте или на пейджер.|  
|**include_event_description**|**tinyint**|Указывает, следует ли включить в текст уведомления описание ошибки SQL Server из журнала приложений Microsoft Windows.|  
|**database_name**|**sysname**|База данных, ошибка в которой приводит к появлению предупреждения. Если имя базы данных равно значению NULL, предупреждение появляется независимо от места возникновения ошибки.|  
|**event_description_keyword**|**nvarchar(100)**|Описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в журнале приложений Windows, которое должно соответствовать указанной последовательности символов.|  
|**occurrence_count**|**int**|Количество раз возникновения предупреждения.|  
|**count_reset_date**|**int**|Дата **occurrence_count** последнего сброса.|  
|**count_reset_time**|**int**|Время **occurrence_count** последнего сброса.|  
|**job_id**|**uniqueidentifier**|Идентификационный номер задания, выполняющегося при срабатывании данного предупреждения.|  
|**job_name**|**sysname**|Имя задания, выполняющегося при срабатывании данного предупреждения.|  
|**has_notification**|**int**|Ненулевое значение, если один или более операторов уведомлены данным предупреждением. Результат логической операции OR одного или нескольких следующих значений:<br /><br /> **1**= уведомлен по электронной почте<br /><br /> **2**= уведомлен по пейджеру<br /><br /> **4**= имеет **net send** уведомления.|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performance_condition**|**nvarchar(512)**|Если **тип** — **2**, этом столбце содержится определение условий производительности; в противном случае столбец содержит значение NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Всегда будет «[без категорий]» для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.|  
|**wmi_namespace**|**sysname**|Если **тип** — **3**, в этом столбце указывается пространство имен WMI-события.|  
|**wmi_query**|**nvarchar(512)**|Если **тип** — **3**, в этом столбце отображается запрос WMI-события.|  
|**type**|**int**|Тип события:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предупреждение о событии<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оповещение о производительности<br /><br /> **3** = предупреждение о событии WMI|  
  
 Когда  **@legacy_format**  — **1**, **sp_help_alert** возвращает следующий результирующий набор.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Присвоенный системой уникальный целочисленный идентификатор.|  
|**name**|**sysname**|Имя предупреждения (например, Демонстрация: полный **msdb** журнала).|  
|**event_source**|**nvarchar(100)**|Источник события. Всегда будет иметь **MSSQLServer** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Код ошибки сообщения, который определен для предупреждения (Обычно соответствует номеру ошибки в **sysmessages** таблицы). Если уровень важности используется для определения предупреждения, **message_id** — **0** или иметь значение NULL.|  
|**severity**|**int**|Уровень серьезности (от **9** через **25**, **110**, **120**, **130**, или 1**40**) определяющий оповещение.|  
|**включен**|**tinyint**|Состояние ли в настоящее время включено предупреждение (**1**) или нет (**0**). Отправка отключенных предупреждений не производится.|  
|**delay_between_responses**|**int**|Время ожидания (в секундах) между ответами на предупреждение.|  
|**last_occurrence_date**|**int**|Дата последнего возникновения предупреждения.|  
|**last_occurrence_time**|**int**|Время последнего возникновения предупреждения.|  
|**last_response_date**|**int**|Дата последнего предупреждения ответа от **SQLServerAgent** службы.|  
|**last_response_time**|**int**|Время последнего предупреждения ответа от **SQLServerAgent** службы.|  
|**notification_message**|**nvarchar(512)**|Необязательное дополнительное сообщение, отправляемое оператору по электронной почте или на пейджер.|  
|**include_event_description**|**tinyint**|Указывает, следует ли включить в текст сообщения уведомления описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из журнала приложений Windows.|  
|**database_name**|**sysname**|База данных, ошибка в которой приводит к появлению предупреждения. Если имя базы данных равно значению NULL, предупреждение появляется независимо от места возникновения ошибки.|  
|**event_description_keyword**|**nvarchar(100)**|Описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в журнале приложений Windows, которое должно соответствовать указанной последовательности символов.|  
|**occurrence_count**|**int**|Количество раз возникновения предупреждения.|  
|**count_reset_date**|**int**|Дата **occurrence_count** последнего сброса.|  
|**count_reset_time**|**int**|Время **occurrence_count** последнего сброса.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**job_name**|**sysname**|Задание по требованию, выполняющееся в ответ на данное предупреждение.|  
|**has_notification**|**int**|Ненулевое значение, если один или более операторов уведомлены данным предупреждением. Значение является результатом логической операции OR над одним или несколькими следующими значениями:<br /><br /> **1**= уведомлен по электронной почте<br /><br /> **2**= уведомлен по пейджеру<br /><br /> **4**= имеет **net send** уведомления.|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)].|  
|**performance_condition**|**nvarchar(512)**|Если **тип** — **2**, в этом столбце указывается определение условия производительности. Если **тип** — **3**, в этом столбце отображается запрос WMI-события. В противном случае столбец содержит значение NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Всегда будет "**[Некатегоризированные]**" для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.|  
|**type**|**int**|Тип предупреждения:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предупреждение о событии<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оповещение о производительности<br /><br /> **3** = предупреждение о событии WMI|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_alert** должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена предопределенная роль базы данных **SQLAgentOperatorRole** в базе данных **msdb** .  
  
 Дополнительные сведения о **SQLAgentOperatorRole**, в разделе [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Примеры  
 В следующем примере выдаются сведения о предупреждении `Demo: Sev. 25 Errors`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [Хранимая процедура sp_update_alert &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
