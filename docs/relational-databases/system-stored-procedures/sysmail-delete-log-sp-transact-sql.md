---
title: sysmail_delete_log_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_log_sp_TSQL
- sysmail_delete_log_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_log_sp
ms.assetid: e94b37a1-70ad-46a5-86c0-721892156f7c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db6f15fe8ce2f515bf79211e6db49a135eb6fb3f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890972"
---
# <a name="sysmail_delete_log_sp-transact-sql"></a>sysmail_delete_log_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет события из журнала компонента Database Mail. Удаляются либо все события, либо только события, удовлетворяющие критериям даты или типа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_log_sp  [ [ @logged_before = ] 'logged_before' ]  
    [, [ @event_type = ] 'event_type' ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @logged_before = ] 'logged_before'`Удаляет записи вплоть до даты и времени, указанных аргументом *logged_before* . *logged_before* имеет тип **DateTime** со значением NULL по умолчанию. Значение NULL соответствует всем датам.  
  
`[ @event_type = ] 'event_type'`Удаляет записи журнала типа, указанного в качестве *event_type*. *event_type* имеет тип **varchar (15)** и не имеет значения по умолчанию. Допустимые записи: **Success**, **warning**, **Error**и **информационный**. NULL соответствует всем типам событий.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 Для окончательного удаления записей из журнала Database Mail используйте хранимую процедуру **sysmail_delete_log_sp** . Необязательный аргумент позволяет удалять записи определенной давности. Из этого следует, что удаляются события, созданные ранее даты, заданной в аргументе. Необязательный аргумент позволяет удалять только события определенного типа, указанные в качестве аргумента **event_type** .  
  
 При удалении записей из журнала компонента Database Mail записи электронной почты не удаляются из таблиц Database Mail. Используйте [sysmail_delete_mailitems_sp](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md) , чтобы удалить электронную почту из Database Mail таблиц.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут обращаться к этой процедуре.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-deleting-all-events"></a>A. Удаление всех событий  
 В следующем примере из журнала компонента Database Mail удаляются все события.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp ;  
GO  
```  
  
### <a name="b-deleting-the-oldest-events"></a>Б. Удаление самых старых событий  
 В следующем примере из журнала компонента Database Mail удаляются события, созданные до 9 октября 2005 года.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @logged_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-events-of-a-certain-type"></a>В. Удаление всех событий определенного типа  
 В следующем примере из журнала компонента Database Mail удаляются все сообщения «success».  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @event_type = 'success' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sysmail_event_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)   
 [Создание задания агента SQL Server по архивации сообщений компонента Database Mail и журналов событий базы данных](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
