---
title: Начало работы с безопасности SQL Server в Linux | Документация Майкрософт
description: В этой статье описаны действия стандартных параметров безопасности.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.openlocfilehash: 655aebb0c07c812a7aa6c81e7c7033d85e8b7ce2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705203"
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Пошаговое руководство для реализации функций безопасности SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Если вы являетесь пользователем Linux даже новичок в SQL Server, перечисленные ниже объясняется, как задачи безопасности. Они не являются уникальными или для Linux, а также дать вам представление о областей для ее дальнейшего изучения. В каждом примере ссылка подробная документация для этой области.

> [!NOTE]
>  В следующих примерах используется **AdventureWorks2014** образца базы данных. Инструкции о том, как получить и установить этот образец базы данных, см. в разделе [восстановить базу данных SQL Server из Windows и Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Создайте имя входа и пользователя базы данных 

Предоставлять другим пользователям доступ к SQL Server путем создания имени входа в базе данных master с помощью [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) инструкции. Пример:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

> [!NOTE]
>  Всегда используйте надежный пароль, вместо звездочки в предыдущей команде.

Имена входа можно подключиться к SQL Server и иметь доступ (с ограниченными разрешениями) к базе данных master. Чтобы подключиться к базе данных пользователя, имени входа необходимо соответствующее удостоверение на уровне базы данных, именем пользователя базы данных. Пользователи, относящихся к каждой базе данных и должны создаваться отдельно в каждой базе данных, чтобы предоставить им доступ. Переход в базу данных AdventureWorks2014 в следующем примере и затем использует [CREATE USER](../t-sql/statements/create-user-transact-sql.md) инструкцию, чтобы создать пользователя с именем Ларри, который связан с именем для входа с именем Ларри. На то, что имя входа и пользователя связаны (сопоставляются друг с другом), они представляют собой разные объекты. Имя входа — это принцип уровня сервера. Пользователь является участником уровня базы данных.

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- Учетной записью администратора SQL Server можно подключиться к любой базе данных и можно создать дополнительные имена входа и пользователи в любой базе данных.  
- Когда пользователь создает базу данных они становятся владельцем базы данных, что можно подключиться к этой базе данных. Владельцы базы данных можно создать дополнительных пользователей.

Позже вы можете проверять подлинность других имен входа, чтобы создать дополнительные имена входа, предоставив этому пользователю `ALTER ANY LOGIN` разрешение. В базе данных, можно обеспечить возможность создания большего числа пользователей, предоставив этому пользователю других пользователей `ALTER ANY USER` разрешение. Пример:   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

Теперь Ларри имени входа можно создать дополнительные имена входа и пользователь Джерри может создать больше пользователей.


## <a name="granting-access-with-least-privileges"></a>Предоставление доступа с минимальным числом привилегий

Первых регистрируетесь для подключения к базе данных пользователя будет «администратор» и «учетные записи владельца базы данных. Тем не менее эти пользователи имеют все разрешения, доступные в базе данных. Это больше разрешений, чем у большинства пользователей. 

Если вы только начинаете, можно назначить некоторые общие категории разрешения с помощью встроенной *предопределенных ролей базы данных*. Например `db_datareader` предопределенной роли базы данных на чтение всех таблиц в базе данных, но не вносить изменения. Предоставить членство в предопределенной роли базы данных с помощью [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md) инструкции. Добавить пользователя в следующем примере `Jerry` для `db_datareader` предопределенной роли базы данных.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Список предопределенных ролей базы данных, см. в разделе [роли уровня базы данных](../relational-databases/security/authentication-access/database-level-roles.md).

Позже, когда будете готовы настроить более точно управлять доступом к данным (настоятельно рекомендуется), создать свои собственные роли пользовательскую базу данных с помощью [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md) инструкции. Затем можно назначьте определенные детализированные разрешения вам пользовательские роли.

Например, следующие инструкции создают роли базы данных с именем `Sales`, предоставляет `Sales` группе возможность см. в разделе, обновление и удаление строк из `Orders` таблицы, а затем добавляет пользователя `Jerry` для `Sales` роли.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

For more information about the permission system, see [Getting Started with Database Engine Permissions](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## Configure row-level security  

[Row-Level Security](../relational-databases/security/row-level-security.md) enables you to restrict access to rows in a database based on the user executing a query. This feature is useful for scenarios like ensuring that customers can only access their own data or that workers can only access data that is pertinent to their department.   

The following steps walk through setting up two Users with different row-level access to the `Sales.SalesOrderHeader` table. 

Create two user accounts to test the row level security:    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Grant read access on the `Sales.SalesOrderHeader` table to both users:    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Create a new schema and inline table-valued function. The function returns 1 when a row in the `SalesPersonID` column matches the ID of a `SalesPerson` login or if the user executing the query is the Manager user.   
   
```     
CREATE SCHEMA Security;   
GO   
   
CREATE FUNCTION Security.fn_securitypredicate(@SalesPersonID AS int)     
    RETURNS TABLE   
WITH SCHEMABINDING   
AS     
   RETURN SELECT 1 AS fn_securitypredicate_result    
WHERE ('SalesPerson' + CAST(@SalesPersonId as VARCHAR(16)) = USER_NAME())     
    OR (USER_NAME() = 'Manager');    
```   

Create a security policy adding the function as both a filter and a block predicate on the table:  

```
Создание SalesFilter ПОЛИТИКИ безопасности   
ДОБАВЛЕНИЕ Security.fn_securitypredicate(SalesPersonID) ПРЕДИКАТА ФИЛЬТРА    
  НА Sales.SalesOrderHeader,   
ДОБАВЛЕНИЕ ПРЕДИКАТА Security.fn_securitypredicate(SalesPersonID) блока    
  НА Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Execute the following to query the `SalesOrderHeader` table as each user. Verify that `SalesPerson280` only sees the 95 rows from their own sales and that the `Manager` can see all the rows in the table.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
ОТМЕНИТЬ; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
ОТМЕНИТЬ;   
```
 
Alter the security policy to disable the policy.  Now both users can access all rows. 

```
ALTER SalesFilter ПОЛИТИКИ безопасности   
С (STATE = OFF);    
``` 


## Enable dynamic data masking

[Dynamic Data Masking](../relational-databases/security/dynamic-data-masking.md) enables you to limit the exposure of sensitive data to users of an application by fully or partially masking certain columns. 

Use an `ALTER TABLE` statement to add a masking function to the `EmailAddress` column in the `Person.EmailAddress` table: 
 
```
USE AdventureWorks2014; GO ALTER TABLE Person.EmailAddress     ALTER COLUMN EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
Create a new user `TestUser` with `SELECT` permission on the table, then execute a query as `TestUser` to view the masked data:   

```  
Создание пользователя TestUser без входа в СИСТЕМУ;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
ВЫБЕРИТЕ EmailAddressID, EmailAddress из Person.EmailAddress;       
ОТМЕНИТЬ;    
```
 
Verify that the masking function changes the email address in the first record from:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## Enable Transparent Data Encryption

One threat to your database is the risk that someone will steal the database files off of your hard-drive. This could happen with an intrusion that gets elevated access to your system, through the actions of a problem employee, or by theft of the computer containing the files (such as a laptop).

Transparent Data Encryption (TDE) encrypts the data files as they are stored on the hard drive. The master database of the SQL Server database engine has the encryption key, so that the database engine can manipulate the data. The database files cannot be read without access to the key. High-level administrators can manage, backup, and recreate the key, so the database can be moved, but only by selected people. When TDE is configured, the `tempdb` database is also automatically encrypted. 

Since the Database Engine can read the data, Transparent Data Encryption does not protect against unauthorized access by administrators of the computer who can directly read memory, or access SQL Server through an administrator account.

### Configure TDE

- Create a master key
- Create or obtain a certificate protected by the master key
- Create a database encryption key and protect it by the certificate
- Set the database to use encryption

Configuring TDE requires `CONTROL` permission on the master database and `CONTROL` permission on the user database. Typically an administrator configures TDE. 

The following example illustrates encrypting and decrypting the `AdventureWorks2014` database using a certificate installed on the server named `MyServerCert`.


```
USE master;  
GO  

СОЗДАНИЕ ГЛАВНОГО КЛЮЧА ENCRYPTION BY PASSWORD = "***";  
GO  

Создание сертификата MyServerCert с ТЕМОЙ = 'Мои базы данных сертификат ключа шифрования';  
GO  

USE AdventureWorks2014;   GO
  
CREATE DATABASE ENCRYPTION KEY  
С ПОМОЩЬЮ АЛГОРИТМА = AES_256  
ENCRYPTION BY SERVER MyServerCert сертификата;  
GO
  
ALTER DATABASE AdventureWorks2014  
ЗАДАТЬ ШИФРОВАНИЕ   
```

To remove TDE, execute `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

The encryption and decryption operations are scheduled on background threads by SQL Server. You can view the status of these operations using the catalog views and dynamic management views in the list that appears later in this topic.   

> [!WARNING]
>  Backup files of databases that have TDE enabled are also encrypted by using the database encryption key. As a result, when you restore these backups, the certificate protecting the database encryption key must be available. This means that in addition to backing up the database, you have to make sure that you maintain backups of the server certificates to prevent data loss. Data loss will result if the certificate is no longer available. For more information, see [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

For more information about TDE, see [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## Configure backup encryption
SQL Server has the ability to encrypt the data while creating a backup. By specifying the encryption algorithm and the encryptor (a certificate or asymmetric key) when creating a backup, you can create an encrypted backup file.    
  
> [!WARNING]  
>  It is very important to back up the certificate or asymmetric key, and preferably to a different location than the backup file it was used to encrypt. Without the certificate or asymmetric key, you cannot restore the backup, rendering the backup file unusable. 
 
 
The following example creates a certificate, and then creates a backup protected by the certificate.
```
Используйте master;   GO   создать СЕРТИФИКАТ BackupEncryptCert   с ТЕМОЙ = «Резервные копии базы данных»;   GO резервное копирование базы данных [AdventureWorks2014]   на ДИСК = N'/var/opt/mssql/backups/AdventureWorks2014.bak "  
на  
  СЖАТИЕ,  
  ENCRYPTION   
   (  
   АЛГОРИТМ = AES_256,  
   СЕРТИФИКАТ сервера = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

For more information, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).


## Next steps

For more information about the security features of SQL Server, see [Security Center for SQL Server Database Engine and Azure SQL Database](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
