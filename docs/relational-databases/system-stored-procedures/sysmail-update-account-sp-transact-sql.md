---
title: sysmail_update_account_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_account_sp
- sysmail_update_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_account_sp
ms.assetid: ba2fdccc-5ed4-40ef-a479-79497b4d61aa
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 09af9a0190b8ba3b01c72cfa29e0647ad6d6b74d
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528436"
---
# <a name="sysmailupdateaccountsp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет данные в существующей учетной записи компонента Database Mail.  
 
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_update_account_sp [ [ @account_id = ] account_id ] [ , ] [ [ @account_name = ] 'account_name' ] ,  
    [ @email_address = ] 'email_address' ,   
    [ @display_name = ] 'display_name' ,   
    [ @replyto_address = ] 'replyto_address' ,  
    [ @description = ] 'description' ,   
    [ @mailserver_name = ] 'server_name' ,   
    [ @mailserver_type = ] 'server_type' ,   
    [ @port = ] port_number ,   
    [ @timeout = ] 'timeout' ,  
    [ @username = ] 'username' ,  
    [ @password = ] 'password' ,  
    [ @use_default_credentials = ] use_default_credentials ,  
    [ @enable_ssl = ] enable_ssl   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @account_id = ] account_id` Идентификатор учетной записи должен быть обновлен. *account_id* — **int**, значение по умолчанию NULL. Хотя бы один из *account_id* или *account_name* должен быть указан. Если указаны оба аргумента, процедура изменяет имя учетной записи.  
  
`[ @account_name = ] 'account_name'` Имя учетной записи для обновления. *account_name* — **sysname**, значение по умолчанию NULL. Хотя бы один из *account_id* или *account_name* должен быть указан. Если указаны оба аргумента, процедура изменяет имя учетной записи.  
  
`[ @email_address = ] 'email_address'` Новый адрес электронной почты для отправки сообщений. Этот адрес должен быть адресом электронной почты Интернета. Имя сервера в адресе принадлежит серверу, который используется компонентом Database Mail для отправки почты от имени этой учетной записи. *email_address* — **nvarchar(128)**, значение по умолчанию NULL.  
  
`[ @display_name = ] 'display_name'` Новое отображаемое имя для использования в сообщениях электронной почты с этой учетной записи. *display_name* — **nvarchar(128)**, не имеет значения по умолчанию.  
  
`[ @replyto_address = ] 'replyto_address'` Новый адрес для использования в заголовке ответа для сообщений электронной почты с этой учетной записи. *replyto_address* — **nvarchar(128)**, не имеет значения по умолчанию.  
  
`[ @description = ] 'description'` Новое описание для учетной записи. *Описание* — **nvarchar(256)**, значение по умолчанию NULL.  
  
`[ @mailserver_name = ] 'server_name'` Новое имя почтового SMTP-сервера для этой учетной записи. На компьютере под управлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть способен Разрешить *имя_сервера* IP-адресу. *имя_сервера* — **sysname**, не имеет значения по умолчанию.  
  
`[ @mailserver_type = ] 'server_type'` Новый тип почтового сервера. *server_type* — **sysname**, не имеет значения по умолчанию. Только значение **'SMTP'** поддерживается.  
  
`[ @port = ] port_number` Новый номер порта почтового сервера. *номер_порта* — **int**, не имеет значения по умолчанию.  
  
`[ @timeout = ] 'timeout'` Параметр времени ожидания для SmtpClient.Send при отправке единственного сообщения электронной почты. *Время ожидания* — **int** в секундах, по умолчанию.  
  
`[ @username = ] 'username'` Новое имя пользователя для входа почтовый сервер. *Имя пользователя* — **sysname**, не имеет значения по умолчанию.  
  
`[ @password = ] 'password'` Новый пароль, используемый для входа на почтовый сервер. *пароль* — **sysname**, не имеет значения по умолчанию.  
  
`[ @use_default_credentials = ] use_default_credentials` Указывает, следует ли отправить почту на SMTP-сервер, используя учетные данные [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] службы. **use_default_credentials** имеет тип bit и не имеет значения по умолчанию. Если этот аргумент равен 1, компонент Database Mail использует учетные данные компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Если этот параметр равен 0, компонент Database Mail использует **@username** и **@password** для проверки подлинности на SMTP-сервера. Если **@username** и **@password** имеют значение NULL, то будет использоваться анонимная проверка подлинности. Перед указанием этого аргумента следует проконсультироваться с администратором SMTP  
  
`[ @enable_ssl = ] enable_ssl` Указывает, шифрует ли компонент Database Mail соединение при помощи Secure Sockets Layer (SSL). Используйте этот аргумент, если требуется поддержка протокола SSL для SMTP-сервера. **enable_ssl** имеет тип bit и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если указаны имя учетной записи и идентификатор учетной записи, то хранимая процедура изменяет имя учетной записи наряду с изменением данных учетной записи. Изменение имени учетной записи может быть полезно для исправления ошибок в имени учетной записи.  
  
 Хранимая процедура **sysmail_update_account_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-information-for-an-account"></a>A. Изменение данных учетной записи  
 В следующем примере обновляется учетная запись `AdventureWorks Administrator` в **msdb** базы данных. Данные для учетной записи устанавливается в соответствии с предоставленными значениями.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_name = 'AdventureWorks Administrator'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
### <a name="b-changing-the-name-of-an-account-and-the-information-for-an-account"></a>Б. Изменение имени учетной записи и ее данных  
 В следующем примере изменяется имя, а также обновляются данные учетной записи с идентификатором `125`. Новое имя учетной записи -`Backup Mail Server`.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_id = 125  
    ,@account_name = 'Backup Mail Server'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp-backup.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
