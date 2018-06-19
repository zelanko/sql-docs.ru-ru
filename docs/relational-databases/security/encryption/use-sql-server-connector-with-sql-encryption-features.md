---
title: Использование Соединителя SQL Server с компонентами шифрования SQL | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Connector, using
- EKM, with SQL Server Connector
ms.assetid: 58fc869e-00f1-4d7c-a49b-c0136c9add89
caps.latest.revision: 14
author: aliceku
ms.author: aliceku
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 78fb6c3a345f92d51cec24954a21264847a96557
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695585"
---
# <a name="use-sql-server-connector-with-sql-encryption-features"></a>Использование Соединителя SQL Server с компонентами шифрования SQL
[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]
  Типичные операции шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием асимметричного ключа, защищенного хранилищем ключей Azure, включают в себя три следующих области.  
  
-   Прозрачное шифрование данных с помощью асимметричного ключа из хранилища ключей Azure  
  
-   Шифрование резервных копий с помощью асимметричного ключа из хранилища ключей  
  
-   Шифрование данных на уровне столбца с помощью асимметричного ключа из хранилища ключей  
  
 Перед выполнением описанных здесь инструкций выполните части с I по IV в статье [Этапы настройки расширенного управления ключами с использованием хранилища ключей Azure](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md).  
 
> [!NOTE]  
>  Версии 1.0.0.440 и старше были заменены и больше не поддерживаются в рабочих средах. Выполните обновление до версии 1.0.1.0 или более поздней, посетив [Центр загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=45344) и используя инструкции на странице [Соединитель SQL Server, приложение](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md) в разделе "Обновление соединителя SQL Server".  
  
## <a name="transparent-data-encryption-by-using-an-asymmetric-key-from-azure-key-vault"></a>Прозрачное шифрование данных с помощью асимметричного ключа из хранилища ключей Azure  
 После выполнения частей с I по IV, описанных в статье "Этапы настройки расширенного управления ключами с использованием хранилища ключей Azure", используйте хранилище ключей Azure для шифрования ключа шифрования базы данных с помощью TDE.  
Вам потребуется создать учетные данные и имя входа, а также ключ шифрования базы данных, который шифрует данные и журналы в базе данных. Чтобы зашифровать базу данных, для нее требуется разрешение **CONTROL** . На приведенном ниже рисунке показана иерархия ключа шифрования при использовании хранилища ключей Azure.  
  
 ![ekm-key-hierarchy-with-akv](../../../relational-databases/security/encryption/media/ekm-key-hierarchy-with-akv.png "ekm-key-hierarchy-with-akv")  
  
1.  **Создание учетных данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для ядра СУБД, которые будут использоваться при прозрачном шифровании данных**  
  
     Ядро СУБД использует учетные данные для доступа к хранилищу ключей во время загрузки базы данных. Рекомендуется создать другой **идентификатор клиента** и **секрет** Azure Active Directory в части I для [!INCLUDE[ssDE](../../../includes/ssde-md.md)], чтобы ограничить предоставляемые разрешения хранилища ключей.  
  
     Измените приведенный ниже скрипт [!INCLUDE[tsql](../../../includes/tsql-md.md)] следующим образом.  
  
    -   Измените аргумент `IDENTITY` (`ContosoDevKeyVault`), чтобы он указывал на хранилище ключей Azure.
        - Если вы используете **общедоступную службу Azure**, замените аргумент `IDENTITY` на имя вашего хранилища ключей Azure из части II.
        - Если вы используете **частное облако Azure** (например, Azure для государственных организаций, китайскую или немецкую версию Azure), замените аргумент `IDENTITY` на URI хранилища, возвращенный на шаге 3 в части II. Не включайте https:// в URI хранилища.   
  
    -   Замените первую часть аргумента `SECRET` на **идентификатор клиента** Azure Active Directory из части I. В этом примере **идентификатор клиента** имеет значение `EF5C8E094D2A4A769998D93440D8115D`.  
  
        > [!IMPORTANT]  
        >  Необходимо удалить дефисы из **идентификатора клиента**.  
  
    -   Дополните вторую часть аргумента `SECRET` **секретом клиента** из части I. В этом примере **секрет клиента** из части I имеет значение `Replace-With-AAD-Client-Secret`. Окончательная строка аргумента `SECRET` будет представлять собой длинную последовательность букв и цифр *без дефисов*.  
  
    ```sql  
    USE master;  
    CREATE CREDENTIAL Azure_EKM_TDE_cred   
        WITH IDENTITY = 'ContosoDevKeyVault', -- for public Azure
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.usgovcloudapi.net', -- for Azure Government
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.azure.cn', -- for Azure China
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.microsoftazure.de', -- for Azure Germany   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DReplace-With-AAD-Client-Secret'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;  
    ```  
  
