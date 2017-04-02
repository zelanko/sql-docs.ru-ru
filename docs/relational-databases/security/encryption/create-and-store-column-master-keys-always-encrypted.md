---
title: "Создание и хранение главных ключей столбцов (постоянное шифрование) | Microsoft Docs"
ms.custom: ""
ms.date: "07/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-security"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 856e8061-c604-4ce4-b89f-a11876dd6c88
caps.latest.revision: 26
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 24
---
# Создание и хранение главных ключей столбцов (постоянное шифрование)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

*Главные ключи столбцов* являются защищающими ключами, которые используются в режиме постоянного шифрования для кодирования ключей шифрования столбцов. Главные ключи столбцов должны храниться в надежном хранилище ключей и быть доступны для приложений, которым необходимо зашифровать или расшифровать данные, а также для средств для настройки постоянного шифрования и управления ключами постоянного шифрования.

Эта статья содержит подробные сведения о выборе хранилища ключей и создании главных ключей столбцов для постоянного шифрования. Подробные сведения см. в разделе [Overview of Key Management for Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md) (Общие сведения об управлении ключами для постоянного шифрования).

## Выбор хранилища ключей для главного ключа столбца

Постоянное шифрование поддерживает несколько хранилищ ключей для хранения главных ключей столбцов постоянного шифрования. Поддерживаемые хранилища зависят от используемого драйвера и версии.

Следует принимать во внимание две высокоуровневые категории хранилищ ключей — *локальные хранилища ключей* и *централизованные хранилища ключей*.

###  Какое хранилище использовать — локальное или централизованное?

* **Локальные хранилища ключей** могут использоваться только приложениями на компьютерах с локальным хранилищем ключей. Другими словами, нужно реплицировать хранилище ключей и ключ на каждый компьютер, где запущено приложение. Примером локального хранилища ключей является хранилище сертификатов Windows. При использовании локального хранилища ключей необходимо убедиться, что хранилище ключей существует на каждом компьютере, на котором размещается приложение, и что компьютер содержит главные ключи столбцов, необходимые приложению для доступа к данным, защищенным с помощью постоянного шифрования. При первой подготовке главного ключа столбца или при изменении (смене) ключа необходимо проверить, что ключ будет развернут на всех компьютерах, где размещены приложения.

