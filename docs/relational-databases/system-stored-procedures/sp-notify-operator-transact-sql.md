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
ms.openlocfilehash: 74558320df59414a756e1655bb073e9bf0d7d73c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107978"
---
# <a name="sp_notify_operator-transact-sql"></a>sp_notify_operator (Transact-SQL)
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
`[ @profile_name = ] 'profilename'`Имя профиля Database Mail, используемого для отправки сообщения. *filename* имеет тип **nvarchar (128)**. Если параметр *filename* не указан, используется профиль Database Mail по умолчанию.  
  
`[ @id = ] id`Идентификатор оператора, которому отправляется сообщение. *ID* имеет **тип int**и значение по умолчанию NULL. Необходимо указать один из *идентификаторов* или *имя* .  
  
`[ @name = ] 'name'`Имя оператора, которому отправляется сообщение. *имя* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Необходимо указать один из *идентификаторов* или *имя* .  
  
> **Примечание.** Перед получением сообщений необходимо определить адрес электронной почты оператора.  
  
`[ @subject = ] 'subject'`Тема сообщения электронной почты. *subject* имеет тип **nvarchar (256)** и не имеет значения по умолчанию.  
  
`[ @body = ] 'message'`Текст сообщения электронной почты. *Message* имеет тип **nvarchar (max)** и не имеет значения по умолчанию.  
  
`[ @file_attachments = ] 'attachment'`Имя файла, который необходимо присоединить к сообщению электронной почты. *вложение* имеет тип **nvarchar (512)** и не имеет значения по умолчанию.  
  
`[ @mail_database = ] 'mail_host_database'`Указывает имя базы данных обслуживания почты. *mail_host_database* имеет тип **nvarchar (128)**. Если *mail_host_database* не указано, по умолчанию используется база данных **msdb** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Отправляет данное сообщение на адрес электронной почты указанного оператора. Если оператор не имеет настроенного адреса электронной почты, возвращается ошибка.  
  
 Компонент Database Mail и базы данных обслуживания почты должны быть сконфигурированы до отправки уведомления оператору.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эта хранимая процедура может выполняться членами предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Агент SQL Server хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
