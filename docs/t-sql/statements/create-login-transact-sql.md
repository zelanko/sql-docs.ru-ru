---
title: CREATE LOGIN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3b28cde8935c3a2c4b25f20ef727358b918e6680
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155657"
---
# <a name="create-login-transact-sql"></a>CREATE LOGIN (Transact-SQL)

Создает имя для входа в SQL Server, Базу данных SQL, Хранилище данных SQL или базы данных Microsoft Analytics Platform System. Щелкните одну из следующих вкладок, чтобы изучить синтаксис, аргументы, примечания, разрешения и примеры для конкретной версии.

CREATE LOGIN участвует в транзакциях. Если откат транзакции CREATE LOGIN выполняется в рамках транзакции, для создания имени для входа также выполняется откат. При выполнении в транзакции созданное имя входа не может использоваться до фиксации транзакции.

Дополнительные сведения о соглашениях о синтаксисе см. в статье [Соглашения о синтаксисе в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="click-a-product"></a>Выберите продукт!

В следующей строке щелкните имя продукта, который вас интересует. На этой веб-странице отобразится другой контент, относящийся к выбранному продукту.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

||||||
|-|-|-|-|-|
|**\*_ SQL Server \*_** &nbsp;|[Отдельная база данных/эластичный пул Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-current)|[Управляемый экземпляр Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-mi-current)|[Хранилище данных<br />SQL](create-login-transact-sql.md?view=azure-sqldw-latest)|[Analytics Platform<br />System (PDW)](create-login-transact-sql.md?view=aps-pdw-2016)
||||||

&nbsp;

## <a name="sql-server"></a>SQL Server

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

## <a name="arguments"></a>Аргументы

*login_name* — указывает имя пользователя для создаваемого имени входа. Имена входа бывают четырех типов: имена входа SQL Server, имена входа Windows, имена входа, сопоставленные с помощью сертификата, а также имена входа, сопоставленные с помощью асимметричного ключа. При создании имен входа, сопоставленных с учетной записью домена Windows, необходимо использовать имя входа версии, более ранней, чем Windows 2000, с форматом [\<domainName>\\<login_name>]. Нельзя использовать имя участника-пользователя в формате login_name@DomainName. См. приведенный ниже пример Г. Имена входа проверки подлинности имеют тип **sysname**, должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md) и не могут содержать символ "**\\**". Имена входа Windows могут содержать символы «**\\**». Имена входа, основанные на пользователях Active Directory, могут иметь не более 21 символа в длину.

PASSWORD **=**'*password*' Применяется только к именам входа SQL Server. Задает пароль для создаваемого имени входа. Выбирайте надежные пароли. Дополнительные сведения см. в статьях [Надежные пароли](../../relational-databases/security/strong-passwords.md) и [Политика паролей](../../relational-databases/security/password-policy.md). Начиная с SQL Server 2012 (11.x), сохраненные сведения о пароле вычисляются с помощью SHA-512 "соленого" пароля.

В паролях учитывается регистр символов. Пароли всегда должны содержать не менее восьми символов и не могут содержать более 128 символов. Пароли могут содержать символы a-z, A-Z, 0-9 и большинство неалфавитных символов. Пароли не могут содержать одиночные кавычки или *login_name*.

PASSWORD **=** *hashed\_password* — применяется только к ключевому слову HASHED. Указывает хэшированное значение пароля для создаваемого имени входа.

HASHED Применяется только к именам входа SQL Server. Указывает, что пароль, введенный после аргумента PASSWORD, уже хэширован. Если этот параметр не выбран, то строка, введенная в качестве пароля, хэшируется перед сохранением в базе данных. Данный параметр может быть применен только для миграции баз данных с одного сервера на другой. Не используйте параметр HASHED для создания новых имен входа. Параметр HASHED нельзя использовать с хэшами, созданными в SQL 7 или более ранних версиях.

MUST_CHANGE применяется только к именам входа SQL Server. Если этот параметр задан, то при первом использовании нового имени входа SQL Server запрашивает новый пароль.

CREDENTIAL **=**_credential\_name_ — имя учетных данных для сопоставления с новым именем входа SQL Server. Учетные данные уже должны существовать на сервере. В настоящее время этот параметр только связывает учетные данные с именем входа. Учетные данные не могут быть сопоставлены с именем входа системного администратора (sa).

SID = *sid* — используется для повторного создания имени входа. Применяется только к именам входа проверки подлинности SQL Server, но не относится к именам входа проверки подлинности Windows. Указывает идентификатор SID нового имени входа проверки подлинности SQL Server. Если этот параметр не используется, SQL Server назначает идентификатор SID автоматически. Структура идентификатора SID зависит от версии SQL Server. Идентификатор SID имени входа SQL Server: 16-байтовое (**binary(16)**) литеральное значение, основанное на GUID. Например, `SID = 0x14585E90117152449347750164BA00A7`.

DEFAULT_DATABASE **=**_database_ — указывает базу данных по умолчанию, связываемую с именем входа. Если этот параметр не задан, то базой данных по умолчанию становится master.

DEFAULT_LANGUAGE **=**_language_ — указывает язык по умолчанию, присвоенный имени входа. Если этот параметр не задан, то в качестве языка по умолчанию выбирается текущий язык по умолчанию для сервера. При смене языка по умолчанию для сервера язык по умолчанию имени входа не меняется.

CHECK_EXPIRATION **=** { ON | **OFF** } — применяется только к именам входа SQL Server. Указывает, должна ли политика истечения срока действия паролей принудительно применяться к этому имени входа. Значение по умолчанию — OFF.

