---
title: Прозрачное шифрование данных в базе данных SQL Azure | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6af7c52741b85a2733b93c2b1ed8c03a14dd6343
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928225"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Прозрачное шифрование данных в Базе данных SQL Azure
  Прозрачное шифрование данных [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] (предварительная версия) защищает от угроз вредоносных действий, в реальном времени выполняя шифрование и расшифровку неактивных файлов базы данных, связанных резервных копий и журнала транзакций. При этом способ использования не меняется.

 При использовании TDE хранилище всей базы данных шифруется с помощью симметричного ключа, который называется ключом шифрования базы данных. В [!INCLUDE[ssSDS](../includes/sssds-md.md)] для защиты ключа шифрования базы данных используется встроенный сертификат сервера. Встроенный сертификат сервера уникален для каждого сервера [!INCLUDE[ssSDS](../includes/sssds-md.md)] . Если база данных находится в отношении GeoDR, на каждом сервере для защиты используется разный ключ. Если две базы данных подключены к одному серверу, используется один встроенный сертификат. [!INCLUDE[msCoName](../includes/msconame-md.md)] автоматически меняет эти сертификаты каждые 90 дней. Общее описание прозрачного шифрования данных см. в разделе [Прозрачное шифрование данных (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md).

 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] не поддерживает интеграцию хранилища ключей Azure с TDE. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , запущенный на виртуальной машине Azure, может использовать асимметричный ключ из хранилища ключей. Дополнительные сведения см. в разделе [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).