* **Централизованные хранилища ключей** обслуживают приложения на нескольких компьютерах. Примером централизованного хранилища ключей является [хранилище ключей Azure](https://azure.microsoft.com/services/key-vault/). Централизованное хранилище ключей обычно упрощает управление ключами, так как вам не требуется поддерживать несколько копий главных ключей столбцов на нескольких компьютерах. Необходимо убедиться, что приложения настроены для подключения к централизованному хранилищу ключей.

### Какие хранилища ключей поддерживаются клиентскими драйверами с включенным постоянным шифрованием?

Клиентские драйверы с включенным постоянным шифрованием — это драйверы клиента SQL Server со встроенной поддержкой для внедрения постоянного шифрования в клиентские приложения. Они включают в себя несколько встроенных поставщиков распространенных хранилищ ключей. Обратите внимание, что некоторые драйверы также позволяют реализовывать и регистрировать настраиваемый поставщик хранилища главных ключей столбцов, поэтому вы можете использовать любое хранилище ключей, даже если для него отсутствует встроенный поставщик. Делая выбор между встроенным поставщиком и настраиваемым поставщиком, необходимо учитывать, что использование встроенного поставщика обычно связано с незначительным изменением приложений (в некоторых случаях требуется только изменить строку подключения к базе данных).

Доступные встроенные поставщики зависят от выбранного драйвера, версии драйвера и операционной системы.  Обратитесь к документации по постоянному шифрованию для конкретного драйвера, чтобы определить, какие готовые хранилища ключей поддерживаются, и узнать, поддерживает ли ваш драйвер настраиваемые поставщики хранилищ ключей.

- [Разработка приложений с помощью постоянного шифрования и поставщика данных .NET Framework для SQL Server](../../../relational-databases/security/encryption/develop using always encrypted with .net framework data provider.md)


### Поддерживаемые средства

Для настройки постоянного шифрования и управления ключами постоянного шифрования можно использовать [среду SQL Server Management Studio](https://msdn.microsoft.com/library/Hh213248.aspx) и [модуль SqlServer PowerShell](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update). Список хранилищ ключей, поддерживающих это средство, см. в следующих разделах:

- [Configure Always Encrypted using SQL Server Management Studio (Настройка постоянного шифрования с помощью среды SQL Server Management Studio)](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)
- [Настройка постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)


## Создание главных ключей столбцов в хранилище сертификатов Windows    

Главный ключ столбца может быть сертификатом, который хранится в хранилище сертификатов Windows. Обратите внимание, что драйвер с поддержкой постоянного шифрования не проверяет дату окончания срока действия или цепочку центра сертификации. Сертификат просто используется как пара ключей, состоящая из открытого и закрытого ключей.

Чтобы быть допустимым главным ключом столбца, сертификат должен отвечать следующим условиям:
* являться сертификатом X.509;
* храниться в одном из расположений хранилища сертификатов: *local machine* или *current user* (чтобы создать сертификат в хранилище сертификатов локального компьютера, необходимо иметь права администратора на целевом компьютере);
* содержать закрытый ключ (рекомендуемая длина ключей в сертификате — 2048 бит или больше);
* поддерживать обмен ключами.


Существует несколько способов создания сертификата, который является допустимым главным ключом столбца, но проще всего создать самозаверяющий сертификат.


### Создание самозаверяющего сертификата с помощью PowerShell

Для создания самозаверяющего сертификата используется командлет [New-SelfSignedCertificate](https://technet.microsoft.com/library/hh848633.aspx). В примере ниже показано создание сертификата, который можно использовать в качестве главного ключа столбца для постоянного шифрования.

```
New-SelfSignedCertificate is a Windows PowerShell cmdlet that creates a self-signed certificate. The below examples show how to generate a certificate that can be used as a column master key for Always Encrypted.
$cert = New-SelfSignedCertificate -Subject "AlwaysEncryptedCert" -CertStoreLocation Cert:CurrentUserMy -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage KeyEncipherment -KeySpec KeyExchange -KeyLength 2048 

# To create a certificate in the local machine certificate store location you need to run the cmdlet as an administrator.
$cert = New-SelfSignedCertificate -Subject "AlwaysEncryptedCert" -CertStoreLocation Cert:LocalMachineMy -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage KeyEncipherment -KeySpec KeyExchange -KeyLength 2048
```

### Создание самозаверяющего сертификата с помощью среды SQL Server Management Studio (SSMS)

Подробные сведения см. в разделе [Configure Always Encrypted using SQL Server Management Studio (Настройка постоянного шифрования с помощью среды SQL Server Management Studio)](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md).
Пошаговое руководство, где используется среда SSMS и ключи постоянного шифрования сохраняются в хранилище сертификатов Windows, см. в статье [Постоянное шифрование: защита конфиденциальных данных в базе данных SQL с помощью шифрования базы данных и хранение ключей шифрования в хранилище сертификатов Windows](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/).


### Предоставление приложениям и пользователям доступа к сертификатам

Если главный ключ столбца является сертификатом, хранящимся в расположении хранилища сертификатов на *локальном компьютере*, необходимо экспортировать сертификат с закрытым ключом и импортировать его на все компьютеры, где размещены приложения, которые будут шифровать или расшифровывать данные, хранящиеся в зашифрованных столбцах, или средства для настройки постоянного шифрования и для управления ключами постоянного шифрования. Кроме того, каждому пользователю должно быть предоставлено разрешение на чтение сертификата, хранящегося в расположение хранилища сертификатов на локальном компьютера, чтобы он мог использовать сертификат в качестве главного ключа столбца.

Если главный ключ столбца является сертификатом, хранящимся в расположении хранилища сертификатов под учетной записью *текущего пользователя*, необходимо экспортировать сертификат с закрытым ключом и импортировать его в расположение хранилища сертификатов для всех учетных записей пользователей, где размещены приложения, которые будут шифровать или расшифровывать данные, хранящиеся в зашифрованных столбцах, или средства для настройки постоянного шифрования и для управления ключами постоянного шифрования (на всех компьютерах с этими приложениями или средствами). Настройка разрешений не требуется — после входа в систему пользователь может обращаться ко всем сертификатам в расположении хранилища сертификатов текущего пользователя.

#### Использование PowerShell
Для импорта и экспорта сертификата используются командлеты [Import-PfxCertificate](https://msdn.microsoft.com/library/hh848625.aspx) и [Export-PfxCertificate](https://msdn.microsoft.com/library/hh848635.aspx).

#### Использование консоли управления (MMC) 

Чтобы предоставить пользователю разрешение на *чтение* сертификата, хранящегося в расположение хранилища сертификатов на локальном компьютере, выполните приведенные далее действия.

1.  Откройте окно командной строки и введите **mmc**.
2.  В консоли MMC в меню **Файл** выберите **Добавить или удалить оснастку**.
3.  В диалоговом окне **Добавление или удаление оснастки** нажмите кнопку **Добавить**.
4.  В диалоговом окне **Добавление изолированной оснастки** выберите **Сертификаты** и нажмите кнопку **Добавить**.
5.  В диалоговом окне оснастки **Сертификаты** выберите **Учетная запись компьютера** и нажмите кнопку **Готово**.
6.  В диалоговом окне **Добавление изолированной оснастки** нажмите кнопку **Закрыть**.
7.  В диалоговом окне **Добавление или удаление оснастки** нажмите кнопку **ОК**.
8.  В оснастке **Сертификаты** найдите сертификат в папке **Сертификаты/Личное**, правой кнопкой мыши щелкните "Сертификат", укажите**Все задачи** и выберите **Управление закрытыми ключами**.
9.  В диалоговом окне **Безопасность** добавьте разрешение на чтение для учетной записи пользователя (если необходимо).

## Создание главных ключей столбцов в хранилище ключей Azure

Хранилище ключей Azure обеспечивает защиту криптографических ключей и удобно для хранения главных ключей столбцов для постоянного шифрования, особенно в том случае, если приложения размещены в Azure. Для создания ключа в [хранилище ключей Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/) необходимы [подписка Azure](https://azure.microsoft.com/free/) и хранилище ключей Azure.

#### Использование PowerShell

В примере ниже показано создание хранилища ключей Azure и ключа и последующее предоставление разрешений нужному пользователю.

```
# Create a column master key in Azure Key Vault.
Login-AzureRmAccount
$SubscriptionId = "<Azure subscription ID>"
$resourceGroup = "<resource group name>"
$azureLocation = "<key vault location>"
$akvName = "<key vault name>"
$akvKeyName = "<column master key name>"
$azureCtx = Set-AzureRMContext -SubscriptionId $SubscriptionId # Sets the context for the below cmdlets to the specified subscription.
New-AzureRmResourceGroup –Name $resourceGroup –Location $azureLocation # Creates a new resource group - skip, if you desire group already exists.
New-AzureRmKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation -SKU premium # Creates a new key vault - skip if your vault already exists.
Set-AzureRmKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, delete, list, update, import, backup, restore, wrapKey, unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account
$akvKey = Add-AzureKeyVaultKey -VaultName $akvName -Name $akvKeyName -Destination HSM
```

#### SQL Server Management Studio (SSMS)

Пошаговое руководство, где используется среда SSMS и ключи постоянного шифрования сохраняются в хранилище ключей Azure, см. в статье [Постоянное шифрование: защита конфиденциальных данных в базе данных SQL с помощью шифрования данных и хранение ключей шифрования в хранилище ключей Azure](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted-azure-key-vault).

### Предоставление приложениям и пользователям доступа к ключам в хранилище ключей Azure

При использовании ключа хранилища ключей Azure в качестве главного ключа столбца приложение должно пройти проверку подлинности в Azure, а удостоверение приложения должно иметь следующие разрешения на доступ к хранилищу ключей: *get*, *unwrapKey* и *verify*. 

Для подготовки ключей шифрования столбцов, которые защищены с помощью главного ключа столбца, хранящегося в хранилище ключей Azure, необходимы разрешения *get*, *unwrapKey*, *wrapKey*, *sign* и *verify*. Кроме того, для создания ключа в хранилище ключей Azure необходимо разрешение *create*, для просмотра содержимого хранилища ключей требуется разрешение *list*.

#### Использование PowerShell

Чтобы предоставить пользователям и приложениям доступ к фактическим ключам в хранилище ключей Azure, необходимо задать политику доступа к хранилищу ([Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx)).

```
$vaultName = "<vault name>"
$resourceGroupName = "<resource group name>"
$userPrincipalName = "<user to grant access to>"
$clientId = "<client Id>"

# grant users permissions to the keys:
Set-AzureRmKeyVaultAccessPolicy -VaultName $vaultName -ResourceGroupName $resourceGroupName -PermissionsToKeys create,get,wrapKey,unwrapKey,sign,verify,list -UserPrincipalName $userPrincipalName
# grant applications permissions to the keys:
Set-AzureRmKeyVaultAccessPolicy  -VaultName $vaultName  -ResourceGroupName $resourceGroupName -ServicePrincipalName $clientId -PermissionsToKeys get,wrapKey,unwrapKey,sign,verify,list
```

## Создание главных ключей столбцов в аппаратных модулях безопасности с помощью CNG

Главный ключ столбца для постоянного шифрования может храниться в хранилище ключей, реализующем API криптографии следующего поколения (CNG). Как правило, этот тип хранилища является аппаратным модулем безопасности (HSM). HSM — это физическое устройство, которое защищает цифровые ключи и управляет ими, а также обеспечивает обработку шифрования. Аппаратные модули безопасности традиционно имеют вид подключаемой платы или внешнего устройства, напрямую подключаемого к компьютеру (локальный HSM) или сетевому серверу.

Чтобы модуль HSM был доступен для приложений на данном компьютере, на компьютере должен быть установлен и настроен поставщик хранилища ключей (KSP), реализующий CNG. Клиентский драйвер с постоянным шифрованием (поставщик хранилища главных ключей столбцов в драйвере) использует KSP для шифрования и расшифровки ключей шифрования столбцов, защищенных главным ключом столбца, который хранится в хранилище ключей.

В состав Windows входит ПО поставщика хранилища ключей Microsoft Software Key Storage Provider — программный поставщик KSP, который можно использовать для тестирования. См. раздел [CNG Key Storage Providers](https://msdn.microsoft.com/library/windows/desktop/bb931355.aspx) (Поставщики хранилища ключей CNG).

### Создание главных ключей столбцов в хранилище ключей с помощью CNG или KSP

Главный ключ столбца должен быть асимметричным ключом (парой открытого и закрытого ключей), использующим алгоритм RSA. Рекомендуемая длина ключа — 2048 или больше.

#### Использование средств с поддержкой HSM
Обратитесь к документации по имеющемуся аппаратному модулю безопасности.

#### Использование PowerShell

Для создания ключа в хранилище ключей с помощью CNG в PowerShell можно использовать API-интерфейсы .NET.


```
$cngProviderName = "Microsoft Software Key Storage Provider" # If you have an HSM, you can use a KSP for your HSM instead of a Microsoft KSP
$cngAlgorithmName = "RSA"
$cngKeySize = 2048 # Recommended key size for Always Encrypted column master keys
$cngKeyName = "AlwaysEncryptedKey" # Name identifying your new key in the KSP
$cngProvider = New-Object System.Security.Cryptography.CngProvider($cngProviderName)
$cngKeyParams = New-Object System.Security.Cryptography.CngKeyCreationParameters
$cngKeyParams.provider = $cngProvider
$cngKeyParams.KeyCreationOptions = [System.Security.Cryptography.CngKeyCreationOptions]::OverwriteExistingKey
$keySizeProperty = New-Object System.Security.Cryptography.CngProperty("Length", [System.BitConverter]::GetBytes($cngKeySize), [System.Security.Cryptography.CngPropertyOptions]::None);
$cngKeyParams.Parameters.Add($keySizeProperty)
$cngAlgorithm = New-Object System.Security.Cryptography.CngAlgorithm($cngAlgorithmName)
$cngKey = [System.Security.Cryptography.CngKey]::Create($cngAlgorithm, $cngKeyName, $cngKeyParams)
```

#### Использование среды SQL Server Management Studio

См. раздел [Provisioning Column Master using SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt757096.aspx#Anchor_2) (Подготовка главных ключей столбцов с помощью среды SQL Server Management Studio (SSMS)).


### Предоставление приложениям и пользователям доступа к ключам CNG

Сведения о настройке KSP на компьютере и предоставлении приложениям и пользователям доступа к HSM см. в документации по HSM и KSP.

## Создание главных ключей столбцов в аппаратных модулях безопасности с помощью CAPI

Главный ключ столбца для постоянного шифрования может храниться в хранилище ключей, реализующем API криптографии (CAPI). Как правило, такое хранилище представляет собой аппаратный модуль безопасности (HSM) — физическое устройство, которое защищает цифровые ключи и управляет ими, а также обеспечивает обработку шифрования. Аппаратные модули безопасности традиционно имеют вид подключаемой платы или внешнего устройства, напрямую подключаемого к компьютеру (локальный HSM) или сетевому серверу.

Чтобы модуль HSM был доступен для приложений на данном компьютере, на компьютере должен быть установлен и настроен поставщик служб шифрования (CSP), реализующий CAPI. Клиентский драйвер с постоянным шифрованием (поставщик хранилища главных ключей столбцов в драйвере) использует CSP для шифрования и расшифровки ключей шифрования столбцов, защищенных главным ключом столбца, который хранится в хранилище ключей. Примечание. CAPI — это устаревший API, который не рекомендуется использовать. Если для вашего модуля HSM доступен поставщик KSP, следует использовать именно его, а не CSP или CAPI.

CSP должен поддерживать алгоритм RSA, используемый с постоянным шифрованием.

В состав Windows входят следующие программные (не поддерживаемые модулем HSM) поставщики CSP, которые поддерживают RSA и могут использоваться в целях тестирования: Microsoft Enhanced RSA и AES Cryptographic Provider.

### Создание главных ключей столбцов в хранилище ключей с помощью CAPI или CSP

Главный ключ столбца должен быть асимметричным ключом (парой открытого и закрытого ключей), использующим алгоритм RSA. Рекомендуемая длина ключа — 2048 или больше.

#### Использование средств с поддержкой HSM
Обратитесь к документации по имеющемуся аппаратному модулю безопасности.

#### Использование среды SQL Server Management Studio (SSMS)
См. подраздел "Provisioning Column Master Keys" (Подготовка главных ключей столбцов) раздела "Configuring Always Encrypted using SQL Server Management Studio" (Настройка постоянного шифрования с помощью среды SQL Server Management Studio).

 
### Предоставление приложениям и пользователям доступа к ключам CNG
Сведения о настройке CSP на компьютере и предоставлении приложениям и пользователям доступа к HSM см. в документации по HSM и CSP.
 
 
## Следующие шаги  
  
- [Настройка ключей постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md)
- [Смена ключей постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [Configure Always Encrypted using SQL Server Management Studio (Настройка постоянного шифрования с помощью среды SQL Server Management Studio)](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)

  
## Дополнительные ресурсы  

- [Общие сведения об управлении ключами для постоянного шифрования](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Always Encrypted (ядро СУБД)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Develop Applications using Always Encrypted with the .NET Framework Data Provider for SQL Server (Разработка приложений с помощью постоянного шифрования и поставщика данных .NET Framework для SQL Server)](../../../relational-databases/security/encryption/develop using always encrypted with .net framework data provider.md)
- [Блог о постоянном шифровании](https://blogs.msdn.microsoft.com/sqlsecurity/tag/always-encrypted/)
    
