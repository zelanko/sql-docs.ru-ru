---
title: Приступая к работе с безопасностью SQL Server в Linux
description: Ознакомьтесь с функциями безопасности SQL Server в Linux, чтобы узнать больше о возможных областях для анализа.
author: VanMSFT
ms.author: vanto
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ecc72850-8b01-492e-9a27-ec817648f0e0
ms.openlocfilehash: 031005dcb6a5353e9e4f0b73a7a45d667d2212e7
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88088811"
---
# <a name="walkthrough-for-the-security-features-of-sql-server-on-linux"></a>Пошаговое руководство по функциям обеспечения безопасности в SQL Server на Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Если вы работаете с Linux и еще не знакомы с SQL Server, ознакомьтесь со следующими задачами, которые демонстрируют некоторые функции обеспечения безопасности. Они не являются уникальными для Linux и лишь задают общие направления для дальнейшего изучения. В каждом примере приводится ссылка на подробную документацию по соответствующей теме.

> [!NOTE]
>  В следующих примерах используется образец базы данных **AdventureWorks2014**. Инструкции по получению и установке этого образца базы данных см. в статье [Восстановление базы данных SQL Server из Windows в Linux](sql-server-linux-migrate-restore-database.md).


## <a name="create-a-login-and-a-database-user"></a>Создание имени входа и пользователя базы данных 

Предоставьте другим пользователям доступ к SQL Server, создав имя входа в базе данных master с помощью инструкции [CREATE LOGIN](../t-sql/statements/create-login-transact-sql.md). Пример:

```
CREATE LOGIN Larry WITH PASSWORD = '************';  
```

> [!NOTE]
>  Всегда используйте надежный пароль вместо звездочек в предыдущей команде.

Имена входа могут подключаться к SQL Server и обращаться (с ограниченными разрешениями) к базе данных master. Для подключения к пользовательской базе данных имя входа должно иметь соответствующее удостоверение на уровне базы данных, называемое пользователем базы данных. Пользователи относятся к конкретной базе данных, и их нужно создавать отдельно в каждой базе данных для предоставления им доступа. Следующий пример переносит вас в базу данных AdventureWorks2014, а затем с помощью инструкции [CREATE USER](../t-sql/statements/create-user-transact-sql.md) создает пользователя Larry, сопоставленного с именем входа Larry. Хотя имя входа и пользователь связаны (сопоставлены друг с другом), это разные объекты. Имя входа является субъектом уровня сервера. Пользователь является субъектом уровня базы данных.

```
USE AdventureWorks2014;
GO
CREATE USER Larry;
GO
```

- Учетная запись администратора SQL Server может подключаться к любой базе данных и создавать дополнительные имена входа и пользователей в любой базе данных.  
- Когда пользователь создает базу данных, он становится ее владельцем, который может подключаться к этой базе данных. Владельцы базы данных могут создавать дополнительных пользователей.

Позже вы сможете авторизовать другие имена входа, чтобы создать дополнительные имена входа, предоставив им разрешение `ALTER ANY LOGIN`. Внутри базы данных вы можете авторизовать других пользователей, чтобы создать дополнительных пользователей, предоставив им разрешение `ALTER ANY USER`. Пример:   

```
GRANT ALTER ANY LOGIN TO Larry;   
GO   
   
USE AdventureWorks2014;   
GO   
GRANT ALTER ANY USER TO Jerry;    
GO   
```

Теперь имя входа Larry может создать дополнительные имена входа, а пользователь Jerry может создать дополнительных пользователей.


## <a name="granting-access-with-least-privileges"></a>Предоставление доступа с минимальными правами

Первыми пользователями, подключающимися к пользовательской базе данных, будут учетные записи администратора и владельца базы данных. Однако у этих пользователей есть все разрешения, доступные в базе данных. Это гораздо больше, чем нужно большинству пользователей. 

Когда вы только приступаете к работе, можно назначить некоторые общие категории разрешений с помощью встроенных *предопределенных ролей базы данных*. Например, предопределенная роль базы данных `db_datareader` может считывать все таблицы в базе данных, но не вносить изменения. Предоставьте членство в предопределенной роли базы данных с помощью инструкции [ALTER ROLE](../t-sql/statements/alter-role-transact-sql.md). В следующем примере пользователь `Jerry` добавляется в предопределенную роль базы данных `db_datareader`.   
   
