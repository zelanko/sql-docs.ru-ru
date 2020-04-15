---
title: sysmail_update_account_sp (Трансакт-СЗЛ) Документы Майкрософт
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
ms.openlocfilehash: 3dd772a1519ea856cac0302d31be9eb7d0f9d782
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283230"
---
# <a name="sysmail_update_account_sp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
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
`[ @account_id = ] account_id`Идентификатор учетной записи для обновления. *account_id* **int**, с дефолтом NULL. Необходимо указать по крайней мере один из *account_id* или *account_name.* Если указаны оба аргумента, процедура изменяет имя учетной записи.  
  
`[ @account_name = ] 'account_name'`Название учетной записи для обновления. *account_name* является **sysname**, с дефолтом NULL. Необходимо указать по крайней мере один из *account_id* или *account_name.* Если указаны оба аргумента, процедура изменяет имя учетной записи.  
  
`[ @email_address = ] 'email_address'`Новый адрес электронной почты для отправки сообщения. Этот адрес должен быть адресом электронной почты Интернета. Имя сервера в адресе принадлежит серверу, который используется компонентом Database Mail для отправки почты от имени этой учетной записи. *email_address* **nvarchar (128)**, с дефолтом NULL.  
  
`[ @display_name = ] 'display_name'`Новое имя дисплея для использования в сообщениях электронной почты из этой учетной записи. *display_name* **nvarchar (128)**, без дефолта.  
  
`[ @replyto_address = ] 'replyto_address'`Новый адрес для использования в заголовке reply-To сообщений электронной почты из этой учетной записи. *replyto_address* **nvarchar (128)**, без дефолта.  
  
`[ @description = ] 'description'`Новое описание учетной записи. *описание* **nvarchar (256)**, с дефолтом NULL.  
  
`[ @mailserver_name = ] 'server_name'`Новое название почтового сервера SMTP для использования в этой учетной записи. Компьютер, который [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает, должен быть в состоянии решить *server_name* на IP-адрес. *server_name* **sysname,** без по умолчанию.  
  
`[ @mailserver_type = ] 'server_type'`Новый тип почтового сервера. *server_type* **sysname,** без по умолчанию. Поддерживается только значение **'SMTP'.**  
  
`[ @port = ] port_number`Новый номер порта почтового сервера. *port_number* **int,** без по умолчанию.  
  
`[ @timeout = ] 'timeout'`Параметр тайм-аута для SmtpClient.Send одного сообщения электронной почты. *Тайм-аут* int в **секундах,** без по умолчанию.  
  
`[ @username = ] 'username'`Новое имя пользователя для входа на почтовый сервер. *Имя пользователя* **sysname,** без по умолчанию.  
  
`[ @password = ] 'password'`Новый пароль для входа на почтовый сервер. *пароль* **sysname**, без по умолчанию.  
  
`[ @use_default_credentials = ] use_default_credentials`Уточняется, отправлять ли почту на сервер SMTP с помощью учетных данных [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] службы. **use_default_credentials** бит, без по умолчанию. Если этот аргумент равен 1, компонент Database Mail использует учетные данные компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Когда этот параметр равен 0, Database Mail использует ** \@имя пользователя** и ** \@пароль** для проверки подлинности на сервере SMTP. Если ** \@имя пользователя** и ** \@пароль** являются NULL, то он будет использовать анонимную аутентификацию. Перед указанием этого аргумента следует проконсультироваться с администратором SMTP  
  
`[ @enable_ssl = ] enable_ssl`Уточняется, шифрует ли Database Mail связь с помощью Transport Layer Security (TLS), ранее известного как Безопасный слой розеток (SSL). Используйте эту опцию, если TLS требуется на вашем сервере SMTP. **enable_ssl** бит, без по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успех) или **1** (неудача)  
  
## <a name="remarks"></a>Remarks  
 Если указаны имя учетной записи и идентификатор учетной записи, то хранимая процедура изменяет имя учетной записи наряду с изменением данных учетной записи. Изменение имени учетной записи может быть полезно для исправления ошибок в имени учетной записи.  
  
 Сохраненная процедура **sysmail_update_account_sp** находится в базе данных **msdb** и принадлежит схеме **dbo.** Процедура должна быть выполнена с трехчастей имя, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-information-for-an-account"></a>A. Изменение данных учетной записи  
 Следующий пример обновляет `AdventureWorks Administrator` учетную запись в базе данных **msdb.** Данные для учетной записи устанавливается в соответствии с предоставленными значениями.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Почта базы данных](../../relational-databases/database-mail/database-mail.md)   
 [Создание учетной записи почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Процедуры хранения почты базы данных &#40;&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
