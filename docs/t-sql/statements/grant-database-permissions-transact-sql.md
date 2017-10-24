---
title: "ПРЕДОСТАВИТЬ разрешения базы данных (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server]
- database permissions [SQL Server]
- granting permissions [SQL Server], databases
- permissions [SQL Server], databases
- database permissions [SQL Server], granting
- GRANT statement, databases
ms.assetid: 499e5ed6-945c-4791-ab45-68dec0b9c289
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 87e47c70ab448aae1a2803e2a3302a4f4361b373
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="grant-database-permissions-transact-sql"></a>GRANT, предоставление разрешений на базу данных (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Предоставляет разрешения на базу данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GRANT <permission> [ ,...n ]    
    TO <database_principal> [ ,...n ] [ WITH GRANT OPTION ]  
    [ AS <database_principal> ]  
  
<permission>::=    
permission | ALL [ PRIVILEGES ]  
  
<database_principal> ::=   
    Database_user   
  | Database_role   
  | Application_role   
  | Database_user_mapped_to_Windows_User   
  | Database_user_mapped_to_Windows_Group   
  | Database_user_mapped_to_certificate   
  | Database_user_mapped_to_asymmetric_key   
  | Database_user_with_no_login    
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Указывает разрешение, которое может быть предоставлено в базе данных. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 ALL  
 Этот параметр не предоставляет все возможные разрешения. Предоставление разрешения ALL эквивалентно предоставлению следующих разрешений: BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE и CREATE VIEW.  
  
 PRIVILEGES  
 Включено для обеспечения совместимости с требованиями ISO. Не изменяет работу ALL.  
  
 WITH GRANT OPTION  
 Показывает, что участнику будет дана возможность предоставлять указанное разрешение другим участникам.  
  
 AS \<database_principal > Указывает участника, от которого участник, выполняющий данный запрос, наследует право предоставления разрешения.  
  
 *Пользователь_базы_данных*  
 Указывает пользователя базы данных.  
  
 *Database_role*  
 Указывает роль базы данных.  
  
 *Application_role*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 Указывает роль приложения.  
  
 *Database_user_mapped_to_Windows_User*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с пользователем Windows.  
  
 *Database_user_mapped_to_Windows_Group*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с группой Windows.  
  
 *Database_user_mapped_to_certificate*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с сертификатом.  
  
 *Database_user_mapped_to_asymmetric_key*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает пользователя базы данных, сопоставленного с асимметричным ключом.  
  
 *Database_user_with_no_login*  
 Указывает пользователя базы данных, не сопоставленного с субъектом серверного уровня.  
  
## <a name="remarks"></a>Замечания  
  
> [!IMPORTANT]  
>  Сочетание разрешений ALTER и REFERENCE в некоторых случаях может позволить просматривать данные или выполнять несанкционированные функции. Например: пользователь с разрешением ALTER на таблицу и разрешением REFERENCE на функцию может создавать вычисляемый столбец на основе функции и выполнять ее. В этом случае пользователю также требуется разрешение SELECT на вычисляемый столбец.  
  
 База данных — это защищаемый объект, хранящийся на сервере, который является родителем базы данных в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно предоставлять в базе данных, перечислены в следующей таблице вместе с общими разрешениями, неявно содержащими их.  
  
|Разрешение в базе данных|Содержится в разрешении базы данных|Подразумевается в разрешении сервера|  
|-------------------------|------------------------------------|----------------------------------|  
|ADMINISTER DATABASE BULK OPERATIONS<br/>**Область применения:** [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].|CONTROL|CONTROL SERVER|
|ALTER|CONTROL|ALTER ANY DATABASE|  
|ALTER ANY APPLICATION ROLE|ALTER|CONTROL SERVER|  
|ALTER ANY ASSEMBLY|ALTER|CONTROL SERVER|  
|ALTER ANY ASYMMETRIC KEY|ALTER|CONTROL SERVER|  
|ALTER ANY CERTIFICATE|ALTER|CONTROL SERVER|  
|ALTER ANY COLUMN ENCRYPTION KEY|ALTER|CONTROL SERVER|  
|ALTER ЛЮБОГО ОПРЕДЕЛЕНИЯ ГЛАВНОГО КЛЮЧА СТОЛБЦА|ALTER|CONTROL SERVER|  
|ALTER ANY CONTRACT|ALTER|CONTROL SERVER|  
|ALTER ANY DATABASE AUDIT|ALTER|ALTER ANY SERVER AUDIT|  
|ALTER ANY DATABASE DDL TRIGGER|ALTER|CONTROL SERVER|  
|ALTER ANY DATABASE EVENT NOTIFICATION|ALTER|ALTER ANY EVENT NOTIFICATION|  
|ALTER ANY DATABASE EVENT SESSION<br />**Область применения**: [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].|ALTER|ALTER ANY EVENT SESSION|  
|ALTER ANY DATABASE SCOPED CONFIGURATION<br /> **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|CONTROL|CONTROL SERVER|  
|ALTER ANY DATASPACE|ALTER|CONTROL SERVER|  
|ALTER ANY EXTERNAL DATA SOURCE|ALTER|CONTROL SERVER|  
|ALTER ANY EXTERNAL FILE FORMAT|ALTER|CONTROL SERVER|  
|ALTER ВНЕШНИЕ БИБЛИОТЕКИ <br /> **Область применения**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].|CONTROL|CONTROL SERVER |    
|ALTER ANY FULLTEXT CATALOG|ALTER|CONTROL SERVER|  
|ALTER ANY MASK|CONTROL|CONTROL SERVER|  
|ALTER ANY MESSAGE TYPE|ALTER|CONTROL SERVER|  
|ALTER ANY REMOTE SERVICE BINDING|ALTER|CONTROL SERVER|  
|ALTER ANY ROLE|ALTER|CONTROL SERVER|  
|ALTER ANY ROUTE|ALTER|CONTROL SERVER|  
|ALTER ANY SCHEMA|ALTER|CONTROL SERVER|  
|ALTER ANY SECURITY POLICY<br /> **Область применения**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|CONTROL|CONTROL SERVER|  
|ALTER ANY SERVICE|ALTER|CONTROL SERVER|  
|ALTER ANY SYMMETRIC KEY|ALTER|CONTROL SERVER|  
|ALTER ANY USER|ALTER|CONTROL SERVER|  
|AUTHENTICATE|CONTROL|AUTHENTICATE SERVER|  
|BACKUP DATABASE|CONTROL|CONTROL SERVER|  
|BACKUP LOG|CONTROL|CONTROL SERVER|  
|CHECKPOINT|CONTROL|CONTROL SERVER|  
|CONNECT|CONNECT REPLICATION|CONTROL SERVER|  
|CONNECT REPLICATION|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|CREATE AGGREGATE|ALTER|CONTROL SERVER|  
|CREATE ASSEMBLY|ALTER ANY ASSEMBLY|CONTROL SERVER|  
|CREATE ASYMMETRIC KEY|ALTER ANY ASYMMETRIC KEY|CONTROL SERVER|  
|CREATE CERTIFICATE|ALTER ANY CERTIFICATE|CONTROL SERVER|  
|CREATE CONTRACT|ALTER ANY CONTRACT|CONTROL SERVER|  
|CREATE DATABASE|CONTROL|CREATE ANY DATABASE|  
|CREATE DATABASE DDL EVENT NOTIFICATION|ALTER ANY DATABASE EVENT NOTIFICATION|CREATE DDL EVENT NOTIFICATION|  
|CREATE DEFAULT|ALTER|CONTROL SERVER|  
|CREATE FULLTEXT CATALOG|ALTER ANY FULLTEXT CATALOG|CONTROL SERVER|  
|CREATE FUNCTION|ALTER|CONTROL SERVER|  
|CREATE MESSAGE TYPE|ALTER ANY MESSAGE TYPE|CONTROL SERVER|  
|CREATE PROCEDURE|ALTER|CONTROL SERVER|  
|CREATE QUEUE|ALTER|CONTROL SERVER|  
|CREATE REMOTE SERVICE BINDING|ALTER ANY REMOTE SERVICE BINDING|CONTROL SERVER|  
|CREATE ROLE|ALTER ANY ROLE|CONTROL SERVER|  
|CREATE ROUTE|ALTER ANY ROUTE|CONTROL SERVER|  
|CREATE RULE|ALTER|CONTROL SERVER|  
|CREATE SCHEMA|ALTER ANY SCHEMA|CONTROL SERVER|  
|CREATE SERVICE|ALTER ANY SERVICE|CONTROL SERVER|  
|CREATE SYMMETRIC KEY|ALTER ANY SYMMETRIC KEY|CONTROL SERVER|  
|CREATE SYNONYM|ALTER|CONTROL SERVER|  
|CREATE TABLE|ALTER|CONTROL SERVER|  
|CREATE TYPE|ALTER|CONTROL SERVER|  
|CREATE VIEW|ALTER|CONTROL SERVER|  
|CREATE XML SCHEMA COLLECTION|ALTER|CONTROL SERVER|  
|DELETE|CONTROL|CONTROL SERVER|  
|Выполните|CONTROL|CONTROL SERVER|  
|EXECUTE ANY EXTERNAL SCRIPT <br /> **Область применения**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)].|CONTROL|CONTROL SERVER|   
|INSERT|CONTROL|CONTROL SERVER|  
|KILL DATABASE CONNECTION<br />**Область применения**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|CONTROL|ALTER ANY CONNECTION|  
|REFERENCES|CONTROL|CONTROL SERVER|  
|SELECT|CONTROL|CONTROL SERVER|  
|SHOWPLAN|CONTROL|ALTER TRACE|  
|SUBSCRIBE QUERY NOTIFICATIONS|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|UNMASK|CONTROL|CONTROL SERVER|  
|UPDATE|CONTROL|CONTROL SERVER|  
|VIEW ANY COLUMN ENCRYPTION KEY DEFINITION|CONTROL|VIEW ANY DEFINITION|  
|VIEW ANY COLUMN MASTER KEY DEFINITION|CONTROL|VIEW ANY DEFINITION|  
|VIEW DATABASE STATE|CONTROL|VIEW SERVER STATE|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое.  
  
 При использовании параметра AS налагаются следующие дополнительные требования.  
  
