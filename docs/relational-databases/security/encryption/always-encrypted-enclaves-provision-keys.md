---
description: Подготовка ключей с поддержкой анклава
title: Подготовка ключей с поддержкой анклава | Документация Майкрософт
ms.custom: ''
ms.date: 10/01/2019
ms.prod: sql
ms.reviewer: vanto
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 77a438ee4f495429bbe0eb9c1e98728ecb324009
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91867666"
---
# <a name="provision-enclave-enabled-keys"></a>Подготовка ключей с поддержкой анклава
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

В этой статье описывается подготовка ключей с поддержкой анклава, которые поддерживают вычисления в безопасных анклавах на стороне сервера, используемых для [Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md). 

При подготовке ключей с поддержкой анклава применяются общие рекомендации и процессы для [управления ключами Always Encrypted](overview-of-key-management-for-always-encrypted.md). В этой статье приводятся конкретные сведения, касающиеся Always Encrypted с безопасными анклавами.

Для подготовки главного ключа столбца с поддержкой анклава с помощью SQL Server Management Studio или PowerShell требуется, чтобы новый ключ поддерживал вычисления анклава. В этом случае средство (SSMS или PowerShell) создаст инструкцию `CREATE COLUMN MASTER KEY`, которая задает `ENCLAVE_COMPUTATIONS` в метаданных главного ключа столбцов в базе данных. Дополнительные сведения см. в статье [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md). 

Это средство добавит в свойства главного ключа цифровую подпись, которая выполняется с использованием главного ключа столбца и будет храниться в метаданных базы данных. Эта подпись предотвращает вредоносное изменение параметра `ENCLAVE_COMPUTATIONS`. Драйверы клиента SQL проверяют подписи, прежде чем разрешить использование анклава. Это позволяет администраторам безопасности контролировать, какие данные столбцов могут быть вычислены внутри анклава.

Свойство `ENCLAVE_COMPUTATIONS` является неизменяемым — вы не сможете изменить его после определения главного ключа столбца в метаданных. Чтобы включить вычисления анклава с помощью ключа шифрования столбца, который шифруется данным главным ключом столбца, необходимо заменить главный ключ столбца на главный ключ столбца с поддержкой анклава. См. статью [Смена ключей с поддержкой анклава](always-encrypted-enclaves-rotate-keys.md).

> [!NOTE]
> В настоящее время SSMS и PowerShell поддерживают главные ключи столбцов с поддержкой анклава, хранящиеся в Azure Key Vault или хранилище сертификатов Windows. Аппаратные модули безопасности (использующие CNG или CAPI) не поддерживаются.

Чтобы создать ключ шифрования столбца с поддержкой анклава, для шифрования нового ключа нужно выбрать главный ключ столбца с поддержкой анклава. 

В следующих разделах содержатся более подробные сведения о подготовке ключей с поддержкой анклава с помощью SSMS и PowerShell.

## <a name="provision-enclave-enabled-keys-using-sql-server-management-studio"></a>Подготовка ключей с поддержкой анклава с помощью SQL Server Management Studio
В SQL Server Management Studio 18.3 или более поздних версий можно подготовить следующие ключи.
- Главный ключ столбца с поддержкой анклава — в диалоговом окне **Новый главный ключ столбца**.
- Ключ шифрования столбца с поддержкой анклава — в диалоговом окне **Новый ключ шифрования столбца**.

> [!NOTE]
> В настоящее время [мастер Always Encrypted](always-encrypted-wizard.md) не поддерживает создание ключей с поддержкой анклава. Однако сначала можно создать ключи с поддержкой анклава, используя приведенные выше диалоговые окна, а затем во время работы мастера выбрать уже существующее шифрование столбца с поддержкой анклава для столбцов, которые требуется зашифровать.

### <a name="provision-enclave-enabled-column-master-keys-with-the-new-column-master-key-dialog"></a>Подготовка главных ключей столбцов с поддержкой анклава с помощью диалогового окна "Новый главный ключ столбца"
Чтобы подготовить главный ключ столбца с поддержкой анклава, выполните действия, описанные в разделе [Подготовка главных ключей столбцов с помощью диалогового окна "Новый главный ключ столбца"](configure-always-encrypted-keys-using-ssms.md#provision-column-master-keys-with-the-new-column-master-key-dialog). Установите флажок **Разрешить вычисления анклава**. См. снимок экрана ниже.

![Разрешение вычислений анклава](./media/always-encrypted-enclaves/allow-enclave-computations.png)

> [!NOTE]
> Флажок **Разрешить вычисления анклава** отображается только в том случае, если экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] содержит правильно инициализированный безопасный анклав. Дополнительные сведения см. в статье [Настройка типа анклава для Always Encrypted](../../../database-engine/configure-windows/configure-column-encryption-enclave-type.md).

