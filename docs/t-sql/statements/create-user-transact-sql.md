---
title: "Создание пользователя (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/28/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WITHOUT_LOGIN_TSQL
- CREATE_USER_TSQL
- SQL13.SWB.DATABASEUSER.OWNEDSCHEMAS.F1
- WITHOUT LOGIN
- CREATE USER
- ALLOW_ENCRYPTED_VALUE_MODIFICATIONS
- ALLOW_ENCRYPTED_VALUE_MODIFICATIONS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- adding users
- WITHOUT LOGIN [SQL Server]
- CREATE USER statement
- database user additions [SQL Server]
- USER WITHOUT LOGIN [SQL Server]
- users [SQL Server], adding
- users [SQL Server]
ms.assetid: 01de7476-4b25-4d58-85b7-1118fe64aa80
caps.latest.revision: 111
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47004dfe9ec810fec68a63849755021690f98fdb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-user-transact-sql"></a>CREATE USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Добавляет нового пользователя в текущую базу данных. Ниже перечислены одиннадцать типов пользователей с помощью образца наиболее базовый синтаксис:  
  
**Пользователи на основе имен входа в базе данных master** это наиболее распространенный тип пользователя.  
  
-   Пользователь с именем входа на основе учетной записи Windows Active Directory. `CREATE USER [Contoso\Fritz];`     
-   Пользователь с именем входа, задаваемым по группе Windows. `CREATE USER [Contoso\Sales];`   
-   Пользователь с именем входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. `CREATE USER Mary;`  
  
**Пользователи, которые проходят проверку подлинности на базе** рекомендуется для того, чтобы повысить переносимость базы данных.  
 Всегда разрешено в [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. Допускается только в автономной базе данных в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
-   Пользователь, соответствующий пользователю Windows без имени входа. `CREATE USER [Contoso\Fritz];`    
-   Пользователь, соответствующий группе Windows без имени входа. `CREATE USER [Contoso\Sales];`  
-   Пользователь в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] или [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] на основе проверки пользователей Azure Active Directory. `CREATE USER [Contoso\Fritz] FROM EXTERNAL PROVIDER;`     

-   Пользователь автономной базы данных с паролем. (Недоступно в [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].)`CREATE USER Mary WITH PASSWORD = '********';`   
  
**Пользователям, соответствующим участникам Windows, которые подключаются через имена входа группы Windows**  
  
-   Пользователь, соответствующий пользователю Windows, который не имеет имени входа, но может подключаться к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] за счет членства в роли Windows. `CREATE USER [Contoso\Fritz];`  
  
-   Пользователь, соответствующий группе Windows, которая не имеет имени входа, но может подключаться к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] за счет членства в другой роли Windows. `CREATE USER [Contoso\Fritz];`  
  
**Пользователи, которые не удается проверить подлинность** эти пользователи не смогут войти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
-   Пользователь без имени входа. Не может выполнить вход, но ему можно предоставлять разрешения. `CREATE USER CustomApp WITHOUT LOGIN;`    
-   Пользователь, связанный с сертификатом. Не может выполнить вход, но может предоставлять разрешения и подписывать модули. `CREATE USER TestProcess FOR CERTIFICATE CarnationProduction50;`  
-   Пользователь, связанный с асимметричным ключом. Не может выполнить вход, но может предоставлять разрешения и подписывать модули. `CREATE User TestProcess FROM ASYMMETRIC KEY PacificSales09;`   
 
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Syntax Users based on logins in master  
CREATE USER user_name   
    [   
        { FOR | FROM } LOGIN login_name   
    ]  
    [ WITH <limited_options_list> [ ,... ] ]   
[ ; ]  
  