|AS *granting_principal*|Необходимо дополнительное разрешение|  
|------------------------------|------------------------------------|  
|Пользователь базы данных|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный имени входа Windows|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный группе Windows|Членство в группе Windows, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный сертификату|Членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, сопоставленный асимметричному ключу|Членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Пользователь базы данных, не сопоставленный ни с одним участником на уровне сервера|Разрешение IMPERSONATE для пользователя, членство в предопределенной роли базы данных db_securityadmin, членство в предопределенной роли базы данных db_owner или членство в предопределенной роли сервера sysadmin.|  
|Роль базы данных|Разрешение ALTER на роль, членство в предопределенной роли базы данных db_securityadmin, предопределенной роли базы данных db_owner или предопределенной роли сервера sysadmin.|  
|Роль приложения|Разрешение ALTER на роль, членство в предопределенной роли базы данных db_securityadmin, предопределенной роли базы данных db_owner или предопределенной роли сервера sysadmin.|  
  
 Владельцы объектов могут предоставлять разрешения на объекты, которыми они владеют. Участники, имеющие разрешение CONTROL на защищаемый объект, могут предоставлять разрешение на этот защищаемый объект.  
  
 Участники, которым предоставлено разрешение CONTROL SERVER, такие как члены предопределенной роли сервера &lt;legacyBold&gt;sysadmin&lt;/legacyBold&gt;, могут предоставлять любое разрешение на любой защищаемый объект сервера.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-permission-to-create-tables"></a>A. Предоставление разрешения на создание таблиц  
 В следующем примере предоставляется `CREATE TABLE` разрешение на `AdventureWorks` базы данных для пользователя `MelanieK`.  
  
```  
USE AdventureWorks;  
GRANT CREATE TABLE TO MelanieK;  
GO  
```  
  
### <a name="b-granting-showplan-permission-to-an-application-role"></a>Б. Предоставление разрешения SHOWPLAN роли приложения  
 В следующем примере роли приложения `SHOWPLAN` предоставляется разрешение `AdventureWorks2012` в базе данных `AuditMonitor`.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
```  
USE AdventureWorks2012;  
GRANT SHOWPLAN TO AuditMonitor;  
GO  
```  
  
### <a name="c-granting-create-view-with-grant-option"></a>В. Предоставление разрешения CREATE VIEW с параметром GRANT OPTION  
 В следующем примере пользователю `CREATE VIEW` предоставляется разрешение `AdventureWorks2012` в базе данных `CarmineEs` с правом предоставлять разрешение `CREATE VIEW` другим участникам.  
  
```  
USE AdventureWorks2012;  
GRANT CREATE VIEW TO CarmineEs WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


