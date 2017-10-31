---
title: "СОЗДАЙТЕ имя входа (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_LOGIN_TSQL
- CREATE LOGIN
- LOGIN_TSQL
- LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], logins
- mapping logins [SQL Server]
- logins [SQL Server], creating
- CREATE LOGIN statement
- permissions [SQL Server], logins
- Windows domain accounts [SQL Server]
- re-hashing passwords
- certificates [SQL Server], logins
ms.assetid: eb737149-7c92-4552-946b-91085d8b1b01
caps.latest.revision: 101
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: e0b84743a9c3c578954560613c69f2863af8aa01
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="create-login-transact-sql"></a>CREATE LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Создает имя входа компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
CREATE LOGIN login_name { WITH <option_list1> | FROM <sources> }  
  
<option_list1> ::=   
    PASSWORD = { 'password' | hashed_password HASHED } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
    SID = sid  
    | DEFAULT_DATABASE = database      
    | DEFAULT_LANGUAGE = language  
    | CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
    | CREDENTIAL = credential_name   
  
<sources> ::=  
    WINDOWS [ WITH <windows_options>[ ,... ] ]  
    | CERTIFICATE certname  
    | ASYMMETRIC KEY asym_key_name  
  
<windows_options> ::=        
    DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse  
  
CREATE LOGIN login_name  
 { WITH <option_list3> }  
  
<option_list3> ::=   
    PASSWORD = { 'password' }  
    [ SID = sid ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }  
  
<option_list1> ::=   
    PASSWORD = { 'password' } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
      CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