--Users that authenticate at the database  
CREATE USER   
    {  
      windows_principal [ WITH <options_list> [ ,... ] ]  
  
    | user_name WITH PASSWORD = 'password' [ , <options_list> [ ,... ]   
    | Azure_Active_Directory_principal FROM EXTERNAL PROVIDER   
    }  
  
 [ ; ]  
  
--Users based on Windows principals that connect through Windows group logins  
CREATE USER   
    {   
          windows_principal [ { FOR | FROM } LOGIN windows_principal ]  
        | user_name { FOR | FROM } LOGIN windows_principal  
}  
    [ WITH <limited_options_list> [ ,... ] ]   
[ ; ]  
  
--Users that cannot authenticate   
CREATE USER user_name   
    {  
         WITHOUT LOGIN [ WITH <limited_options_list> [ ,... ] ]  
       | { FOR | FROM } CERTIFICATE cert_name   
       | { FOR | FROM } ASYMMETRIC KEY asym_key_name   
    }  
 [ ; ]  
  
<options_list> ::=  
      DEFAULT_SCHEMA = schema_name  
    | DEFAULT_LANGUAGE = { NONE | lcid | language name | language alias }  
    | SID = sid   
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ] ]  
  
<limited_options_list> ::=  
      DEFAULT_SCHEMA = schema_name ]   
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ] ]  
  
-- SQL Database syntax when connected to a federation member  
CREATE USER user_name  
[;]  
```  

```  
-- Syntax for Azure SQL Data Warehouse  
  
CREATE USER user_name   
    [ { { FOR | FROM } { LOGIN login_name }   
      | WITHOUT LOGIN  
    ]   
    [ WITH DEFAULT_SCHEMA = schema_name ]  
[;]

CREATE USER Azure_Active_Directory_principal FROM EXTERNAL PROVIDER  
    [ WITH DEFAULT_SCHEMA = schema_name ]  
[;]
``` 
  
```  
-- Syntax for Parallel Data Warehouse  
  
CREATE USER user_name   
    [ { { FOR | FROM }  
      {   
        LOGIN login_name   
      }   
      | WITHOUT LOGIN  
    ]   
    [ WITH DEFAULT_SCHEMA = schema_name ]  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_пользователя*  
 Указывает имя, по которому пользователь идентифицируется в этой базе данных. *имя_пользователя* — **sysname**. Он может иметь длину до 128 символов. Когда создается пользователь, соответствующий участнику Windows, именем пользователя становится имя участника Windows, если не указано другое имя.  
  
 Имя входа *login_name*  
 Указывает имя входа, для которого создается пользователь базы данных. *login_name* должно быть допустимым именем входа на сервере. Может быть именем входа, соответствующим участнику Windows (пользователю или группе) или именем входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда это имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входит в базу данных, оно получает имя и идентификатор создаваемого пользователя базы данных. При создании имени входа, сопоставленного с участником Windows, используйте формат **[***\<domainName >*  **\\**   *\<loginName >***]**. Примеры см. в разделе [сводку синтаксиса](#SyntaxSummary).  
  
 Если инструкция CREATE USER — единственная инструкция в пакете SQL, то база данных SQL Windows Azure поддерживает предложение WITH LOGIN. Если инструкция CREATE USER не единственная в пакете SQL или выполняется в динамическом коде SQL, предложение WITH LOGIN не поддерживается.  
  
 Значение DEFAULT_SCHEMA = *schema_name*  
 Указывает первую схему, которую найдет сервер, после того, как он получит имена объектов для пользователя данной базы данных.  
  
 "*windows_principal*"  
 Указывает участника Windows, для которого создается пользователь базы данных. *Windows_principal* может быть пользователь Windows или группы Windows. Пользователь будет создаваться даже в том случае, если *windows_principal* не имеет имени входа. При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если *windows_principal* не имеет имени входа Windows, участник должен пройти проверку подлинности в [!INCLUDE[ssDE](../../includes/ssde-md.md)] через членство в группе Windows, который имеет имя входа, или строка соединения должна Укажите автономной базы данных в качестве исходного каталога. При создании пользователя на основе участника Windows, используйте формат **[***\<domainName >*  **\\**   *\< loginName >***]**. Примеры см. в разделе [сводку синтаксиса](#SyntaxSummary). Пользователи, основанный на количестве пользователей Active Directory ограничены имена менее 21 символов.    
  
 "*Azure_Active_Directory_principal*"  
 **Применяется к**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)], [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].  
  
 Указывает участника Azure Active Directory, для которого создается пользователь базы данных. *Azure_Active_Directory_principal* может быть пользователя Azure Active Directory или группы Azure Active Directory. (Azure Active Directory — пользователи не могут иметь имена входа Windows [!INCLUDE[ssSDS](../../includes/sssds-md.md)]; только пользователи базы данных.) Строку подключения необходимо указать автономной базы данных в качестве исходного каталога. 

 Для пользователей используйте полный псевдоним их основного домена.   
 
-   `CREATE USER [bob@contoso.com] FROM EXTERNAL PROVIDER;`  
  
-   `CREATE USER [alice@fabrikam.onmicrosoft.com] FROM EXTERNAL PROVIDER;`

 Для групп безопасности, используйте *отображаемое имя* группы безопасности. Для *Медсестрам* группы безопасности, следует использовать:  
  
-   `CREATE USER [Nurses] FROM EXTERNAL PROVIDER;`  
  
 Дополнительные сведения см. в статье [Подключение к базе данных SQL с использованием проверки подлинности Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication).  
  
С ПАРОЛЕМ = "*пароль*"  
 **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Может использоваться только в автономной базе данных. Задает пароль для создаваемого пользователя. Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]сохраненные сведения о пароле вычисляется с помощью SHA-512 криптографического пароля.  
  
WITHOUT LOGIN  
 Указывает, что пользователь не должен сопоставляться с существующим именем входа.  
  
СЕРТИФИКАТ *cert_name*  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Указывает сертификат, для которого создается пользователь базы данных.  
  
АСИММЕТРИЧНЫЙ ключ *asym_key_name*  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Указывает асимметричный ключ, для которого создается пользователь базы данных.  
  
DEFAULT_LANGUAGE = *{NONE | \<lcid > | \<название языка > | \<псевдоним языка >}*  
 **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Задает язык по умолчанию для нового пользователя. Если для пользователя задается язык по умолчанию, а затем язык базы данных по умолчанию изменяется, то язык по умолчанию для пользователя сохраняет указанное значение. Если язык по умолчанию не указывается, то языком по умолчанию для пользователя становится язык по умолчанию для базы данных. Если язык по умолчанию для пользователя не указывается, а язык по умолчанию для базы данных изменяется после создания пользователя, то язык по умолчанию для пользователя меняется на новый язык по умолчанию для базы данных.  
  
> [!IMPORTANT]  
>  *DEFAULT_LANGUAGE* используется только для пользователя автономной базы данных.  
  
SID = *sid*  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применимо только для пользователей с паролями (проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) в автономной базе данных. Указывает идентификатор SID нового пользователя базы данных. Если этот параметр не выбран, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначает идентификатор SID автоматически. Используйте параметр идентификатора SID для создания пользователей в нескольких базах данных с одинаковыми идентификаторами SID. Это полезно при создании пользователей в нескольких базах данных для подготовки отказоустойчивого Always On. Чтобы определить идентификатор безопасности пользователя, запрос sys.database_principals.  
  
ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ON | **OFF** ]]  
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Отключает проверки шифрованных метаданных на сервере в операциях массового копирования. Это позволяет пользователю массово Копировать зашифрованные данные между таблицами или базами данных, без расшифровки данных. Значение по умолчанию — OFF.  
  