||
|-|
|Область **применения**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Предварительная версия в некоторых регионах](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|

> [!IMPORTANT]
>  В настоящий момент это предварительная версия функции. Я признаю и соглашаюсь, что в отношении использования в моих базах данных прозрачного шифрования данных [!INCLUDE[ssSDS](../includes/sssds-md.md)] действуют условия предварительной версии, приведенные в моем лицензионном соглашении (например, Соглашении Enterprise, соглашении для Microsoft Azure или соглашении Microsoft Online Subscription), а также [дополнительные условия использования предварительных версий Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

 Просмотр состояния TDE применяется даже в подмножестве географических регионов, в которых сообщается, что версия семейства V12 [!INCLUDE[ssSDS](../includes/sssds-md.md)] теперь общедоступна. Прозрачное шифрование данных для [!INCLUDE[ssSDS](../includes/sssds-md.md)] не используется в рабочих базах данных до тех пор, пока [!INCLUDE[msCoName](../includes/msconame-md.md)] не объявит, что функция TDE становится общедоступной. Дополнительные сведения о [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12 можно найти в разделе [Новые возможности версии 12 базы данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).

##  <a name="permissions"></a><a name="Permissions"></a> Permissions
 Чтобы подписаться на предварительную версию и настроить TDE через портал Azure с помощью REST API или PowerShell, необходимо подключиться в качестве владельца, участника или диспетчера безопасности SQL Azure.

 Чтобы настроить TDE с помощью [!INCLUDE[tsql](../includes/tsql-md.md)] :

-   Нужен доступ к предварительной версии TDE.

-   Чтобы создать ключ шифрования базы данных, нужны права администратора [!INCLUDE[ssSDS](../includes/sssds-md.md)] или роль **dbmanager** в базе данных master и разрешение **CONTROL** .

-   Чтобы выполнить инструкцию ALTER DATABASE с параметром SET, нужна только роль **dbmanager** .

##  <a name="sign-up-for-the-preview-of-tde-and-enable-tde-on-a-database"></a><a name="Preview"></a>Зарегистрируйтесь для использования предварительной версии TDE и включите TDE в базе данных

1.  Посетите портал Azure по адресу [https://portal.azure.com](https://portal.azure.com) и войдите с помощью учетной записи администратора или участника Azure.

2.  В области слева нажмите кнопку **ОБЗОР** и выберите **Базы данных SQL**.

3.  Выбрав пункт **Базы данных SQL** в области слева, выберите свою пользовательскую базу данных.

4.  В колонке базы данных щелкните **Все параметры**.

5.  В колонке **Параметры** выберите **Прозрачное шифрование данных (предварительная версия)** , чтобы открыть колонку **Прозрачное шифрование данных ПРЕДВАРИТЕЛЬНАЯ ВЕРСИЯ** . Если вы еще не подписались на предварительную версию TDE, параметры шифрования данных будут неактивны.

6.  Щелкните **УСЛОВИЯ ПРЕДВАРИТЕЛЬНОЙ ВЕРСИИ**.

7.  Ознакомьтесь с условиями предварительной версии и, если вы согласны с условиями, установите флажок **прозрачные енкриптионпревиев термины данных** и нажмите кнопку **ОК** в нижней части страницы. Возврат в колонку **Енкриптионпревиев данных** , где теперь должна быть включена кнопка **шифрования данных** .

8.  В колонке **Шифрование данных ПРЕДВАРИТЕЛЬНАЯ ВЕРСИЯ** переместите кнопку **Шифрование данных** в положение **ВКЛ**и нажмите кнопку **Сохранить** вверху страницы. В разделе **Состояние шифрования** будет отображаться приблизительный ход прозрачного шифрования данных.

     ![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")

     Кроме того, отслеживать ход шифрования можно, подключившись к [!INCLUDE[ssSDS](../includes/sssds-md.md)] с помощью инструмента запросов, например [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , в качестве пользователя базы данных с разрешением **VIEW DATABASE STATE** . Запросите `encryption_state` Столбец представления [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) .

##  <a name="enabling-tde-on-sssds-by-using-transact-sql"></a><a name="Encrypt"></a>Включение TDE в с [!INCLUDE[ssSDS](../includes/sssds-md.md)] помощью Transact-SQL
 Далее предполагается, что вы уже подписались на предварительную версию.

###  <a name="TsqlProcedure"></a>

1.  Подключитесь к базе данных, используя учетные данные администратора или участника роли **dbmanager** в базе данных master.

2.  Выполните следующие инструкции, чтобы создать ключ шифрования и зашифровать базу данных.

    ```sql
    -- Create the database encryption key that will be used for TDE.
    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_256 
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;

    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;
    GO
    ```

3.  Чтобы отслеживать ход выполнения шифрования в [!INCLUDE[ssSDS](../includes/sssds-md.md)] , пользователи базы данных с разрешением **Просмотр состояния базы данных** могут запрашивать `encryption_state` столбец представления [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) .

## <a name="enabling-tde-on-sql-database-by-using-powershell"></a>Включение TDE в Базе данных SQL с помощью PowerShell
 Включить и отключить TDE можно с помощью следующих команд Azure PowerShell. Перед выполнением команды подключите свою учетную запись к окну PS. Далее предполагается, что вы уже подписались на предварительную версию. Дополнительные сведения о PowerShell см. в разделе [Установка и настройка Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

1.  Чтобы включить TDE и просмотреть состояние шифрования:

    ```powershell
    Switch-AzureMode -Name AzureResourceManager
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"

    Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    ```

2.  Чтобы отключить TDE:

    ```powershell
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"
    Switch-AzureMode -Name AzureServiceManagement
    ```

##  <a name="decrypting-a-tde-protected-database-on-sssds"></a><a name="Decrypt"></a>Расшифровка защищенной базы данных TDE на[!INCLUDE[ssSDS](../includes/sssds-md.md)]

#### <a name="to-disable-tde-by-using-the-azure-portal"></a>Отключение TDE с помощью портала Azure

1.  Посетите портал Azure по адресу [https://portal.azure.com](https://portal.azure.com) и войдите с помощью учетной записи администратора или участника Azure.

2.  В области слева нажмите кнопку **ОБЗОР** и выберите **Базы данных SQL**.

3.  Выбрав пункт **Базы данных SQL** в области слева, выберите свою пользовательскую базу данных.

4.  В колонке базы данных щелкните **Все параметры**.

5.  В колонке **Параметры** выберите **Прозрачное шифрование данных (предварительная версия)** , чтобы открыть колонку **Прозрачное шифрование данных ПРЕДВАРИТЕЛЬНАЯ ВЕРСИЯ** .

6.  В колонке **Прозрачное шифрование данных ПРЕДВАРИТЕЛЬНАЯ ВЕРСИЯ** переместите кнопку **Шифрование данных** в положение **ВЫКЛ**и нажмите кнопку **Сохранить** вверху страницы. В разделе **Состояние шифрования** будет отображаться приблизительный ход прозрачной расшифровки данных.

     Кроме того, отслеживать ход расшифровки можно, подключившись к [!INCLUDE[ssSDS](../includes/sssds-md.md)] с помощью инструмента запросов, например [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , в качестве пользователя базы данных с разрешением **VIEW DATABASE STATE** . Запросите `encryption_state` Столбец представления [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql).

#### <a name="to-disable-tde-by-using-transact-sql"></a>Отключение TDE с помощью Transact-SQL

1.  Подключитесь к базе данных, используя учетные данные администратора или участника роли **dbmanager** в базе данных master.

2.  Выполните следующие инструкции, чтобы расшифровать базу данных.

    ```sql
    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;
    GO
    ```

3.  Чтобы отслеживать ход выполнения шифрования в [!INCLUDE[ssSDS](../includes/sssds-md.md)] , пользователи базы данных с разрешением **Просмотр состояния базы данных** могут запрашивать `encryption_state` столбец представления [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) .

##  <a name="working-with-tde-protected-databases-on-sssds"></a><a name="Working"></a>Работа с защищенными базами данных TDE в[!INCLUDE[ssSDS](../includes/sssds-md.md)]
 Расшифровывать базы данных для работы в Azure не нужно. Параметры TDE базы данных-источника прозрачно наследуются целевым объектом. Сюда входят операции, связанные с:

-   геовосстановлением;

-   самостоятельным восстановлением до точки во времени;

-   восстановлением удаленной базы данных;

-   активной георепликацией;

-   созданием копии базы данных.

##  <a name="moving-a-tde-protected-database-on-using-bacpac-files"></a><a name="Moving"></a>Перемещение базы данных, защищенной TDE, в среде с помощью. BACPAC-файлы
 При экспорте базы данных с защитой TDE с помощью функции экспорта на портале [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] или в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ее содержимое не шифруется. Содержимое хранится в незашифрованных файлах .bacpac.  Не забудьте защитить файлы .bacpac соответствующим образом и включить TDE после завершения импорта новой базы данных.

## <a name="related-sql-server-topic"></a>Связанный раздел по SQL Server
 [Включение TDE с помощью расширенного управления ключами](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)

## <a name="see-also"></a>См. также:
 [Прозрачное шифрование данных &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [Создание учетных данных &#40;transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE асимметричный ключ &#40;TRANSACT-](/sql/t-sql/statements/create-asymmetric-key-transact-sql) SQL&#41;[Создание ключа шифрования базы данных &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql) [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) [инструкции ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)
