---
title: sp_notify_operator (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
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
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: db32f3bf2f6c70bb300852c5f1b994e0896c8c6b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
> **Примечание:** адрес электронной почты должен быть определен для оператора, прежде чем они смогут получать сообщения.  
  
 [  **@subject=** ] **"***субъекта***"**  
 Тема сообщения электронной почты. *Тема* — **nvarchar(256)** без значения по умолчанию.  
  
 [  **@body=** ] **"***сообщение***"**  
 Текст сообщения электронной почты. *сообщение* — **nvarchar(max)** без значения по умолчанию.  
  
 [  **@file_attachments=** ] **"***вложения***"**  
 Имя файла, прилагаемого к сообщению электронной почты. *вложение* — **nvarchar(512)**, не имеет значения по умолчанию.  
  
 [  **@mail_database=** ] **"***mail_host_database***"**  
 Указывает имя базы данных обслуживания почты. *mail_host_database* — **nvarchar(128)**. Если не *mail_host_database* указано, **msdb** базы данных используется по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Отправляет данное сообщение на адрес электронной почты указанного оператора. Если оператор не имеет настроенного адреса электронной почты, возвращается ошибка.  
  
 Компонент Database Mail и базы данных обслуживания почты должны быть сконфигурированы до отправки уведомления оператору.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Хранимая процедура sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