```   
USE AdventureWorks2014;   
GO   
   
ALTER ROLE db_datareader ADD MEMBER Jerry;   
```   

Список предопределенных ролей базы данных см. в разделе [Роли уровня базы данных](../relational-databases/security/authentication-access/database-level-roles.md).

Позже, когда вы будете готовы более точно настроить доступ к данным (настоятельно рекомендуется), создайте собственные пользовательские роли базы данных с помощью инструкции [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md). Затем назначьте определенные детализированные разрешения своим настраиваемым ролям.

Например, следующие инструкции создают роль базы данных `Sales`, предоставляют группе `Sales` возможность видеть, обновлять и удалять строки из таблицы `Orders`, а затем добавляют пользователя `Jerry` в роль `Sales`.   
   
```   
CREATE ROLE Sales;   
GRANT SELECT ON Object::Sales TO Orders;   
GRANT UPDATE ON Object::Sales TO Orders;   
GRANT DELETE ON Object::Sales TO Orders;   
ALTER ROLE Sales ADD MEMBER Jerry;   
```

Дополнительные сведения о системе разрешений см. в статье [Приступая к работе с разрешениями ядра СУБД](../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).


## <a name="configure-row-level-security"></a>Настройка безопасности на уровне строк  

[Безопасность на уровне строк](../relational-databases/security/row-level-security.md) позволяет ограничить доступ к строкам в таблице базы данных в зависимости от характеристик пользователя, выполняющего запрос. Эта функция полезна в таких сценариях, как обеспечение доступа клиентов только к их собственным данным, а также предоставление работникам доступа только к тем данным, которые относятся к их отделу.   

Ниже описано, как настроить двух пользователей с разным доступом на уровне строк к таблице `Sales.SalesOrderHeader`. 

Создайте две учетные записи пользователей для тестирования безопасности на уровне строк.    
   
```   
USE AdventureWorks2014;   
GO   
   
CREATE USER Manager WITHOUT LOGIN;     
   
CREATE USER SalesPerson280 WITHOUT LOGIN;    
```

Предоставьте обоим пользователям доступ на чтение к таблице `Sales.SalesOrderHeader`.    
   
```   
GRANT SELECT ON Sales.SalesOrderHeader TO Manager;      
GRANT SELECT ON Sales.SalesOrderHeader TO SalesPerson280;
```
   
Создайте новую схему и встроенную функцию с табличным значением. Функция возвращает 1, если строка в столбце `SalesPersonID` соответствует идентификатору имени входа `SalesPerson` или если пользователь, выполняющий запрос, является пользователем Manager.   
   
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

Создайте политику безопасности, добавив функцию в качестве фильтра и предиката блокировки для таблицы.  

```
CREATE SECURITY POLICY SalesFilter   
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader,   
ADD BLOCK PREDICATE Security.fn_securitypredicate(SalesPersonID)    
  ON Sales.SalesOrderHeader   
WITH (STATE = ON);   
```

Выполните следующую процедуру, чтобы запросить таблицу `SalesOrderHeader` от имени каждого пользователя. Убедитесь, что `SalesPerson280` видит только 95 строк из своих продаж, а `Manager` может видеть все строки в таблице.  

```    
EXECUTE AS USER = 'SalesPerson280';   
SELECT * FROM Sales.SalesOrderHeader;    
REVERT; 
 
EXECUTE AS USER = 'Manager';   
SELECT * FROM Sales.SalesOrderHeader;   
REVERT;   
```
 
Измените политику безопасности, чтобы отключить политику.  Теперь оба пользователя могут получить доступ ко всем строкам. 

```
ALTER SECURITY POLICY SalesFilter   
WITH (STATE = OFF);    
``` 


## <a name="enable-dynamic-data-masking"></a>Включение динамического маскирования данных

[Динамическое маскирование данных](../relational-databases/security/dynamic-data-masking.md) позволяет ограничить раскрытие конфиденциальных данных для пользователей приложения путем полной или частичной маскировки определенных столбцов. 

Используйте инструкцию `ALTER TABLE`, чтобы добавить функцию маскирования в столбец `EmailAddress` таблицы `Person.EmailAddress`. 
 
```
USE AdventureWorks2014;
GO
ALTER TABLE Person.EmailAddress    
ALTER COLUMN EmailAddress    
ADD MASKED WITH (FUNCTION = 'email()');
``` 
 
