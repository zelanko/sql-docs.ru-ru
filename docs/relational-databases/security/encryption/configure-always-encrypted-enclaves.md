---
title: Настройка Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6e6fd1a6bdb0ada4f7256c07b487c31574756191
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712477"
---
# <a name="configure-always-encrypted-with-secure-enclaves"></a>Настройка Always Encrypted с безопасными анклавами
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md) расширяет существующую функцию [Always Encrypted](always-encrypted-database-engine.md), чтобы обеспечить расширенные функции защиты конфиденциальных данных.

Чтобы настроить функцию Always Encrypted с безопасными анклавами, используйте следующий рабочий процесс:

1. Настройте аттестацию службы защиты узла (HGS).
2. Установите [!INCLUDE[sql-server-2019](..\..\..\includes\sssqlv15-md.md)] на компьютере SQL Server.
3. Установите инструменты на клиентском компьютере или компьютере разработки.
4. Настройте тип анклава в экземпляре SQL Server.
5. Подготовьте ключи с поддержкой анклава.
6. Зашифруйте столбцы, содержащие конфиденциальные данные.
 


## <a name="configure-your-environment"></a>Настройка среды

Чтобы использовать безопасные анклавы с Always Encrypted, в вашей среде должны быть установлены предварительные версии Windows Server 2019 и SQL Server Management Studio (SSMS) 18.0, .NET Framework и несколько других компонентов. В следующих разделах приведены сведения и ссылки для получения необходимых компонентов.

### <a name="sql-server-computer-requirements"></a>Требования к компьютеру с SQL Server

Для компьютера, на котором работает SQL Server, требуется следующая операционная система и версия SQL Server:

*SQL Server*:

- [!INCLUDE[sql-server-2019](..\..\..\includes\sssqlv15-md.md)] или более поздней версии.

*Windows*:

- Windows 10 Корпоративная, версия 1809.
- Windows Server DataCenter (полугодовой канал), версия 1809.
- Windows Server 2019 DataCenter

> [!IMPORTANT]
> Компьютер с SQL Server должен быть настроен как защищенный узел, проверяемый HGS. Аттестация доверенного платформенного модуля является рекомендуемым методом аттестации анклава для рабочих сред. Для нее требуется, чтобы SQL Server выполнялся на физическом компьютере, а не на виртуальной машине. Виртуальные машины подходят только для подготовительных сред.

### <a name="hgs-computer-requirements"></a>Требования к компьютеру с HGS

Во время тестирования и прототипирования достаточно одного компьютера с HGS. Для рабочей среды настоятельно рекомендуется использовать отказоустойчивый кластер Windows с 3 компьютерами.

Служба защитника узлов Windows должна быть установлена ​​на отдельных компьютерах с HGS, а не на одном компьютере с SQL Server. Дополнительные сведения о требованиях к компьютеру с HGS и его настройке для Always Encrypted в SQL Server см. в [этой статье](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server).


### <a name="determine-your-attestation-service-url"></a>Определение URL-адреса службы аттестации

Чтобы определить URL-адрес службы аттестации, необходимо настроить средства и приложения:

