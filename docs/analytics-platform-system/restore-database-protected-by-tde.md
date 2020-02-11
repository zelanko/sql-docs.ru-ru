---
title: Восстановление базы данных, защищенной с помощью прозрачного шифрования
description: Выполните следующие действия, чтобы восстановить базу данных, зашифрованную с помощью прозрачного шифрования данных в хранилище Parallel Data System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 53707c62e018b9923f2bb923a4df46f6917d2902
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400438"
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Восстановление базы данных, защищенной с помощью TDE, в Parallel Data Warehouse
Выполните следующие действия, чтобы восстановить базу данных, зашифрованную с помощью прозрачного шифрования данных.  
  
Пример [использования прозрачное шифрование данных](transparent-data-encryption.md#using-tde) содержит код для включения TDE в `AdventureWorksPDW2012` базе данных. Следующий код продолжит этот пример, создав резервную копию базы данных на исходном устройстве аналитики (ТД), а затем восстановив сертификат и базу данных на другом устройстве.  
  
Первым шагом является создание резервной копии базы данных-источника.  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
Подготовьте новую SQL Server PDW для TDE, создав главный ключ, включив шифрование и создав сетевые учетные данные.  
  
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
  
Последние два шага повторно создают сертификат с помощью резервных копий из исходной SQL Server PDW. Используйте пароль, который использовался при создании резервной копии сертификата.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert  
    FROM FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'   
    WITH PRIVATE KEY (FILE = '\\SECURE_SERVER\cert\MyServerCert.key',   
    DECRYPTION BY PASSWORD = '<password>');  
  
RESTORE DATABASE AdventureWorksPDW2012   
    FROM DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>См. также:  
[BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[Создание sp_pdw_add_network_credentials главного ключа](../t-sql/statements/create-master-key-transact-sql.md) 
[](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[СОЗДАТЬ СЕРТИФИКАТ](../t-sql/statements/create-certificate-transact-sql.md)  
[RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