```  
  
## <a name="arguments"></a>Аргументы  
 *login_name*  
 Указывает имя пользователя для создаваемого имени входа. Существует четыре типа имен входа: имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имена входа Windows, имена входа, сопоставленные с помощью сертификата, а также имена входа, сопоставленные с помощью асимметричного ключа. При создании имен входа, сопоставленных с учетной записью домена Windows, необходимо использовать имя входа пред-Windows 2000 пользователя в формате [\<domainName >\\< login_name >]. Нельзя использовать UPN в формате login_name@DomainName. См. приведенный ниже пример Г. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]имена входа являются типом **sysname** и должны соответствовать правилам для [идентификаторы](http://msdn.microsoft.com/library/ms175874.aspx) и не может содержать "**\\**". Имена входа Windows могут содержать символы «**\\**». Имена входа, основанный на количестве пользователей Active Directory ограничены имена менее 21 символов.  
  
 ПАРОЛЬ **= "***пароль***"**  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Задает пароль для создаваемого имени входа. Следует использовать надежные пароли. Дополнительные сведения см. [Strong Passwords](../../relational-databases/security/strong-passwords.md) и [политика паролей](../../relational-databases/security/password-policy.md). Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]сохраненные сведения о пароле вычисляется с помощью SHA-512 криптографического пароля.  
  
 В паролях учитывается регистр символов. Пароли всегда должны содержать не менее 8 символов и не могут содержать более 128 символов.  Пароли могут содержать символы a-z, A-Z, 0-9 и большинство неалфавитных символов. Пароли не могут содержать одинарные кавычки или *login_name*.  
  
 ПАРОЛЬ  **=**  *hashed_password*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применимо только к ключевому слову HASHED. Указывает хэшированное значение пароля для создаваемого имени входа.  
  
 HASHED  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает, что пароль, введенный после аргумента PASSWORD, уже хэширован. Если этот параметр не выбран, то строка, введенная в качестве пароля, хэшируется перед сохранением в базе данных. Данный параметр может быть применен только для миграции баз данных с одного сервера на другой. Не используйте параметр HASHED для создания новых имен входа. Параметр HASHED нельзя использовать с хэшами, созданными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7 или более ранних версий.  
  
 MUST_CHANGE  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если этот параметр задан, то при первом использовании нового имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запрашивается новый пароль.  
  
 Учетные данные  **=**  *credential_name*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя учетных данных для сопоставления с новым именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Учетные данные уже должны существовать на сервере. В настоящее время этот параметр только связывает учетные данные с именем входа. Учетные данные, не может быть сопоставлен имени входа системного администратора (sa).  
  
 SID = *sid*  
 Используется для повторного создания имени входа. Применяется к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только имена входа, не имена входа проверки подлинности Windows. Указывает идентификатор SID нового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа для проверки подлинности. Если этот параметр не используется, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически назначает идентификатор SID. Структура идентификатора безопасности зависит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]идентификатор SID имени входа: 16-байтовое (**binary(16)**) литеральное значение, основанное на GUID. Например, `SID = 0x14585E90117152449347750164BA00A7`.  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)]идентификатор SID имени входа: структура SID, допустимая для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Как правило, это 32-байтовый (**binary(32)**) литерал, состоящий из `0x01060000000000640000000000000000` плюс 16 байт, представляющих GUID. Например, `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`.  
  
DEFAULT_DATABASE  **=**  *базы данных*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 База данных по умолчанию, связываемая с именем входа. Если этот параметр не задан, то базой данных по умолчанию становится master.  
  
DEFAULT_LANGUAGE  **=**  *языка*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Язык по умолчанию, назначаемый имени входа. Если этот параметр не задан, то в качестве языка по умолчанию выбирается текущий язык по умолчанию для сервера. При смене языка по умолчанию для сервера язык по умолчанию имени входа не меняется.  
  
CHECK_EXPIRATION  **=**  {ON | **OFF** }  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает, должна ли политика истечения срока действия паролей принудительно применяться к этому имени входа. Значение по умолчанию — OFF.  
  
CHECK_POLICY  **=**  { **ON** | {OFF}  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к именам входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указывает, что политики паролей Windows компьютера, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должны принудительно применяться к этому имени входа. Значение по умолчанию — ON.  
  
 Если политика Windows требует надежных паролей, то пароль должен обладать по крайней мере тремя из следующих четырех качеств:  
  
-   Наличие символов верхнего регистра (A-Z).  
-   Наличие строчных символов (a-z).  
-   Числа (0-9).  
-   Один из неалфавитных символов, например пробел, _, @, *, ^, %! #, $ или &.  
  
WINDOWS  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя входа сопоставлено с именем входа Windows.  
  
СЕРТИФИКАТ *certname*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя сертификата, связываемого с данным именем входа. Этот сертификат должен уже существовать в базе данных master.  
  
АСИММЕТРИЧНЫЙ ключ *asym_key_name*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Имя асимметричного ключа, связываемого с данным именем входа. Этот ключ должен уже существовать в базе данных master.  
  
## <a name="remarks"></a>Замечания  
 В паролях учитывается регистр символов.  
  
 Предварительное хэширование паролей поддерживается только при создании имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если задан параметр MUST_CHANGE, то параметры CHECK_EXPIRATION и CHECK_POLICY должны иметь значение ON. В противном случае выполнение инструкции приведет к ошибке.  
  
 Сочетание CHECK_POLICY = OFF и CHECK_EXPIRATION = ON не поддерживается.  
  
 Если значение CHECK_POLICY равно OFF, *lockout_time* сбрасывается и CHECK_EXPIRATION имеет значение OFF.  
  
> [!IMPORTANT]  
>  Параметры CHECK_EXPIRATION и CHECK_POLICY будут принудительно применяться только в [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] или более поздних версиях. Дополнительные сведения см. в разделе [Password Policy](../../relational-databases/security/password-policy.md).  
  
 Имена входа, созданные из сертификатов или асимметричных ключей, используются только для подписи кода. Они не могут использоваться для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Имя входа можно создать на основе сертификата или ассиметричного ключа только в том случае, если сертификат или асимметричный ключ уже существуют в базе данных master.  
  
 Скрипт для передачи имен входа см. в разделе [Способы передачи имен входа и паролей между экземплярами SQL Server 2005 и SQL Server 2008](http://support.microsoft.com/kb/918992).  
  
 При создании имени входа оно автоматически включается, и ему предоставляется разрешение **CONNECT SQL** уровня сервера.  
  
 Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-and-includesssdwincludessssdw-mdmd-logins"></a>[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] имена входа  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)], **CREATE LOGIN** инструкция должна быть единственной инструкцией в пакете.  
  
 В некоторых методах подключения к [!INCLUDE[ssSDS](../../includes/sssds-md.md)], такие как **sqlcmd**, необходимо добавить [!INCLUDE[ssSDS](../../includes/sssds-md.md)] имя сервера, чтобы имя входа в строке подключения с помощью  *\<входа >* @  *\<server >* нотации. Например, если имя входа — `login1` и полное имя [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервер `servername.database.windows.net`, *username* параметр строки подключения должен быть `login1@servername`. Так как общая длина *username* параметра составляет 128 символов *login_name* ограничено до 127 символов минус длина имени сервера. В примере `login_name` может иметь длину не более 117 символов, поскольку `servername` имеет длину 10 символов.  
  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] необходимо подключиться к базе данных master, чтобы создать имя входа.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]правила позволяют создать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа проверки подлинности в формате \<loginname > @\<имя_сервера >. Если ваш [!INCLUDE[ssSDS](../../includes/sssds-md.md)] сервер **myazureserver** и вход выполнен  **myemail@live.com** , то необходимо указать имя входа в виде  **myemail@live.com @myazureserver**  .  
  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)], требуются данные входа для проверки подлинности подключения и правила брандмауэра уровня сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедитесь в том, что база данных имеет последнюю версию таблицы, имена входа, выполните [DBCC FLUSHAUTHCACHE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
 Дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)] имена входа, в разделе [Управление базами данных и именами входа в базе данных SQL Windows Azure](http://msdn.microsoft.com/library/ee336235.aspx).  
  
## <a name="permissions"></a>Permissions  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], требуется **ALTER ANY LOGIN** разрешение на сервер или членство в **securityadmin** предопределенной роли сервера.  
  
 В службах [!INCLUDE[ssSDS](../../includes/sssds-md.md)] создавать новые имена входа могут только имя входа участника уровня сервера (созданного процессом провизионирования) или члены роли `loginmanager` базы данных в базе данных master.  
  
 Если используется параметр **CREDENTIAL** , также необходимо разрешение **ALTER ANY CREDENTIAL** на сервере.  
  
## <a name="next-steps"></a>Следующие шаги  
 После создания имени входа, имя входа подключается к [!INCLUDE[ssDE](../../includes/ssde-md.md)] или [!INCLUDE[ssSDS](../../includes/sssds-md.md)] , но только разрешения, предоставленные **открытый** роли. Попробуйте выполнить некоторые из приведенных ниже действий.  
  
-   Чтобы подключиться к базе данных, создайте пользователя базы данных для имени входа. Дополнительные сведения см. в разделе [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md).  
  
-   Создание роли сервера, определяемого пользователем с помощью [CREATE SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-server-role-transact-sql.md). Воспользуйтесь инструкциями **ALTER SERVER ROLE** … **Добавить ЧЛЕНА** для добавления нового имени входа к роли сервера, определяемой пользователем. Дополнительные сведения см. в разделе [CREATE SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-server-role-transact-sql.md) и [ALTER РОЛИ сервера &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
-   Используйте **sp_addsrvrolemember** Добавление имени входа к предопределенной роли сервера. Дополнительные сведения см. в разделе [роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md) и [sp_addsrvrolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
-   Используйте **GRANT** инструкции для предоставления разрешений уровня сервера с новым именем входа или роли, содержащей имя входа. Дополнительные сведения см. в разделе [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Создание имени входа с паролем  
 В следующем примере создается имя входа для конкретного пользователя и назначается пароль.  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-with-a-password"></a>Б. Создание имени входа с паролем  
 В следующем примере создается имя входа для конкретного пользователя и назначается пароль. Параметр `MUST_CHANGE` требует, чтобы пользователь изменил этот пароль при первом подключении к серверу.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>' MUST_CHANGE;  
GO  
```  
  
