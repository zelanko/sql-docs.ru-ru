---
title: "Прозрачное шифрование данных в базе данных SQL Azure | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
- MSDN content
- MSDN - SQL DB
ms.date: 09/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TDE, SQL Database
- encryption (SQL Database), TDE
- Transparent Data Encryption, SQL Database
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1c607015f1ead5b19d4c32c5bac62eb624b0578b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Прозрачное шифрование данных в Базе данных SQL Azure
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx_md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] Прозрачное шифрование данных защищает от угроз вредоносных действий, в реальном времени выполняя шифрование и расшифровку неактивной базы данных, связанных резервных копий и файлов журнала транзакций. При этом изменение приложения не требуется.  
  
 TDE шифрует пространство хранения всей базы данных, используя симметричный ключ, который называется ключом шифрования базы данных. В [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] для защиты ключа шифрования базы данных используется встроенный сертификат сервера. Встроенный сертификат сервера уникален для каждого сервера [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] . Если база данных находится в отношении GeoDR, на каждом сервере для защиты используется разный ключ. Если две базы данных подключены к одному серверу, используется один встроенный сертификат. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] автоматически меняет эти сертификаты каждые 90 дней. Общее описание прозрачного шифрования данных см. в разделе [Прозрачное шифрование данных (TDE)](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md).  
  
 [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] не поддерживает интеграцию хранилища ключей Azure с TDE. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , запущенный на виртуальной машине Azure, может использовать асимметричный ключ из хранилища ключей. Дополнительные сведения см. в разделе [Расширенное управление ключами с помощью хранилища ключей Azure (SQL Server)](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
##  <a name="Permissions"></a> Разрешения  
 Чтобы настроить TDE через портал Azure с помощью REST API или PowerShell, необходимо подключиться в качестве владельца, участника или диспетчера безопасности SQL Azure.  
  
 Чтобы настроить TDE с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] :  
  
-   Чтобы выполнить инструкцию ALTER DATABASE с параметром SET, нужно участие в роли **dbmanager** .  
  
##  <a name="Preview"></a> Включение TDE в базе данных с помощью портала  
  