CHECK_POLICY **=** { **ON** | OFF } — применяется только к именам входа SQL Server. Указывает, что политики паролей Windows компьютера, на котором работает SQL Server, должны принудительно применяться к этому имени входа. Значение по умолчанию — ON.

Если политика Windows требует надежных паролей, то пароль должен обладать по крайней мере тремя из следующих четырех качеств:

- Наличие символов верхнего регистра (A-Z).
- Наличие строчных символов (a-z).
- Числа (0-9).
- Один из неалфавитных символов, например пробел, _, @, *, ^, %! #, $ или &.

WINDOWS — указывает, что имя входа сопоставлено с именем входа Windows.

CERTIFICATE *certname* — определяет имя сертификата, связываемого с данным именем входа. Этот сертификат должен уже существовать в базе данных master.

ASYMMETRIC KEY *asym_key_name* — определяет имя асимметричного ключа, связываемого с этим именем входа. Этот ключ должен уже существовать в базе данных master.

## <a name="remarks"></a>Remarks

- В паролях учитывается регистр символов.
- Предварительное хэширование паролей поддерживается только при создании имен входа SQL Server.
- Если задан параметр MUST_CHANGE, то параметры CHECK_EXPIRATION и CHECK_POLICY должны иметь значение ON. В противном случае выполнение инструкции приведет к ошибке.
- Сочетание CHECK_POLICY = OFF и CHECK_EXPIRATION = ON не поддерживается.
- Если значение CHECK_POLICY равно OFF, то *lockout_time* сбрасывается и параметру CHECK_EXPIRATION также присваивается значение OFF.

> [!IMPORTANT]
> Параметры CHECK_EXPIRATION и CHECK_POLICY принудительно применяются только в Windows Server 2003 и более поздних версиях. Дополнительные сведения см. в разделе [Политика паролей](../../relational-databases/security/password-policy.md).

- Имена входа, созданные из сертификатов или асимметричных ключей, используются только для подписи кода. Они не могут использоваться для подключения к SQL Server. Имя входа можно создать на основе сертификата или ассиметричного ключа только в том случае, если сертификат или асимметричный ключ уже существуют в базе данных master.
- Скрипт для передачи имен входа см. в разделе [Способы передачи имен входа и паролей между экземплярами SQL Server 2005 и SQL Server 2008](https://support.microsoft.com/kb/918992).
- При создании имени входа оно автоматически включается, и ему предоставляется разрешение **CONNECT SQL** уровня сервера.
- Для разрешения доступа [режим проверки подлинности](../../relational-databases/security/choose-an-authentication-mode.md) сервера должен соответствовать типу имени входа.
- Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="permissions"></a>Разрешения

- Создавать имена входа могут только пользователи с разрешением **ALTER ANY LOGIN** на сервере или имеющие членство в предопределенной роли сервера **securityadmin**. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) и [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).
- Если используется параметр **CREDENTIAL** , также необходимо разрешение **ALTER ANY CREDENTIAL** на сервере.

## <a name="after-creating-a-login"></a>После создания имени входа

Созданное имя входа может подключаться к SQL Server, но имеет разрешения только для роли **public**. Попробуйте выполнить некоторые из приведенных ниже действий.

- Чтобы подключиться к базе данных, создайте пользователя базы данных для имени входа. Дополнительные сведения см. в статье об инструкции [CREATE USER](../../t-sql/statements/create-user-transact-sql.md).
- Создайте определяемую пользователем роль сервера с помощью [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md). Воспользуйтесь инструкциями **ALTER SERVER ROLE** ... **ADD MEMBER** для добавления нового имени входа к определяемой пользователем роли сервера. Дополнительные сведения см. в статьях [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) и [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).
- Воспользуйтесь процедурой **sp_addsrvrolemember** для добавления имени входа к предопределенной роли сервера. Дополнительные сведения см. в разделе [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md) и [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).
- Воспользуйтесь инструкцией **GRANT**, чтобы предоставить разрешения уровня сервера новому имени входа или роли, содержащей это имя входа. Дополнительные сведения см. в статье [GRANT](../../t-sql/statements/grant-transact-sql.md).

## <a name="examples"></a>Примеры

### <a name="a-creating-a-login-with-a-password"></a>A. Создание имени входа с паролем

В следующем примере создается имя входа для конкретного пользователя и назначается пароль.

```sql
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';
GO
```

### <a name="b-creating-a-login-with-a-password-that-must-be-changed"></a>Б. Создание имени входа с паролем, который необходимо изменить

В следующем примере создается имя входа для конкретного пользователя и назначается пароль. Параметр `MUST_CHANGE` требует, чтобы пользователь изменил этот пароль при первом подключении к серверу.

**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

```sql
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>'
    MUST_CHANGE, CHECK_EXPIRATION = ON;
GO
```

> [!NOTE]
> Невозможно использовать параметр MUST_CHANGE, если параметр CHECK_EXPIRATION имеет значение OFF.

### <a name="c-creating-a-login-mapped-to-a-credential"></a>В. Создание имени входа, сопоставленного с учетными данными

В следующем примере создается имя входа для конкретного пользователя с использованием идентификатора пользователя. Это имя входа сопоставляется с учетными данными.

**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

```sql
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',
    CREDENTIAL = <credentialName>;
GO
```

### <a name="d-creating-a-login-from-a-certificate"></a>Г. Создание имени входа на основе сертификата

В следующем примере создается имя входа для конкретного пользователя на основе сертификата в базе данных master.

**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