Создайте нового пользователя `TestUser` с разрешением `SELECT` для таблицы, а затем выполните запрос от имени `TestUser` для просмотра маскированных данных.   

```  
CREATE USER TestUser WITHOUT LOGIN;   
GRANT SELECT ON Person.EmailAddress TO TestUser;    
 
EXECUTE AS USER = 'TestUser';   
SELECT EmailAddressID, EmailAddress FROM Person.EmailAddress;       
REVERT;    
```
 
Убедитесь, что функция маскирования меняет адрес электронной почты первой записи с:
  
|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |ken0@adventure-works.com |    
 
into 

|EmailAddressID |EmailAddress |  
|----|---- |   
|1 |kXXX@XXXX.com |   


## <a name="enable-transparent-data-encryption"></a>Включение прозрачного шифрования данных

Одной из угроз для базы данных является риск того, что кто-то украдет файлы базы данных с вашего жесткого диска. Это может произойти при атаке, предоставляющей повышенные права доступа к вашей системе, в результате действий сотрудника или кражи компьютера, содержащего файлы (например, ноутбука).

Прозрачное шифрование данных (TDE) шифрует файлы данных по мере их сохранения на жестком диске. База данных master ядра СУБД SQL Server содержит ключ шифрования, чтобы ядро СУБД могло манипулировать данными. Файлы базы данных невозможно прочитать без доступа к этому ключу. Администраторы высокого уровня могут управлять этим ключом, выполнять его резервное копирование и повторно создавать его, чтобы базу данных можно было перемещать, но только отдельным пользователям. При настройке TDE база данных `tempdb` также автоматически шифруется. 

Так как ядро СУБД может считывать данные, прозрачное шифрование данных не защищает от несанкционированного доступа администраторов компьютера, которые могут напрямую считывать память или получить доступ к SQL Server через учетную запись администратора.

### <a name="configure-tde"></a>Настройка TDE

- Создайте главный ключ
- Создайте или получите сертификат, защищенный главным ключом
- Создайте ключ шифрования базы данных и защитите его с помощью сертификата
- Задайте ведение шифрования базы данных

Для настройки TDE требуется разрешение `CONTROL` в базе данных master и разрешение `CONTROL` в пользовательской базе данных. Обычно TDE настраивает администратор. 

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

Чтобы удалить TDE, выполните `ALTER DATABASE AdventureWorks2014 SET ENCRYPTION OFF;`.   

Операции шифрования и расшифровки планируются SQL Server в фоновых потоках. Состояние этих операций можно просмотреть в представлениях каталога и динамических административных представлениях в списке, представленном далее в этом разделе.   

> [!WARNING]
>  Файлы резервных копий баз данных, в которых включено TDE, также шифруются с помощью ключа шифрования базы данных. Поэтому для восстановления таких резервных копий необходимо иметь сертификат, защищающий ключ шифрования базы данных. Это значит, что помимо резервного копирования базы данных обязательно необходимо сохранять резервные копии сертификатов серверов, чтобы не допустить потери данных. Если сертификат станет недоступным, это приведет к потере данных. Дополнительные сведения см. в статье [SQL Server Certificates and Asymmetric Keys](../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  

Дополнительные сведения о TDE см. в статье [Прозрачное шифрование данных (TDE)](../relational-databases/security/encryption/transparent-data-encryption-tde.md).   


## <a name="configure-backup-encryption"></a>Настройка шифрования резервных копий
SQL Server может шифровать данные при создании резервной копии. Указав алгоритм шифрования и шифратор (сертификат или асимметричный ключ) при создании резервной копии, можно создать зашифрованный файл резервной копии.    
  
> [!WARNING]
> Очень важно создать резервную копию сертификата или асимметричного ключа и предпочтительно в ином местоположении, чем зашифрованный ими файл резервной копии. Без сертификата или асимметричного ключа резервную копию нельзя будет восстановить, т. е. файл резервной копии будет непригоден для использования. 
 
 
Следующий пример создает сертификат, а затем создает резервную копию, защищенную этим сертификатом.

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

Дополнительные сведения см. в статье [Шифрование резервной копии](../relational-databases/backup-restore/backup-encryption.md).


## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о функциях безопасности в SQL Server см. в статье [Центр обеспечения безопасности для ядра СУБД SQL Server и Базы данных SQL Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).