2.  **Создание имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для [!INCLUDE[ssDE](../../../includes/ssde-md.md)] для прозрачного шифрования данных**  
  
     Создайте имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и добавьте в него учетные данные из этапа 1. В этом примере [!INCLUDE[tsql](../../../includes/tsql-md.md)] используется тот же ключ, который был импортирован ранее.  
  
    ```sql  
    USE master;  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it loads a database   
    -- encrypted by TDE.  
    CREATE LOGIN TDE_Login   
    FROM ASYMMETRIC KEY CONTOSO_KEY;  
    GO   
  
    -- Alter the TDE Login to add the credential for use by the   
    -- Database Engine to access the key vault  
    ALTER LOGIN TDE_Login   
    ADD CREDENTIAL Azure_EKM_TDE_cred ;  
    GO  
    ```  
  
3.  **Создание ключа шифрования базы данных (DEK)**  
  
     Ключ DEK будет шифровать файлы данных и журналов в экземпляре базы данных и в свою очередь будет зашифрован с помощью асимметричного ключа хранилища ключей Azure. Ключ DEK можно создать, используя любой поддерживаемый алгоритм [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или длину ключа.  
  
    ```sql  
    USE ContosoDatabase;  
    GO  
  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;  
    GO  
    ```  
  
4.  **Включение кэша TDE**  
  
    ```sql  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE ContosoDatabase   
    SET ENCRYPTION ON;  
    GO  
    ```  
  
     С помощью [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]убедитесь, что прозрачное шифрование данных включено, подключившись к базе данных с использованием обозревателя объектов. Щелкните правой кнопкой мыши базу данных, наведите указатель на пункт **Задачи**, а затем щелкните **Управление шифрованием в базе данных**.  
  
     ![ekm-tde-object-explorer](../../../relational-databases/security/encryption/media/ekm-tde-object-explorer.png "ekm-tde-object-explorer")  
  
     В диалоговом окне **Управление шифрованием в базе данных** проверьте, что TDE включено, и определите, какой асимметричный ключ используется для шифрования ключа DEK.  
  
     ![ekm-tde-dialog-box](../../../relational-databases/security/encryption/media/ekm-tde-dialog-box.png "ekm-tde-dialog-box")  
  
     Можно также выполнить приведенный ниже скрипт [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Состояние шифрования 3 указывает на зашифрованную базу данных.  
  
    ```sql  
    USE MASTER  
    SELECT * FROM sys.asymmetric_keys  
  
    -- Check which databases are encrypted using TDE  
    SELECT d.name, dek.encryption_state   
    FROM sys.dm_database_encryption_keys AS dek  
    JOIN sys.databases AS d  
         ON dek.database_id = d.database_id;  
    ```  
  
    > [!NOTE]  
    >  База данных `tempdb` шифруется автоматически, когда любая база данных включает прозрачное шифрование данных.  
  
## <a name="encrypting-backups-by-using-an-asymmetric-key-from-the-key-vault"></a>Шифрование резервных копий с помощью асимметричного ключа из хранилища ключей  
 Зашифрованные резервные копии поддерживаются начиная с [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]. В следующем примере создается и восстанавливается резервная копия, зашифрованная ключом шифрования данных, который защищен асимметричным ключом в хранилище ключей.  
[!INCLUDE[ssDE](../../../includes/ssde-md.md)] требуются учетные данные при доступе к хранилищу ключей во время загрузки базы данных. Рекомендуется создать другой идентификатор клиента и секрет Azure Active Directory в части I для ядра СУБД, чтобы ограничить предоставляемые разрешения хранилища ключей.  
  
1.  **Создание учетных данных SQL Server для ядра СУБД, которые будут использоваться при шифровании резервной копии**  
  
     Измените приведенный ниже скрипт [!INCLUDE[tsql](../../../includes/tsql-md.md)] следующим образом.  
  
    -   Измените аргумент `IDENTITY` (`ContosoDevKeyVault`), чтобы он указывал на хранилище ключей Azure.
        - Если вы используете **общедоступную службу Azure**, замените аргумент `IDENTITY` на имя вашего хранилища ключей Azure из части II.
        - Если вы используете **частное облако Azure** (например, Azure для государственных организаций, китайскую или немецкую версию Azure), замените аргумент `IDENTITY` на URI хранилища, возвращенный на шаге 3 в части II. Не включайте https:// в URI хранилища.    
  
    -   Замените первую часть аргумента `SECRET` на **идентификатор клиента** Azure Active Directory из части I. В этом примере **идентификатор клиента** имеет значение `EF5C8E094D2A4A769998D93440D8115D`.  
  
        > [!IMPORTANT]  
        >  Необходимо удалить дефисы из **идентификатора клиента**.  
  
    -   Дополните вторую часть аргумента `SECRET` **секретом клиента** из части I. В этом примере **секрет клиента** из части I имеет значение `Replace-With-AAD-Client-Secret`. Окончательная строка аргумента `SECRET` будет представлять собой длинную последовательность букв и цифр *без дефисов*.   
  
        ```sql  
        USE master;  
  
        CREATE CREDENTIAL Azure_EKM_Backup_cred   
            WITH IDENTITY = 'ContosoDevKeyVault', -- for public Azure
            -- WITH IDENTITY = 'ContosoDevKeyVault.vault.usgovcloudapi.net', -- for Azure Government
            -- WITH IDENTITY = 'ContosoDevKeyVault.vault.azure.cn', -- for Azure China
            -- WITH IDENTITY = 'ContosoDevKeyVault.vault.microsoftazure.de', -- for Azure Germany   
            SECRET = 'EF5C8E094D2A4A769998D93440D8115DReplace-With-AAD-Client-Secret'   
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;    
        ```  
  
2.  **Создание имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для [!INCLUDE[ssDE](../../../includes/ssde-md.md)] для шифрования резервной копии**  
  
     Создайте имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которое будет использоваться [!INCLUDE[ssDE](../../../includes/ssde-md.md)]для шифрования резервных копий, и добавьте к нему учетные данные из этапа 1. В этом примере [!INCLUDE[tsql](../../../includes/tsql-md.md)] используется тот же ключ, который был импортирован ранее.  
  
    > [!IMPORTANT]  
    >  Нельзя использовать асимметричный ключ для шифрования резервной копии, если вы уже использовали его для прозрачного шифрования данных (предыдущий пример) или для шифрования на уровне столбца (следующий пример).  
  
     В этом примере используется асимметричный ключ `CONTOSO_KEY_BACKUP` из хранилища ключей, который мог быть импортирован или создан ранее для базы данных master на этапе 5 в части IV.  
  
    ```sql  
    USE master;  
  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it is encrypting the backup.  
    CREATE LOGIN Backup_Login   
    FROM ASYMMETRIC KEY CONTOSO_KEY_BACKUP;  
    GO   
  
    -- Alter the Encrypted Backup Login to add the credential for use by   
    -- the Database Engine to access the key vault  
    ALTER LOGIN Backup_Login   
    ADD CREDENTIAL Azure_EKM_Backup_cred ;  
    GO  
    ```  
  
3.  **Резервное копирование базы данных**  
  
     Зашифруйте архивированную базу данных асимметричным ключом, сохраненным в хранилище ключей.
     
     В следующем примере обратите внимание, что если база данных уже была зашифрована методом TDE и асимметричный ключ `CONTOSO_KEY_BACKUP` отличается от асимметричного ключа TDE, резервная копия будет зашифрована с помощью асимметричного ключа TDE и `CONTOSO_KEY_BACKUP`. Целевому экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] потребуется оба ключа для расшифровки резервной копии.
  
    ```sql  
    USE master;  
  
    BACKUP DATABASE [DATABASE_TO_BACKUP]  
    TO DISK = N'[PATH TO BACKUP FILE]'   
    WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD,   
    ENCRYPTION(ALGORITHM = AES_256,   
    SERVER ASYMMETRIC KEY = [CONTOSO_KEY_BACKUP]);  
    GO  
    ```  
  
4.  **Восстановление базы данных.**  
    
    Чтобы восстановить резервную копию базы данных, зашифрованную методом TDE, целевой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должен иметь копию асимметричного ключа Key Vault, используемого для шифрования. Это можно сделать так:  
    
    - Если исходный асимметричный ключ, используемый для TDE, больше не находится в Key Vault, восстановите резервную копию ключа Key Vault или повторно импортируйте ключ из локального модуля HSM. **Важно!** Чтобы отпечаток ключа совпал с записанным в резервной копии базы данных,ключ должен иметь **изначальное имя ключа Key Vault**.
    
    - Выполните шаги 1 и 2 на целевом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].
    
    - Когда экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] получит доступ к асимметричным ключам, которые используются для шифрования резервной копии, восстановите базу данных на сервере.
    
     Пример кода восстановления:  
  
    ```sql  
    RESTORE DATABASE [DATABASE_TO_BACKUP]  
    FROM DISK = N'[PATH TO BACKUP FILE]'   
        WITH FILE = 1, NOUNLOAD, REPLACE;  
    GO  
    ```  
  
     Дополнительные сведения о параметрах резервного копирования см. в статье [BACKUP (Transact-SQL)](../../../t-sql/statements/backup-transact-sql.md).  
  
