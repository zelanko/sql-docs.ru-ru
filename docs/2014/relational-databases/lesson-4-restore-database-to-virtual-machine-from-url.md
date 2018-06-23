---
title: Занятие 5. (Необязательно) Шифрование базы данных с помощью прозрачного шифрования данных | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c8ef2e904c197822721a5c48f811a2a895b5ca59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194024"
---
# <a name="lesson-5-optional-encrypt-your-database-using-tde"></a>Занятие 5. (Необязательно) Шифрование базы данных с помощью TDE
  В качестве дополнительного шага вы можете зашифровать созданную базу данных. Функция прозрачного шифрования данных (TDE) выполняет в реальном времени шифрование и дешифрование файлов данных и журналов в операциях ввода-вывода. При таком типе шифрования используется ключ шифрования базы данных (DEK), который хранится в загрузочной записи базы данных, чтобы он был доступен при восстановлении. Дополнительные сведения см. в разделе [прозрачное шифрование данных &#40;TDE&#41; ](security/encryption/transparent-data-encryption.md) и [перемещение защищенной базы данных прозрачного шифрования данных на другой сервер SQL](security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   Получили учетную запись хранения Windows Azure.  
  
-   Создали контейнер с использованием вашей учетной записи хранения Windows Azure.  
  
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
  
 For detailed information the Transact-SQL statements that have been used in this lesson, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql), [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql), [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql), [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql), and [sys.dm_database_encryption_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).  
  
 **Следующее занятие:**  
  
 [Занятие 6. Перенос базы данных с исходного локального компьютера на целевой компьютер в Microsoft Azure](lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
