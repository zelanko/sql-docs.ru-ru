---
title: Восстановление базы данных, защищаемую прозрачным Шифрованием - Parallel Data Warehouse | Документы Microsoft
description: Выполните следующие действия для восстановления базы данных, который зашифрован с применением прозрачного шифрования данных в аналитику платформы системы Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: a791d4110dc70c506025f8f11fb06b9ba2e5dcb3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Восстановление базы данных, защищаемую прозрачным Шифрованием в Parallel Data Warehouse
Восстановление базы данных, зашифрованного с помощью прозрачного шифрования данных, выполните следующие действия.  
  
[С помощью прозрачного шифрования данных](transparent-data-encryption.md#using-tde) пример содержит код, включить прозрачное шифрование данных на `AdventureWorksPDW2012` базы данных. Следующий код этого примера продолжается путем создания резервной копии базы данных на устройстве исходного Analytics Platform System (APS) и восстановления сертификата и базы данных на разные устройства.  
  
Первым шагом является создание резервной копии базы данных-источника.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Подготовка SQL Server PDW для прозрачного шифрования данных, создании главного ключа, Включение шифрования и создании учетных данных в сети.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
Последние два этапа повторно создайте сертификат с помощью резервных копий из исходного SQL Server PDW. Используйте пароль, который использовался при создании резервной копии сертификата.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert  
    FROM FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'   
    WITH PRIVATE KEY (FILE = '\\SECURE_SERVER\cert\MyServerCert.key',   
    DECRYPTION BY PASSWORD = '<password>');  
  
RESTORE DATABASE AdventureWorksPDW2012   
    FROM DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>См. также  
[РЕЗЕРВНОЕ КОПИРОВАНИЕ БАЗЫ ДАННЫХ](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md) 
[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[СОЗДАНИЕ СЕРТИФИКАТА](../t-sql/statements/create-certificate-transact-sql.md)  
[ВОССТАНОВЛЕНИЕ БАЗЫ ДАННЫХ](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
