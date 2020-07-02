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
ms.openlocfilehash: df0cbdda40b8e473ce81bf95b7c38e1cd2ec75c0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783674"
---
# <a name="sysmail_update_account_sp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

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
`[ @account_id = ] account_id`Идентификатор учетной записи для обновления. *account_id* имеет **тип int**и значение по умолчанию NULL. Необходимо указать хотя бы один *account_id* или *account_name* . Если указаны оба аргумента, процедура изменяет имя учетной записи.  
  
`[ @account_name = ] 'account_name'`Имя учетной записи для обновления. Аргумент *account_name* имеет тип **sysname**и значение по умолчанию NULL. Необходимо указать хотя бы один *account_id* или *account_name* . Если указаны оба аргумента, процедура изменяет имя учетной записи.  
  
`[ @email_address = ] 'email_address'`Новый адрес электронной почты, из которого отправляется сообщение. Этот адрес должен быть адресом электронной почты Интернета. Имя сервера в адресе принадлежит серверу, который используется компонентом Database Mail для отправки почты от имени этой учетной записи. *email_address* имеет тип **nvarchar (128)** и значение по умолчанию NULL.  
  
`[ @display_name = ] 'display_name'`Новое отображаемое имя, используемое для сообщений электронной почты из этой учетной записи. *display_name* имеет тип **nvarchar (128)** и не имеет значения по умолчанию.  
  
`[ @replyto_address = ] 'replyto_address'`Новый адрес, который будет использоваться в заголовке ответа для сообщений электронной почты из этой учетной записи. *replyto_address* имеет тип **nvarchar (128)** и не имеет значения по умолчанию.  
  
`[ @description = ] 'description'`Новое описание учетной записи. *Description* имеет тип **nvarchar (256)** и значение по умолчанию NULL.  
  
`[ @mailserver_name = ] 'server_name'`Новое имя почтового SMTP-сервера, который будет использоваться для этой учетной записи. Компьютер, на котором выполняется, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность разрешить *server_name* IP-адресу. Аргумент *server_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @mailserver_type = ] 'server_type'`Новый тип почтового сервера. Аргумент *server_type* имеет тип **sysname**и не имеет значения по умолчанию. Поддерживается только значение **"SMTP"** .  
  
`[ @port = ] port_number`Новый номер порта почтового сервера. *port_number* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @timeout = ] 'timeout'`Параметр timeout для SmtpClient. Send одного сообщения электронной почты. *Время ожидания* равно **int** в секундах и не имеет значения по умолчанию.  
  
`[ @username = ] 'username'`Новое имя пользователя, используемое для входа на почтовый сервер. *Имя пользователя* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @password = ] 'password'`Новый пароль, используемый для входа на почтовый сервер. Аргумент *Password* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @use_default_credentials = ] use_default_credentials`Указывает, следует ли отправлять почту на SMTP-сервер, используя учетные данные [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] службы. **use_default_credentials** имеет бит и не имеет значения по умолчанию. Если этот аргумент равен 1, компонент Database Mail использует учетные данные компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Если этот параметр равен 0, Database Mail использует ** \@ имя пользователя** и ** \@ пароль** для проверки подлинности на SMTP-сервере. Если ** \@ имя пользователя** и ** \@ пароль** имеют значение null, будет использоваться анонимная проверка подлинности. Перед указанием этого аргумента следует проконсультироваться с администратором SMTP  
  
`[ @enable_ssl = ] enable_ssl`Указывает, будет ли Database Mail шифровать связь с помощью протокола TLS, который ранее назывался SSL (SSL). Используйте этот параметр, если на SMTP-сервере требуется TLS. **enable_ssl** имеет бит и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Если указаны имя учетной записи и идентификатор учетной записи, то хранимая процедура изменяет имя учетной записи наряду с изменением данных учетной записи. Изменение имени учетной записи может быть полезно для исправления ошибок в имени учетной записи.  
  
 Хранимая процедура **sysmail_update_account_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-information-for-an-account"></a>A. Изменение данных учетной записи  
 В следующем примере выполняется обновление учетной записи `AdventureWorks Administrator` в базе данных **msdb** . Данные для учетной записи устанавливается в соответствии с предоставленными значениями.  
  
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
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
