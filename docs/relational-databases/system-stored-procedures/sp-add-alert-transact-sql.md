---
title: sp_add_alert (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_alert
- sp_add_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_alert
ms.assetid: d9b41853-e22d-4813-a79f-57efb4511f09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 848f3cffb3c05f16b339233c89892396b5443e4f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "71174259"
---
# <a name="sp_add_alert-transact-sql"></a>sp_add_alert (Transact-SQL)
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
`[ @name = ] 'name'`Имя предупреждения. Имя появляется в сообщении электронной почты или пейджера, отправленном в ответ на предупреждение. Он должен быть уникальным и может содержать символ процента (**%**). Аргумент *Name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @message_id = ] message_id`Номер ошибки сообщения, определяющего оповещение. (Обычно это соответствует номеру ошибки в таблице **sysmessages** .) *message_id* имеет **тип int**и значение по умолчанию **0**. Если для определения предупреждения используется *серьезность* , *message_id* должны быть равны **0** или null.  
  
> [!NOTE]  
>  Отправка предупреждений может быть вызвана только ошибками **sysmessages** , записанными в журнал приложений Microsoft Windows.  
  
`[ @severity = ] severity`Степень серьезности (от **1** до **25**), определяющая предупреждение. Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщения, хранящиеся в таблице **sysmessages** , отправленной в журнал приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows с указанной степенью серьезности, приводят к отправке оповещения. *уровень серьезности* — **int**и значение по умолчанию 0. Если для определения предупреждения используется *message_id* , *уровень серьезности* должен быть **равен 0**.  
  
`[ @enabled = ] enabled`Указывает текущее состояние предупреждения. *Enabled* имеет тип **tinyint**и значение по умолчанию 1 (включено). Если значение **равно 0**, предупреждение не включено и не срабатывает.  
  
`[ @delay_between_responses = ] delay_between_responses`Период ожидания в секундах между ответами на предупреждение. *delay_between_responses*имеет **тип int**и значение по умолчанию **0**, что означает отсутствие ожидания между ответами (каждое вхождение предупреждения создает ответ). Отклик может иметь одну из следующих форм либо обе формы.  
  
-   Одно или несколько уведомлений отправлено через электронную почту или пейджер.  
  
-   Задание к выполнению.  
  
 Установкой этого значения можно предотвратить, например отправку нежелательных почтовых сообщений, если предупреждение возникает многократно за короткий промежуток времени.  
  
`[ @notification_message = ] 'notification_message'`Необязательное дополнительное сообщение, отправляемое оператору как часть уведомления электронной почты, **команды net send**или пейджера. *notification_message* имеет тип **nvarchar (512)** и значение по умолчанию NULL. Указание *notification_message* полезно для добавления специальных примечаний, таких как процедуры по восдобавлению носителей.  
  
`[ @include_event_description_in = ] include_event_description_in`Указывает, следует ли включать описание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ошибки как часть сообщения уведомления. *include_event_description_in*имеет тип **tinyint**, значение по умолчанию — **5** (электронная почта и **net send**) и может иметь одно или несколько из этих значений в сочетании с логическим оператором **or** .  
  
> [!IMPORTANT]
>  Параметры пейджера и **команды net send** будут удалены из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
|Значение|Description|  
|-----------|-----------------|  
|**0**|None|  
|**1**|электронная почта;|  
|**2**|Пейджер|  
|**4**|**NET SEND**|  
  
`[ @database_name = ] 'database'`База данных, в которой должна произойти ошибка для срабатывания предупреждения. Если *база данных*не указана, предупреждение срабатывает независимо от того, где произошла ошибка. *база данных* имеет тип **sysname**. Символы, заключенные в квадратные скобки ([ ]), являются недопустимыми. Значение по умолчанию — NULL.  
  
`[ @event_description_keyword = ] 'event_description_keyword_pattern'`Последовательность символов, которая должна быть похожа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] описание ошибки. Могут использоваться символы-шаблоны выражений [!INCLUDE[tsql](../../includes/tsql-md.md)] LIKE. *event_description_keyword_pattern* имеет тип **nvarchar (100)** и значение по умолчанию NULL. Этот параметр полезен для фильтрации имен объектов (например, **% customer_table%**).  
  
`[ @job_id = ] job_id`Идентификационный номер задания, выполняемого в ответ на это предупреждение. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'`Имя задания, которое должно быть выполнено в ответ на это предупреждение. Аргумент *job_name*имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* , но нельзя указать оба значения.  
  
`[ @raise_snmp_trap = ] raise_snmp_trap`Не реализовано [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в версии 7,0. *raise_snmp_trap* имеет тип **tinyint**и значение по умолчанию 0.  
  
`[ @performance_condition = ] 'performance_condition'`— Это значение, выраженное в формате "*итемкомпараторвалуе*". *performance_condition* имеет тип **nvarchar (512)** со ЗНАЧЕНИЕМ по умолчанию NULL и состоит из этих элементов.  
  
|Элемент формата|Description|  
|--------------------|-----------------|  
|*Элемент*|Объект производительности, счетчик производительности или именованный экземпляр счетчика.|  
|*Сравнения*|Один из следующих операторов: >, < или =|  
|*Value*|Числовое значение счетчика|  
  
`[ @category_name = ] 'category'`Имя категории оповещений. *Category* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @wmi_namespace = ] 'wmi_namespace'`Пространство имен WMI для запроса событий. Аргумент *wmi_namespace* имеет тип **sysname**и значение по умолчанию NULL. Поддерживаются только пространства имен на локальном сервере.  
  
`[ @wmi_query = ] 'wmi_query'`Запрос, указывающий событие WMI для предупреждения. *wmi_query* имеет тип **nvarchar (512)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_add_alert** должны запускаться из базы данных **msdb** .  
  
 Это обстоятельства, при которых ошибки или сообщения, сформированные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], передаются в журнал приложений Windows и, следовательно, могут вызвать следующие предупреждения.  
  
-   Ошибки с уровнем серьезности 19 и выше **sys. messages**  
  
-   Любая инструкция RAISERROR, выполненная с синтаксисом WITH LOG.  
  
-   Все ошибки **sys. messages** , измененные или созданные с помощью **sp_altermessage**  
  
-   Любое событие, регистрируемое с помощью **xp_logevent**  
  
 
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает простой графический способ управления всей системой предупреждений и рекомендуется для настройки инфраструктуры предупреждений.  
  
 Если предупреждение функционирует неправильно, проверьте:  
  
-   работает ли служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   появилось ли событие в журнале приложений Windows;  
  
-   включено ли предупреждение.  
  
-   События, сформированные посредством процедуры **xp_logevent** , появляются в базе данных master. Поэтому **xp_logevent** не вызывает срабатывание предупреждения, если только значение аргумента **\@database_name** для предупреждения не равно **'master'** или NULL.  
  
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
  
## <a name="see-also"></a>См. также:  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_delete_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [sys. sysperfinfo &#40;&#41;Transact-SQL](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