```sql
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

**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

```sql
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;
GO
```

### <a name="f-creating-a-login-from-a-sid"></a>Е. Создание имени входа на основе SID

В следующем примере создается имя входа с проверкой подлинности SQL Server и определяется его SID.

```sql
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';
GO
```

Наш запрос возвращает идентификатор SID 0x241C11948AEEB749B0D22646DB1A19F2. Ваш запрос вернет другое значение. Следующие выражения удаляют имя входа, а затем повторно создают имя входа. Используйте SID из предыдущего запроса.

```sql
DROP LOGIN TestLogin;
GO

CREATE LOGIN TestLogin
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;

SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';
GO
```

## <a name="see-also"></a>См. также:

- [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)
- [Субъекты](../../relational-databases/security/authentication-access/principals-database-engine.md)
- [Политика паролей](../../relational-databases/security/password-policy.md)
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Создание имени для входа](../../relational-databases/security/authentication-access/create-a-login.md)

::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2017)|**_\* Отдельная база данных/эластичный пул Базы данных SQL<br /> \*_**|[Управляемый экземпляр Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-mi-current)|[Хранилище данных<br />SQL](create-login-transact-sql.md?view=azure-sqldw-latest)|[Analytics Platform<br />System (PDW)](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-database-single-databaseelastic-pool"></a>Отдельная база данных или эластичный пул Базы данных SQL Azure

## <a name="syntax"></a>Синтаксис

```
-- Syntax for Azure SQL Database
CREATE LOGIN login_name
 { WITH <option_list> }

<option_list> ::=
    PASSWORD = { 'password' }
    [ , SID = sid ]
```

## <a name="arguments"></a>Аргументы

*login_name* — указывает имя пользователя для создаваемого имени входа. Отдельная база данных или эластичный пул Базы данных SQL Azure поддерживает только имена входа SQL.

PASSWORD **='** password**'*  — указывает пароль для создаваемого имени входа SQL. Выбирайте надежные пароли. Дополнительные сведения см. в статьях [Надежные пароли](../../relational-databases/security/strong-passwords.md) и [Политика паролей](../../relational-databases/security/password-policy.md). Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] сохраненные сведения о пароле вычисляются с помощью SHA-512 соленого пароля.

В паролях учитывается регистр символов. Пароли всегда должны содержать не менее восьми символов и не могут содержать более 128 символов. Пароли могут содержать символы a-z, A-Z, 0-9 и большинство неалфавитных символов. Пароли не могут содержать одиночные кавычки или *login_name*.

SID = *sid* — используется для повторного создания имени входа. Применяется только к именам входа проверки подлинности SQL Server, но не относится к именам входа проверки подлинности Windows. Указывает идентификатор SID нового имени входа проверки подлинности SQL Server. Если этот параметр не используется, SQL Server назначает идентификатор SID автоматически. Структура идентификатора SID зависит от версии SQL Server. Для базы данных SQL это 32-байтовый (**binary(32)**) литерал, состоящий из `0x01060000000000640000000000000000` плюс 16 байт, представляющих GUID. Например, `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`.

## <a name="remarks"></a>Remarks

- В паролях учитывается регистр символов.
- Скрипт для передачи имен входа см. в разделе [Способы передачи имен входа и паролей между экземплярами SQL Server 2005 и SQL Server 2008](https://support.microsoft.com/kb/918992).
- При создании имени входа оно автоматически включается, и ему предоставляется разрешение **CONNECT SQL** уровня сервера.
- Для разрешения доступа [режим проверки подлинности](../../relational-databases/security/choose-an-authentication-mode.md) сервера должен соответствовать типу имени входа.
- Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="login"></a>Имя входа

### <a name="sql-database-logins"></a>Имена входа базы данных SQL

Инструкция **CREATE LOGIN** должна быть единственной инструкцией в пакете.

В некоторых методах подключения к базе данных SQL, например **sqlcmd**, необходимо добавить имя сервера базы данных SQL к имени входа в строке подключения с помощью нотации *\<login>*@*\<server>*. Например, если имя входа — `login1`, а полное имя сервера базы данных SQL —`servername.database.windows.net`, то параметр *username* в строке подключения должен иметь вид `login1@servername`. Так как общая длина параметра *username* составляет 128 символов, длина имени *login_name* ограничена до 127 символов минус длина имени сервера. В примере `login_name` может иметь длину не более 117 символов, поскольку `servername` имеет длину 10 символов.

В базе данных SQL для создания имени входа необходимо подключение к базе данных master.

Правила SQL Server позволяют создать имя входа для проверки подлинности SQL Server в формате \<loginname>@\<servername>. Если сервер [!INCLUDE[ssSDS](../../includes/sssds-md.md)] — **myazureserver**, а имя входа —**myemail@live.com**, то необходимо указать имя входа в виде **myemail@live.com@myazureserver**.

В базе данных SQL данные имени входа необходимы для проверки подлинности подключения, и правила брандмауэра на уровне сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедиться в том, что база данных имеет последнюю версию таблицы имен входа, выполните инструкцию [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).

Дополнительные сведения об именах входа базы данных SQL см. в статье [Управление базами данных и именами входа в Базу данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins).

## <a name="permissions"></a>Разрешения

Создавать имена входа могут только имена входа участника уровня сервера (созданного процессом подготовки) или члены роли базы данных `loginmanager` в базе данных master. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) и [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).

## <a name="logins"></a>Имена входа

- Требуется разрешение **ALTER ANY LOGIN** на сервере или членство в предопределенной роли сервера **securityadmin**. Выполнять эту команду может только учетная запись Azure Active Directory (Azure AD) с разрешением **ALTER ANY LOGIN** на сервере или членством в разрешении securityadmin.
- Требуется членство в Azure AD в том же каталоге, который используется для сервера Базы данных SQL Azure.

## <a name="after-creating-a-login"></a>После создания имени входа

Созданное имя входа может подключаться к базе данных SQL, но имеет разрешения только для роли **public**. Попробуйте выполнить некоторые из приведенных ниже действий.

- Чтобы подключиться к базе данных, создайте в этой базе данных пользователя для имени входа. Дополнительные сведения см. в статье об инструкции [CREATE USER](../../t-sql/statements/create-user-transact-sql.md).
- Чтобы предоставить разрешения пользователю базы данных, используйте инструкцию **ALTER SERVER ROLE** ... **ADD MEMBER** для добавления пользователя в одну из встроенных ролей базы данных или пользовательскую роль либо напрямую предоставьте пользователю разрешения с помощью инструкции [GRANT](../../t-sql/statements/grant-transact-sql.md). Дополнительные сведения см. в разделах [Пользователи без прав администратора](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users), [Дополнительные административные роли на уровне сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) и [GRANT](grant-transact-sql.md).
- Чтобы предоставить разрешения уровня сервера, создайте пользователя базы данных в базе данных master и с помощью инструкции **ALTER SERVER ROLE** ... **ADD MEMBER** добавьте пользователя в одну из административных ролей сервера. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) и [Роли сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).
- Воспользуйтесь инструкцией **GRANT**, чтобы предоставить разрешения уровня сервера новому имени входа или роли, содержащей это имя входа. Дополнительные сведения см. в статье [GRANT](../../t-sql/statements/grant-transact-sql.md).

## <a name="examples"></a>Примеры

### <a name="a-creating-a-login-with-a-password"></a>A. Создание имени входа с паролем

В следующем примере создается имя входа для конкретного пользователя и назначается пароль.

```sql
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';
GO
```

### <a name="b-creating-a-login-from-a-sid"></a>Б. Создание имени входа на основе SID

В следующем примере создается имя входа с проверкой подлинности SQL Server и определяется его SID.

```sql
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';

SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';
GO
```

Наш запрос возвращает идентификатор SID 0x241C11948AEEB749B0D22646DB1A19F2. Ваш запрос вернет другое значение. Следующие выражения удаляют имя входа, а затем повторно создают имя входа. Используйте SID из предыдущего запроса.

```sql
DROP LOGIN TestLogin;
GO

CREATE LOGIN TestLogin
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;

SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';
GO
```

## <a name="see-also"></a>См. также:

- [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)
- [Субъекты](../../relational-databases/security/authentication-access/principals-database-engine.md)
- [Политика паролей](../../relational-databases/security/password-policy.md)
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Создание имени для входа](../../relational-databases/security/authentication-access/create-a-login.md)

::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2017)|[Отдельная база данных/эластичный пул Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-current)|**_\* Управляемый экземпляр Базы данных SQL<br /> \*_**|[Хранилище данных<br />SQL](create-login-transact-sql.md?view=azure-sqldw-latest)|[Analytics Platform<br />System (PDW)](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-database-managed-instance"></a>Управляемый экземпляр Базы данных SQL Azure

## <a name="syntax"></a>Синтаксис

```sql
-- Syntax for Azure SQL Database managed instance
CREATE LOGIN login_name [FROM EXTERNAL PROVIDER] { WITH <option_list> [,..]}

<option_list> ::=
    PASSWORD = {'password'}
    | SID = sid
    | DEFAULT_DATABASE = database
    | DEFAULT_LANGUAGE = language