## <a name="column-level-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a>Шифрование данных на уровне столбца с помощью асимметричного ключа из хранилища ключей  
 В следующем примере создается симметричный ключ, защищенный асимметричным ключом в хранилище ключей. Затем симметричный ключ используется для шифрования данных в базе данных.  
  
> [!IMPORTANT]  
>  Нельзя использовать асимметричный ключ для шифрования на уровне столбца, если вы уже использовали его для прозрачного шифрования данных или для шифрования резервной копии (предыдущие примеры).  
  
 В этом примере используется асимметричный ключ `CONTOSO_KEY_COLUMNS` из хранилища ключей, который мог быть импортирован или создан ранее, как описано в этапе 3 раздела 3 статьи [Этапы настройки расширенного управления ключами с использованием хранилища ключей Azure](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md). Для использования асимметричного ключа в базе данных `ContosoDatabase` необходимо выполнить инструкцию `CREATE ASYMMETRIC KEY` еще раз, чтобы предоставить базе данных `ContosoDatabase` ссылку на ключ.  
  
```sql  
USE [ContosoDatabase];  
GO  
  
-- Create a reference to the key in the key vault  
CREATE ASYMMETRIC KEY CONTOSO_KEY_COLUMNS   
FROM PROVIDER [AzureKeyVault_EKM_Prov]  
WITH PROVIDER_KEY_NAME = 'ContosoDevRSAKey2',  
CREATION_DISPOSITION = OPEN_EXISTING;  
  
-- Create the data encryption key.  
-- The data encryption key can be created using any SQL Server   
-- supported algorithm or key length.  
-- The DEK will be protected by the asymmetric key in the key vault  
  
CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY  
    WITH ALGORITHM=AES_256  
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY_COLUMNS;  
  
DECLARE @DATA VARBINARY(MAX);  
  
--Open the symmetric key for use in this session  
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY   
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY_COLUMNS;  
  
--Encrypt syntax  
SELECT @DATA = ENCRYPTBYKEY  
    (  
    KEY_GUID('DATA_ENCRYPTION_KEY'),   
    CONVERT(VARBINARY,'Plain text data to encrypt')  
    );  
  
-- Decrypt syntax  
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));  
  
--Close the symmetric key  
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;  
```  
  
## <a name="see-also"></a>См. также:  
 [Этапы настройки расширенного управления ключами с использованием хранилища ключей Azure](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md)   
 [Расширенное управление ключами с помощью хранилища ключей Azure](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
 [Включенный параметр конфигурации сервера поставщика расширенного управления ключами](../../../database-engine/configure-windows/ekm-provider-enabled-server-configuration-option.md)   
 [Обслуживание и устранение неполадок соединителя SQL Server](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md)  
  
  
