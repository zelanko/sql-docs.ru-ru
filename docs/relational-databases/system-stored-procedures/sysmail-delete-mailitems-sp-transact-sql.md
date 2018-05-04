---
title: sysmail_delete_mailitems_sp (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sysmail_delete_mailitems_sp_TSQL
- sysmail_delete_mailitems_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_mailitems_sp
ms.assetid: f87c9f4a-bda1-4bce-84b2-a055a3229ecd
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 81911e04266abf51f28a8906910290bf3d0179f3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysmaildeletemailitemssp-transact-sql"></a>sysmail_delete_mailitems_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Окончательно удаляет сообщения электронной почты из внутренних таблиц компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_mailitems_sp  [ [ @sent_before = ] 'sent_before' ]  
    [ , [ @sent_status = ] 'sent_status' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@sent_before=** ] **"***sent_before***"**  
 Удаляет сообщения электронной почты до даты и времени, указанных в *sent_before* аргумент. *sent_before* — **datetime** и значение по умолчанию NULL. Значение NULL соответствует всем датам.  
  
 [ **@sent_status=** ] **'***sent_status***'**  
 Удаляет сообщения электронной почты типа, заданного параметром *sent_status*. *sent_status* — **varchar(8)** без значения по умолчанию. Допустимыми значениями являются **отправляемых**, **неотправленные**, **Повтор**, и **сбой**. Значение NULL соответствует всем состояниям.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Сообщения компонента Database Mail и их вложения хранятся в **msdb** базы данных. Сообщения должны периодически удаляться, чтобы предотвратить **msdb** рост больше, чем ожидается, так и в соответствии со своей программой хранения документов организации. Используйте **sysmail_delete_mailitems_sp** хранимую процедуру, чтобы окончательно удалить сообщения электронной почты из таблиц компонента Database Mail. Необязательный аргумент позволяет удалить только старые сообщения, указав дату и время. Сообщения, которые старше этого аргумента, будут удалены. Другие необязательные аргументы можно удалить только сообщения определенного типа, указанный как **sent_status** аргумент. Необходимо указать аргумент для **@sent_before** или **@sent_status**. Чтобы удалить все сообщения, используйте  **@sent_before = getdate()**.  
  
 Удаление сообщений электронной почты также удаляет вложения, связанные с этими сообщениями. Удаление сообщений не удаляет соответствующие записи в **sysmail_event_log**. Используйте [sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md) для удаления элементов из журнала.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эта хранимая процедура предоставляется для выполнения членам **sysadmin** предопределенной роли сервера и **DatabaseMailUserRole**. Члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру для удаления сообщений электронной почты, посланных всеми пользователями. Члены **DatabaseMailUserRole** можно удалить только сообщениях, отправленных этим пользователем.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-deleting-all-e-mails"></a>A. Удаление всех сообщений электронной почты  
 Следующий пример удаляет все сообщения электронной почты в системе компонента Database Mail.  
  
```  
DECLARE @GETDATE datetime  
SET @GETDATE = GETDATE();  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @GETDATE;  
GO  
```  
  
### <a name="b-deleting-the-oldest-e-mails"></a>Б. Удаление самых старых сообщений электронной почты  
 Следующий пример удаляет сообщения электронной почты в журнале компонента Database Mail, принятые раньше `October 9, 2005`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-e-mails-of-a-certain-type"></a>В. Удаление всех сообщений электронной почты указанного типа  
 Следующий пример удаляет все неудачные сообщения электронной почты в журнале компонента Database Mail.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_status = 'failed' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_event_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_mailattachments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md)   
 [Создание задания агента SQL Server по архивации сообщений компонента Database Mail и журналов событий базы данных](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
