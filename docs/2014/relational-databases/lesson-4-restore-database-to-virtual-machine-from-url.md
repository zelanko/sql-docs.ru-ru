---
title: Занятие 5. Используемых Шифрование базы данных с помощью TDE | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4eda59ac47444eb589e17d6e1aab2428c77a991f
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154522"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>Занятие 5. (Необязательно) Шифрование базы данных с помощью TDE
  В качестве дополнительного шага вы можете зашифровать созданную базу данных. Функция прозрачного шифрования данных (TDE) выполняет в реальном времени шифрование и дешифрование файлов данных и журналов в операциях ввода-вывода. При таком типе шифрования используется ключ шифрования базы данных (DEK), который хранится в загрузочной записи базы данных, чтобы он был доступен при восстановлении. Дополнительные сведения см. в [разделе &#40;прозрачное шифрование данных&#41; TDE](security/encryption/transparent-data-encryption.md) и [Перемещение базы данных, защищенной TDE, в другую SQL Server](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   У вас есть учетная запись хранения Azure.  
  
-   Вы создали контейнер в учетной записи хранения Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на исходном компьютере.  
  
-   Создали базу данных с помощью процедуры, описанной в занятии 4.  
  
 Чтобы зашифровать базу данных, выполните следующие действия.  
  
1.  На исходном компьютере внесите изменения и выполните в окне запроса следующие инструкции.  
  
    ```  
  
    -- Create a master key and a server certificate   
    USE master   
    GO   
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01';   
    GO   
    CREATE CERTIFICATE MySQLCert WITH SUBJECT = 'SQL - Azure Storage Certification'   
    GO   
    -- Create a backup of the server certificate in the master database.   
    -- Store TDS certificates in the source machine locally.   
    BACKUP CERTIFICATE MySQLCert   
    TO FILE = 'C:\certs\MySQLCert.CER'   
    WITH PRIVATE KEY   
    (   
    FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
    ENCRYPTION BY PASSWORD = 'MySQLKey01'   
    );  
  
    ```  
  
2.  Затем зашифруйте новую базу данных на исходном компьютере, выполнив следующие действия.  
  
    ```  
  
    -- Switch to the new database.   
    -- Create a database encryption key, that is protected by the server certificate in the master database.    
    -- Alter the new database to encrypt the database using TDE.   
    USE TestDB1;   
    GO   
    -- Encrypt your database   
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE MySQLCert   
    GO   
  
    ALTER DATABASE TestDB1   
    SET ENCRYPTION ON   
    GO  
  
    ```  
  
 Чтобы узнать состояние шифрования базы данных и связанных ключей шифрования базы данных, выполните следующую инструкцию:  
  
```  
  
SELECT * FROM sys.dm_database_encryption_keys;   
GO  
  
```  
  
 Подробные сведения об инструкциях Transact-SQL, которые использовались в этом занятии, см. в статьях [Создание базы данных &#40;SQL Server Transact-&#41;SQL](/sql/t-sql/statements/create-database-sql-server-transact-sql), [инструкция ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql), [Создание главного ключа &#40; Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)и [sys. DM _database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).  
  
 **Следующее занятие:**  
  
 [Занятие 6. Перенос базы данных с исходного компьютера на конечный компьютер в Azure](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