> [!WARNING]  
>  Неправильное использование этого параметра может привести к повреждению данных. Дополнительные сведения см. в разделе [перенос конфиденциальных данных с помощью постоянного шифрования](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).  
  
## <a name="remarks"></a>Замечания  
 Если предложение FOR LOGIN не указано, новый пользователь базы данных будет сопоставлен с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеющим такое же имя.  
  
 Схемой по умолчанию будет первая схема, которую найдет сервер, после того, как получит имена объектов для данного пользователя базы данных. Если не указано иное, схемой по умолчанию будет владелец объектов, создаваемых этим пользователем базы данных.  
  
 Если пользователь имеет схему по умолчанию, будет использоваться эта схема. Если у пользователя нет схемы по умолчанию, но он является членом группы, которая имеет схему по умолчанию, используется схема по умолчанию группы. Если пользователь не имеет схемы по умолчанию и является членом нескольких групп, схемой по умолчанию для этого пользователя будет схема по умолчанию группы Windows с минимальным значением principal_id и явно заданной схемой по умолчанию. (Невозможно явно выбрать одну из доступных схем по умолчанию как предпочтительную.) Если нельзя определить схему по умолчанию для пользователя, **dbo** схема будет использоваться.  
  
 Значение DEFAULT_SCHEMA может быть установлено до создания схемы, на которую оно указывает.  
  
 Значение DEFAULT_SCHEMA не может указываться при создании пользователя, сопоставленного с сертификатом или асимметричным ключом.  
  
 Значение параметра DEFAULT_SCHEMA не учитывается, если пользователь является членом предопределенной роли сервера sysadmin. Для всех членов предопределенной роли сервера sysadmin по умолчанию установлена схема `dbo`.  
  
 Предложение WITHOUT LOGIN создает пользователя, который не сопоставляется с именем входа SQL Server. Такой пользователь может подключиться к базе данных как guest. Этому пользователю без имени входа можно назначать разрешения, и когда контекст безопасности меняется на пользователя без имени входа, то исходные пользователи получают его разрешения. См. пример [г. Создание и использование пользователя без имени входа](#withoutLogin).  
  
 Только для пользователей, сопоставленных с участниками Windows может содержать символ обратной косой черты (**\\**).  
  
 С помощью инструкции CREATE USER нельзя создать пользователя guest, потому что пользователь guest уже существует в каждой базе данных. Активировать пользователя guest можно, предоставив ему разрешение CONNECT, как показано далее:  
  
```  
GRANT CONNECT TO guest;  
GO  
```  
  
 Сведения о пользователях базы данных можно увидеть в [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) представления каталога.  
  
##  <a name="SyntaxSummary"></a>Сводка синтаксиса  
 **Пользователи, на основе имен входа в базе данных master**  
  
 В следующем списке показан возможный синтаксис для пользователей, связанных с именами входа. Параметры схемы по умолчанию не указываются.  
  
-   `CREATE USER [Domain1\WindowsUserBarry]`  
-   `CREATE USER [Domain1\WindowsUserBarry] FOR LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsUserBarry] FROM LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FOR LOGIN [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FROM LOGIN [Domain1\WindowsGroupManagers]`  
-   `CREATE USER SQLAUTHLOGIN`  
-   `CREATE USER SQLAUTHLOGIN FOR LOGIN SQLAUTHLOGIN`  
-   `CREATE USER SQLAUTHLOGIN FROM LOGIN SQLAUTHLOGIN`  
  
**Пользователи, проходящие проверку подлинности базы данных**  
  
 В следующем списке показан возможный синтаксис для пользователей, которые могут использоваться только в автономной базе данных. Созданные пользователи не будут связаны с именами входа в **master** базы данных. Параметры схемы и языковые параметры, задаваемые по умолчанию, не указываются.  
  
> [!IMPORTANT]  
>  Этот синтаксис предоставляет пользователям доступ к базе данных и новый доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   `CREATE USER [Domain1\WindowsUserBarry]`  
-   `CREATE USER [Domain1\WindowsGroupManagers]`  
-   `CREATE USER Barry WITH PASSWORD = 'sdjklalie8rew8337!$d'`  
  
**Пользователи, на основе участников Windows без имени для входа в базе данных master**  
  
 В следующем списке показан возможный синтаксис для пользователей, имеющих доступ к [!INCLUDE[ssDE](../../includes/ssde-md.md)] в качестве группы Windows, но не имеют имени входа в **master**. Такой синтаксис можно использовать во всех типах базы данных. Параметры схемы и языковые параметры, задаваемые по умолчанию, не указываются.  
  
 Этот синтаксис аналогичен пользователям, соответствующим именам входа в базе данных master, однако пользователи данной категории не имеют имени входа в базе данных master. Пользователь должен получать доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] с помощью имени входа группы Windows.  
  
 Этот синтаксис аналогичен пользователям автономной базы данных, соответствующим участникам Windows, однако пользователи данной категории не получают новый доступ к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   `CREATE USER [Domain1\WindowsUserBarry]`  