```

> [!IMPORTANT]
> Имена входа Azure AD для управляемого экземпляра Базы данных SQL находятся в **общедоступной предварительной версии**. Синтаксически эта функция оформляется с помощью предложения **FROM EXTERNAL PROVIDER**.

## <a name="arguments"></a>Аргументы

*login_name* — учетные данные, которые при использовании вместе с предложением **FROM EXTERNAL PROVIDER** указывают субъект Azure Active Directory (AD). Субъектом может быть пользователь, группа или приложение Azure AD. В противном случае оно представляет созданное имя входа SQL.

FROM EXTERNAL PROVIDER </br>
Указывает, что имя входа предназначено для проверки подлинности Azure AD.

PASSWORD **=** '*password*' — указывает пароль для создаваемого имени входа SQL. Выбирайте надежные пароли. Дополнительные сведения см. в статьях [Надежные пароли](../../relational-databases/security/strong-passwords.md) и [Политика паролей](../../relational-databases/security/password-policy.md). Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] сохраненные сведения о пароле вычисляются с помощью SHA-512 соленого пароля.

В паролях учитывается регистр символов. Пароли всегда должны содержать не менее восьми символов и не могут содержать более 128 символов. Пароли могут содержать символы a-z, A-Z, 0-9 и большинство неалфавитных символов. Пароли не могут содержать одиночные кавычки или *login_name*.

SID **=** *sid* — используется для повторного создания имени входа. Применяется только для имен входа с проверкой подлинности SQL Server. Указывает идентификатор SID нового имени входа проверки подлинности SQL Server. Если этот параметр не используется, SQL Server назначает идентификатор SID автоматически. Структура идентификатора SID зависит от версии SQL Server. Для базы данных SQL это 32-байтовый (**binary(32)**) литерал, состоящий из `0x01060000000000640000000000000000` плюс 16 байт, представляющих GUID. Например, `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`.

## <a name="remarks"></a>Remarks

- В паролях учитывается регистр символов.
- Появился новый синтаксис для создания субъектов уровня сервера, сопоставленных с учетными записями Azure AD (**FROM EXTERNAL PROVIDER**)
- Когда указывается **FROM EXTERNAL PROVIDER**:

  - значение login_name должно представлять имеющуюся учетную запись Azure AD (пользователя, группу или приложение), доступную в Azure AD для текущего управляемого экземпляра SQL Azure. Для субъектов Azure AD действуют такие требования синтаксиса CREATE LOGIN:
    - имя участника-пользователя (UserPrincipalName) объекта Azure AD для пользователей Azure AD;
    - отображаемое имя (DisplayName) объекта Azure AD для групп и приложений Azure AD.
  - Этот параметр невозможно использовать совместно с параметром **PASSWORD**.
  - Сейчас первое имя входа Azure AD должно создаваться стандартной учетной записью SQL Server (не относящейся к Azure AD), то есть `sysadmin`, используя приведенный выше синтаксис.
  - При создании имени входа Azure AD с участием администратора Azure AD для управляемого экземпляра Базы данных SQL возникает следующая ошибка:</br>
      `Msg 15247, Level 16, State 1, Line 1
      User does not have permission to perform this action.`
  - Это известное ограничение **общедоступной предварительной версии**, которая будет исправлена в будущем.
  - Создав первое имя входа Azure AD, можно создать с его помощью другие имена входа Azure AD, предоставив ему необходимые разрешения.
- По умолчанию, когда предложение **FROM EXTERNAL PROVIDER** опущено, создается регулярное имя входа SQL.
- Имена для входа Azure AD отображаются в sys.server_principals со значением столбца типа, равным **E**, и type_desc, равным **EXTERNAL_LOGIN** для имен входа, сопоставленных пользователям Azure AD, или значением столбца типа **X** и значением type_desc **EXTERNAL_GROUP** для имен входа, которые сопоставляются с группами Azure AD.
- Скрипт для передачи имен входа см. в разделе [Способы передачи имен входа и паролей между экземплярами SQL Server 2005 и SQL Server 2008](https://support.microsoft.com/kb/918992).
- При создании имени входа оно автоматически включается, и ему предоставляется разрешение **CONNECT SQL** уровня сервера.

## <a name="logins-and-permissions"></a>Имена входа и разрешения

Создавать имена входа могут только имена входа участника уровня сервера (созданного процессом подготовки) или члены роли базы данных `securityadmin` или `sysadmin` в базе данных master. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) и [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).

Стандартные разрешения, предоставляемые по умолчанию только что созданному имени входа Azure AD в базе данных master: **CONNECT SQL** и **VIEW ANY DATABASE**.

### <a name="sql-database-managed-instance-logins"></a>Имена входа управляемого экземпляра Базы данных SQL

- Требуется разрешение **ALTER ANY LOGIN** на сервере или членство в предопределенной роли сервера `securityadmin` или `sysadmin`. Выполнять команду создания может только учетная запись Azure Active Directory (Azure AD) с разрешением **ALTER ANY LOGIN** на сервере или членством в одной из этих ролей.
- Если имя входа является субъектом SQL, только имена входа, которые относятся к роли `sysadmin`, могут использовать команду создания, чтобы создавать имена входа для учетной записи Azure AD.
- Требуется членство в Azure AD в том же каталоге, который используется для управляемого экземпляра SQL Azure.

## <a name="after-creating-a-login"></a>После создания имени входа

Созданное имя входа может подключаться к управляемому экземпляру Базы данных SQL, но c разрешениями только для роли **public**. Попробуйте выполнить некоторые из приведенных ниже действий.

- Чтобы создать пользователя Azure AD по имени входа Azure AD, см. раздел [CREATE USER](../../t-sql/statements/create-user-transact-sql.md).
- Чтобы предоставить разрешения пользователю базы данных, используйте инструкцию **ALTER SERVER ROLE** ... **ADD MEMBER** для добавления пользователя в одну из встроенных ролей базы данных или пользовательскую роль либо напрямую предоставьте пользователю разрешения с помощью инструкции [GRANT](../../t-sql/statements/grant-transact-sql.md). Дополнительные сведения см. в разделах [Пользователи без прав администратора](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users), [Дополнительные административные роли на уровне сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) и [GRANT](grant-transact-sql.md).
- Чтобы предоставить разрешения уровня сервера, создайте пользователя базы данных в базе данных master и с помощью инструкции **ALTER SERVER ROLE** ... **ADD MEMBER** добавьте пользователя в одну из административных ролей сервера. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) и [Роли сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).
  - Используйте следующую команду, чтобы добавить роль `sysadmin` для имени входа Azure AD: `ALTER SERVER ROLE sysadmin ADD MEMBER [AzureAD_Login_name]`
- Воспользуйтесь инструкцией **GRANT**, чтобы предоставить разрешения уровня сервера новому имени входа или роли, содержащей это имя входа. Дополнительные сведения см. в статье [GRANT](../../t-sql/statements/grant-transact-sql.md).

## <a name="limitations"></a>Ограничения

- Сопоставление имени входа Azure AD с группой Azure AD в качестве владельца базы данных не поддерживается.
- Олицетворение участников уровня сервера Azure AD с помощью других субъектов Azure AD поддерживается, например с помощью предложения [EXECUTE AS](execute-as-transact-sql.md).
- Только субъекты уровня сервера SQL (имена входа), которые относятся к роли `sysadmin`, могут выполнять следующие операции, предназначенные для субъектов Azure AD:
  - EXECUTE AS USER
  - EXECUTE AS LOGIN

## <a name="examples"></a>Примеры

### <a name="a-creating-a-login-with-a-password"></a>A. Создание имени входа с паролем

В следующем примере создается имя входа для конкретного пользователя и назначается пароль.

 ```sql
 CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';
 GO
 ```

### <a name="b-creating-a-login-from-a-sid"></a>Б. Создание имени входа на основе SID

 В следующем примере создается имя входа с проверкой подлинности SQL Server и определяется его SID.

 ```sql
 CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';

 SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';
 GO
 ```

Наш запрос возвращает идентификатор SID 0x241C11948AEEB749B0D22646DB1A19F2. Ваш запрос вернет другое значение. Следующие выражения удаляют имя входа, а затем повторно создают имя входа. Используйте SID из предыдущего запроса.

 ```sql
 DROP LOGIN TestLogin;
 GO

 CREATE LOGIN TestLogin
 WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;

 SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';
 GO
 ```

### <a name="c-creating-a-login-for-a-local-azure-ad-account"></a>В. Создание имени входа для локальной учетной записи Azure AD

 В следующем примере создается имя входа для учетной записи Azure AD joe@myaad.onmicrosoft.com, существующей в Azure AD *myaad*.

```sql
CREATE LOGIN [joe@myaad.onmicrosoft.com] FROM EXTERNAL PROVIDER
GO
```

### <a name="d-creating-a-login-for-a-federated-azure-ad-account"></a>Г. Создание имени входа для федеративной учетной записи Azure AD

 В следующем примере создается имя входа для федеративной учетной записи Azure AD bob@contoso.com, существующей в Azure AD *contoso*. Пользователь Боб также может быть гостем.

```sql
CREATE LOGIN [bob@contoso.com] FROM EXTERNAL PROVIDER
GO
```

### <a name="e-creating-a-login-for-an-azure-ad-group"></a>Д. Создание имени входа для группы Azure AD

 В следующем примере создается имя входа для группы Azure AD *mygroup*, существующей в Azure AD *myaad*.

```sql
CREATE LOGIN [mygroup] FROM EXTERNAL PROVIDER
GO
```

### <a name="f-creating-a-login-for-an-azure-ad-application"></a>Е. Создание имени входа для приложения Azure AD

В следующем примере создается имя входа для приложения Azure AD *myapp*, существующего в Azure AD *myaad*.

```sql
CREATE LOGIN [myapp] FROM EXTERNAL PROVIDER
```

### <a name="g-check-newly-added-logins"></a>Ж. Проверка новых имен входа

Чтобы проверить вновь добавленное имя входа, выполните следующую команду T-SQL:

```sql
SELECT *
FROM sys.server_principals;
GO
```

## <a name="see-also"></a>См. также:

- [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)
- [Субъекты](../../relational-databases/security/authentication-access/principals-database-engine.md)
- [Политика паролей](../../relational-databases/security/password-policy.md)
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Создание имени для входа](../../relational-databases/security/authentication-access/create-a-login.md)

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2017)|[Отдельная база данных/эластичный пул Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-current)|[Управляемый экземпляр Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-mi-current)|**_\* Хранилище данных<br />SQL \*_**|[Analytics Platform<br />System (PDW)](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-data-warehouse"></a>Хранилище данных SQL Azure

## <a name="syntax"></a>Синтаксис

```
-- Syntax for Azure SQL Data Warehouse
CREATE LOGIN login_name
 { WITH <option_list> }

