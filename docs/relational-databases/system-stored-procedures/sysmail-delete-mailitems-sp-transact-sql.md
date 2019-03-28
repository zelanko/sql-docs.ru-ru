---
title: sysmail_delete_mailitems_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_mailitems_sp_TSQL
- sysmail_delete_mailitems_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_mailitems_sp
ms.assetid: f87c9f4a-bda1-4bce-84b2-a055a3229ecd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a8549d33b000744f4d8430ee306e0083455894c
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531766"
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
`[ @sent_before = ] 'sent_before'` Удаляет сообщения электронной почты до даты и времени, указанных *sent_before* аргумент. *sent_before* — **datetime** и значение по умолчанию NULL. Значение NULL соответствует всем датам.  
  
`[ @sent_status = ] 'sent_status'` Удаляет сообщения электронной почты типа, заданного параметром *sent_status*. *sent_status* — **varchar(8)** не имеет значения по умолчанию. Допустимыми значениями являются **отправленных**, **неотправленных**, **повторная попытка**, и **сбой**. Значение NULL соответствует всем состояниям.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Сообщения компонента Database Mail и их вложения хранятся в **msdb** базы данных. Сообщения должны периодически удаляться, чтобы предотвратить **msdb** от увеличения размера, чем ожидалось и в соответствии с вашей программы по хранению документов организации. Используйте **sysmail_delete_mailitems_sp** хранимую процедуру, чтобы окончательно удалить сообщения электронной почты из таблиц компонента Database Mail. Необязательный аргумент позволяет удалить только старые сообщения, указав дату и время. Сообщения, которые старше этого аргумента, будут удалены. Еще один необязательный аргумент позволяет удалить только сообщения определенного типа, заданный как **sent_status** аргумент. Необходимо указать аргумент для **@sent_before** или **@sent_status**. Чтобы удалить все сообщения, используйте  **@sent_before = getdate()**.  
  
 Удаление сообщений электронной почты также удаляет вложения, связанные с этими сообщениями. Удаление сообщений не удаляет соответствующие записи из **sysmail_event_log**. Используйте [sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md) для удаления элементов из журнала.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию, эта хранимая процедура предоставляется для выполнения членам **sysadmin** предопределенной роли сервера и **DatabaseMailUserRole**. Членами **sysadmin** предопределенной роли сервера могут выполнять эту процедуру для удаления сообщений электронной почты, посланных всеми пользователями. Членами **DatabaseMailUserRole** можно удалить только сообщениях, отправленных пользователем.  
  
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
 [Создание задания агента SQL Server по архивации сообщений и журналов событий компонента Database Mail](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