-   `CREATE USER [Domain1\WindowsUserBarry] FOR LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsUserBarry] FROM LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FOR LOGIN [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FROM LOGIN [Domain1\WindowsGroupManagers]`  
  
**Пользователи, которые не удается пройти проверку подлинности**  
  
 В следующем списке показан возможный синтаксис для пользователей, которые не могут выполнять вход в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   `CREATE USER RIGHTSHOLDER WITHOUT LOGIN`  
-   `CREATE USER CERTUSER FOR CERTIFICATE SpecialCert`  
-   `CREATE USER CERTUSER FROM CERTIFICATE SpecialCert`  
-   `CREATE USER KEYUSER FOR ASYMMETRIC KEY SecureKey`  
-   `CREATE USER KEYUSER FROM ASYMMETRIC KEY SecureKey`  
  
## <a name="security"></a>безопасность  
 При создании пользователя предоставляется доступ к базе данных, однако доступ к объектам в базе данных не предоставляется автоматически. После создания пользователи обычно добавляются в роли базы данных, которые имеют разрешение на доступ к объектам базы данных, либо разрешения на объект предоставляются непосредственно пользователю. Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
### <a name="special-considerations-for-contained-databases"></a>Замечания, относящиеся к автономным базам данных  
 При подключении к автономной базе данных, если пользователь не имеет имени входа в **master** базы данных, строка подключения должна содержать имя автономной базы данных как исходного каталога. Параметр исходного каталога всегда обязателен для пользователя автономной базы данных с паролем.  
  
 Создание пользователей в автономной базе данных позволяет отделить базу данных от экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], что позволяет легко переместить ее в другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [автономных баз данных](../../relational-databases/databases/contained-databases.md) и [пользователи автономной базы данных — создание переносимой базы данных](../../relational-databases/security/contained-database-users-making-your-database-portable.md). Для изменения пользователя базы данных от пользователя на основе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности имени входа для пользователя автономной базы данных с паролем, в разделе [sp_migrate_user_to_contained &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md).  
  
 В автономной базе данных пользователям не обязательно иметь имена входа **master** базы данных. Администраторы [!INCLUDE[ssDE](../../includes/ssde-md.md)] должны учитывать, что доступ к автономной базе данных можно предоставлять на уровне базы данных, а не на уровне компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Дополнительные сведения см. в статье [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md).  
  
 При использовании пользователей автономной базы данных [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] настройте доступ с помощью правила брандмауэра уровня базы данных вместо правила брандмауэра уровня сервера. Дополнительные сведения см. в разделе [sp_set_database_firewall_rule &#40; База данных Azure SQL &#41; ](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md).
 
Для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] пользователей автономной базы данных, среда SSMS можно поддерживают многофакторную проверку подлинности. Дополнительные сведения см. в разделе [Поддержка SSMS для Azure AD MFA с использованием Базы данных SQL и хранилища данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/).  
  