### <a name="c-creating-a-login-mapped-to-a-credential"></a>В. Создание имени входа, сопоставленного с учетными данными  
 В следующем примере создается имя входа для конкретного пользователя с использованием идентификатора пользователя. Это имя входа сопоставляется с учетными данными.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',   
    CREDENTIAL = <credentialName>;  
GO  
```  
  
### <a name="d-creating-a-login-from-a-certificate"></a>Г. Создание имени входа на основе сертификата  
 В следующем примере создается имя входа для конкретного пользователя на основе сертификата в базе данных master.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE MASTER;  
CREATE CERTIFICATE <certificateName>  
    WITH SUBJECT = '<login_name> certificate in master database',  
    EXPIRY_DATE = '12/05/2025';  
GO  
CREATE LOGIN <login_name> FROM CERTIFICATE <certificateName>;  
GO  
```  
  
### <a name="e-creating-a-login-from-a-windows-domain-account"></a>Д. Создание имени входа на основе учетной записи домена Windows  
 В следующем примере имя входа создается на основе учетной записи домена Windows.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;  
GO  
```  
  
### <a name="f-creating-a-login-from-a-sid"></a>Е. Создание имени входа на основе SID  
 В следующем примере сначала создается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа для проверки подлинности и определяет его SID имени входа.  
  
```  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Наш запрос возвращает 0x241C11948AEEB749B0D22646DB1A19F2 в качестве SID. Ваш запрос вернет другое значение. Следующие выражения удаляют имя входа, а затем повторно создают имя входа. Используйте SID из предыдущего запроса.  
  
```  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>Ж. Создание имени входа для проверки подлинности SQL Server с паролем  
 В следующем примере создается имя входа `Mary7` с паролем `A2c3456`.  
  
```tsql  
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;  
```  
  
### <a name="h-using-options"></a>З. С помощью параметров  
 В следующем примере создается имя входа `Mary8` с помощью пароля, а также ряд необязательных аргументов.  
  
```  
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
```  
  
### <a name="i-creating-a-login-from-a-windows-domain-account"></a>И. Создание имени входа на основе учетной записи домена Windows  
 В следующем примере создается имя входа с учетной записью домена Windows с именем `Mary` в `Contoso` домена.  
  
```  
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Политика паролей](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN &#40; Transact-SQL &#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Создание имени входа](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  