1.  Откройте портал Azure на странице [https://portal.azure.com](https://portal.azure.com) и войдите с использованием учетной записи администратора или участника Azure.  
  
2.  В области слева нажмите кнопку **ПРОСМОТРЕТЬ ВСЕ**и выберите **Базы данных SQL**.  
  
3.  После этого выберите пользовательскую базу данных. ****  
  
4.  В колонке базы данных щелкните **Все параметры**.  
  
5.  В колонке **Параметры** выберите **Прозрачное шифрование данных** , чтобы открыть колонку **Прозрачное шифрование данных** .  
  
6.  В колонке **Шифрование данных** установите кнопку **Шифрование данных** в положение **ВКЛ**и нажмите кнопку **Сохранить** вверху страницы, чтобы применить настройки. В разделе **Состояние шифрования** будет отображаться приблизительный ход прозрачного шифрования данных.  
  
     ![Начало шифрования базы данных SQL TDE](../../../relational-databases/security/encryption/media/sqldb-tde-encrypt.png "Начало шифрования базы данных SQL TDE")  
  
     Кроме того, отслеживать ход шифрования можно, подключившись к [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] с помощью инструмента запросов, например [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , в качестве пользователя базы данных с разрешением **VIEW DATABASE STATE** . Выполните запрос к столбцу **encryption_state** представления [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
##  <a name="Encrypt"></a> Включение TDE в [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] с помощью Transact-SQL  
 Включить TDE можно следующим образом.  
  
###  <a name="TsqlProcedure"></a>  
  
1.  Подключитесь к базе данных, используя учетные данные администратора или участника роли **dbmanager** в базе данных master.  
  
2.  Выполните следующие инструкции, чтобы зашифровать базу данных.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;  
    GO  
    ```  
  
3.  Чтобы отслеживать ход шифрования в [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], пользователи базы данных с разрешением **VIEW DATABASE STATE** могут выполнять запрос к столбцу **encryption_state** представления [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
##  <a name="EncryptPS"></a> Включение и отключение TDE в [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] с помощью PowerShell  
 Включить и отключить TDE можно с помощью следующих команд Azure PowerShell. Перед выполнением команды нужно подключить учетную запись к окну PS. Настройте этот пример, указав собственные значения параметров `ServerName`, `ResourceGroupName`и `DatabaseName` . Дополнительные сведения о PowerShell см. в разделе [Установка и настройка Azure PowerShell](http://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!NOTE]  
>  Чтобы продолжить, следует установить и настроить Azure PowerShell версии 1.0. Можно использовать и версию 0.9.8, но она устарела и требует перехода на командлеты Azure Resource Manager с помощью команды `PS C:\> Switch-AzureMode -Name AzureResourceManager` .  
  
###  <a name="PSlProcedure"></a>  
  
1.  Чтобы включить TDE, получите состояние TDE и просмотрите операцию шифрования.  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
    ```  
  
     Если используется версия 0.9.8, используйте команды Set-AzureSqlDatabaseTransparentDataEncryption, Get-AzureSqlDatabaseTransparentDataEncryption и Get-AzureSqlDatabaseTransparentDataEncryptionActivity.  
  
2.  Чтобы отключить TDE:  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"  
  
    ```  
  
     Если используется версия 0.9.8, используйте команду Set-AzureSqlDatabaseTransparentDataEncryption.  
  
##  <a name="Decrypt"></a> Расшифровка базы данных с защитой TDE в [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
  
#### <a name="to-disable-tde-by-using-the-azure-portal"></a>Отключение TDE с помощью портала Azure  
  
1.  Откройте портал Azure на странице [https://portal.azure.com](https://portal.azure.com) и войдите с использованием учетной записи администратора или участника Azure.  
  
2.  В области слева нажмите кнопку **ПРОСМОТРЕТЬ ВСЕ**и выберите **Базы данных SQL**.  
  
3.  После этого выберите пользовательскую базу данных. ****  
  
4.  В колонке базы данных щелкните **Все параметры**.  
  
5.  В колонке **Параметры** выберите **Прозрачное шифрование данных** , чтобы открыть колонку **Прозрачное шифрование данных** .  
  
6.  В колонке **Прозрачное шифрование данных** установите кнопку **Шифрование данных** в положение **ВЫКЛ**и нажмите кнопку **Сохранить** вверху страницы. В разделе **Состояние шифрования** будет отображаться приблизительный ход прозрачной расшифровки данных.  
  
     Кроме того, отслеживать ход расшифровки можно, подключившись к [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] с помощью инструмента запросов, например [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] , в качестве пользователя базы данных с разрешением **VIEW DATABASE STATE** . Выполните запрос к столбцу **encryption_state** представления [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
#### <a name="to-disable-tde-by-using-transact-sql"></a>Отключение TDE с помощью Transact-SQL  
  
1.  Подключитесь к базе данных, используя учетные данные администратора или участника роли **dbmanager** в базе данных master.  
  
2.  Выполните следующие инструкции, чтобы расшифровать базу данных.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;  
    GO  
    ```  
  
3.  Чтобы отслеживать ход шифрования в [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], пользователи базы данных с разрешением **VIEW DATABASE STATE** могут выполнять запрос к столбцу **encryption_state** представления [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
##  <a name="Working"></a> Перемещение защищенной с помощью TDE базы данных в [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
 Расшифровывать базы данных для работы в Azure не нужно. Параметры TDE базы данных-источника прозрачно наследуются целевым объектом. Сюда входят операции, связанные с:  
  
-   геовосстановлением;  
  
-   самостоятельным восстановлением до точки во времени;  
  
-   восстановлением удаленной базы данных;  
  
-   активной георепликацией;  
  
-   созданием копии базы данных.  
  
 При экспорте базы данных с защитой TDE с помощью функции экспорта на портале [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] или в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ее экспортируемое содержимое не шифруется. Экспортированное содержимое хранится в незашифрованных файлах BACPAC. Не забудьте защитить файлы .bacpac соответствующим образом и включить TDE после завершения импорта новой базы данных. 
 
 Например, если файл BACPAC экспортируется из локальной версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то импортированное содержимое новой базы данных не шифруется автоматически. Аналогично, при экспорте файла BACPAC из [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] в локальную версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]новая база данных не шифруется автоматически.  
 
 Единственным исключением является экспорт в и из [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] — TDE в новой базе данных включено, но сам файл BACPAC все равно не шифруется.
  
## <a name="related-sql-server-topic"></a>Связанный раздел по SQL Server  
 [Enable TDE on SQL Server Using EKM (Включение прозрачного шифрования данных в SQL Server с помощью расширенного управления ключами)](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="see-also"></a>См. также:  
 [Прозрачное шифрование данных (TDE)](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../../t-sql/statements/alter-database-transact-sql.md)  
  
  