<option_list> ::=
    PASSWORD = { 'password' }
    [ , SID = sid ]
```

## <a name="arguments"></a>Аргументы

*login_name* — указывает имя пользователя для создаваемого имени входа. База данных SQL Azure поддерживает только имена входа SQL.

PASSWORD **='** password**'*  — указывает пароль для создаваемого имени входа SQL. Выбирайте надежные пароли. Дополнительные сведения см. в статьях [Надежные пароли](../../relational-databases/security/strong-passwords.md) и [Политика паролей](../../relational-databases/security/password-policy.md). Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] сохраненные сведения о пароле вычисляются с помощью SHA-512 соленого пароля.

В паролях учитывается регистр символов. Пароли всегда должны содержать не менее восьми символов и не могут содержать более 128 символов. Пароли могут содержать символы a-z, A-Z, 0-9 и большинство неалфавитных символов. Пароли не могут содержать одиночные кавычки или *login_name*.

 SID = *sid* — используется для повторного создания имени входа. Применяется только к именам входа проверки подлинности SQL Server, но не относится к именам входа проверки подлинности Windows. Указывает идентификатор SID нового имени входа проверки подлинности SQL Server. Если этот параметр не используется, SQL Server назначает идентификатор SID автоматически. Структура идентификатора SID зависит от версии SQL Server. Для хранилища данных SQL это 32-байтовый (**binary(32)**) литерал, состоящий из `0x01060000000000640000000000000000` плюс 16 байт, представляющих GUID. Например, `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`.

## <a name="remarks"></a>Remarks

- В паролях учитывается регистр символов.
- Скрипт для передачи имен входа см. в разделе [Способы передачи имен входа и паролей между экземплярами SQL Server 2005 и SQL Server 2008](https://support.microsoft.com/kb/918992).
- При создании имени входа оно автоматически включается, и ему предоставляется разрешение **CONNECT SQL** уровня сервера.
- Для разрешения доступа [режим проверки подлинности](../../relational-databases/security/choose-an-authentication-mode.md) сервера должен соответствовать типу имени входа.
- Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="logins"></a>Имена входа

Инструкция **CREATE LOGIN** должна быть единственной инструкцией в пакете.

В некоторых методах подключения к хранилищу данных SQL, например **sqlcmd**, необходимо добавить имя сервера хранилища данных SQL к имени входа в строке подключения с помощью нотации *\<login>*@*\<server>*. Например, если имя входа — `login1`, а полное имя сервера хранилища данных SQL —`servername.database.windows.net`, то параметр *username* в строке подключения должен иметь вид `login1@servername`. Так как общая длина параметра *username* составляет 128 символов, длина имени *login_name* ограничена до 127 символов минус длина имени сервера. В примере `login_name` может иметь длину не более 117 символов, поскольку `servername` имеет длину 10 символов.

В хранилище данных SQL для создания имени входа необходимо подключение к базе данных master.

Правила SQL Server позволяют создать имя входа для проверки подлинности SQL Server в формате \<loginname>@\<servername>. Если сервер [!INCLUDE[ssSDS](../../includes/sssds-md.md)] — **myazureserver**, а имя входа —**myemail@live.com**, то необходимо указать имя входа в виде **myemail@live.com@myazureserver**.

В хранилище данных SQL данные имени входа необходимы для проверки подлинности подключения, и правила брандмауэра на уровне сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедиться в том, что база данных имеет последнюю версию таблицы имен входа, выполните инструкцию [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).

Дополнительные сведения об именах входа для Хранилища данных SQL см. в статье [Управление базами данных и именами входа в Базу данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins).

## <a name="permissions"></a>Разрешения

Создавать имена входа могут только имена входа участника уровня сервера (созданного процессом подготовки) или члены роли базы данных `loginmanager` в базе данных master. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) и [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).

## <a name="after-creating-a-login"></a>После создания имени входа

Созданное имя входа может подключаться к хранилищу данных SQL, но имеет разрешения только для роли **public**. Попробуйте выполнить некоторые из приведенных ниже действий.

- Чтобы подключиться к базе данных, создайте пользователя базы данных для имени входа. Дополнительные сведения см. в статье об инструкции [CREATE USER](../../t-sql/statements/create-user-transact-sql.md).
- Чтобы предоставить разрешения пользователю базы данных, используйте инструкцию **ALTER SERVER ROLE** ... **ADD MEMBER** для добавления пользователя в одну из встроенных ролей базы данных или пользовательскую роль либо напрямую предоставьте пользователю разрешения с помощью инструкции [GRANT](grant-transact-sql.md). Дополнительные сведения см. в разделах [Пользователи без прав администратора](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users), [Дополнительные административные роли на уровне сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) и [GRANT](grant-transact-sql.md).
- Чтобы предоставить разрешения уровня сервера, создайте пользователя базы данных в базе данных master и с помощью инструкции **ALTER SERVER ROLE** ... **ADD MEMBER** добавьте пользователя в одну из административных ролей сервера. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) и [Роли сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).

- Воспользуйтесь инструкцией **GRANT**, чтобы предоставить разрешения уровня сервера новому имени входа или роли, содержащей это имя входа. Дополнительные сведения см. в статье [GRANT](../../t-sql/statements/grant-transact-sql.md).

## <a name="examples"></a>Примеры

### <a name="a-creating-a-login-with-a-password"></a>A. Создание имени входа с паролем

В следующем примере создается имя входа для конкретного пользователя и назначается пароль.

```sql
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';
GO
```

### <a name="b-creating-a-login-from-a-sid"></a>Б. Создание имени входа на основе SID

 В следующем примере создается имя входа с проверкой подлинности SQL Server и определяется его SID.

```sql
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';

SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';
GO
```

Наш запрос возвращает идентификатор SID 0x241C11948AEEB749B0D22646DB1A19F2. Ваш запрос вернет другое значение. Следующие выражения удаляют имя входа, а затем повторно создают имя входа. Используйте SID из предыдущего запроса.

```sql
DROP LOGIN TestLogin;
GO

CREATE LOGIN TestLogin
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;

SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';
GO
```

## <a name="see-also"></a>См. также:

- [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)
- [Субъекты](../../relational-databases/security/authentication-access/principals-database-engine.md)
- [Политика паролей](../../relational-databases/security/password-policy.md)
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Создание имени для входа](../../relational-databases/security/authentication-access/create-a-login.md)

::: moniker-end
::: moniker range=">=aps-pdw-2016||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2017)|[Отдельная база данных/эластичный пул Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-current)|[Управляемый экземпляр Базы данных SQL<br />](create-login-transact-sql.md?view=azuresqldb-mi-current)|[Хранилище данных<br />SQL](create-login-transact-sql.md?view=azure-sqldw-latest)|**_\* Analytics<br />Platform System (PDW) \*_**

&nbsp;

## <a name="analytics-platform-system"></a>Система платформы аналитики

## <a name="syntax"></a>Синтаксис

```
-- Syntax for Analytics Platform System
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }

<option_list1> ::=
    PASSWORD = { 'password' } [ MUST_CHANGE ]
    [ , <option_list> [ ,... ] ]
  
<option_list> ::=
      CHECK_EXPIRATION = { ON | OFF}
    | CHECK_POLICY = { ON | OFF}