### <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY USER для базы данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-database-user-based-on-a-sql-server-login"></a>A. Создание пользователя базы данных, соответствующего имени входа SQL Server  
 В следующем примере сначала создается имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `AbolrousHazem`, а затем создается соответствующий пользователь `AbolrousHazem` в базе данных `AdventureWorks2012`.  
  
```  
CREATE LOGIN AbolrousHazem   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
```   
Изменить базу данных пользователей. Например, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать `USE AdventureWorks2012` инструкции. В [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], необходимо создать новое подключение к пользовательской базе данных.

```   
CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
GO   
```  
  
### <a name="b-creating-a-database-user-with-a-default-schema"></a>Б. Создание пользователя базы данных со схемой по умолчанию  
 В следующем примере вначале создается имя входа `WanidaBenshoof` с паролем на сервер, а затем в базе данных создается соответствующий пользователь `Wanida` со схемой по умолчанию `Marketing`.  
  
```  
CREATE LOGIN WanidaBenshoof   
    WITH PASSWORD = '8fdKJl3$nlNv3049jsKK';  
USE AdventureWorks2012;  
CREATE USER Wanida FOR LOGIN WanidaBenshoof   
    WITH DEFAULT_SCHEMA = Marketing;  
GO  
```  
  
### <a name="c-creating-a-database-user-from-a-certificate"></a>В. Создание пользователя базы данных из сертификата  
 В следующем примере в базе данных создается пользователь `JinghaoLiu` из сертификата `CarnationProduction50`.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE AdventureWorks2012;  
CREATE CERTIFICATE CarnationProduction50  
    WITH SUBJECT = 'Carnation Production Facility Supervisors',  
    EXPIRY_DATE = '11/11/2011';  
