---
title: sysmail_add_account_sp (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_account_sp
- sysmail_add_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_account_sp
ms.assetid: 65e15e2e-107c-49c3-b12c-f4edf0eb1617
author: stevestein
ms.author: sstein
ms.openlocfilehash: d382d8ee7a871244213467b7a46bdc5b864c55cb
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381904"
---
# <a name="sysmail_add_account_sp-transact-sql"></a>sysmail_add_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Создает новую учетную запись компонента Database Mail, хранящую сведения об учетной записи SMTP.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_add_account_sp  [ @account_name = ] 'account_name',  
    [ @email_address = ] 'email_address' ,  
    [ [ @display_name = ] 'display_name' , ]  
    [ [ @replyto_address = ] 'replyto_address' , ]  
    [ [ @description = ] 'description' , ]  
    [ @mailserver_name = ] 'server_name'   
    [ , [ @mailserver_type = ] 'server_type' ]  
    [ , [ @port = ] port_number ]  
    [ , [ @username = ] 'username' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @use_default_credentials = ] use_default_credentials ]  
    [ , [ @enable_ssl = ] enable_ssl ]  
    [ , [ @account_id = ] account_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @account_name = ] 'account_name'` имя добавляемой учетной записи. Аргумент *account_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @email_address = ] 'email_address'` адрес электронной почты, с которого отправляется сообщение. Этот адрес должен быть адресом электронной почты Интернета. *email_address* имеет тип **nvarchar (128)** и не имеет значения по умолчанию. Например, учетная запись для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может отправить сообщение электронной почты с адреса "злоумышленник **\@Adventure-Works.com**".  
  
`[ @display_name = ] 'display_name'` отображаемое имя для использования в сообщениях электронной почты от этой учетной записи. *display_name* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Например, учетная запись для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может отображать имя **Агент SQL Server автоматической почты** в сообщениях электронной почты.  
  
`[ @replyto_address = ] 'replyto_address'` адрес, на который отправляются ответы на сообщения от этой учетной записи. *replyto_address* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Например, ответы на учетную запись агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут быть отправлены администратору базы данных **данв\@Adventure-Works.com**.  
  
`[ @description = ] 'description'` — описание учетной записи. *Description* имеет тип **nvarchar (256)** и значение по умолчанию NULL.  
  
`[ @mailserver_name = ] 'server_name'` имя или IP-адрес почтового SMTP-сервера, который будет использоваться для этой учетной записи. Компьютер, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должен иметь возможность разрешить *server_name* IP-адресу. Аргумент *server_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @mailserver_type = ] 'server_type'` тип сервера электронной почты. Аргумент *server_type* имеет тип **sysname**и значение по умолчанию **"SMTP"** .  
  
`[ @port = ] port_number` номер порта для почтового сервера. *port_number* имеет **тип int**и значение по умолчанию 25.  
  
`[ @username = ] 'username'` имя пользователя, используемое для входа на сервер электронной почты. *username* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Если этот параметр установлен в NULL, компонент Database Mail не использует проверку подлинности для этой учетной записи. Если почтовый сервер не требует проверки подлинности, используйте NULL в качестве имени пользователя.  
  
`[ @password = ] 'password'` пароль, используемый для входа на сервер электронной почты. *Password* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Нет необходимости указывать пароль, если не указано имя пользователя.  
  
`[ @use_default_credentials = ] use_default_credentials` указывает, следует ли отправлять почту на SMTP-сервер, используя учетные данные [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** имеет бит и значение по умолчанию 0. Если этот аргумент равен 1, компонент Database Mail использует учетные данные компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Если этот параметр равен 0, Database Mail отправляет **\@имя пользователя** и **\@параметры пароля** , если они есть, в противном случае отправляет сообщение электронной почты без **\@имени пользователя** и **\@параметров пароля** .  
  
`[ @enable_ssl = ] enable_ssl` указывает, шифруется ли Database Mail связь с помощью SSL. **Enable_ssl** имеет бит и значение по умолчанию 0.  
  
`[ @account_id = ] account_id OUTPUT` возвращает идентификатор учетной записи для новой учетной записи. *account_id* имеет **тип int**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Database Mail предоставляет отдельные параметры для **\@email_address**, **\@display_name**и **\@** replyto_address. Параметр **\@email_address** является адресом, из которого отправляется сообщение. Параметр **\@display_name** — это имя, отображаемое в поле **от:** сообщения электронной почты. Параметр **\@replyto_address** — это адрес, куда будут отправляться ответы на сообщение электронной почты. Например, учетная запись, используемая для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], может отправлять сообщения электронной почты с адреса, используемого только агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сообщения с этого адреса должны отображать понятные имена, таким образом получатели могут легко определить, что сообщение отправлено агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если получатель отвечает на сообщение, ответ должен быть доставлен администратору базы данных, а не на адрес агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом сценарии учетная запись использует **SqlAgent@Adventure-Works.com** в качестве адреса электронной почты. Отображаемое имя имеет значение **Агент SQL Server автоматической рассылки**. Учетная запись использует **danw@Adventure-Works.com** в качестве адреса ответа, поэтому ответы на сообщения, отправленные из этой учетной записи, отправляются администратору базы данных, а не по адресу электронной почты для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью указания независимых значений для этих трех параметров компонент Database Mail позволяет настраивать сообщения так, как необходимо.  
  
 Параметр **\@mailserver_type** поддерживает значение **"SMTP"** .  
  
 Если **\@use_default_credentials** — 1 почта отправляется на SMTP-сервер с использованием учетных данных [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Если **\@use_default_credentials** имеет значение 0, а для учетной записи указаны **\@имя пользователя** и **пароль\@** , то учетная запись использует проверку подлинности SMTP. **\@username** и **\@Password** — это учетные данные, используемые учетной записью для SMTP-сервера, а не учетные данные для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или сети, в которой находится компьютер.  
  
 Хранимая процедура **sysmail_add_account_sp** находится в базе данных **msdb** и принадлежит схеме **dbo** . Процедура должна быть выполнена с именем, сопоставленным с тремя частями, если текущей базой данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения EXECUTE для этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается учетная запись с именем `AdventureWorks Administrator`. Эта учетная запись использует адрес электронной почты `dba@Adventure-Works.com` и посылает почту на почтовый SMTP-сервер `smtp.Adventure-Works.com`. Сообщения электронной почты, отправленные с этой учетной записи, показывают `AdventureWorks Automated Mailer` в строке сообщения **From:** . Ответы на сообщения направляются по адресу `danw@Adventure-Works.com`.  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
## <a name="see-also"></a>См. также статью  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создание учетной записи Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail хранимых &#40;процедур TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
