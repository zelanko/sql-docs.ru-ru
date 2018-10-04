---
title: Создание зашифрованной резервной копии | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7fcfdf8a6d25d950970952d9f5dec93a523dc37f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205634"
---
# <a name="create-an-encrypted-backup"></a>Создание зашифрованной резервной копии
  В этом разделе описаны шаги, необходимые для создания зашифрованной резервной копии с помощью Transact-SQL.  
  
## <a name="backup-to-disk-with-encryption"></a>Резервное копирование на диск с шифрованием  
 **Предварительные условия.**  
  
-   Доступ к локальному диску или хранилищу с достаточным количеством места для создания резервной копии базы данных.  
  
-   Главный ключ базы данных для базы данных master и сертификат или доступный асимметричный ключ на экземпляре SQL Server. Требования и разрешения шифрования см. в разделе [Backup Encryption](backup-encryption.md).  
  
 Выполните следующие шаги, чтобы создать зашифрованную резервную копию базы данных на локальном диске. В примере используется пользовательская база данных MyTestDB.  
  
1.  **Создайте главный ключ базы данных master:** выберите пароль для шифрования копии главного ключа, которая будет храниться в базе данных. Подключитесь к ядру СУБД, откройте новое окно запроса, скопируйте в него следующий пример и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **Создание сертификата резервной копии.** Создайте сертификат резервной копии в базе данных master. Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку **Выполнить**  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **Создание резервной копии базы данных.** Укажите алгоритм шифрования и сертификат для использования. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 Пример шифрования резервной копии, защищенной с помощью EKM, см. в статье [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
### <a name="backup-to-windows-azure-storage-with-encryption"></a>Резервное копирование в хранилище больших двоичных объектов Windows Azure с шифрованием  
 При создании резервной копии в хранилище Windows Azure с помощью опции **Резервное копирование SQL Server на URL-адрес** шаги шифрования остаются теми же, но в качестве места назначения необходимо использовать URL-адрес, а для проверки подлинности в хранилище Windows Azure — учетные данные SQL. Если вы хотите настроить [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] с применением параметров шифрования, см. в разделе [Настройка SQL Server Managed Backup to Windows Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) и [Настройка SQL Server Managed Backup to Windows Azure для групп доступности](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 **Предварительные условия.**  
  
-   Учетная запись хранения Windows и контейнер. Дополнительные сведения см. в разделе [Lesson 1: Create Windows Azure Storage Objects](../../tutorials/lesson-1-create-windows-azure-storage-objects.md).  
  
-   Главный ключ базы данных для базы данных master и сертификат или асимметричный ключ на экземпляре SQL Server. Требования и разрешения шифрования см. в разделе [Backup Encryption](backup-encryption.md).  
  
1.  **Создание учетных данных SQL Server.** Для создания учетных данных SQL Server подключитесь к ядру СУБД, откройте новое окно запроса, скопируйте в него следующий пример и нажмите кнопку **Выполнить**.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **Создание главного ключа базы данных.** Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных. Подключитесь к ядру СУБД, откройте новое окно запроса, скопируйте в него следующий пример и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **Создание сертификата резервной копии.** Создайте сертификат резервной копии в базе данных master. Вставьте следующий пример в окно запроса и нажмите **Выполнить**.  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **Создание резервной копии базы данных.** Укажите алгоритм шифрования и сертификат для использования. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' – this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
