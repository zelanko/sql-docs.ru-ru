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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a4cfa0178b04a53c3d5ea8419d063d636507a39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019930"
---
# <a name="sysmaildeletelogsp-transact-sql"></a>sysmail_delete_log_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет события из журнала компонента Database Mail. Удаляются либо все события, либо только события, удовлетворяющие критериям даты или типа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_delete_log_sp  [ [ @logged_before = ] 'logged_before' ]  
    [, [ @event_type = ] 'event_type' ]  
  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @logged_before = ] 'logged_before'` Удаляет записи до даты и времени, заданного параметром *logged_before* аргумент. *logged_before* — **datetime** и значение по умолчанию NULL. Значение NULL соответствует всем датам.  
  
`[ @event_type = ] 'event_type'` Удаляет журнальные записи определенного типа, заданного аргументом *event_type*. *event_type* — **varchar(15)** не имеет значения по умолчанию. Допустимыми значениями являются **успех**, **предупреждение**, **ошибка**, и **Информационное**. NULL соответствует всем типам событий.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Используйте **sysmail_delete_log_sp** хранимую процедуру, чтобы окончательно удалить записи из журнала компонента Database Mail. Необязательный аргумент позволяет удалять записи определенной давности. Из этого следует, что удаляются события, созданные ранее даты, заданной в аргументе. Необязательный аргумент позволяет удалять только события определенного типа, заданный как **event_type** аргумент.  
  
 При удалении записей из журнала компонента Database Mail записи электронной почты не удаляются из таблиц Database Mail. Используйте [sysmail_delete_mailitems_sp](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md) для удаления электронной почты из таблиц компонента Database Mail.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера можно получить доступ к этой процедуре.  
  
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
 [Создание задания агента SQL Server по архивации сообщений и журналов событий компонента Database Mail](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
