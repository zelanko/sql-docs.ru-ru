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
manager: craigg
ms.openlocfilehash: a388fb39082ec936b473afd7fc96ff99e7d92350
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830022"
---
# <a name="sysmailaddaccountsp-transact-sql"></a>sysmail_add_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [ **@account_name** =] **"***account_name***"**  
 Имя добавляемой учетной записи. *account_name* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@email_address** =] **"***email_address***"**  
 Адрес электронной почты, от имени которого посылается сообщение. Этот адрес должен быть адресом электронной почты Интернета. *email_address* — **nvarchar(128)**, не имеет значения по умолчанию. Например, учетная запись для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента позволяет отправлять сообщения с адреса **SqlAgent@Adventure-Works.com**.  
  
 [ **@display_name** =] **"***display_name***"**  
 Отображаемое имя, которое используется в сообщениях электронной почты, отправляемых от имени этой учетной записи. *display_name* — **nvarchar(128)**, значение по умолчанию NULL. Например, учетная запись для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента могут отображаться имя **SQL Server Agent Automated Mailer** в сообщениях электронной почты.  
  
 [ **@replyto_address** =] **"***replyto_address***"**  
 Адрес, на который отправляются ответы на сообщения данной учетной записи. *replyto_address* — **nvarchar(128)**, значение по умолчанию NULL. Например, ответы учетной записи для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента может перейти к администратору базы данных, **danw@Adventure-Works.com**.  
  
 [ **@description** =] **"***описание***"**  
 Описание учетной записи. *Описание* — **nvarchar(256)**, значение по умолчанию NULL.  
  
 [ **@mailserver_name** = ] **'***server_name***'**  
 Имя или IP-адрес почтового SMTP-сервера, который используется для этой учетной записи. На компьютере под управлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть способен Разрешить *имя_сервера* IP-адресу. *имя_сервера* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@mailserver_type** =] '*server_type*"  
 Тип сервера электронной почты. *server_type* — **sysname**, значение по умолчанию **'SMTP'**...  
  
 [ **@port** =] *номер_порта*  
 Номер порта сервера электронной почты. *номер_порта* — **int**, значение по умолчанию 25.  
  
 [ **@username** =] **"***username***"**  
 Имя пользователя, используемое при входе на сервер электронной почты. *имя пользователя* — **nvarchar(128)**, значение по умолчанию NULL. Если этот параметр установлен в NULL, компонент Database Mail не использует проверку подлинности для этой учетной записи. Если почтовый сервер не требует проверки подлинности, используйте NULL в качестве имени пользователя.  
  
 [ **@password** =] **"***пароль***"**  
 Пароль, используемый при входе на сервер электронной почты. *пароль* — **nvarchar(128)**, значение по умолчанию NULL. Нет необходимости указывать пароль, если не указано имя пользователя.  
  
 [ **@use_default_credentials** =] use_default_credentials  
 Указывает, посылать ли почту серверу SMTP с помощью учетных данных компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** имеет тип bit и значение по умолчанию 0. Если этот аргумент равен 1, компонент Database Mail использует учетные данные компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Если этот параметр равен 0, компонент Database Mail посылает **@username** и **@password** параметров, если он имеется, в противном случае отправляет электронную почту без **@username**и **@password** параметров.  
  
 [ **@enable_ssl** =] enable_ssl  
 Определяет, шифрует ли компонент Database Mail передаваемые данные с помощью протокола Secure Sockets Layer. **Enable_ssl** имеет тип bit и значение по умолчанию 0.  
  
 [ **@account_id** =] *account_id* выходных данных  
 Возвращает идентификатор новой учетной записи. *account_id* — **int**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Компонент Database Mail предоставляет отдельные значения для аргументов **@email_address**, **@display_name**, и **@replyto_address**. **@email_address** Параметр – адрес, с которого отправляется сообщение. **@display_name** Параметр является именем, отображаемым в **из:** сообщения электронной почты. **@replyto_address** Параметр – адрес, куда будут отправляться ответов на сообщения электронной почты. Например, учетная запись, используемая для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], может отправлять сообщения электронной почты с адреса, используемого только агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сообщения с этого адреса должны отображать понятные имена, таким образом получатели могут легко определить, что сообщение отправлено агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если получатель отвечает на сообщение, ответ должен быть доставлен администратору базы данных, а не на адрес агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом сценарии учетная запись использует **SqlAgent@Adventure-Works.com** как адрес электронной почты. Отображаемое имя присваивается **SQL Server Agent Automated Mailer**. Учетная запись использует **danw@Adventure-Works.com** как обратного адреса, поэтому ответы на сообщения, отправленные с этой учетной записи перейдите к администратору базы данных, а не адрес электронной почты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. С помощью указания независимых значений для этих трех параметров компонент Database Mail позволяет настраивать сообщения так, как необходимо.  
  
 **@mailserver_type** Поддерживает значение **'SMTP'**.  
  
 Когда **@use_default_credentials** — 1, почта отправляется на SMTP-сервер, используя учетные данные [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Когда **@use_default_credentials** равно 0 и **@username** и **@password** указанных для учетной записи, учетная запись использует проверку подлинности SMTP. **@username** И **@password** — это учетные данные, используемые учетной записью для SMTP-сервера, а не учетные данные для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или компьютер находится в сети.  
  
 Хранимая процедура **sysmail_add_account_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру необходимо выполнять с трехкомпонентным именем, если текущая база данных не **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию члены выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается учетная запись с именем `AdventureWorks Administrator`. Эта учетная запись использует адрес электронной почты `dba@Adventure-Works.com` и посылает почту на почтовый SMTP-сервер `smtp.Adventure-Works.com`. Электронные сообщения, отправляемые из этой учетной записи, отображают `AdventureWorks Automated Mailer` на **из:** строки сообщения. Ответы на сообщения направляются по адресу `danw@Adventure-Works.com`.  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Создайте учетную запись почты базы данных](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
