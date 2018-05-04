---
title: sp_add_alert (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_alert
- sp_add_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_alert
ms.assetid: d9b41853-e22d-4813-a79f-57efb4511f09
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d4cbc7acfb07c28a8380be87ac7010be92274e7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spaddalert-transact-sql"></a>sp_add_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает предупреждение.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_alert [ @name = ] 'name'   
     [ , [ @message_id = ] message_id ]   
     [ , [ @severity = ] severity ]   
     [ , [ @enabled = ] enabled ]  
     [ , [ @delay_between_responses = ] delay_between_responses ]   
     [ , [ @notification_message = ] 'notification_message' ]   
     [ , [ @include_event_description_in = ] include_event_description_in ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @event_description_keyword = ] 'event_description_keyword_pattern' ]   
     [ , { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ]   
     [ , [ @raise_snmp_trap = ] raise_snmp_trap ]   
     [ , [ @performance_condition = ] 'performance_condition' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@name =** ] **"***имя***"**  
 Имя предупреждения. Имя появляется в сообщении электронной почты или пейджера, отправленном в ответ на предупреждение. Оно должно быть уникальным и может содержать символа процента (**%**) символов. *имя* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@message_id =** ] *message_id*  
 Номер сообщения об ошибке, которое определяет предупреждение. (Обычно соответствует номеру ошибки в **sysmessages** таблицы.) *message_id* — **int**, значение по умолчанию **0**. Если *серьезность* используется для определения предупреждения, *message_id* должно быть **0** или иметь значение NULL.  
  
> [!NOTE]  
>  Только **sysmessages** ошибки записываются в журнал приложений Microsoft Windows может вызвать отправку предупреждения.  
  
 [  **@severity =** ] *серьезности*  
 Уровень серьезности (от **1** через **25**), определяемый предупреждением. Любой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщение, находящееся в **sysmessages** таблицы отправляется [!INCLUDE[msCoName](../../includes/msconame-md.md)] в журнале приложений Windows с указанной степенью серьезности вызывает отправку предупреждения. *Серьезность* — **int**, значение по умолчанию 0. Если *message_id* используется для определения предупреждения, *серьезность* должно быть **0**.  
  
 [  **@enabled =** ] *включена*  
 Показывает текущее состояние предупреждения. *включить* — **tinyint**, значение по умолчанию 1 (включено). Если **0**, предупреждение не включено и не срабатывает.  
  
 [  **@delay_between_responses =** ] *delay_between_responses*  
 Период ожидания (в секундах) между откликами на предупреждение. *delay_between_responses*— **int**, значение по умолчанию **0**, что означает, что нет времени ожидания между ответами (каждое вхождение предупреждения формирует отклик). Отклик может иметь одну из следующих форм либо обе формы.  
  
-   Одно или несколько уведомлений отправлено через электронную почту или пейджер.  
  
-   Задание к выполнению.  
  
 Установкой этого значения можно предотвратить, например отправку нежелательных почтовых сообщений, если предупреждение возникает многократно за короткий промежуток времени.  
  
 [  **@notification_message =** ] **"***notification_message***"**  
 Необязательное дополнительное сообщение, отправляемое оператору как часть сообщения электронной почты, **net send**, или на пейджер. *notification_message* — **nvarchar(512)**, значение по умолчанию NULL. Указание *notification_message* можно использовать для добавления специальных комментариев, таких как корректирующие процедуры.  
  
 [  **@include_event_description_in =** ] *include_event_description_in*  
 Указывает, следует ли включить в текст сообщения уведомления с описанием ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *include_event_description_in*— **tinyint**, значение по умолчанию **5** (электронной почты и **net send**) и может иметь одно или несколько из следующих значений, соединенных **Или** логический оператор.  
  
