---
title: sp_notify_operator (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4d45252f16703cb52a3e78c1b236dd9d4cbfbde4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846402"
---
# <a name="spnotifyoperator-transact-sql"></a>sp_notify_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отправляет оператору сообщения по электронной почте с помощью компонента Database Mail.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@profile_name=** ] **"***profilename***"**  
 Имя профиля Database Mail, используемого для отправки сообщения. *ProfileName* — **nvarchar(128)**. Если *profilename* не указан, используется профиль компонента Database Mail по умолчанию.  
  
 [ **@id=** ] *id*  
 Идентификатор оператора, которому отправляется сообщение. *Идентификатор* — **int**, значение по умолчанию NULL. Один из *идентификатор* или *имя* должен быть указан.  
  
 [  **@name=** ] **"***имя***"**  
 Имя оператора, которому отправляется сообщение. *имя* — **nvarchar(128)**, значение по умолчанию NULL. Один из *идентификатор* или *имя* должен быть указан.  
  
> **Примечание:** адрес электронной почты должны быть определены для оператора, прежде чем они могут получать сообщения.  
  
 [  **@subject=** ] **"***субъекта***"**  
 Тема сообщения электронной почты. *Тема* — **nvarchar(256)** не имеет значения по умолчанию.  
  
 [  **@body=** ] **"***сообщение***"**  
 Текст сообщения электронной почты. *сообщение* — **nvarchar(max)** не имеет значения по умолчанию.  
  
 [  **@file_attachments=** ] **"***вложения***"**  
 Имя файла, прилагаемого к сообщению электронной почты. *вложение* — **nvarchar(512)**, не имеет значения по умолчанию.  
  
 [  **@mail_database=** ] **"***mail_host_database***"**  
 Указывает имя базы данных обслуживания почты. *mail_host_database* — **nvarchar(128)**. Если не *mail_host_database* указано, **msdb** база данных используется по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Отправляет данное сообщение на адрес электронной почты указанного оператора. Если оператор не имеет настроенного адреса электронной почты, возвращается ошибка.  
  
 Компонент Database Mail и базы данных обслуживания почты должны быть сконфигурированы до отправки уведомления оператору.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере уведомление по электронной почте отправляется оператору `François Ajenstat` с помощью профиля компонента `AdventureWorks Administrator` Database Mail. Тема сообщения электронной почты: `Test Notification`. Сообщение электронной почты содержит текст «This is a test of notification via e-mail».  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Хранимая процедура sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
