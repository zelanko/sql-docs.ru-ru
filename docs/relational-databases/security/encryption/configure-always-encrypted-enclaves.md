---
title: Настройка Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 27f78de54735559365f771aaee3669b8f08856c7
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72902991"
---
# <a name="configure-always-encrypted-with-secure-enclaves"></a>Настройка Always Encrypted с безопасными анклавами

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md) расширяет существующую функцию [Always Encrypted](always-encrypted-database-engine.md), чтобы обеспечить расширенные функции защиты конфиденциальных данных.

Чтобы настроить функцию Always Encrypted с безопасными анклавами, используйте следующий рабочий процесс.

1. Настройте аттестацию службы защиты узла (HGS).
2. Установите [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] на компьютере SQL Server.
3. Установите инструменты на клиентском компьютере или компьютере разработки.
4. Настройте тип анклава в экземпляре SQL Server.
5. Подготовьте ключи с поддержкой анклава.
6. Зашифруйте столбцы, содержащие конфиденциальные данные.

> [!NOTE]
> Пошаговое руководство о том, как настроить тестовую среду и протестировать функциональные возможности Always Encrypted с безопасными анклавами в SSMS, см. в статье [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="configure-your-environment"></a>Настройка среды

Чтобы использовать безопасные анклавы с Always Encrypted, в вашей среде должны быть установлены Windows Server 2019 (предварительная версия), SQL Server Management Studio (SSMS) 18.0, платформа .NET Framework и несколько других компонентов. В следующих разделах приведены сведения и ссылки для получения необходимых компонентов.

### <a name="sql-server-computer-requirements"></a>Требования к компьютеру с SQL Server

Для компьютера, на котором работает SQL Server, требуется следующая операционная система и версия SQL Server:

*SQL Server*:

- [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] или более поздней версии

*Windows*:

- Windows 10 Корпоративная, версия 1809.
- Windows Server DataCenter (полугодовой канал), версия 1809.
- Windows Server 2019 DataCenter

> [!IMPORTANT]
> Компьютер с SQL Server должен быть настроен как защищенный узел, проверяемый HGS. Аттестация доверенного платформенного модуля является рекомендуемым методом аттестации анклава для рабочих сред. Для нее требуется, чтобы SQL Server выполнялся на физическом компьютере, а не на виртуальной машине. Виртуальные машины подходят только для подготовительных сред.

### <a name="hgs-computer-requirements"></a>Требования к компьютеру с HGS

Во время тестирования и прототипирования достаточно одного компьютера с HGS. Для рабочей среды мы рекомендуем использовать отказоустойчивый кластер Windows с тремя компьютерами.

Служба защитника узлов Windows должна быть установлена ​​на отдельных компьютерах с HGS, а не на одном компьютере с SQL Server. Дополнительные сведения о требованиях к компьютеру с HGS и его настройке для Always Encrypted в SQL Server см. в [этой статье](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server).


### <a name="determine-your-attestation-service-url"></a>Определение URL-адреса службы аттестации

Чтобы определить URL-адрес службы аттестации, необходимо настроить средства и приложения:

1. Войдите в систему на компьютере SQL Server от имени администратора.
2. Запустите оболочку PowerShell от имени администратора.
3. Выполните команду [Get-HGSClientConfiguration](https://docs.microsoft.com/powershell/module/hgsclient/get-hgsclientconfiguration).
4. Запишите и сохраните свойство AttestationServerURL. Оно должно выглядеть приблизительно так: `https://x.x.x.x/Attestation`.

### <a name="install-tools"></a>Средства установки

Установите следующие инструменты на клиентском компьютере или компьютере разработки.

1. [.NET Framework 4.7.2](https://www.microsoft.com/net/download/dotnet-framework-runtime).
2. [SSMS 18.0 или более поздней версии](../../../ssms/download-sql-server-management-studio-ssms.md).
3. [Модуль SQL Server PowerShell](../../../powershell/download-sql-server-ps-module.md) 21.1 или более поздней версии.
4. [Visual Studio (рекомендуется версия 2017 или более поздняя)](https://visualstudio.microsoft.com/downloads/).
5. [Пакет разработчика для .NET Framework 4.7.2](https://www.microsoft.com/net/download/visual-studio-sdks).
6. [Пакет NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) версии 2.2.0 или более поздней.
7. [Пакет NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders ](https://www.nuget.org/packages?q=Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders).

Используйте пакеты NuGet в проектах Visual Studio для разработки приложений, использующих Always Encrypted с безопасными анклавами. Первый пакет требуется только в том случае, если главные ключи столбцов хранятся в Azure Key Vault. Дополнительные сведения см. в разделе [Разработка приложений, отправляющих полнофункциональные запросы в Visual Studio](#develop-applications-issuing-rich-queries-in-visual-studio).

### <a name="configure-a-secure-enclave"></a>Настройка безопасного анклава

На клиентском компьютере или компьютере разработки:

1. Откройте SSMS и подключитесь к экземпляру SQL Server в качестве администратора Active Directory (AD).
2. Чтобы проверить поддержку Always Encrypted с безопасными анклавами в вашем экземпляре, выполните следующий запрос:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type';
   ```

    Запрос должен вернуть строку, которая выглядит следующим образом:  

    | name                           | value | value_in_use |
    | ------------------------------ | ----- | -------------|
    | column encryption enclave type (тип анклава для шифрования столбцов) | 0     | 0            |

3. Установите безопасный тип анклава для анклавов VBS.

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1;
   RECONFIGURE;
   ```

4. Перезапустите экземпляр SQL Server, чтобы предыдущее изменение вступило в силу. Можно перезапустить этот экземпляр в SSMS, щелкнув его правой кнопкой мыши в обозревателе объектов и выбрав "Перезапуск". После перезагрузки экземпляра снова подключитесь к нему.

5. Убедитесь, что безопасный анклав загружен, выполнив следующий запрос:

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type';
   ```   

    Запрос должен вернуть строку, которая выглядит следующим образом:  

    | name                           | value | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type (тип анклава для шифрования столбцов) | 1     | 1              |

6. Чтобы активировать полнофункциональные вычисления в зашифрованных столбцах, выполните следующий запрос:

   ```sql
   DBCC traceon(127,-1);
   ```

    > [!NOTE]
    > Полнофункциональные вычисления в [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] по умолчанию отключены. Их необходимо включить с помощью вышеуказанной инструкции после каждой перезагрузки экземпляра SQL Server.

## <a name="provision-enclave-enabled-keys"></a>Подготовка ключей с поддержкой анклава

Введение ключей с поддержкой анклава принципиально не меняет [рабочие процессы подготовки ключей и управления ими для функции Always Encrypted](overview-of-key-management-for-always-encrypted.md). Единственное изменение затрагивает процесс подготовки главного ключа столбца. Его теперь можно пометить как ключ с поддержкой анклава (по умолчанию главные ключи столбцов не поддерживают анклав). Когда вы включаете поддержку анклава для главного ключа столбца с помощью SSMS или PowerShell, происходит следующее.

- В метаданных главного ключа столбца в базе данных задается свойство `ENCLAVE_COMPUTATIONS`.
- Значения свойств главного ключа столбца (включая свойство `ENCLAVE_COMPUTATIONS`) получают цифровую подпись. Средство добавляет в метаданные подпись, которая производится с использованием фактического главного ключа столбца. Эта подпись предотвращает вредоносное изменение параметра `ENCLAVE_COMPUTATIONS`. Драйверы клиента SQL проверяют подписи, прежде чем разрешить использование анклава. Это позволяет администраторам безопасности контролировать, какие данные столбцов могут быть вычислены внутри анклава.

Свойство `ENCLAVE_COMPUTATIONS` главного ключа столбца является неизменяемым. Вы не сможете изменить его после подготовки ключа. Однако можно заменить главный ключ столбца новым ключом, у которого значение свойства `ENCLAVE_COMPUTATIONS` отличается от значения для исходного ключа. Процесс замены главного ключа столбца описан [здесь](#make-columns-enclave-enabled-by-rotating-their-column-master-key). Дополнительные сведения о свойстве `ENCLAVE_COMPUTATIONS`вы найдете в статье [CREATE COLUMN MASTER KEY](../../../t-sql/statements/create-column-master-key-transact-sql.md).

Чтобы подготовить ключ шифрования столбцов с поддержкой анклава, необходимо убедиться, что главный ключ столбца, который шифрует ключ шифрования столбцов, также поддерживает анклав.

В настоящее время для подготовки ключей с поддержкой анклава применяются следующие ограничения:

- Главные ключи столбцов с поддержкой анклава должны храниться в [хранилище сертификатов Windows](/windows/desktop/seccrypto/managing-certificates-with-certificate-stores) или в [Azure Key Vault](/azure/key-vault/key-vault-whatis/). Хранение главных ключей столбцов с поддержкой анклава в других типах хранилищ ключей (например, в аппаратных модулях безопасности или настраиваемых хранилищах ключей) в настоящее время не поддерживается.

### <a name="provision-enclave-enabled-keys-using-sql-server-management-studio-ssms"></a>Подготовка ключей с поддержкой анклава с помощью SQL Server Management Studio (SSMS)

Ниже приведены шаги по созданию ключей с поддержкой анклава (требуется SSMS 18.0 или более поздняя версия):

1. Подключитесь к базе данных с помощью SSMS.
2. В **обозревателе объектов** разверните базу данных и перейдите к пункту **Безопасность** > **Ключи Always Encrypted**.
3. Подготовьте новый главный ключ столбца с поддержкой анклава:

    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Создать главный ключ столбца...** .
    2. Выберите имя главного ключа столбца.
    3. Убедитесь, что выбрано значение **Хранилище сертификатов Windows (текущий пользователь или локальный компьютер)** или **Azure Key Vault**.
    4. Выберите **Разрешить вычисления анклава**.
    5. Если вы выбрали Azure Key Vault, войдите в Azure и выберите хранилище ключей. Дополнительные сведения о создании хранилища ключей для Always Encrypted см. в статье [Управление хранилищами ключей на портале Azure](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).
    6. Выберите свой ключ, если он уже существует, или создайте новый ключ, следуя указаниям в форме.
    7. Нажмите кнопку **ОК**.

        ![Разрешение вычислений анклава](./media/always-encrypted-enclaves/allow-enclave-computations.png)

4. Создайте новый ключ шифрования столбцов с поддержкой анклава:

    1. Щелкните правой кнопкой мыши **Ключи Always Encrypted** и выберите **Создать ключ шифрования столбца**.
    2. Введите имя для нового ключа шифрования столбцов.
    3. В раскрывающемся списке **Главный ключ столбца** выберите ключ, созданный на предыдущих шагах.
    4. Нажмите кнопку **ОК**.

### <a name="provision-enclave-enabled-keys-using-powershell"></a>Подготовка ключей с поддержкой анклава с помощью PowerShell

В следующих разделах приведены примеры скриптов PowerShell для подготовки ключей с поддержкой анклава. Приведены (новые) шаги, относящиеся к Always Encrypted с безопасными анклавами. Дополнительные сведения (не только для Always Encrypted с безопасными анклавами) о подготовке ключей с помощью PowerShell см. в статье [Manage your key vaults from Azure portal](configure-always-encrypted-keys-using-powershell.md) (Управление хранилищами ключей на портале Azure).

#### <a name="provisioning-enclave-enabled-keys---windows-certificate-store"></a>Подготовка ключей с поддержкой анклава — хранилище сертификатов Windows

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

#### <a name="provisioning-enclave-enabled-keys---azure-key-vault"></a>Подготовка ключей с поддержкой анклава — Azure Key Vault

На компьютере клиента или компьютере разработки откройте интегрированную среду сценариев Windows PowerShell и запустите следующий скрипт.

**Шаг 1. Подготовка главного ключа столбца в Azure Key Vault**

Это также можно сделать с помощью портала Azure. Дополнительные сведения см. в статье [Manage your key vaults from Azure portal](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/) (Управление хранилищами ключей на портале Azure).


```powershell
Import-Module Az
Connect-AzAccount

# User values
$SubscriptionId = "<Azure SubscriptionId>"
$resourceGroup = "<resource group name>"
$azureLocation = "<datacenter location>"
$akvName = "<key vault name>"
$akvKeyName = "<key name>"

# Set the context to the specified subscription.
$azureCtx = Set-AzContext -SubscriptionId $SubscriptionId

# Create a new resource group - skip, if your desired group already exists.
New-AzResourceGroup -Name $resourceGroup -Location $azureLocation

# Create a new key vault - skip if your vault already exists.
New-AzKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation

# Grant yourself permissions needed to create and use the column master key.
Set-AzKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, list, update, wrapKey,unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account

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

Чтобы получить список главных ключей столбцов, которые настроены в базе данных, запросите представление каталога [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md) (например, через SSMS). Здесь есть новый столбец **allow_enclave_computations** с информацией о том, поддерживает ли главный ключ столбца анклав.

```sql
SELECT name, allow_enclave_computations
FROM sys.column_master_keys;
```

Ключ шифрования столбца поддерживает анклав, если он зашифрован с помощью ключей столбца с поддержкой анклава. Чтобы получить ключи шифрования столбцов, используйте представления [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md), [sys.column_encryption_key_values](../../system-catalog-views/sys-column-encryption-key-values-transact-sql.md) и [sys.column_encryption_keys](../../system-catalog-views/sys-column-encryption-keys-transact-sql.md).

```sql
SELECT cek.name AS [cek_name]
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
FROM sys.column_master_keys cmk
JOIN sys.column_encryption_key_values cekv
   ON cmk.column_master_key_id = cekv.column_master_key_id
JOIN sys.column_encryption_keys cek
   ON cekv.column_encryption_key_id = cek.column_encryption_key_id;
```

Если столбец зашифрован с помощью ключей с поддержкой анклава, он также поддерживает анклав. Чтобы определить, какие столбцы поддерживают анклав, используйте следующий запрос:

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
ON cmk.column_master_key_id = cekv.column_master_key_id;
```

## <a name="manage-collations"></a>Управление параметрами сортировки

Always Encrypted ограничивает параметры сортировки. Сортировка, отличная от BIN2, не допускается для символьных столбцов, зашифрованных с помощью детерминированного шифрования. Это ограничение также применяется к столбцам строк с поддержкой анклава.

Использование сортировок, которые не относятся к типу BIN2, разрешено для столбцов символьных строк, зашифрованных с помощью случайного шифрования и ключей шифрования столбцов с поддержкой анклава. Однако единственной новой функцией, которая включена для таких столбцов, является шифрование на месте. Чтобы использовать полнофункциональные вычисления (сопоставление шаблонов, операции сравнения), для зашифрованного столбца необходимо применить сортировку BIN2.

В таблице ниже приведены функциональные возможности для строковых столбцов с поддержкой анклава, в зависимости от типа шифрования и порядка сортировки.

| **Порядок сортировки** | **Детерминированное шифрование** | **Случайное шифрование**                 |
| ------------------------ | ---------------------------- | ----------------------------------------- |
| **Не BIN2**             | Не поддерживается                | Шифрование на месте                       |
| **BIN2**                 | Сравнение на равенство          | Шифрование на месте и полнофункциональные вычисления |

### <a name="determining-and-changing-collations"></a>Установка и изменение параметров сортировки

В SQL Server параметры сортировки могут быть установлены на уровне сервера, базы данных или столбца. Общие указания о том, как определить текущие параметры сортировки и изменить сортировку на уровне сервера, базы данных или столбца, см. в статье о [поддержке сортировки и Юникода](../../collations/collation-and-unicode-support.md).

### <a name="special-considerations-for-non-unicode-string-columns"></a>Особые замечания относительно строковых столбцов не в Юникоде

Следующее дополнительное ограничение, налагаемое в драйверах клиента SQL (не относящееся к Always Encrypted), применяется к столбцам строк не в Юникоде (ASCII). Если перезаписать параметры сортировки базы данных для строкового столбца не в Юникоде (char, varchar), необходимо убедиться, что параметры сортировки столбца используют ту же кодовую страницу, что и параметры сортировки базы данных.
Чтобы просмотреть все параметры сортировки вместе с идентификаторами кодовой страницы, используйте следующий запрос:

```sql
SELECT [Name]
   , [Description]
   , [CodePage] = COLLATIONPROPERTY([Name], 'CodePage')
FROM ::fn_helpcollations();
```

Например, `Chinese_Traditional_Stroke_Order_100_CI_AI_WS` и `Chinese_Traditional_Stroke_Order_100_BIN2` имеют одинаковую кодовую страницу (950), но `Chinese_Traditional_Stroke_Order_100_CI_AI_WS` и `Latin1_General_100_BIN2` используют разные кодовые страницы (950 и 1252, соответственно). Указанное выше ограничение не применяется к столбцам строк в Юникоде (`nchar`, `nvarchar`). Попробуйте задать тип данных "Юникод" для создаваемых зашифрованных столбцов или изменить тип на "Юникод" перед шифрованием существующего столбца.

## <a name="create-a-new-table-with-enclave-enabled-columns"></a>Создание новой таблицы со столбцами с поддержкой анклава

Можно создать новую таблицу с зашифрованными столбцами с помощью инструкции [CREATE TABLE (Transact-SQL)](../../../t-sql/statements/create-table-transact-sql.md). Always Encrypted с безопасными анклавами не изменяет синтаксис этой инструкции.

1. Используя SSMS, подключитесь к своей базе данных и откройте окно запроса.

     > [!NOTE]
     > Функция Always Encrypted не должна быть включена в строке подключения для этой задачи.

2. В окне запроса выполните инструкцию `CREATE TABLE`, чтобы создать новую таблицу, указав предложение `ENCRYPTED WITH` в [определении столбца](../../../t-sql/statements/alter-table-column-definition-transact-sql.md) для каждого столбца, который нужно зашифровать. Чтобы столбец поддерживал анклав, укажите ключ шифрования столбцов с поддержкой анклава. Вам также может потребоваться указать сортировку BIN2 для строковых столбцов, если она не является сортировкой по умолчанию для вашей базы данных. Дополнительные сведения см. в разделе настройки параметров сортировки.

### <a name="example-of-creating-a-new-table-with-enclave-enabled-columns"></a>Пример создания новой таблицы со столбцами с поддержкой анклава

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
    [Salary] [money] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY];
GO
```

## <a name="add-a-new-enclave-enabled-column-to-an-existing-table"></a>Добавление нового столбца с поддержкой анклава в существующую таблицу

Можно добавить новый зашифрованный столбец к существующей таблице с помощью инструкции [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) / ADD. Always Encrypted с безопасными анклавами не изменяет синтаксис этой инструкции.

1. Используя SSMS, подключитесь к своей базе данных и откройте окно запроса.

   Для этой задачи не обязательно, чтобы функция Always Encrypted была включена в строке подключения.

2. В окне запроса выполните инструкцию ALTER TABLE с предложением ADD, указав предложение ENCRYPTED WITH в [определении столбца](../../../t-sql/statements/alter-table-column-definition-transact-sql.md) и используя ключ шифрования столбцов с поддержкой анклава. Вам также может потребоваться указать сортировку BIN2 для строковых столбцов, если она не является сортировкой по умолчанию для вашей базы данных. Дополнительные сведения см. в разделе настройки параметров сортировки.

### <a name="example-of-adding-a-new-enclave-enabled-column-to-an-existing-table"></a>Пример добавления нового столбца с поддержкой анклава в существующую таблицу

Предполагая, что CEK1 является ключом шифрования столбцов с поддержкой анклава, приведенная ниже инструкция добавляет новый зашифрованный столбец с именем BirthDate, который поддерживает как полнофункциональные запросы, так и шифрование на месте (так как столбец использует случайное шифрование).

```sql
ALTER TABLE [dbo].[Employees]
ADD [BirthDate] [Date] ENCRYPTED WITH (
COLUMN_ENCRYPTION_KEY = [CEK1],
ENCRYPTION_TYPE = Randomized,
ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL;
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

### <a name="encrypt-an-existing-plaintext-column-in-place"></a>Шифрование на месте для существующего столбца с открытым текстом

Вы можете зашифровать существующий столбец с открытым текстом на месте с помощью инструкции [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) / ALTER COLUMN, если используется ключ шифрования столбцов с поддержкой анклава.

Чтобы зашифровать столбец с помощью ключа без поддержки анклава, следует использовать инструменты на стороне клиента, такие как мастер Always Encrypted в SSMS или командлет Set-SqlColumnEncryption в модуле SqlServer PowerShell. Подробная информация доступна в следующих статьях:

- [Мастер постоянного шифрования](always-encrypted-wizard.md)
- [Настройка шифрования столбцов с помощью PowerShell](configure-column-encryption-using-powershell.md)


#### <a name="prerequisites-for-encrypting-an-existing-plaintext-column-in-place"></a>Предварительные условия для шифрования на месте для существующего столбца с открытым текстом

- Существующий столбец не зашифрован.
- Вы подготовили ключи с поддержкой анклава.
- У вас есть доступ к главному ключу столбца.

#### <a name="steps-for-encrypting-existing-plaintext-column-in-place"></a>Процедура шифрования на месте для существующего столбца с открытым текстом

1. Подготовьте окно запроса SSMS с активированными вычислениями в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).
2. В окне запроса выполните инструкцию ALTER TABLE с предложением ALTER COLUMN, указав ключ шифрования столбцов с поддержкой анклава в предложении ENCRYPTED WITH. Если это строковый столбец (например, char, varchar, nchar, nvarchar), вам также может потребоваться изменить сортировку на BIN2. Дополнительные сведения см. в разделе настройки параметров сортировки.
    
    > [!NOTE]
    > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

3. Очистите кэш планов от всех пакетов и хранимых процедур, которые обращаются к таблице, чтобы обновить сведения о параметрах шифрования. 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > Если вы не удалите план затронутого запроса из кэша, первое выполнение запроса после шифрования может завершиться сбоем.

    > [!NOTE]
    > Внимательно используйте `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE` или `DBCC FREEPROCCACHE` для очистки кэша планов, так как эта операция может привести к временному ухудшению производительности запросов. Чтобы свести к минимуму негативное влияние очистки кэша, вы можете выборочно удалять планы только для затронутых запросов.

4.  Вызовите [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md), чтобы обновить метаданные параметров каждого модуля (хранимая процедура, функция, представление, триггер), которые сохранены в [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) и могут быть аннулированы в результате шифрования столбцов.

#### <a name="example-of-encrypting-existing-plaintext-column-in-place"></a>Пример шифрования на месте для существующего столбца с открытым текстом

В приведенном ниже примере предполагается:

- CEK1 — это ключ шифрования столбцов с поддержкой анклава.

- Столбец SSN содержит открытый текст и в настоящий момент использует Latin1 и параметры сортировки, отличные от BIN2 (например, Latin1Latin1\_General\_CI\_AI\_KS\_WS).

Инструкция шифрует столбец SSN, используя случайное шифрование и ключ шифрования столбцов с поддержкой анклава. Она также перезаписывает сортировку базы данных по умолчанию соответствующими (в той же кодовой странице) параметрами сортировки BIN2.

Операция выполняется в сети (ONLINE = ON). Также обратите внимание на вызов **ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE**, который восстанавливает планы запросов, затронутые изменением схемы таблицы.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

### <a name="make-an-existing-encrypted-column-enclave-enabled"></a>Добавление поддержки анклава в существующий зашифрованный столбец

У вас есть несколько способов включить функцию анклава для существующего столбца без поддержки анклава. Выбор метода зависит от нескольких факторов:

- **Область или степень детализации**. Вы хотите включить функцию анклава для подмножества столбцов или для всех столбцов, защищенных данным главным ключом столбцов?
- **Размер данных**. Каков размер таблиц, содержащих столбцы, для которых нужно реализовать поддержку анклава?
- Вы также хотите изменить тип шифрования для своих столбцов? Помните, что только случайное шифрование поддерживает полнофункциональные вычисления (сопоставление шаблонов, операторы сравнения). Если столбец зашифрован с использованием детерминированного шифрования, придется повторно зашифровать его с помощью случайного шифрования, чтобы разблокировать все функциональные возможности анклава.

Ниже приведены три способа реализации поддержки анклавов для существующих столбцов.

#### <a name="option-1-rotate-the-column-master-key-to-replace-it-with-an-enclave-enabled-column-master-key"></a>Вариант 1. Замените главный ключ столбца на главный ключ столбца с поддержкой анклава.
  
- Преимущества.
  - Не требуется повторное шифрование данных, то есть обычно это самый быстрый подход. Это рекомендуемый подход для столбцов, содержащих большие объемы данных, при условии, что все столбцы, для которых нужно включить полнофункциональные вычисления, уже используют детерминированное шифрование, и поэтому их не нужно шифровать повторно.
  - Этот подход позволяет включить функцию анклава для нескольких столбцов в масштабе, так как он реализует поддержку анклава для всех ключей шифрования столбцов и всех зашифрованных столбцов, связанных с исходным главным ключом столбца.
  
- Недостатки.
  - Не поддерживает изменение типа шифрования с детерминированного на случайное, поэтому, хотя этот способ разблокирует шифрование на месте для столбцов, зашифрованных детерминированным образом, он не позволяет использовать полнофункциональные вычисления.
  - Не позволяет выборочно преобразовывать некоторые из столбцов, связанных с данным главным ключом столбца.
  - Вводит накладные расходы на управление ключами — необходимо создать новый главный ключ столбца и сделать его доступным для приложений, которые запрашивают затрагиваемые столбцы.  

#### <a name="option-2-this-approach-involves-two-steps-1-rotating-the-column-master-key-as-in-option-1-and-2-re-encrypting-a-subset-of-deterministically-encrypted-columns-using-randomized-encryption-to-enable-rich-computations-for-those-columns"></a>Вариант 2. Этот подход включает в себя два шага: 1) замену главного ключа столбца (как в варианте 1) и 2) повторное шифрование подмножества детерминировано зашифрованных столбцов с использованием случайного шифрования, чтобы обеспечить полнофункциональные вычисления для этих столбцов.
  
- Преимущества.
  - Повторно шифрует данные на месте, поэтому рекомендуется использовать полнофункциональные запросы для детерминировано зашифрованных столбцов, содержащих большие объемы данных. Шаг 1 разблокирует шифрование на месте для столбцов, использующих детерминированное шифрование, поэтому шаг 2 можно выполнить на месте.
  - Позволяет включить функциональность анклава для нескольких столбцов в масштабе.
  
- Недостатки.
  - Не позволяет выборочно преобразовывать некоторые из столбцов, связанных с данным главным ключом столбца.
  - Вводит накладные расходы на управление ключами — необходимо создать новый главный ключ столбца и сделать его доступным для приложений, которые запрашивают затрагиваемые столбцы.

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

Always Encrypted с использованием анклавов добавляет новое назначение для рабочего процесса замены основных ключей столбцов. Если старый главный ключ столбца не поддерживает анклав, а новый главный ключ столбца поддерживает, процесс замены эффективно реализует поддержку анклава для всех ключей шифрования столбцов, связанных с главным ключом столбца. При смене главного ключа столбца не выполняется повторное шифрование данных, поэтому мы рекомендуем использовать именно этот процесс для включения анклава для существующих столбцов.

При смене главного ключа столбца не изменяется тип шифрования затрагиваемых столбцов. Таким образом, этот процесс может разблокировать только шифрование на месте для столбцов, зашифрованных детерминировано. Чтобы разблокировать полнофункциональные вычисления для столбцов, использующих детерминированное шифрование, необходимо повторно зашифровать их (на месте) после смены главного ключа столбца.

Вам также может понадобиться изменить параметры сортировки для строковых столбцов, использующих случайное шифрование, на параметры сортировки BIN2, чтобы разблокировать полнофункциональные вычисления. Дополнительные сведения см. в разделе настройки параметров сортировки.

Процесс смены главного ключа столбца одинаков, независимо от того, поддерживает ли этот ключ анклав. Сведения о том, как сменить главный ключ столбца, приведены по следующим ссылкам:

- [Смена главного ключа столбца с помощью SSMS](configure-always-encrypted-using-sql-server-management-studio.md)
- [Смена главного ключа столбца с помощью PowerShell](rotate-always-encrypted-keys-using-powershell.md)

Для удобства ниже приведен пример скрипта PowerShell для смены главного ключа столбца.

#### <a name="prerequisites-of-rotating-the-column-master-key-for-enclave-enabled-columns"></a>Предварительные условия для смены главного ключа столбцов, поддерживающих анклав

- Вы подготовили новый главный ключ столбца с поддержкой анклава.
- У вас есть доступ к старому и новому главному ключу столбца.
- Все строковые столбцы, защищенные старым главным ключом столбца, используют параметры сортировки BIN2.

> [!NOTE]
> Кроме того, можно изменить параметры сортировки строковых столбцов после смены главного ключа столбца.

#### <a name="steps-for-rotating-the-column-master-key-for-enclave-enabled-columns"></a>Процедура смены главного ключа столбцов, поддерживающих анклав

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

#### <a name="prerequisites-for-re-encrypting-columns-in-place"></a>Предварительные условия для повторного шифрования столбцов на месте

- Столбец шифруется с помощью ключа шифрования с поддержкой анклава.
- Вы подготовили новый ключ шифрования столбцов с поддержкой анклава (если ваша цель заключается в замене текущего ключа шифрования столбцов с поддержкой анклава, защищающего столбец).
- У вас есть доступ к главному ключу столбца.

#### <a name="steps-for-re-encrypting-columns-in-place"></a>Процедура повторного шифрования столбцов на месте

1. Подготовьте окно запроса SSMS с поддержкой вычислений в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. В окне запроса выполните инструкцию [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) с предложением ALTER COLUMN, указав следующее в предложении ENCRYPTED WITH:
    
    1. Имя нового ключа шифрования столбцов с поддержкой анклава при смене текущего ключа. Если ключ шифрования столбцов не изменяется, необходимо указать имя текущего ключа.
    
    2. Новый тип шифрования, если он изменяется. Если тип шифрования не изменяется, необходимо указать текущий тип шифрования.
        
       Если столбец, который повторно шифруется, использует параметры сортировки (BIN2), отличающиеся от параметров сортировки базы данных по умолчанию, необходимо включить фразу COLLATE и указать текущие параметры сортировки столбцов в определении столбца (чтобы сохранить параметры сортировки одинаковыми).
        
       > [!NOTE]
       > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

3. Очистите кэш планов от всех пакетов и хранимых процедур, которые обращаются к таблице, чтобы обновить сведения о параметрах шифрования. 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > Если вы не удалите план затронутого запроса из кэша, первое выполнение запроса после шифрования может завершиться сбоем.

    > [!NOTE]
    > Внимательно используйте ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE или DBCC FREEPROCCACHE для очистки кэша планов, так как это может привести к временному ухудшению производительности запросов. Чтобы свести к минимуму негативное влияние очистки кэша, вы можете выборочно удалять планы только для затронутых запросов.

4.  Вызовите [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md), чтобы обновить метаданные параметров каждого модуля (хранимая процедура, функция, представление, триггер), которые сохранены в [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) и могут быть аннулированы в результате повторного шифрования столбцов.

#### <a name="examples-of-re-encrypting-columns-in-place"></a>Примеры повторного шифрования столбцов на месте

Предполагая, что столбец SSN в настоящее время шифруется с помощью ключа шифрования с поддержкой анклава с именем CEK1 и детерминированного шифрования, а текущие параметры сортировки, установленные на уровне столбца, имеют тип Latin1\_General\_BIN2, приведенная ниже инструкция повторно шифрует столбец с помощью случайного шифрования и того же ключа.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

Если столбец SSN в настоящее время шифруется с помощью ключа шифрования с поддержкой анклава с именем CEK1 и детерминированного шифрования, а параметры сортировки базы данных по умолчанию являются параметрами сортировки BIN2 (и не заданы на уровне столбца), приведенная ниже инструкция повторно шифрует столбец с помощью нового ключа с поддержкой анклава с именем CEK2 (без изменения типа шифрования).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION\_TYPE = Deterministic
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

Если столбец SSN в настоящее время шифруется с помощью ключа шифрования с поддержкой анклава с именем CEK1 и детерминированного шифрования, а параметры сортировки базы данных по умолчанию являются параметрами сортировки BIN2 (и не заданы на уровне столбца), приведенная ниже инструкция повторно шифрует столбец с помощью нового ключа с поддержкой анклава и случайного шифрования. Кроме того, операция выполняется в оперативном режиме.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL 
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

### <a name="re-encrypt-columns-on-the-client-side"></a>Повторное шифрование столбцов на стороне клиента

Устаревший метод для повторного шифрования (шифрования или расшифровки) столбцов использует средства на стороне клиента, такие как мастер Always Encrypted или PowerShell. Как правило, использование этого метода не рекомендуется, за исключением случаев, когда таблица, содержащая столбцы (которые повторно шифруются), небольшая и если вашей целью является объединение повторного шифрования столбца с новым ключом с поддержкой анклава и изменения типа шифрования (с детерминированного на случайное).

Если при повторном шифровании столбца используется случайное шифрование, возможно, потребуется изменить параметры сортировки на BIN2 (до или после повторного шифрования), чтобы разблокировать полнофункциональные вычисления. Дополнительные сведения см. в разделе настройки параметров сортировки.

Подробная информация доступна в следующих статьях:

  - Смена ключей шифрования столбцов с использованием SSMS: <https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-wizard>
  - Смена ключей шифрования столбцов с использованием PowerShell: <https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-column-encryption-using-powershell>

### <a name="decrypt-a-column-in-place"></a>Расшифровка столбца на месте

Если столбец зашифрован с помощью ключа шифрования столбцов с поддержкой анклава, его можно расшифровать (преобразовать в столбец с открытым текстом) на месте с помощью инструкции ALTER TABLE. Кроме того, операция выполняется в оперативном режиме.

#### <a name="prerequisites-for-decrypting-a-column-in-place"></a>Предварительные условия для расшифровки столбца на месте

- Столбец шифруется с помощью ключа шифрования с поддержкой анклава.
- У вас есть доступ к главному ключу столбца.

#### <a name="steps-for-decrypting-a-column-in-place"></a>Процедура расшифровки столбца на месте

1. Подготовьте окно запроса SSMS с поддержкой вычислений в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. В окне запроса выполните инструкцию [ALTER TABLE (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) с предложением ALTER COLUMN, указав нужную конфигурацию столбца **без** предложения ENCRYPTED WITH:
    
    > [!NOTE]
    > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

3. Очистите кэш планов от всех пакетов и хранимых процедур, которые обращаются к таблице, чтобы обновить сведения о параметрах шифрования. 

    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```

    > [!NOTE]
    > Если вы не удалите план затронутого запроса из кэша, первое выполнение запроса после шифрования может завершиться сбоем.

    > [!NOTE]
    > Внимательно используйте ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE или DBCC FREEPROCCACHE для очистки кэша планов, так как это может привести к временному ухудшению производительности запросов. Чтобы свести к минимуму негативное влияние очистки кэша, вы можете выборочно удалять планы только для затронутых запросов.

4. Вызовите [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md), чтобы обновить метаданные параметров каждого модуля (хранимая процедура, функция, представление, триггер), которые сохранены в [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) и могут быть аннулированы в результате шифрования столбцов.

#### <a name="example-for-decrypting-a-column-in-place"></a>Пример расшифровки столбца на месте

Предполагая, что столбец SSN зашифрован и текущие параметры сортировки на уровне столбца имеют тип Latin1\_General\_BIN2, приведенная ниже инструкция расшифровывает столбец (и не изменяет параметры сортировки). Кроме того, можно изменить параметры сортировки, например на отличные от BIN2 в той же инструкции.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

## <a name="issue-rich-queries-against-encrypted-columns-using-ssms"></a>Отправка полнофункциональных запросов к зашифрованным столбцам с помощью SSMS

Самый быстрый способ попробовать полнофункциональные запросы к столбцам с поддержкой анклава — отправить их из окна запроса SSMS с включенным определением параметров для Always Encrypted. Дополнительные сведения об этой полезной возможности в SSMS см. в следующих ресурсах:

- [Определение параметров для Always Encrypted — использование SSMS для вставки, обновления и фильтрации зашифрованных столбцов](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)
- [Запрос зашифрованных столбцов](configure-always-encrypted-using-sql-server-management-studio.md#querying-encrypted-columns)

### <a name="prerequisites-for-issuing-rich-queries-against-encrypted-columns-using-ssms"></a>Предварительные условия для отправки полнофункциональных запросов к зашифрованным столбцам с помощью SSMS

- Столбцы с поддержкой анклава для выполнения запроса.
- У вас есть доступ к главному ключу столбца (или ключам).

### <a name="steps-for-issuing-rich-queries-against-encrypted-columns-using-ssms"></a>Процедура отправки полнофункциональных запросов к зашифрованным столбцам с помощью SSMS

1. Подготовьте окно запроса SSMS с поддержкой вычислений в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Подготовка окна запросов SSMS при включенной функции Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. Включите определение параметров для Always Encrypted.

    1. В главном меню SSMS выберите **Запрос**.
    2. Щелкните **Параметры запроса...** .
    3. Выберите **Выполнение** > **Дополнительно**.
    4. Установите или снимите флажок "Enable Parameterization for Always Encrypted" (Включить параметризацию для Always Encrypted).
    5. Нажмите кнопку «ОК».

3. Создайте и выполните запросы с использованием полнофункциональных вычислений для зашифрованных столбцов. Необходимо объявить переменную Transact-SQL для каждого значения, предназначенного для зашифрованного столбца в запросе. Переменные должны использовать встроенные инициализации (не могут быть заданы через инструкцию SET).

    > [!NOTE]
    > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

### <a name="example-of-rich-queries-against-encrypted-columns"></a>Примеры полнофункциональных запросов к зашифрованным столбцам

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
    [Salary] [money] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY];
GO
```

CEK1 — это ключ шифрования столбцов с поддержкой анклава.

Вот пример запроса к таблице, который соответствует рекомендациям для параметризации:

```sql
DECLARE @SSNPattern [char](11) = '%1111%'
DECLARE @MinSalary [money] = 1000
SELECT *
FROM [dbo].[Employees]
WHERE SSN LIKE @SSNPattern
    AND [Salary] >= @MinSalary;
GO;
```

## <a name="create-and-use-indexes-on-enclave-enabled-columns-using-randomized-encryption"></a>Создание и использование индексов в столбцах с поддержкой анклава с помощью случайного шифрования

Поскольку индекс столбца с поддержкой анклава с использованием случайного шифрования сохраняет зашифрованное значение ключа индекса, а сортировка выполняется по значениям в открытом тексте, ядро SQL Server вынуждено использовать анклав для любых операций, подразумевающих создание или обновление индекса, в том числе:

- создание или перестроение индекса;
- вставка, обновление или удаление строки в таблице (содержащей индексированный и зашифрованный столбец), которое активирует вставку ключа в индекс и (или) удаление ключа из индекса;
- выполнение команд DBCC, которые подразумевают проверку целостности индексов, например [DBCC CHECKDB (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) или [DBCC CHECKTABLE (Transact-SQL)](../../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md);
- восстановление базы данных (например, после сбоя и перезапуска SQL Server), если оно включает отмену любых операций с индексом (см. более подробное описание ниже).

Все указанные выше операции требуют, чтобы в анклаве существовал ключ шифрования столбца для индексированного столбца, который позволит расшифровать ключи индекса. Обычно анклав может получить ключ шифрования столбца одним из двух способов:
- напрямую из клиентского приложения;
- из кэша ключей шифрования столбцов.

### <a name="invoke-indexing-operations-with-column-encryption-keys-provided-directly-by-the-client"></a>Вызов операций индексирования с ключами шифрования столбцов, полученными напрямую от клиента

Чтобы операции индексирования работали в такой конфигурации, выполняющее соответствующий запрос приложение должно сделать следующее.

- Подключиться к базе данных с поддержкой Always Encrypted и анклавных вычислений.
- Приложение должно иметь доступ к главному ключу столбца, который защищает ключ шифрования столбца для индексированного столбца.

Как только ядро SQL Server выполнит синтаксический анализ запроса и определит, что для его выполнения потребуется обновить индекс для зашифрованного столбца, оно затребует от драйвера клиента необходимый CEK от анклава по защищенному каналу. Обратите внимание, что это именно этот механизм используется для передачи в анклав ключей шифрования столбца, необходимых для обработки запросов без операций индексирования.

Этот метод полезен тем, что позволяет сделать индексы по зашифрованным столбцам незаметными для приложений, которые уже подключены к базе данных с поддержкой Always Encrypted и анклавных вычислений, а также использовать анклав для обработки запросов. После того, как вы создадите индекс по столбцу, драйвер внутри приложения будет прозрачно предоставлять ключи шифрования столбцов в анклав для операций индексирования. Обратите внимание на то, что создание индексов может увеличить количество запросов, для которых приложению придется отправлять в анклав ключи шифрования столбцов.

Пошаговые инструкции по использованию этого метода см. в статье [Tutorial: Creating and using indexes on enclave-enabled columns using randomized encryption](../tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md) (Руководство. Создание и использование индексов в столбцах с поддержкой анклава с помощью случайного шифрования).

### <a name="invoke-indexing-operations-using-cached-column-encryption-keys"></a>Вызов операций индексирования с использованием кэшированных ключей шифрования столбцов

Когда клиентское приложение отправляет ключ шифрования столбца в анклав (для обработки запроса, который требует анклавных вычислений), этот анклав кэширует ключ шифрования столбца во внутреннем кэше (он расположен внутри анклава и не доступен снаружи).

Теперь, если то же или другое клиентское приложение (от имени того же или другого пользователя) запустит операцию с индексом без прямого предоставления шифрования столбца, анклав попробует найти в кэше ключ шифрования этого столбца. Это означает, что операция с индексом будет выполнена успешно даже без получения ключа от клиентского приложения.

Чтобы этот метод вызова операций индексирования работал нормально, приложение должно подключаться к базе данных без поддержки Always Encrypted, а соответствующий ключ шифрования столбца должен быть доступен во внутреннем кэше анклава.

Этот метод вызова операций поддерживается только для тех запросов, которые не требуют ключей шифрования столбцов для других операций, не связанных с индексами. Например, вставка новой строки с помощью инструкции INSERT в таблицу, которая содержит зашифрованный столбец, потребует подключения к базе данных с активацией поддержки Always Encrypted в строке подключения, а также доступа к ключам, независимо от наличия индекса для зашифрованного столбца.

Этот метод полезен в следующих случаях.

- Когда нужно сделать так, чтобы наличие индексов для столбцов с поддержкой анклава и случайным шифрованием было незаметным для приложений и пользователей, у которых нет доступа к ключам и данным в формате открытого текста. Так вы сможете гарантировать, что создание индекса для зашифрованного столбца не нарушит работу существующих запросов. То есть при выполнении запроса из приложения без доступа к ключам в таблице, содержащей зашифрованные столбцы, работа этого приложения будет успешно продолжаться и не потребуется предоставлять ему ключи после того, как администратор базы данных создаст индекс. В качестве примера рассмотрим приложение, которое выполняет представленный ниже запрос к таблице **Employees** из предыдущего примера, пока администратор базы данных еще не создал индекс для зашифрованного столбца. 

   ```sql
   DELETE FROM [dbo].[Employees] WHERE [EmployeeID] = 1;
   GO
   ```

   Если приложение отправляет запрос через подключение без поддержки Always Encrypted и анклавных вычислений, запрос завершится успешно, так как он не требует вычислений по зашифрованным столбцам. После того, как администратор базы данных создаст индекс по зашифрованным столбцам, этот запрос будет требовать удаления ключей индекса из индексов, а для этой операции анклаву требуются ключи шифрования столбцов. Но даже при этом приложение будет успешно выполнять запрос через прежнее подключение, если владелец данных предоставил в анклав ключи шифрования столбцов.

- Разделение ролей для управления индексами позволяет администраторам баз данных создавать и изменять индексы по зашифрованным столбцам, не получая доступа к конфиденциальным данным. 

Пошаговые инструкции по использованию этого метода см. в статье [Tutorial: Creating and using indexes on enclave-enabled columns using randomized encryption](../tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md) (Руководство. Создание и использование индексов в столбцах с поддержкой анклава с помощью случайного шифрования).

## <a name="develop-applications-issuing-rich-queries-in-visual-studio"></a>Разработка приложений, которые отправляют полнофункциональные запросы, в Visual Studio

### <a name="set-up-your-visual-studio-project"></a>Настройка проекта в Visual Studio

Чтобы использовать функцию Always Encrypted с безопасными анклавами в приложении .NET Framework, вам нужно убедиться в том, что приложение создано на основе .NET Framework 4.7.2 и интегрировано с [пакетом NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders). Кроме того, если вы храните главный ключ столбца в Azure Key Vault, необходимо также интегрировать приложение с [пакетом NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) версии 2.2.0 или более поздней. 

1. Запустите Visual Studio.
2. Создайте новый проект Visual C\# или откройте существующий.
3. Убедитесь, что в проекте настроена по крайней мере платформа .NET Framework 4.7.2. Щелкните правой кнопкой мыши проект в обозревателе решений, выберите "Свойства" и установите целевую платформу. NET Framework 4.7.2.

4. Установите следующий пакет NuGet. Щелкните **Инструменты** (главное меню) > **Диспетчер пакетов NuGet** > **Консоль диспетчера пакетов**. Выполните следующий код в консоли диспетчера пакетов.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders -IncludePrerelease
   ```

5. Если вы используете Azure Key Vault для хранения главных ключей столбцов, установите следующие пакеты NuGet, щелкнув **Инструменты** (главное меню) > **Диспетчер пакетов NuGet** > **Консоль диспетчера пакетов**. Выполните следующий код в консоли диспетчера пакетов.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider -IncludePrerelease -Version 2.2.0
   Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
   ```

6. Выберите проект и нажмите кнопку "Установить".
7. Откройте файл конфигурации из проекта (например, App.config или Web.config).
8. В разделе \<configuration\> добавьте или обновите разделы \<configSections\>.

   A. Если в разделе \<configuration\> **нет** раздела \<configSections\>, добавьте приведенное ниже содержимое сразу после раздела \<configuration\>.
   
      ```xml
      <configSections>
         <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
      </configSections>
      ```
   Б. Если в разделе \<configuration\> уже есть раздел \<configSections\>, добавьте следующую строку в раздел \<configSections\>:

   ```xml
   <section name="SqlColumnEncryptionEnclaveProviders"  type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data,  Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
   ```

9. В разделе конфигурации под \<configSections\> добавьте следующий раздел, где указан поставщик анклава, который будет использоваться для подтверждения и взаимодействия с анклавами VBS:

   ```xml
   <SqlColumnEncryptionEnclaveProviders>
       <providers>
           <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.VirtualizationBasedSecurityEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
       </providers>
   </SqlColumnEncryptionEnclaveProviders>
   ```

Ниже представлен полный пример файла app.config для простого консольного приложения.
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
  </configSections>
  <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.2" />
    </startup>

  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="VBS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider, Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders, Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders>
</configuration>
```
### <a name="develop-and-test-your-app"></a>Разработка и тестирование приложения

Чтобы использовать Always Encrypted и вычисления в анклаве, приложение должно подключаться к базе данных с помощью следующих двух ключевых слов в строке подключения: `Column Encryption Setting = Enabled; Enclave Attestation Url=https://x.x.x.x/Attestation` (где xxxx может быть IP-адресом, доменом и т. д).

Кроме того, приложение должно соответствовать общим рекомендациям, применяемых к приложениям, использующим Always Encrypted. Например, приложение должно иметь доступ к главным ключам столбцов, связанным со столбцами базы данных, на которые ссылаются запросы приложения.

Дополнительные сведения о разработке приложений .NET Framework с использованием Always Encrypted см. в следующих статьях:

- [Разработка с использованием постоянного шифрования с поставщиком данных .NET Framework](develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Always Encrypted: защита конфиденциальных данных в Базе данных SQL и хранение ключей шифрования в Azure Key Vault](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

#### <a name="example-of-simple-application"></a>Пример простого приложения

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
    [Salary] [money] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY];
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

   string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = https://10.193.16.185/Attestation/attestationservice.svc/signingCertificates; Integrated Security = true";

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
   MinSalary.DbType = DbType.Currency;
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