> [!TIP]
> Чтобы проверить, поддерживает ли главный ключ столбца анклав, щелкните его правой кнопкой мыши в обозревателе объектов и выберите пункт **Свойства**. Если ключ поддерживает анклав, в окне свойств ключа отображается **Вычисления анклава: разрешены**. Или можно использовать представление [sys.column_master_keys (Transact-SQL)](../../system-catalog-views/sys-column-master-keys-transact-sql.md).

### <a name="provision-enclave-enabled-column-encryption-keys-with-the-new-column-encryption-key-dialog"></a>Подготовка ключей шифрования столбцов с поддержкой анклава с помощью диалогового окна "Новый ключ шифрования столбца"
Чтобы подготовить ключ шифрования столбца с поддержкой анклава, выполните действия, описанные в разделе [Подготовка ключей шифрования столбцов с помощью диалогового окна "Новый ключ шифрования столбца"](configure-always-encrypted-keys-using-ssms.md#provision-column-encryption-keys-with-the-new-column-encryption-key-dialog). При выборе главного ключа столбца убедитесь, что он поддерживает анклав.

> [!TIP]
> Чтобы проверить, поддерживает ли ключ шифрования столбца анклав, щелкните его правой кнопкой мыши в обозревателе объектов и выберите пункт **Свойства**. Если ключ поддерживает анклав, в окне свойств ключа отображается **Вычисления анклава: разрешены**.

## <a name="provision-enclave-enabled-keys-using-powershell"></a>Подготовка ключей с поддержкой анклава с помощью PowerShell
Для подготовки ключей с поддержкой анклава с помощью PowerShell требуется модуль SqlServer PowerShell версии 21.1.18179 или более поздней.

Как правило, в подготовке ключей с поддержкой анклава задействованы рабочие процессы подготовки ключей PowerShell (с разделением и без разделения ролей) для Always Encrypted, описанные в статье [Подготовка ключей Always Encrypted с помощью PowerShell](configure-always-encrypted-keys-using-powershell.md). В этом разделе приводятся конкретные сведения, касающиеся ключей с поддержкой анклава.

Модуль SqlServer PowerShell расширяет функциональность командлетов [**New-SqlCertificateStoreColumnMasterKeySettings**](/powershell/module/sqlserver/new-sqlcertificatestorecolumnmasterkeysettings) и [**New-SqlAzureKeyVaultColumnMasterKeySettings**](/powershell/module/sqlserver/new-sqlazurekeyvaultcolumnmasterkeysettings) за счет параметра `-AllowEnclaveComputations`, позволяющего указывать главный ключ столбца с поддержкой анклава в ходе процесса подготовки. Каждый командлет создает локальный объект, содержащий свойства главного ключа столбца (хранящегося в Azure Key Vault или в хранилище сертификатов Windows). Если указано, свойство `-AllowEnclaveComputations` помечает ключ как поддерживающий анклав в локальном объекте. Кроме того, командлет обращается к указанному главному ключу столбца (в Azure Key Vault или хранилище сертификатов Windows) для добавления цифровой подписи к свойствам ключа. Созданный объект параметров для нового главного ключа столбца с поддержкой анклава можно использовать в последующем вызове командлета [**New-SqlColumnMasterKey**](/powershell/module/sqlserver/new-sqlcolumnmasterkey) для создания объекта метаданных, описывающего новый ключ в базе данных.

Подготовка ключей шифрования столбцов с поддержкой анклава не отличается от подготовки ключей шифрования столбцов без поддержки анклава. Просто необходимо убедиться, что главный ключ столбца, используемый для шифрования нового ключа шифрования столбца, поддерживает анклав.

> [!NOTE]
> Сейчас модуль SqlServer PowerShell не поддерживает подготовку ключей с поддержкой анклава, хранящихся в аппаратных модулях безопасности (использующих CNG или CAPI).

### <a name="example---provision-enclave-enabled-keys-using-windows-certificate-store"></a>Пример: подготовка ключей с поддержкой анклава с помощью хранилище сертификатов Windows
В приведенном ниже законченном примере демонстрируется подготовка ключей с поддержкой анклава с сохранением главного ключа столбца, хранящегося в хранилище сертификатов Windows. В основе сценария лежит пример из раздела [Хранилище сертификатов Windows без разделения ролей (пример)](configure-always-encrypted-keys-using-powershell.md#windows-certificate-store-without-role-separation-example). Обратите внимание на использование параметра `-AllowEnclaveComputations` в командлете [**New-SqlCertificateStoreColumnMasterKeySettings**](/powershell/module/sqlserver/new-sqlcertificatestorecolumnmasterkeysettings) — это единственное различие между рабочими процессами в двух примерах.

```powershell
# Create a column master key in Windows Certificate Store.
$cert = New-SelfSignedCertificate -Subject "AlwaysEncryptedCert" -CertStoreLocation Cert:CurrentUser\My -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage DataEncipherment -KeySpec KeyExchange

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
# Change the authentication method in the connection string, if needed.
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$database = Get-SqlDatabase -ConnectionString $connStr

# Create a SqlColumnMasterKeySettings object for your column master key
# using the -AllowEnclaveComputations parameter.
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert.Thumbprint -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "CMK1"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database. 
$cekName = "CEK1"
New-SqlColumnEncryptionKey -Name $cekName  -InputObject $database -ColumnMasterKey $cmkName
```

### <a name="example---provision-enclave-enabled-keys-using-azure-key-vault"></a>Пример: подготовка ключей с поддержкой анклава с помощью Azure Key Vault
В приведенном ниже законченном примере демонстрируется подготовка ключей с поддержкой анклава с сохранением главного ключа столбца в Azure Key Vault. В основе сценария лежит пример из раздела [Azure Key Vault без разделения ролей (пример)](configure-always-encrypted-keys-using-powershell.md#azure-key-vault-without-role-separation-example). Важно отметить два различия между рабочим процессом для ключей с поддержкой анклава и процессом для ключей без поддержки анклава. 
- В приведенном ниже сценарии командлет [**New-SqlCertificateStoreColumnMasterKeySettings**](/powershell/module/sqlserver/new-sqlcertificatestorecolumnmasterkeysettings) использует параметр `-AllowEnclaveComputations` для создания главного ключа столбца с поддержкой анклава. 
- Сценарий вызывает командлет [**Add-SqlAzureAuthenticationContext**](/powershell/module/sqlserver/add-sqlazureauthenticationcontext) для входа в Azure перед вызовом командлета [**New-SqlAzureKeyVaultColumnMasterKeySettings**](/powershell/module/sqlserver/new-sqlazurekeyvaultcolumnmasterkeysettings). Вход в Azure необходим, поскольку с заданным параметром `-AllowEnclaveComputations` командлет **New-SqlAzureKeyVaultColumnMasterKeySettings** вызывает Azure Key Vault для подписывания свойств главного ключа столбца.

```powershell
# Create a column master key in Azure Key Vault.
Import-Module Az
Connect-AzAccount
$SubscriptionId = "<Azure SubscriptionId>"
$resourceGroup = "<resource group name>"
$azureLocation = "<datacenter location>"
$akvName = "<key vault name>"
$akvKeyName = "<key name>"
$azureCtx = Set-AzConteXt -SubscriptionId $SubscriptionId # Sets the context for the below cmdlets to the specified subscription.
New-AzResourceGroup -Name $resourceGroup -Location $azureLocation # Creates a new resource group - skip, if your desired group already exists.
New-AzKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation # Creates a new key vault - skip if your vault already exists.
Set-AzKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, delete, list, wrapKey,unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account
$akvKey = Add-AzureKeyVaultKey -VaultName $akvName -Name $akvKeyName -Destination "Software"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
# Change the authentication method in the connection string, if needed.
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$database = Get-SqlDatabase -ConnectionString $connStr

# Authenticate to Azure - it is required before calling the next cmdlet.
Add-SqlAzureAuthenticationContext -Interactive

# Create a SqlColumnMasterKeySettings object for your column master key. 
$cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyURL $akvKey.ID -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "CMK1"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database. 
$cekName = "CEK1"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```

## <a name="next-steps"></a>Next Steps
- [Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-query-columns.md)
- [Настройка шифрования столбцов на месте с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-configure-encryption.md)
- [Включение Always Encrypted с безопасными анклавами для существующих зашифрованных столбцов](always-encrypted-enclaves-enable-for-encrypted-columns.md)
- [Разработка приложений с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-client-development.md) 

## <a name="see-also"></a>См. также:  
- [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)
- [Управление ключами для Always Encrypted с безопасными анклавами](always-encrypted-enclaves-manage-keys.md)
- [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md)