1. Войдите в систему на компьютере SQL Server от имени администратора.
2. Запустите оболочку PowerShell от имени администратора.
3. Выполните команду [Get-HGSClientConfiguration](https://docs.microsoft.com/powershell/module/hgsclient/get-hgsclientconfiguration).
4. Запишите и сохраните свойство AttestationServerURL. Оно должно выглядеть приблизительно так: `http://x.x.x.x/Attestation`.


### <a name="install-tools"></a>Средства установки

Установите следующие инструменты на клиентском компьютере или компьютере разработки.

1. [.NET Framework 4.7.2](https://www.microsoft.com/net/download/dotnet-framework-runtime).
2. [SSMS 18.0 или более поздней версии](../../../ssms/download-sql-server-management-studio-ssms.md).
3. [Модуль SQL Server PowerShell](../../../powershell/download-sql-server-ps-module.md) 21.5 или более поздней версии.
4. [Visual Studio (рекомендуется версия 2017 или более поздняя)](https://visualstudio.microsoft.com/downloads/).
5. [Пакет разработчика для .NET Framework 4.7.2](https://www.microsoft.com/net/download/visual-studio-sdks).
6. [Пакет NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) версии 2.2.0 или более поздней.
7. [Пакет NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders ](https://www.nuget.org/packages?q=Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders).

Пакеты NuGet предназначены для использования в проектах Visual Studio для разработки приложений, использующих Always Encrypted с безопасными анклавами. Первый пакет требуется только в том случае, если главные ключи столбцов хранятся в Azure Key Vault. Дополнительные сведения см. в разделе [Разработка приложений, отправляющих полнофункциональные запросы в Visual Studio](#develop-applications-issuing-rich-queries-in-visual-studio).

### <a name="configure-a-secure-enclave"></a>Настройка безопасного анклава

На клиентском компьютере или компьютере разработки:

1. Откройте SSMS и подключитесь к экземпляру SQL Server в качестве администратора Active Directory (AD).
2. Чтобы проверить поддержку Always Encrypted с безопасными анклавами в вашем экземпляре, выполните следующий запрос:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```

    Запрос должен вернуть строку, которая выглядит следующим образом:  

    | name                           | value | value_in_use |
    | ------------------------------ | ----- | -------------|
    | тип анклава для шифрования столбцов | 0     | 0            |

3. Установите безопасный тип анклава для анклавов VBS.

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1
   RECONFIGURE
   ```

4. Перезапустите экземпляр SQL Server, чтобы предыдущее изменение вступило в силу. Можно перезапустить экземпляр в SSMS, щелкнув его правой кнопкой мыши в обозревателе объектов и выбрав "Перезапустить". После перезагрузки экземпляра повторно подключитесь к нему.

5. Убедитесь, что безопасный анклав загружен, выполнив следующий запрос:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```   

    Запрос должен вернуть строку, которая выглядит следующим образом:  

    | name                           | value | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | тип анклава для шифрования столбцов | 1     | 1              |

6. Чтобы активировать полнофункциональные вычисления в зашифрованных столбцах, выполните следующий запрос:

   ```sql
   DBCC traceon(127,-1)
   ```

    > [!NOTE]
    > Полнофункциональные вычисления по умолчанию отключены в [!INCLUDE[sql-server-2019](..\..\..\includes\sssqlv15-md.md)]. Их необходимо включить с помощью вышеуказанной инструкции после каждой перезагрузки экземпляра SQL Server.

## <a name="provision-enclave-enabled-keys"></a>Подготовка ключей с поддержкой анклава

Введение ключей с поддержкой анклава принципиально не меняет [рабочие процессы подготовки ключей и управления ими для функции Always Encrypted](overview-of-key-management-for-always-encrypted.md). Единственным изменением является рабочий процесс подготовки главного ключа столбца, где теперь можно пометить ключ как ключ с поддержкой анклава (по умолчанию главные ключи столбцов не поддерживают анклав). При указании нового главного ключа столбца, который должен поддерживать анклав, с помощью SSMS или PowerShell происходит следующее:

- Задается свойство **ENCLAVE_COMPUTATIONS** в метаданных главного ключа столбца в базе данных.
- Значения свойств главного ключа столбца (включая свойство **ENCLAVE_COMPUTATIONS**) получают цифровую подпись. Средство добавляет в метаданные подпись, которая производится с использованием фактического главного ключа столбца. Цель подписи — запретить злонамеренным администраторам баз данных и компьютерам изменять свойство **ENCLAVE_COMPUTATIONS**. Драйверы клиента SQL проверяют подписи, прежде чем разрешить использование анклава. Это позволяет администраторам безопасности контролировать, какие данные столбцов могут быть вычислены внутри анклава.

Свойство **ENCLAVE_COMPUTATIONS** главного ключа столбца является неизменяемым — его нельзя изменить после подготовки ключа. Однако можно заменить главный ключ столбца новым ключом, имеющим другое значение свойства **ENCLAVE_COMPUTATIONS**, чем исходный ключ, с помощью процесса, называемого [сменой главного ключа столбца](#initiate-the-rotation-from-the-current-column-master-key-to-the-new-column-master-key). Дополнительные сведения о свойстве **ENCLAVE_COMPUTATIONS** содержатся в статье [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md).

Чтобы подготовить ключ шифрования столбцов с поддержкой анклава, необходимо убедиться, что главный ключ столбца, который шифрует ключ шифрования столбцов, также поддерживает анклав.

В настоящее время для подготовки ключей с поддержкой анклава применяются следующие ограничения:

- **Главные ключи столбцов с поддержкой анклава должны храниться в хранилище сертификатов Windows или в Azure Key Vault**. Хранение главных ключей столбцов с поддержкой анклава в других типах хранилищ ключей (аппаратных модулях безопасности или настраиваемых хранилищах ключей) в настоящее время не поддерживается.

### <a name="provision-enclave-enabled-keys-using-sql-server-management-studio-ssms"></a>**Подготовка ключей с поддержкой анклава с помощью SQL Server Management Studio (SSMS)**

Ниже приведены шаги по созданию ключей с поддержкой анклава (требуется SSMS 18.0 или более поздняя версия):

1. Подключитесь к базе данных с помощью SSMS.
2. В **обозревателе объектов** разверните базу данных и перейдите к пункту **Безопасность** > **Ключи Always Encrypted**.
3. Подготовьте новый главный ключ столбца с поддержкой анклава:

    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Новый главный ключ столбца...**
    2. Выберите имя главного ключа столбца.
    3. Убедитесь, что выбрано значение **Хранилище сертификатов Windows (текущий пользователь или локальный компьютер)** или **Azure Key Vault**.
    4. Выберите **Разрешить вычисления анклава**.
    5. Если вы выбрали Azure Key Vault, войдите в Azure и выберите хранилище ключей. Дополнительные сведения о том, как создать хранилище ключей для Always Encrypted, см. в статье [Manage your key vaults from Azure portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/) (Управление хранилищами ключей на портале Azure).
    6. Выберите свой ключ, если он уже существует, или создайте новый ключ, следуя указаниям в форме.
    7. Нажмите кнопку **ОК**.

        ![Разрешение вычислений анклава](./media/always-encrypted-enclaves/allow-enclave-computations.png)

4. Создайте ключ шифрования столбцов с поддержкой анклава:

    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Ключ шифрования нового столбца**.
    2. Введите имя для нового ключа шифрования столбцов.
    3. В раскрывающемся списке **Главный ключ столбца** выберите ключ, созданный на предыдущих шагах.
    4. Нажмите кнопку **ОК**.

### <a name="provision-enclave-enabled-keys-using-powershell"></a>**Подготовка ключей с поддержкой анклава с помощью PowerShell**

В следующих разделах приведены примеры скриптов PowerShell для подготовки ключей с поддержкой анклава. Приведены (новые) шаги, относящиеся к Always Encrypted с безопасными анклавами. Дополнительные сведения (не только для Always Encrypted с безопасными анклавами) о подготовке ключей с помощью PowerShell см. в статье [Manage your key vaults from Azure portal](https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell) (Управление хранилищами ключей на портале Azure).

**Подготовка ключей с поддержкой анклава — хранилище сертификатов Windows**

На компьютере клиента или компьютере разработки откройте интегрированную среду сценариев Windows PowerShell и запустите следующий скрипт.

Обратите внимание на использование параметра `-AllowEnclaveComputations` в командлете [ **New-SqlCertificateStoreColumnMasterKeySettings**](https://docs.microsoft.com/powershell/module/sqlserver/new-sqlcertificatestorecolumnmasterkeysettings).

```powershell
# Create a column master key in Windows Certificate Store.
$cert = New-SelfSignedCertificate -Subject "\<Subject Name\>" -CertStoreLocation Cert:CurrentUser\\My -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage DataEncipherment -KeySpec KeyExchange

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Provide the server/db name. Modify the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Create a SqlColumnMasterKeySettings object for your column master key
# using the -AllowEnclaveComputations parameter.
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert.Thumbprint -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```


### <a name="provisioning-enclave-enabled-keys--azure-key-vault"></a>Подготовка ключей с поддержкой анклава — Azure Key Vault

На компьютере клиента или компьютере разработки откройте интегрированную среду сценариев Windows PowerShell и запустите следующий скрипт.

**Шаг 1. Подготовка главного ключа столбца в Azure Key Vault**

Это также можно сделать с помощью портала Azure. Дополнительные сведения см. в статье [Manage your key vaults from Azure portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/) (Управление хранилищами ключей на портале Azure).


```powershell
Import-Module AzureRM
Connect-AzureRmAccount

# User values
$SubscriptionId = "<Azure SubscriptionId>"
$resourceGroup = "<resource group name>"
$azureLocation = "<datacenter location>"
$akvName = "<key vault name>"
$akvKeyName = "<key name>"

# Set the context to the specified subscription.
$azureCtx = Set-AzureRMConteXt -SubscriptionId $SubscriptionId

# Create a new resource group - skip, if your desired group already exists.
New-AzureRmResourceGroup –Name $resourceGroup –Location $azureLocation

# Create a new key vault - skip if your vault already exists.
New-AzureRmKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation

# Grant yourself permissions needed to create and use the column master key.
Set-AzureRmKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, list, update, wrapKey,unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account

# Create a column master key in Azure Key Vault.
$akvKey = Add-AzureKeyVaultKey -VaultName $akvName -Name $akvKeyName -Destination "Software"
```

**Шаг 2. Создание метаданных главного ключа столбца в базе данных, создание ключа шифрования столбцов и создание метаданных ключа шифрования столбцов в базе данных**


```powershell
# Import the SqlServer module.
Import-Module "SqlServer" -Version

# Connect to your database. Provide the server and db name. If needed, modify the connection string.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Authenticate to Azure before calling New-SqlAzureKeyVaultColumnMasterKeySettings,
# because -AllowEnclaveComputations causes a call to Azure Key Vault
# to generate the signature of the column master key.
Add-SqlAzureAuthenticationContext -Interactive

# Create a SqlColumnMasterKeySettings object for your column master key.
$cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyURL $akvKey.ID -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```


## <a name="identify-enclave-enabled-keys-and-columns"></a>Определение ключей и столбцов с поддержкой анклава

Чтобы получить список главных ключей столбцов, настроенных в базе данных, вы можете запросить представление каталога [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md) (например, в SSMS). Новый столбец **allow_enclave_computations** был добавлен в представление. Он указывает, поддерживает ли главный ключ столбца анклав.

```sql
SELECT name, allow_enclave_computations
FROM sys.column_master_keys
```

Чтобы определить, какие ключи шифрования столбцов зашифрованы с помощью ключей с поддержкой анклава (и, таким образом, поддерживают анклав), вам необходимо использовать представления [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md), [sys.column_encryption_key_values](../../system-catalog-views/sys-column-encryption-key-values-transact-sql.md) и [sys.column_encryption_keys](../../system-catalog-views/sys-column-encryption-keys-transact-sql.md).


```sql
SELECT cek.name AS [cek_name]
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
FROM sys.column_master_keys cmk
JOIN sys.column_encryption_key_values cekv
   ON cmk.column_master_key_id = cekv.column_master_key_id
JOIN sys.column_encryption_keys cek
   ON cekv.column_encryption_key_id = cek.column_encryption_key_id
```

Чтобы определить, какие столбцы поддерживают анклав (столбцы, зашифрованные с помощью ключей шифрования столбцов с поддержкой анклава), используйте следующий запрос:

```sql
SELECT c.name AS column_name
, cek.name AS cek_name
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
from sys.columns c
JOIN sys.column_encryption_keys cek 
ON c.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_encryption_key_values cekv 
ON cekv.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_master_keys cmk 
ON cmk.column_master_key_id = cekv.column_master_key_id
```


## <a name="manage-collations"></a>Управление параметрами сортировки

Начиная с первоначального выпуска, Always Encrypted имеет ограничение относительно использования сортировок: сортировки, которые не относятся к типу BIN2, не разрешены для столбцов символьных строк, зашифрованных с использованием детерминированного шифрования. Это ограничение также применяется к столбцам строк с поддержкой анклава.

Использование сортировок, которые не относятся к типу BIN2, разрешено для столбцов символьных строк, зашифрованных с помощью случайного шифрования и ключей шифрования столбцов с поддержкой анклава. Однако единственной новой функцией, которая включена для таких столбцов, является шифрование на месте. Чтобы активировать полнофункциональные вычисления (сопоставление шаблонов, операции сравнения), вы должны убедиться, что столбец использует сортировку BIN2.

В таблице ниже приведены функциональные возможности для строковых столбцов с поддержкой анклава, в зависимости от типа шифрования и порядка сортировки.

| **Порядок сортировки** | **Детерминированное шифрование** | **Случайное шифрование**                 |
| ------------------------ | ---------------------------- | ----------------------------------------- |
| **Не BIN2**             | Не поддерживается                | Шифрование на месте                       |
| **BIN2**                 | Сравнение на равенство          | Шифрование на месте и полнофункциональные вычисления |

### <a name="determining-and-changing-collations"></a>Установка и изменение параметров сортировки

В SQL Server параметры сортировки могут быть установлены на уровне сервера, базы данных или столбца. Общие указания о том, как определить текущие параметры сортировки и изменить сортировку на уровне сервера, базы данных или столбца, см. в статье о [поддержке сортировки и Юникода](https://docs.microsoft.com/sql/relational-databases/collations/collation-and-unicode-support).

**Особые замечания относительно строковых столбцов не в Юникоде**:

Следующее дополнительное ограничение, налагаемое в драйверах клиента SQL (не относящееся к Always Encrypted), применяется к столбцам строк не в Юникоде (ASCII). Если перезаписать параметры сортировки базы данных для строкового столбца не в Юникоде (char, varchar), необходимо убедиться, что параметры сортировки столбца используют ту же кодовую страницу, что и параметры сортировки базы данных.
Чтобы просмотреть все параметры сортировки вместе с идентификаторами кодовой страницы, используйте следующий запрос:

```sql
SELECT [Name]
   , [Description]
   , [CodePage] = COLLATIONPROPERTY([Name], 'CodePage')
FROM ::fn_helpcollations()
```

Например, Chinese_Traditional_Stroke_Order_100_CI_AI_WS и Chinese_Traditional_Stroke_Order_100_BIN2 имеют одинаковую кодовую страницу (950), но Chinese_Traditional_Stroke_Order_100_CI_AI_WS и Latin1_General_100_BIN2 имеют различные кодовые страницы (950 и 1252 соответственно). Указанное выше ограничение не применяется к столбцам строк в Юникоде (nchar, nvarchar). В качестве обходного решения можно задать тип данных "Юникод" для создаваемых зашифрованных столбцов или изменить тип на "Юникод" перед шифрованием существующего столбца.


## <a name="create-a-new-table-with-enclave-enabled-columns"></a>Создание новой таблицы со столбцами с поддержкой анклава

Можно создать новую таблицу с зашифрованными столбцами с помощью инструкции [CREATE TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/create-table-transact-sql). Always Encrypted с безопасными анклавами не изменяет синтаксис этой инструкции.

1. Используя SSMS, подключитесь к своей базе данных и откройте окно запроса.
   
     > [!NOTE]
     > Функция Always Encrypted не должна быть включена в строке подключения для этой задачи.

2. В окне запроса выполните инструкцию CREATE TABLE, чтобы создать новую таблицу, указав предложение ENCRYPTED WITH в [определении столбца](https://docs.microsoft.com/sql/t-sql/statements/alter-table-column-definition-transact-sql) для каждого столбца, который нужно зашифровать. Чтобы столбец поддерживал анклав, укажите ключ шифрования столбцов с поддержкой анклава. Вам также может потребоваться указать сортировку BIN2 для строковых столбцов, если она не является сортировкой по умолчанию для вашей базы данных. Дополнительные сведения см. в разделе настройки параметров сортировки.

### <a name="example"></a>Пример

Приведенная ниже инструкция создает новую таблицу с двумя зашифрованными столбцами: SSN и Salary. Предполагая, что CEK1 является ключом шифрования столбцов с поддержкой анклава, ядро SQL Server поддерживает как шифрование на месте, так и полнофункциональные вычисления для обоих столбцов, потому что в столбцах используется случайное шифрование. Инструкция устанавливает сортировку Latin1\_General\_BIN2 для столбца SSN в Юникоде. Это требуется при условии, что сортировка базы данных по умолчанию отлична от BIN2 Latin1.

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```


## <a name="add-a-new-enclave-enabled-column-to-an-existing-table"></a>Добавление нового столбца с поддержкой анклава в существующую таблицу

Можно добавить новый зашифрованный столбец к существующей таблице с помощью инструкции [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) / ADD. Always Encrypted с безопасными анклавами не изменяет синтаксис этой инструкции.

1. Используя SSMS, подключитесь к своей базе данных и откройте окно запроса.
    
   Функция Always Encrypted не должна быть включена в строке подключения для этой задачи.

2. В окне запроса выполните инструкцию ALTER TABLE с предложением ADD, указав предложение ENCRYPTED WITH в [определении столбца](https://docs.microsoft.com/sql/t-sql/statements/alter-table-column-definition-transact-sql) и используя ключ шифрования столбцов с поддержкой анклава. Вам также может потребоваться указать сортировку BIN2 для строковых столбцов, если она не является сортировкой по умолчанию для вашей базы данных. Дополнительные сведения см. в разделе настройки параметров сортировки.

### <a name="example"></a>Пример

Предполагая, что CEK1 является ключом шифрования столбцов с поддержкой анклава, приведенная ниже инструкция добавляет новый зашифрованный столбец с именем BirthDate, который поддерживает как полнофункциональные запросы, так и шифрование на месте (так как столбец использует случайное шифрование).

```sql
ALTER TABLE [dbo].[Employees]
ADD [BirthDate] [Date] ENCRYPTED WITH (
COLUMN_ENCRYPTION_KEY = [CEK1],
ENCRYPTION_TYPE = Randomized,
ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL
```


## <a name="prepare-an-ssms-query-window-with-always-encrypted-enabled"></a>Подготовка окна запросов SSMS при включенной функции Always Encrypted

Чтобы добавить необходимые параметры подключения для активации вычислений в анклаве:

1. Откройте SSMS.
2. После указания имени сервера и имени базы данных в диалоговом окне подключения к серверу щелкните **Параметры**. Перейдите на вкладку **Always Encrypted**, выберите **Включить Always Encrypted** и укажите URL-адрес аттестации анклава.
    
    ![Настройка шифрования столбца](./media/always-encrypted-enclaves/column-encryption-setting.png)

3. Нажмите кнопку "Подключить".
4. Откройте новое окно запроса.

Кроме того, если у вас уже открыто окно запроса, вот как вы можете обновить его подключение к базе данных, чтобы включить Always Encrypted:

1. Щелкните правой кнопкой мыши в существующем окне запроса.
2. Выберите "Подключение \> Изменить подключение".
3. Нажмите кнопку **Параметры**. Перейдите на вкладку **Always Encrypted**, выберите **Включить Always Encrypted** и укажите URL-адрес аттестации анклава.
4. Нажмите кнопку "Подключить".


## <a name="work-with-encrypted-columns"></a>Работа с зашифрованными столбцами

### <a name="encrypt-an-existing-plaintext-column-in-place"></a>Шифрование существующего столбца с открытым текстом на месте

Вы можете зашифровать существующий столбец с открытым текстом на месте с помощью инструкции [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) / ALTER COLUMN, если используется ключ шифрования столбцов с поддержкой анклава.

Чтобы зашифровать столбец с помощью ключа без поддержки анклава, вам необходимо использовать инструменты на стороне клиента, такие как мастер Always Encrypted в SSMS или командлет Set-SqlColumnEncryption в модуле SqlServer PowerShell. Подробная информация доступна в следующих статьях:

- [Мастер постоянного шифрования](always-encrypted-wizard.md)
- [Настройка шифрования столбцов с помощью PowerShell](configure-column-encryption-using-powershell.md)


### <a name="prerequisites"></a>предварительные требования

- Существующий столбец не зашифрован.
- Вы подготовили ключи с поддержкой анклава.
- У вас есть доступ к главному ключу столбца.

#### <a name="steps"></a>Шаги

1. Подготовьте окно запроса SSMS с активированными вычислениями в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).
2. В окне запроса выполните инструкцию ALTER TABLE с предложением ALTER COLUMN, указав ключ шифрования столбцов с поддержкой анклава в предложении ENCRYPTED WITH. Если это строковый столбец (например, char, varchar, nchar, nvarchar), вам также может потребоваться изменить сортировку на BIN2. Дополнительные сведения см. в разделе настройки параметров сортировки.
    
    > [!NOTE]
    > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

3. (Необязательно.) Очистите кэш планов с помощью [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md), чтобы гарантировать, что планы любого запроса зашифрованных столбцов будут повторно созданы при первом выполнении запроса.
  
    > [!NOTE]
    > Если вы не удалите план затронутого запроса из кэша, первое выполнение запроса после шифрования может завершиться сбоем.

    > [!NOTE]
    > Используйте DBCC FREEPROCCACHE, чтобы очистить кэш планов осторожно, так как это может привести к временному ухудшению производительности запросов. Чтобы свести к минимуму негативное влияние очистки кэша, вы можете выборочно удалять планы только для затронутых запросов.

4.  (Необязательно.) Вызовите [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md), чтобы обновить метаданные параметров каждого модуля (хранимая процедура, функция, представление, триггер), которые могут быть аннулированы в результате шифрования столбцов.

#### <a name="example"></a>Пример

В приведенном ниже примере предполагается:

  - CEK1 — это ключ шифрования столбцов с поддержкой анклава.

  - Столбец SSN содержит открытый текст и в настоящий момент использует Latin1 и параметры сортировки, отличные от BIN2 (например, Latin1Latin1\_General\_CI\_AI\_KS\_WS).

Инструкция шифрует столбец SSN, используя случайное шифрование и ключ шифрования столбцов с поддержкой анклава. Она также перезаписывает сортировку базы данных по умолчанию соответствующими (в той же кодовой странице) параметрами сортировки BIN2.

Операция выполняется в сети (ONLINE = ON). Также обратите внимание на вызов **DBCC FREEPROCCACHE**, повторно создающий планы запросов, на которые повлияло изменение схемы таблицы.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


### <a name="make-an-existing-encrypted-column-enclave-enabled"></a>Создание существующего зашифрованного столбца с поддержкой анклава

Существует несколько способов включения функции анклава для существующего столбца без поддержки анклава. Выбор метода зависит от нескольких факторов:

- **Область или степень детализации**. Вы хотите включить функцию анклава для подмножества столбцов или для всех столбцов, защищенных данным главным ключом столбцов?
- **Размер данных**. Каков размер таблиц, содержащих столбцы, для которых нужно реализовать поддержку анклава?
- Вы также хотите изменить тип шифрования для своих столбцов? Помните, что только случайное шифрование поддерживает полнофункциональные вычисления (сопоставление шаблонов, операторы сравнения). Если столбец зашифрован с использованием детерминированного шифрования, также необходимо будет повторно зашифровать его с помощью случайного шифрования, чтобы разблокировать все функциональные возможности анклава.

Ниже приведены три способа реализации поддержки анклавов для существующих столбцов.

#### <a name="option-1-rotate-the-column-master-key-to-replace-it-with-an-enclave-enabled-column-master-key"></a>Способ 1. Замените главный ключ столбца на главный ключ столбца с поддержкой анклава.
  
- Преимущества.
  - Не требуется повторное шифрование данных, поэтому, как правило, это самый быстрый подход. Это рекомендуемый подход для столбцов, содержащих большие объемы данных, при условии, что все столбцы, для которых нужно включить полнофункциональные вычисления, уже используют детерминированное шифрование, и поэтому их не нужно шифровать повторно.
  - Этот подход позволяет включить функцию анклава для нескольких столбцов в масштабе, так как он реализует поддержку анклава для всех ключей шифрования столбцов и всех зашифрованных столбцов, связанных с исходным главным ключом столбца.
  
- Недостатки.
  - Не поддерживает изменение типа шифрования с детерминированного на случайное, поэтому, хотя этот способ разблокирует шифрование на месте для столбцов, зашифрованных детерминированным образом, он не позволяет использовать полнофункциональные вычисления.
  - Не позволяет выборочно преобразовывать некоторые из столбцов, связанных с данным главным ключом столбца.
  - Вводит накладные расходы на управление ключами — необходимо создать новый главный ключ столбца и сделать его доступным для приложений, которые запрашивают затрагиваемые столбцы.  


#### <a name="option-2-this-approach-involves-two-steps-1-rotating-the-column-master-key-as-in-option-1-and-2-re-encrypting-a-subset-of-deterministically-encrypted-columns-using-randomized-encryption-to-enable-rich-computations-for-those-columns"></a>Способ 2. Этот подход включает в себя два шага: 1) замену главного ключа столбца (как в варианте 1) и 2) повторное шифрование подмножества детерминировано зашифрованных столбцов с использованием случайного шифрования, чтобы обеспечить полнофункциональные вычисления для этих столбцов.
  
- Преимущества.
  - Повторно шифрует данные на месте, поэтому рекомендуется использовать полнофункциональные запросы для детерминировано зашифрованных столбцов, содержащих большие объемы данных. Обратите внимание, что шаг 1 разблокирует шифрование на месте для столбцов, использующих детерминированное шифрование, поэтому шаг 2 можно выполнить на месте.
  - Позволяет включить функциональность анклава для нескольких столбцов в масштабе.
  
- Недостатки.
  - Не позволяет выборочно преобразовывать некоторые из столбцов, связанных с данным главным ключом столбца.
  - Вводит накладные расходы на управление ключами — необходимо создать новый главный ключ столбца и сделать его доступным для приложений, которые запрашивают затрагиваемые столбцы.

#### <a name="option-3-re-encrypting-selected-columns-with-a-new-enclave-enabled-column-encryption-key-and-randomized-encryption-if-needed-on-the-client-side"></a>Способ 3. Повторное шифрование выбранных столбцов с помощью нового ключа шифрования столбцов с поддержкой анклава и случайного шифрования (при необходимости) на стороне клиента.
  
- Преимущества.
  - Позволяет выборочно включить функциональность анклава для одного столбца или небольшого подмножества столбцов.
  - Он может включать полнофункциональные вычисления для детерминировано зашифрованного столбца за один шаг.
  - Он не требует создания нового главного ключа столбца, поэтому оказывает меньшее влияние на приложения.
  
- Недостатки.
  - Все содержимое таблицы, содержащей столбец, необходимо переместить за пределы базы данных для повторного шифрования, поэтому его рекомендуется использовать только для небольших таблиц. 

Дополнительные сведения см. в следующих разделах:
  - [Реализация поддержки анклава для столбцов путем смены главного ключа столбца](#make-columns-enclave-enabled-by-rotating-their-column-master-key)
  - [Повторное шифрование столбцов на месте](#re-encrypt-columns-in-place)
  - [Повторное шифрование столбцов на стороне клиента](#re-encrypt-columns-on-the-client-side)

### <a name="make-columns-enclave-enabled-by-rotating-their-column-master-key"></a>Реализация поддержки анклава для столбцов путем смены главного ключа столбца

Смена главного ключа столбца — это процесс замены существующего главного ключа столбца новым главным ключом столбца. Этот процесс включает повторное шифрование ключей шифрования столбцов, связанных со старым главным ключом столбца, с использованием нового главного ключа столбца. Этот рабочий процесс существует с момента первоначального выпуска Always Encrypted для поддержки замены главного ключа столбца по причинам соответствия требованиям или безопасности (на случай компрометации существующего главного ключа столбца).

Always Encrypted с использованием анклавов добавляет новое назначение для рабочего процесса замены основных ключей столбцов. Предполагая, что старый главный ключ столбца не поддерживает анклав, а новый главный ключ столбца поддерживает, процесс замены эффективно реализует поддержку анклава для всех ключей шифрования столбцов, связанных с главным ключом столбца. При смене главного ключа столбца не выполняется повторное шифрование данных, поэтому рекомендуется использовать возможности анклава для существующих столбцов.

При смене главного ключа столбца не изменяется тип шифрования затрагиваемых столбцов. Таким образом, этот процесс может разблокировать только шифрование на месте для столбцов, зашифрованных детерминировано. Чтобы разблокировать полнофункциональные вычисления для столбцов, использующих детерминированное шифрование, необходимо повторно зашифровать их (на месте) после смены главного ключа столбца.

Вам также может понадобиться изменить параметры сортировки для строковых столбцов, использующих случайное шифрование, на параметры сортировки BIN2, чтобы разблокировать полнофункциональные вычисления. Дополнительные сведения см. в разделе настройки параметров сортировки.

Процесс смены главного ключа столбца одинаков, независимо от того, поддерживает ли этот ключ анклав. Сведения о том, как сменить главный ключ столбца, приведены по следующим ссылкам:

- [Смена главного ключа столбца с помощью SSMS](configure-always-encrypted-using-sql-server-management-studio.md)
- [Смена главного ключа столбца с помощью PowerShell](rotate-always-encrypted-keys-using-powershell.md)

Для удобства ниже приведен пример скрипта PowerShell для смены главного ключа столбца.

#### <a name="pre-requisites"></a>Предварительные требования

- Вы подготовили новый главный ключ столбца с поддержкой анклава.
- У вас есть доступ к старому и новому главному ключу столбца.
- Все строковые столбцы, защищенные старым главным ключом столбца, используют параметры сортировки BIN2. (Примечание. Кроме того, можно изменить параметры сортировки строковых столбцов после смены главного ключа столбца.)

#### <a name="steps"></a>Шаги

Вставьте следующий скрипт в интегрированную среду сценариев Windows PowerShell, заменив \<заполнители\> на конкретные значения:


```powershell
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Modify server/db name or/and the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " +
$databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Set the names of the old/current column master key and the new/target enclave-enabled column master key. (Change the names, if needed).
$oldCmkName = "<old column master key name>"
$newCmkName = "<new column master key name>"

# Authenticate to Azure. Needed only of either column master key is stored in Azure Key Vault.
Add-SqlAzureAuthenticationContext -Interactive

# Initiate the rotation from the current column master key to the new column master key.
Invoke-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName $oldCmkName
-TargetColumnMasterKeyName $newCmkName -InputObject $database

# Complete the rotation of the old column master key.
Complete-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName
$oldCmkName -InputObject $database

# Remove the old column master key metadata.
Remove-SqlColumnMasterKey -Name $oldCmkName -InputObject $database
```


### <a name="re-encrypt-columns-in-place"></a>Повторное шифрование столбцов на месте 

Когда столбец начнет поддерживать анклав, можно выполнить следующие операции на месте (внутри анклава без необходимости перемещать данные из базы данных):

- Смена ключа шифрования столбцов (чтобы заменить его новым ключом), например, для соблюдения правил соответствия, некоторые из которых требуют периодической смены ключей, или по соображениям безопасности (в случае, если ваш ключ шифрования столбцов будет скомпрометирован).
- Изменение типа шифрования, например, с детерминированного на случайное, чтобы разблокировать полнофункциональные вычисления для столбца.

#### <a name="prerequisites"></a>предварительные требования

- Столбец шифруется с помощью ключа шифрования с поддержкой анклава.
- Вы подготовили новый ключ шифрования столбцов с поддержкой анклава (если ваша цель заключается в замене текущего ключа шифрования столбцов с поддержкой анклава, защищающего столбец).
- У вас есть доступ к главному ключу столбца.

#### <a name="steps"></a>Шаги

1. Подготовьте окно запроса SSMS с поддержкой вычислений в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. В окне запроса выполните инструкцию [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) с предложением ALTER COLUMN, указав следующее в предложении ENCRYPTED WITH:
    
    1. Имя нового ключа шифрования столбцов с поддержкой анклава при смене текущего ключа. Если ключ шифрования столбцов не изменяется, необходимо указать имя текущего ключа.
    
    2. Новый тип шифрования в случае его изменения. Если тип шифрования не изменяется, необходимо указать текущий тип шифрования.
        
       Если столбец, который повторно шифруется, использует параметры сортировки (BIN2), отличающиеся от параметров сортировки базы данных по умолчанию, необходимо включить фразу COLLATE и указать текущие параметры сортировки столбцов в определении столбца (чтобы сохранить параметры сортировки одинаковыми).
        
       > [!NOTE]
       > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

3. (Необязательно.) Очистите кэш планов с помощью [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md), чтобы гарантировать, что планы любого запроса повторно зашифрованных столбцов будут повторно созданы при первом выполнении запроса.
    
    Если вы не удалите план для затронутого запроса из кэша, первое выполнение запроса после повторного шифрования может завершиться сбоем.
    
    > [!NOTE]
    > Используйте DBCC FREEPROCCACHE, чтобы очистить кэш планов осторожно, так как это может привести к временному ухудшению производительности запросов. Чтобы свести к минимуму негативное влияние очистки кэша, вы можете выборочно удалять планы только для затронутых запросов. Подробнее см. в статье [DBCC FREEPROCCACHE (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md).

4. (Необязательно.) Вызовите [sp_refresh_parameter_encryption](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql), чтобы обновить метаданные параметров каждого модуля (хранимая процедура, функция, представление, триггер), которые могут быть аннулированы в результате повторного шифрования столбцов.

#### <a name="examples"></a>Примеры

Предполагая, что столбец SSN в настоящее время шифруется с помощью ключа шифрования с поддержкой анклава с именем CEK1 и детерминированного шифрования, а текущие параметры сортировки, установленные на уровне столбца, имеют тип Latin1\_General\_BIN2, приведенная ниже инструкция повторно шифрует столбец с помощью случайного шифрования и того же ключа.


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
GO
DBCC FREEPROCCACHE
GO
```


Предполагая, что столбец SSN в настоящее время шифруется с помощью ключа шифрования с поддержкой анклава с именем CEK1 и детерминированного шифрования, а параметры сортировки базы данных по умолчанию являются параметрами сортировки BIN2 (и не заданы на уровне столбца), приведенная ниже инструкция повторно шифрует столбец с помощью нового ключа с поддержкой анклава с именем CEK2 (без изменения типа шифрования).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION\_TYPE = Deterministic
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
GO
DBCC FREEPROCCACHE
GO
```

Предполагая, что столбец SSN в настоящее время шифруется с помощью ключа шифрования с поддержкой анклава с именем CEK1 и детерминированного шифрования, а параметры сортировки базы данных по умолчанию являются параметрами сортировки BIN2 (и не заданы на уровне столбца), приведенная ниже инструкция повторно шифрует столбец с помощью нового ключа с поддержкой анклава и случайного шифрования. Кроме того, операция выполняется в оперативном режиме.


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL 
WITH (ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


### <a name="re-encrypt-columns-on-the-client-side"></a>Повторное шифрование столбцов на стороне клиента 

Устаревший метод для повторного шифрования (шифрования или расшифровки) столбцов использует средства на стороне клиента, такие как мастер Always Encrypted или PowerShell. Как правило, использование этого метода не рекомендуется, за исключением случаев, когда таблица, содержащая столбцы (которые повторно шифруются), небольшая и если вашей целью является объединение повторного шифрования столбца с новым ключом с поддержкой анклава и изменения типа шифрования (с детерминированного на случайное).

Обратите внимание, если при повторном шифровании столбца используется случайное шифрование, возможно, потребуется изменить параметры сортировки на BIN2 (до или после повторного шифрования), чтобы разблокировать полнофункциональные вычисления. Дополнительные сведения см. в разделе настройки параметров сортировки.

Подробная информация доступна в следующих статьях:

  - Смена ключей шифрования столбцов с использованием SSMS: <https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-wizard>
  - Смена ключей шифрования столбцов с использованием PowerShell: <https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-column-encryption-using-powershell>

### <a name="decrypt-a-column-in-place"></a>Расшифровка столбца на месте

Если столбец зашифрован с помощью ключа шифрования столбцов с поддержкой анклава, его можно расшифровать (преобразовать в столбец с открытым текстом) на месте с помощью инструкции ALTER TABLE. Кроме того, операция выполняется в оперативном режиме.

#### <a name="prerequisites"></a>предварительные требования

- Столбец шифруется с помощью ключа шифрования с поддержкой анклава.
- У вас есть доступ к главному ключу столбца.



#### <a name="steps"></a>Шаги

1.  Подготовьте окно запроса SSMS с поддержкой вычислений в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2.  В окне запроса выполните инструкцию [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) с предложением ALTER COLUMN, указав нужную конфигурацию столбца **без** предложения ENCRYPTED WITH:
    
    > [!NOTE]
    > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

3.  (Необязательно.) Очистите кэш планов с помощью [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md), чтобы гарантировать, что планы любого запроса расшифрованных столбцов будут повторно созданы при первом выполнении запроса.
    
    > [!NOTE]
    > Если вы не удалите план для затронутого запроса из кэша, первое выполнение запроса после расшифровки может завершиться сбоем.
    
    > [!NOTE]
    > Используйте DBCC FREEPROCCACHE, чтобы очистить кэш планов осторожно, так как это может привести к временному ухудшению производительности запросов. Чтобы свести к минимуму негативное влияние очистки кэша, вы можете выборочно удалять планы только для затронутых запросов. Подробнее см. в статье [DBCC FREEPROCCACHE (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md).

4.  (Необязательно.) Вызовите [sp\_refresh\_parameter\_encryption](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql), чтобы обновить метаданные параметров каждого модуля (хранимая процедура, функция, представление, триггер), которые могут быть аннулированы в результате расшифровки столбцов.

#### <a name="example"></a>Пример

Предполагая, что столбец SSN зашифрован и текущие параметры сортировки на уровне столбца имеют тип Latin1\_General\_BIN2, приведенная ниже инструкция расшифровывает столбец (и не изменяет параметры сортировки). Кроме того, можно изменить параметры сортировки, например, на отличные от BIN2 в той же инструкции.


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


## <a name="issue-rich-queries-against-encrypted-columns-using-ssms"></a>Отправка полнофункциональных запросов к зашифрованным столбцам с помощью SSMS

Самый быстрый способ попробовать полнофункциональные запросы к столбцам с поддержкой анклава — отправить их из окна запроса SSMS с включенным определением параметров для Always Encrypted. Дополнительные сведения об этой полезной возможности в SSMS см. в следующих ресурсах:

- [Parameterization for Always Encrypted – Using SSMS to Insert into, Update and Filter by Encrypted Columns](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/) (Определение параметров для Always Encrypted — использование SSMS для вставки, обновления и фильтрации зашифрованных столбцов)
- [Запрос зашифрованных столбцов](configure-always-encrypted-using-sql-server-management-studio.md#querying-encrypted-columns)



### <a name="prerequisites"></a>предварительные требования

- Столбцы с поддержкой анклава для выполнения запроса.
- У вас есть доступ к главному ключу столбца (или ключам).

### <a name="steps"></a>Шаги

1.  Подготовьте окно запроса SSMS с поддержкой вычислений в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2.  Включите определение параметров для Always Encrypted.
    
    1.  В главном меню SSMS выберите **Запрос**.
    2.  Щелкните **Параметры запроса**.
    3.  Выберите **Выполнение** > **Дополнительно**.
    4.  Установите или снимите флажок "Enable Parameterization for Always Encrypted" (Включить определение параметров для Always Encrypted).
    5.  Нажмите кнопку «ОК».

3.  Создайте и выполните запросы с использованием полнофункциональных вычислений для зашифрованных столбцов. Необходимо объявить переменную Transact-SQL для каждого значения, предназначенного для зашифрованного столбца в запросе. Переменные должны использовать встроенные инициализации (не могут быть заданы через инструкцию SET).
    
    > [!NOTE]
    > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

### <a name="example"></a>Пример

В этом примере предполагается, что база данных содержит таблицу, созданную с помощью следующей инструкции.

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```


CEK1 — это ключ шифрования столбцов с поддержкой анклава.

Вот пример запроса к таблице, который соответствует рекомендациям для параметризации:


```sql
DECLARE @SSNPattern CHAR(11) = '%1111%'
DECLARE @MinSalary INT = 1000
SELECT *
FROM [dbo].[Employees]
WHERE SSN LIKE @SSNPattern
    AND [Salary] >= @MinSalary;
GO;
```


## <a name="develop-applications-issuing-rich-queries-in-visual-studio"></a>Разработка приложений, которые отправляют полнофункциональные запросы, в Visual Studio

### <a name="set-up-your-you-visual-studio-project"></a>Настройка проекта Visual Studio

Чтобы использовать функцию Always Encrypted с безопасными анклавами в приложении .NET Framework, вам нужно убедиться, что приложение создано на основе .NET Framework 4.7.2 и интегрировано с пакетом NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders. Кроме того, если вы храните главный ключ столбца в Azure Key Vault, необходимо также интегрировать приложение с пакетом NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider версии 2.2.0 или более поздней. 

1. Запустите Visual Studio.
2. Создайте новый проект Visual C\# или откройте существующий.
3. Убедитесь, что в проекте настроена по крайней мере платформа .NET Framework 4.7.2. Щелкните правой кнопкой мыши проект в обозревателе решений, выберите "Свойства" и установите целевую платформу. NET Framework 4.7.2.

4. Установите следующий пакет NuGet. Щелкните **Инструменты** (главное меню) > **Диспетчер пакетов NuGet** > **Консоль диспетчера пакетов**. Выполните следующий код в консоли диспетчера пакетов.

  ```powershell
  Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider --IncludePrerelease 
  ```

5. Если вы используете Azure Key Vault для хранения главных ключей столбцов, установите следующие пакеты NuGet, щелкнув **Инструменты** (главное меню) > **Диспетчер пакетов NuGet** > **Консоль диспетчера пакетов**. Выполните следующий код в консоли диспетчера пакетов.

  ```powershell
  Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider --IncludePrerelease -Version 2.2.0
  Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
  ```

6. Выберите проект и нажмите кнопку "Установить".
7. Откройте файл конфигурации из проекта (например, App.config или Web.config).
8. Найдите раздел \<configuration\>. В разделе \<configuration\> найдите раздел \<configSections\>. Добавьте следующий раздел в \<configSections\>:

  ```
  <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
  ```

9. В разделе конфигурации под \<configSections\> добавьте следующий раздел, где указан конкретный поставщик анклава, который будет использоваться для подтверждения и взаимодействия с анклавами Intel SGX:

  ```
  \<SqlColumnEncryptionEnclaveProviders\>
      \<providers\>
      \<add name="VBS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.VirtualizationBasedSecurityEnclaveProvider, Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,   Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/\>
      \</SqlColumnEncryptionEnclaveProviders\>
  ```
 

### <a name="develop-and-test-your-app"></a>Разработка и тестирование приложения 

Чтобы использовать Always Encrypted и вычисления в анклаве, ваше приложение должно подключаться к базе данных с помощью следующих двух ключевых слов в строке подключения: `Column Encryption Setting = Enabled; Enclave Attestation Url=http://x.x.x.x/Attestation` (где xxxx может быть IP-адресом, доменом и т. д).

Кроме того, приложение должно соответствовать общим рекомендациям, применяемых к приложениям, использующим Always Encrypted. Например, приложение должно иметь доступ к главным ключам столбцов, связанным со столбцами базы данных, на которые ссылаются запросы приложения.

Дополнительные сведения о разработке приложений .NET Framework с использованием Always Encrypted см. в следующих статьях:

- [Разработка с использованием постоянного шифрования с поставщиком данных .NET Framework](develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Always Encrypted: защита конфиденциальных данных в Базе данных SQL и хранение ключей шифрования в хранилище сертификатов Windows](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

#### <a name="example"></a>Пример

Приведенный ниже код представляет собой простой пример консольного приложения C\#, которое отправляет запрос с предикатом LIKE в таблицу со следующей схемой:

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```

Предполагается, что CEK1 — это ключ шифрования столбцов с поддержкой анклава.


```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.SqlClient;
using System.Data;
namespace ConsoleApp1
{
   class Program
   {
      static void Main(string\[\] args)
   {

   string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = http://10.193.16.185/Attestation/attestationservice.svc/signingCertificates; Integrated Security = true";

using (SqlConnection connection = new SqlConnection(connectionString))
{
   connection.Open();
   
   SqlCommand cmd = connection.CreateCommand();
   cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [Salary] FROM [dbo].[Employees] WHERE [SSN] LIKE @SSNPattern AND [Salary] > @MinSalary;";
   
   SqlParameter paramSSNPattern = cmd.CreateParameter();
   
   paramSSNPattern.ParameterName = @"@SSNPattern";
   paramSSNPattern.DbType = DbType.AnsiStringFixedLength;
   paramSSNPattern.Direction = ParameterDirection.Input;
   paramSSNPattern.Value = "%1111";
   paramSSNPattern.Size = 11;
   
   cmd.Parameters.Add(paramSSNPattern);
   
   SqlParameter MinSalary = cmd.CreateParameter();
   
   MinSalary.ParameterName = @"@MinSalary";
   MinSalary.DbType = DbType.Int32;
   MinSalary.Direction = ParameterDirection.Input;
   MinSalary.Value = 900;
   
   cmd.Parameters.Add(MinSalary);
   cmd.ExecuteNonQuery();
   
   SqlDataReader reader = cmd.ExecuteReader();
   while (reader.Read())
   
   {
     Console.WriteLine(reader);
     Console.WriteLine(reader\[0\] + ", " + reader\[1\] + ", " + reader\[2\] + ", " + reader\[3\]);
   }

   Console.ReadKey();

   }
  }
 }
}
```
