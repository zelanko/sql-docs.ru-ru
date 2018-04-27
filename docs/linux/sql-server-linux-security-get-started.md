---
title: Приступая к работе с безопасности SQL Server для Linux | Документы Microsoft
description: В этой статье описаны действия стандартных параметров безопасности.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.technology: database-engine
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.custom: sql-linux
ms.workload: Inactive
ms.openlocfilehash: 0868aeaec180999590a06f8012a89addb64d1ce1
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Пошаговое руководство для средства безопасности SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Если вы являетесь пользователем Linux, новые для SQL Server, следующие задачи описывают некоторые задачи безопасности. Это не уникальным или уникальным для Linux, а также дает общее представление областей для дальнейшего анализа. В каждом примере ссылку обеспечивает подробная документация для этой области.

>  [!NOTE]
>  В следующих примерах используется **AdventureWorks2014** образца базы данных. Инструкции о том, как получить и установить этот образец базы данных см. в разделе [восстановление базы данных SQL Server из Windows, Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Создайте имя входа и пользователя базы данных 

Предоставлять другим пользователям доступа к SQL Server путем создания имени входа в базе данных master с помощью [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md) инструкции. Например:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

>  [!NOTE]
>  Всегда используйте надежный пароль, вместо звездочки в предыдущей команде.

Имена входа можно подключиться к SQL Server и иметь доступ (с ограниченными разрешениями) к базе данных master. Чтобы подключиться к базе данных пользователя, имя входа должно соответствующих удостоверений на уровне базы данных, называется пользователем базы данных. Пользователи, относящиеся к каждой из баз данных и должны создаваться отдельно в каждой базе данных, чтобы предоставить им доступ. В следующем примере переходят базы данных AdventureWorks2014 и затем использует [CREATE USER](../t-sql/statements/create-user-transact-sql.md) инструкцию, чтобы создать пользователя с именем, связанный с именем входа, с именем Ларри Ларри. На то, что имя входа и пользователя связаны (сопоставляются друг с другом), они являются различными объектами. Имя входа является участника уровня сервера. Пользователь является участником уровня базы данных.

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- Учетной записи администратора SQL Server могут подключаться к любой базе данных, можно создать несколько имен входа и пользователей в любой базе данных.  
- Если кто-то создает базу данных они становятся владелец базы данных, с возможностью подключения к этой базе данных. Владельцы базы данных можно создать несколько пользователей.

Позже вы можете разрешить другие имена входа, чтобы создать дополнительные имена входа, предоставляя им `ALTER ANY LOGIN` разрешение. В базе данных, вы можете разрешить другим пользователям для создания дополнительных пользователей, предоставляя им `ALTER ANY USER` разрешение. Например:   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

Теперь Ларри имени входа можно создать несколько имен входа и пользователь Джерри может создавать дополнительных пользователей.


## <a name="granting-access-with-least-privileges"></a>Предоставление доступа с минимальным числом привилегий

Первый пользователи для подключения к базе данных пользователя будет администратора и учетные записи владельца базы данных. Тем не менее эти пользователи имеют все разрешения, доступные в базе данных. Это больше разрешений, чем большинство пользователей должны иметь. 

При можно только начинающие работу, можно назначить некоторые общие категории разрешения с помощью встроенного *предопределенных ролей базы данных*. Например `db_datareader` предопределенной роли базы данных на чтение всех таблиц в базе данных, но не вносить изменения. Предоставить членство в предопределенной роли базы данных с помощью [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md) инструкции. Добавить пользователя в следующем примере `Jerry` для `db_datareader` предопределенной роли базы данных.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Список предопределенных ролей базы данных см. в разделе [роли уровня базы данных](../relational-databases/security/authentication-access/database-level-roles.md).

Позже, когда будете готовы настроить более точного доступа к данным (настоятельно рекомендуется), создать свои собственные роли определяемую пользователем базу данных с помощью [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md) инструкции. Затем назначьте конкретные детальные разрешения вы пользовательскими ролями.

Например, следующие инструкции создают роли базы данных с именем `Sales`, предоставляет `Sales` группе права на разделе, обновление и удаление строк из `Orders` таблицы, а затем добавляет пользователя `Jerry` для `Sales` роли.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```   

Дополнительные сведения о системе разрешений см. в разделе [Приступая к работе с разрешениями Database Engine](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## <a name="configure-row-level-security"></a>Настройка безопасности на уровне строки  

[Безопасность на уровне строк](../relational-databases/security/row-level-security.md) позволяет ограничить доступ к строкам в базу данных на основании пользователя, выполняющего запрос. Эта возможность полезна для сценариев, таких как обеспечивает, что клиенты имеет доступ только к собственным данным или что работники доступны только данные, которые имеют отношение к их отделу.   

Ниже описано в ходе настройки двух пользователей с разных доступа на уровне строк к `Sales.SalesOrderHeader` таблицы. 

Создайте две учетные записи пользователя для проверки безопасности на уровне строк:    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```   

Предоставьте доступ на чтение на `Sales.SalesOrderHeader` таблицу для обоих пользователей:    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;    
```   
   
Создание новой схемы и встроенные возвращающие табличные значения функции. Функция возвращает 1, если строка в `SalesPersonID` столбца совпадает с Идентификатором `SalesPerson` входа или если пользователь, выполняющий запрос, является пользователем Manager.   
   
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

Создайте политику безопасности, добавляя функцию в качестве фильтра и предиката блокировки для таблицы:  

```
CREATE SECURITY POLICY SalesFilter   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Выполните следующий запрос `SalesOrderHeader` таблицы как для каждого пользователя. Убедитесь, что `SalesPerson280` видит только 95 строки из свои продажи и что `Manager` сможет увидеть все строки в таблице.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
REVERT; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
REVERT;   
```
 
Измените политику безопасности, чтобы отключить политику.  Теперь оба доступ можно все строки. 

```
ALTER SECURITY POLICY SalesFilter   
WITH (STATE = OFF);    
``` 


## <a name="enable-dynamic-data-masking"></a>Включить динамическое маскирование данных

[Динамическое маскирование данных](../relational-databases/security/dynamic-data-masking.md) позволяет ограничить раскрытия конфиденциальных данных, чтобы пользователи приложения, полностью или частично, маскируя определенные столбцы. 

Используйте `ALTER TABLE` инструкцию, чтобы добавить функцию маскирования в `EmailAddress` столбца в `Person.EmailAddress` таблице: 
 
```
USE AdventureWorks2014;
GO
ALTER TABLE Person.EmailAddress    
ALTER COLUMN EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
Создайте нового пользователя `TestUser` с `SELECT` разрешение на таблицу, затем выполните запрос в качестве `TestUser` для просмотра маскированные данные:   

```  
CREATE USER TestUser WITHOUT LOGIN;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
REVERT;    
```
 
Убедитесь, что функция маскирования изменяется адрес электронной почты из первой записи:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## <a name="enable-transparent-data-encryption"></a>Включение прозрачного шифрования данных

Один угроза для базы данных — это риск, что кто-то будет украсть файлы базы данных удаляются с жесткого диска. Это может произойти с вторжений, которое получает повышенные права доступа к вашей системе, через действий сотрудника в проблему или в случае кражи компьютера, содержащего файлы (например, переносным компьютером).

Прозрачное шифрование данных (TDE) шифрует файлы данных, хранящихся на жестком диске. Основной базе данных ядро СУБД SQL Server имеет ключ шифрования, компонент database engine можно управлять данными. Не удается прочитать файлы базы данных без доступа к ключу. Высокоуровневые администраторы могут управлять, резервной копии и повторного создания ключа, так можно переместить базу данных, но только выбранные пользователями. При настройке прозрачного шифрования данных `tempdb` также автоматически шифрование базы данных. 

Так как компонент Database Engine может считывать данные, прозрачное шифрование данных не защищает от несанкционированного доступа со стороны администраторов компьютера, кто может непосредственно считать памяти или доступа к SQL Server с помощью учетной записи администратора.

### <a name="configure-tde"></a>Настройка прозрачного шифрования данных

- Создайте главный ключ
- Создайте или получите сертификат, защищенный главным ключом
- Создайте ключ шифрования базы данных и защитите его с помощью сертификата
- Задайте ведение шифрования базы данных

При настройке прозрачного шифрования данных требуется `CONTROL` разрешений в базе данных master и `CONTROL` разрешения в базе данных пользователя. Обычно администратор настраивает прозрачного шифрования данных. 

В следующем примере демонстрируется шифрование и дешифрование базы данных `AdventureWorks2014` с помощью сертификата с именем `MyServerCert`, установленного на сервере.


```
USE master;  
GO  

CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**********';  
GO  

CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My Database Encryption Key Certificate';  
GO  

USE AdventureWorks2014;  
GO
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_256  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO
  
ALTER DATABASE AdventureWorks2014  
SET ENCRYPTION ON;   
```

Чтобы удалить прозрачное шифрование данных, выполнение `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`   

Операции шифрования и дешифрования запланированы в фоновых потоках в SQL Server. Состояние этих операций можно просмотреть в представлениях каталога и динамических административных представлениях в списке, представленном далее в этом разделе.   

>  [!WARNING]
>  Файлы резервных копий баз данных, в которых включено TDE, также шифруются с помощью ключа шифрования базы данных. Поэтому для восстановления таких резервных копий необходимо иметь сертификат, защищающий ключ шифрования базы данных. Это значит, что помимо резервного копирования базы данных обязательно необходимо сохранять резервные копии сертификатов серверов, чтобы не допустить потери данных. Если сертификат станет недоступным, это приведет к потере данных. Дополнительные сведения см. в статье [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

Дополнительные сведения о TDE см. в разделе [прозрачное шифрование данных (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## <a name="configure-backup-encryption"></a>Настройка шифрования резервной копии
SQL Server имеется возможность шифровать данные при создании резервной копии. Указав алгоритм шифрования и шифратор (сертификат или асимметричный ключ) при создании резервной копии, можно создать зашифрованного файла резервной копии.    
  
> [!WARNING]  
>  Очень важно создать резервную копию сертификата или асимметричного ключа и предпочтительно в ином местоположении, чем зашифрованный ими файл резервной копии. Без сертификата или асимметричного ключа резервную копию нельзя будет восстановить, т. е. файл резервной копии будет непригоден для использования. 
 
 
Следующий пример создает сертификат, а затем создает резервной копии, защищенной с помощью сертификата.
```
USE master;  
GO  
CREATE CERTIFICATE BackupEncryptCert   
   WITH SUBJECT = 'Database backups';  
GO 
BACKUP DATABASE [AdventureWorks2014]  
TO DISK = N'/var/opt/mssql/backups/AdventureWorks2014.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```

Дополнительные сведения см. в разделе [шифрование резервной копии](../relational-databases/backup-restore/backup-encryption.md).


## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о средствах безопасности SQL Server см. в разделе [центр обеспечения безопасности для ядра СУБД SQL Server и базы данных SQL Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