GO  
CREATE USER JinghaoLiu FOR CERTIFICATE CarnationProduction50;  
GO   
```  
  
###  <a name="withoutLogin"></a> Г. Создание и использование пользователя без имени входа  
 В следующем примере создается пользователь базы данных `CustomApp`, который не сопоставляется с именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Затем пример предоставляет пользователю `adventure-works\tengiz0` разрешение на олицетворение `CustomApp` пользователя.  
  
```  
USE AdventureWorks2012 ;  
CREATE USER CustomApp WITHOUT LOGIN ;  
GRANT IMPERSONATE ON USER::CustomApp TO [adventure-works\tengiz0] ;  
GO   
```  
  
 Для использования учетных данных `CustomApp` , пользователь `adventure-works\tengiz0` выполняет следующее выражение.  
  
```  
EXECUTE AS USER = 'CustomApp' ;  
GO  
```  
  
 Для возврата к учетным данным `adventure-works\tengiz0` , пользователь выполняет следующее выражение.  
  
```  
REVERT ;  
GO  
```  
  
### <a name="e-creating-a-contained-database-user-with-password"></a>Д. Создание пользователя автономной базы данных с паролем  
 В следующем примере создается пользователь автономной базы данных с паролем. Этот пример можно выполнить только в автономной базе данных.  
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Этот пример работает в [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)], если удаляется DEFAULT_LANGUAGE.  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE USER Carlo  
WITH PASSWORD='RN92piTCh%$!~3K9844 Bl*'  
    , DEFAULT_LANGUAGE=[Brazilian]  
    , DEFAULT_SCHEMA=[dbo]  
GO   
```  
  
### <a name="f-creating-a-contained-database-user-for-a-domain-login"></a>Е. Создание пользователя автономной базы данных для имени входа домена  
 В следующем примере создается пользователь автономной базы данных для имени входа Fritz в домене Contoso. Этот пример можно выполнить только в автономной базе данных.  
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE USER [Contoso\Fritz] ;  
GO   
```  
  
### <a name="g-creating-a-contained-database-user-with-a-specific-sid"></a>Ж. Создание пользователя автономной базы данных с конкретным идентификатором SID  
 В следующем примере создается пользователь автономной базы данных с проверкой подлинности SQL Server, имя пользователя — CarmenW. Этот пример можно выполнить только в автономной базе данных.  
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE USER CarmenW WITH PASSWORD = 'a8ea v*(Rd##+'  
, SID = 0x01050000000000090300000063FF0451A9E7664BA705B10E37DDC4B7;  
  
```  
  
### <a name="h-creating-a-user-to-copy-encrypted-data"></a>З. Создание пользователя копирование зашифрованных данных  
 В следующем примере создается пользователь, который можно скопировать данные, защищенные с помощью функции постоянного шифрования из одного набора таблиц, содержащих зашифрованные столбцы, другой набор таблиц с зашифрованными столбцами (в той же или другой базе данных).  Дополнительные сведения см. в разделе [перенос конфиденциальных данных с помощью постоянного шифрования](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).  
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
```  
CREATE USER [Chin]   
WITH   
      DEFAULT_SCHEMA = dbo  
    , ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON ;  
```  
  

## <a name="next-steps"></a>Следующие шаги  
После создания пользователя, рассмотрите возможность добавления пользователя к роли базы данных с помощью [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) инструкции.  
Может также потребоваться [разрешения объекта GRANT](../../t-sql/statements/grant-object-permissions-transact-sql.md) роли для доступа к таблицам. Общие сведения о модели безопасности SQL Server см. в разделе [разрешений](../../relational-databases/security/permissions-database-engine.md).   
  
## <a name="see-also"></a>См. также:  
 [Создание пользователя базы данных](../../relational-databases/security/authentication-access/create-a-database-user.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [ALTER USER (Transact-SQL)](../../t-sql/statements/alter-user-transact-sql.md)   
 [УДАЛИТЬ пользователя &#40; Transact-SQL &#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Автономные базы данных](../../relational-databases/databases/contained-databases.md)   
 [Подключение к базе данных SQL с использованием аутентификации Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)   
 [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  