```

## <a name="arguments"></a>Аргументы

*login_name* — указывает имя пользователя для создаваемого имени входа. Имена входа бывают четырех типов: имена входа SQL Server, имена входа Windows, имена входа, сопоставленные с помощью сертификата, а также имена входа, сопоставленные с помощью асимметричного ключа. При создании имен входа, сопоставленных с учетной записью домена Windows, необходимо использовать имя входа версии, более ранней, чем Windows 2000, с форматом [\<domainName>\\<login_name>]. Нельзя использовать имя участника-пользователя в формате login_name@DomainName. См. приведенный ниже пример Г. Имена входа проверки подлинности имеют тип **sysname**, должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md) и не могут содержать символ "**\\**". Имена входа Windows могут содержать символы «**\\**». Имена входа, основанные на пользователях Active Directory, могут иметь не более 21 символа в длину.

PASSWORD **='**_password_' Применяется только к именам входа SQL Server. Задает пароль для создаваемого имени входа. Выбирайте надежные пароли. Дополнительные сведения см. в статьях [Надежные пароли](../../relational-databases/security/strong-passwords.md) и [Политика паролей](../../relational-databases/security/password-policy.md). Начиная с SQL Server 2012 (11.x), сохраненные сведения о пароле вычисляются с помощью SHA-512 "соленого" пароля.

В паролях учитывается регистр символов. Пароли всегда должны содержать не менее восьми символов и не могут содержать более 128 символов. Пароли могут содержать символы a-z, A-Z, 0-9 и большинство неалфавитных символов. Пароли не могут содержать одиночные кавычки или *login_name*.

MUST_CHANGE применяется только к именам входа SQL Server. Если этот параметр задан, то при первом использовании нового имени входа SQL Server запрашивает новый пароль.

CHECK_EXPIRATION **=** { ON | **OFF** } — применяется только к именам входа SQL Server. Указывает, должна ли политика истечения срока действия паролей принудительно применяться к этому имени входа. Значение по умолчанию — OFF.

CHECK_POLICY **=** { **ON** | OFF } — применяется только к именам входа SQL Server. Указывает, что политики паролей Windows компьютера, на котором работает SQL Server, должны принудительно применяться к этому имени входа. Значение по умолчанию — ON.

Если политика Windows требует надежных паролей, то пароль должен обладать по крайней мере тремя из следующих четырех качеств:

- Наличие символов верхнего регистра (A-Z).
- Наличие строчных символов (a-z).
- Числа (0-9).
- Один из неалфавитных символов, например пробел, _, @, *, ^, %! #, $ или &.

WINDOWS — указывает, что имя входа сопоставлено с именем входа Windows.

## <a name="remarks"></a>Remarks

- В паролях учитывается регистр символов.
- Если задан параметр MUST_CHANGE, то параметры CHECK_EXPIRATION и CHECK_POLICY должны иметь значение ON. В противном случае выполнение инструкции приведет к ошибке.
- Сочетание CHECK_POLICY = OFF и CHECK_EXPIRATION = ON не поддерживается.
- Если значение CHECK_POLICY равно OFF, то *lockout_time* сбрасывается и параметру CHECK_EXPIRATION также присваивается значение OFF.

> [!IMPORTANT]
> Параметры CHECK_EXPIRATION и CHECK_POLICY принудительно применяются только в Windows Server 2003 и более поздних версиях. Дополнительные сведения см. в разделе [Политика паролей](../../relational-databases/security/password-policy.md).

- Скрипт для передачи имен входа см. в разделе [Способы передачи имен входа и паролей между экземплярами SQL Server 2005 и SQL Server 2008](https://support.microsoft.com/kb/918992).
- При создании имени входа оно автоматически включается, и ему предоставляется разрешение **CONNECT SQL** уровня сервера.
- Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="permissions"></a>Разрешения

Создавать имена входа могут только пользователи с разрешением **ALTER ANY LOGIN** на сервере или имеющие членство в предопределенной роли сервера **securityadmin**. Дополнительные сведения см. в разделах [Роли уровня сервера](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) и [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).

## <a name="after-creating-a-login"></a>После создания имени входа

Созданное имя входа может подключаться к хранилищу данных SQL, но имеет разрешения только для роли **public**. Попробуйте выполнить некоторые из приведенных ниже действий.

- Чтобы подключиться к базе данных, создайте пользователя базы данных для имени входа. Дополнительные сведения см. в статье об инструкции [CREATE USER](../../t-sql/statements/create-user-transact-sql.md).
- Создайте определяемую пользователем роль сервера с помощью [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md). Воспользуйтесь инструкциями **ALTER SERVER ROLE** ... **ADD MEMBER** для добавления нового имени входа к определяемой пользователем роли сервера. Дополнительные сведения см. в статьях [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) и [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).
- Воспользуйтесь процедурой **sp_addsrvrolemember** для добавления имени входа к предопределенной роли сервера. Дополнительные сведения см. в разделе [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md) и [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).
- Воспользуйтесь инструкцией **GRANT**, чтобы предоставить разрешения уровня сервера новому имени входа или роли, содержащей это имя входа. Дополнительные сведения см. в статье [GRANT](../../t-sql/statements/grant-transact-sql.md).

## <a name="examples"></a>Примеры

### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>Ж. Создание имени входа для проверки подлинности SQL Server с паролем

В следующем примере создается имя входа `Mary7` с паролем `A2c3456`.

```sql
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;
```

### <a name="h-using-options"></a>З. Использование параметров

В следующем примере создается имя входа `Mary8` с паролем и дополнительными аргументами.

```sql
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,
CHECK_EXPIRATION = ON,
CHECK_POLICY = ON;
```

### <a name="i-creating-a-login-from-a-windows-domain-account"></a>И. Создание имени входа на основе учетной записи домена Windows

В следующем примере имя входа создается на основе учетной записи домена Windows `Mary` в домене `Contoso`.

```sql
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;
GO
```

## <a name="see-also"></a>См. также:

- [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)
- [Субъекты](../../relational-databases/security/authentication-access/principals-database-engine.md)
- [Политика паролей](../../relational-databases/security/password-policy.md)
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Создание имени входа](../../relational-databases/security/authentication-access/create-a-login.md)

---

::: moniker-end