> [!IMPORTANT]  
>  Режимы отправки уведомлений с помощью пейджера и команды **net send** будут удалены из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Нет|  
|**1**|электронная почта;
|  
|**2**|Пейджер|  
|**4**|**команда net send.**|  
  
 [  **@database_name =** ] **"***базы данных***"**  
 База данных, в которой должна произойти ошибка, для которой срабатывает предупреждение. Если *базы данных*не указан, предупреждение срабатывает независимо от того, где произошла ошибка. *База данных* — **sysname**. Символы, заключенные в квадратные скобки ([ ]), являются недопустимыми. Значение по умолчанию — NULL.  
  
 [ **@event_description_keyword =** ] **'***event_description_keyword_pattern***'**  
 Последовательность символов, которой должно соответствовать описание ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Могут использоваться символы-шаблоны выражений [!INCLUDE[tsql](../../includes/tsql-md.md)] LIKE. *event_description_keyword_pattern* — **nvarchar(100)**, значение по умолчанию NULL. Этот параметр полезен для фильтрации имен объектов (например, **% customer_table %**).  
  
 [  **@job_id =** ] *job_id*  
 Идентификатор задания, которое запускается в ответ на это предупреждение. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name =** ] **"***job_name***"**  
 Имя задания, которое запускается в ответ на это предупреждение. *job_name*— **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@raise_snmp_trap =** ] *raise_snmp_trap*  
 Не реализовано в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 7.0. *raise_snmp_trap* — **tinyint**, значение по умолчанию 0.  
  
 [  **@performance_condition =** ] **"***performance_condition***"**  
 Значение, выраженное в формате "*itemcomparatorvalue*". *performance_condition* — **nvarchar(512)** значение по умолчанию NULL и состоит из следующих элементов.  
  
|Элемент формата|Описание|  
|--------------------|-----------------|  
|*Элемент*|Объект производительности, счетчик производительности или именованный экземпляр счетчика.|  
|*Оператор сравнения*|Один из этих операторов: >, <, или =|  
|*Value*|Числовое значение счетчика|  
  
 [  **@category_name =** ] **"***категории***"**  
 Имя категории предупреждения. *Категория* — **sysname**, значение по умолчанию NULL.  
  
 [ **@wmi_namespace**=] **"***wmi_namespace***"**  
 Пространство имен WMI для запроса событий. *wmi_namespace* — **sysname**, значение по умолчанию NULL. Поддерживаются только пространства имен на локальном сервере.  
  
 [ **@wmi_query**=] **"***wmi_query***"**  
 Запрос, указывающий событие WMI для предупреждения. *wmi_query* — **nvarchar(512)**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_add_alert** должна запускаться из **msdb** базы данных.  
  
 Это обстоятельства, при которых ошибки или сообщения, сформированные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], передаются в журнал приложений Windows и, следовательно, могут вызвать следующие предупреждения.  
  
-   Серьезности 19 и выше **sys.messages** ошибок  
  
-   Любая инструкция RAISERROR, выполненная с синтаксисом WITH LOG.  
  
-   Любой **sys.messages** ошибки изменен или создан с помощью **sp_altermessage**  
  
-   Любое событие, регистрируются с использованием **xp_logevent**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает простой графический способ управления всей системой предупреждений и рекомендуется для настройки инфраструктуры предупреждений.  
  
 Если предупреждение функционирует неправильно, проверьте:  
  
-   работает ли служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   появилось ли событие в журнале приложений Windows;  
  
-   включено ли предупреждение.  
  
-   События, сформированные посредством процедуры **xp_logevent** , появляются в базе данных master. Поэтому **xp_logevent** не вызывает срабатывание предупреждения, если только значение аргумента **@database_name** для предупреждения не равно **'master'** или NULL.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию только члены предопределенной роли сервера **sysadmin** могут выполнять процедуру **sp_add_alert**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример добавляет предупреждение (Test Alert), которое запускает задание `Back up the AdventureWorks2012 Database` при срабатывании.  
  
> [!NOTE]  
>  Этот пример предполагает, что сообщение 55001 и задание `Back up the AdventureWorks2012 Database` уже существуют. Пример приводится только в целях наглядности.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_alert  
    @name = N'Test Alert',  
    @message_id = 55001,   
   @severity = 0,   
   @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
   @job_name = N'Back up the AdventureWorks2012 Database' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_delete_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [Хранимая процедура sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
