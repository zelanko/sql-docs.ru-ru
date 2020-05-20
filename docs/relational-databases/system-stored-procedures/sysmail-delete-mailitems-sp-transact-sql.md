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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ee0298a714394bdf90009657c3d5b7a4daafebcd
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82814369"
---
# <a name="sysmail_delete_mailitems_sp-transact-sql"></a>sysmail_delete_mailitems_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Окончательно удаляет сообщения электронной почты из внутренних таблиц компонента Database Mail.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_mailitems_sp  [ [ @sent_before = ] 'sent_before' ]  
    [ , [ @sent_status = ] 'sent_status' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ \@sent_before = ] 'sent_before'`Удаляет сообщения электронной почты вплоть до даты и времени, указанных в качестве аргумента *sent_before* . *sent_before* имеет тип **DateTime** со значением NULL по умолчанию. Значение NULL соответствует всем датам.  
  
`[ \@sent_status = ] 'sent_status'`Удаляет сообщения электронной почты типа, указанного *sent_status*. *sent_status* имеет тип **varchar (8)** и не имеет значения по умолчанию. Допустимые записи: **отправлены**, **неотправленные**, **повторные попытки**и **сбой**. Значение NULL соответствует всем состояниям.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Database Mail сообщения и их вложения хранятся в базе данных **msdb** . Сообщения следует периодически удалять, чтобы не допустить роста базы данных **msdb** , чем ожидалось, и в соответствии с программой хранения документов Организации. Используйте **sysmail_delete_mailitems_sp** хранимую процедуру, чтобы окончательно удалить сообщения электронной почты из Database Mail таблиц. Необязательный аргумент позволяет удалить только старые сообщения, указав дату и время. Сообщения, которые старше этого аргумента, будут удалены. Другой необязательный аргумент позволяет удалить только сообщения электронной почты определенного типа, указанные в качестве аргумента **sent_status** . Аргумент необходимо указать либо для ** \@ sent_before** , либо для ** \@ sent_status**. Чтобы удалить все сообщения, используйте ** \@ sent_before = GETDATE ()**.  
  
 Удаление сообщений электронной почты также удаляет вложения, связанные с этими сообщениями. Удаление электронной почты не приводит к удалению соответствующих записей в **sysmail_event_log**. Для удаления элементов из журнала используйте [sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эта хранимая процедура предоставляется для выполнения членам предопределенной роли сервера **sysadmin** и роли **DatabaseMailUserRole**. Члены предопределенной роли сервера **sysadmin** могут выполнять эту процедуру для удаления сообщений электронной почты, отправленных всеми пользователями. Члены **роли DatabaseMailUserRole** могут удалять только сообщения электронной почты, отправленные этим пользователем.  
  
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
  
  
