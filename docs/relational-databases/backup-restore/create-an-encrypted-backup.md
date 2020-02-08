---
title: Создание зашифрованной резервной копии | Документация Майкрософт
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8f0c38d7dd712c5727fc5e9f7f62a35c1b886e1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "70280810"
---
# <a name="create-an-encrypted-backup"></a>Создание зашифрованной резервной копии
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описаны шаги, необходимые для создания зашифрованной резервной копии с помощью Transact-SQL.  Пример использования [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]см. в разделе [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md). 
  
## <a name="backup-to-disk-with-encryption"></a>Резервное копирование на диск с шифрованием  
 **Предварительные условия.**  
  
-   Доступ к локальному диску или хранилищу с достаточным количеством места для создания резервной копии базы данных.  
  
-   Главный ключ базы данных для базы данных master и сертификат или доступный асимметричный ключ на экземпляре SQL Server. Требования и разрешения шифрования см. в разделе [Backup Encryption](../../relational-databases/backup-restore/backup-encryption.md).  
  
 Выполните следующие шаги, чтобы создать зашифрованную резервную копию базы данных на локальном диске. В примере используется пользовательская база данных MyTestDB.  
  
1.  **Создайте главный ключ базы данных master.** Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных. Подключитесь к ядру СУБД, откройте новое окно запроса, скопируйте в него следующий пример и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **Создайте сертификат резервной копии.** Создайте сертификат резервной копии в базе данных master. Скопируйте и вставьте следующий пример в окно запроса и нажмите кнопку **Выполнить**  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **Выполните резервное копирование базы данных.** Укажите алгоритм шифрования и сертификат для использования. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  

    ```
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
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
  
 Пример шифрования резервной копии, защищенной с помощью EKM, см. в статье [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
### <a name="backup-to-azure-storage-with-encryption"></a>Резервное копирование в службу хранилища Azure с шифрованием  
 При создании резервной копии в хранилище Azure с помощью параметра **Резервное копирование SQL Server на URL-адрес** шаги шифрования остаются теми же, но в качестве места назначения необходимо использовать URL-адрес, а для проверки подлинности в хранилище Azure — учетные данные SQL. Сведения о настройке [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] с параметрами шифрования см. в статье [Включение управляемого резервного копирования SQL Server в Microsoft Azure](../../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md).  
  
 **Предварительные условия.**  
  
-   Учетная запись хранения Windows и контейнер. Дополнительные сведения см. в разделе [Занятие 1. Создание объектов службы хранилища Azure](https://msdn.microsoft.com/library/74edd1fd-ab00-46f7-9e29-7ba3f1a446c5).  
  
-   Главный ключ базы данных для базы данных master и сертификат или асимметричный ключ на экземпляре SQL Server. Требования и разрешения шифрования см. в разделе [Backup Encryption](../../relational-databases/backup-restore/backup-encryption.md).  
  
1.  **Создайте учетные данные SQL Server.** Для создания учетных данных SQL Server подключитесь к ядру СУБД, откройте новое окно запроса, скопируйте в него следующий пример и нажмите кнопку **Выполнить**.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **Создайте главный ключ базы данных.** Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных. Подключитесь к ядру СУБД, откройте новое окно запроса, скопируйте в него следующий пример и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **Создайте сертификат резервной копии.** Создайте сертификат резервной копии в базе данных master. Вставьте следующий пример в окно запроса и нажмите **Выполнить**.  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **Выполните резервное копирование базы данных.** Укажите алгоритм шифрования и сертификат для использования. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' - this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  
