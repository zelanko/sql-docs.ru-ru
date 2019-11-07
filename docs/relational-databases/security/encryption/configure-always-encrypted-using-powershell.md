---
title: Настройка постоянного шифрования с помощью PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 10/01/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
ms.assetid: 12f2bde5-e100-41fa-b474-2d2332fc7650
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5c90ea22849dd1d0437cdf058f639bbe546ccab9
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594418"
---
# <a name="configure-always-encrypted-using-powershell"></a>Configure Always Encrypted using PowerShell
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Модуль SqlServer в PowerShell предоставляет командлеты для настройки [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) в [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

## <a name="security-considerations-when-using-powershell-to-configure-always-encrypted"></a>Вопросы безопасности при использовании PowerShell для настройки Always Encrypted

Так как основной задачей функции постоянного шифрования является обеспечение целостности зашифрованных конфиденциальных данных даже в случае нарушения безопасности системы базы данных, выполнение скрипта PowerShell, обрабатывающего ключи или конфиденциальные данные на сервере SQL Server, может снизить или вообще отменить эффект действия функции. Дополнительные рекомендации по безопасности см. в разделе [Security Considerations for Key Management](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management)(Вопросы безопасности для управления ключами).

PowerShell можно использовать для управления ключами Always Encrypted с разделением ролей и без разделения ролей, чтобы контролировать пользователей, имеющих доступ к фактическим ключам шифрования в хранилище ключей и доступ к базе данных.

 Дополнительные рекомендации по безопасности см. в разделе [Security Considerations for Key Management](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management)(Вопросы безопасности для управления ключами).

## <a name="prerequisites"></a>предварительные требования

Установите [модуль SqlServer](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/sqlserver) на защищенном компьютере, который НЕ является компьютером с экземпляром SQL Server. Модуль можно установить непосредственно из коллекции PowerShell.  Дополнительные сведения см. в [инструкциях по скачиванию](../../../ssms/download-sql-server-ps-module.md).


## <a name="importsqlservermodule"></a> Импорт модуля SqlServer 

Загрузка модуля SqlServer

1.  Чтобы установить соответствующую политику выполнения скриптов, используйте командлет **Set-ExecutionPolicy** .
2.  Для импорта модуля SqlServer используйте командлет **Import-Module** .

В этом примере показана загрузка модуля SqlServer.

```
# Import the SQL Server Module.  
Import-Module "SqlServer" 
```

## <a name="connectingtodatabase"></a> Соединение с базой данных

Некоторые командлеты постоянного шифрования работают с данными или метаданными в базе данных и требуют сначала выполнить соединение с базой данных. При настройке постоянного шифрования с помощью модуля SqlServer подключиться к базе данных можно двумя рекомендуемыми способами: 
1. Подключение с помощью командлета **Get-SqlDatabase**.
2. Подключение с помощью поставщика SQL Server PowerShell.

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

### <a name="using-get-sqldatabase"></a>Использование Get-SqlDatabase
Командлет **Get-SqlDatabase** позволяет подключиться к базе данных в SQL Server или в базе данных SQL Azure. Он возвращает объект базы данных, который затем можно передать с помощью параметра **InputObject** командлета, который подключается к базе данных. 

### <a name="using-sql-server-powershell"></a>Использование SQL Server PowerShell

```
# Import the SqlServer module
Import-Module "SqlServer"  

# Connect to your database
# Set the valid server name, database name and authentication keywords in the connection string
$serverName = "<Azure SQL server name>.database.windows.net"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Authentication = Active Directory Integrated"
$database = Get-SqlDatabase -ConnectionString $connStr

# List column master keys for the specified database.
Get-SqlColumnMasterKey -InputObject $database
```

Кроме того, можно применить перенаправление:


```
$database | Get-SqlColumnMasterKey
```

### <a name="using-sql-server-powershell-provider"></a>Использование поставщика SQL Server PowerShell
[Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md) отображает иерархию объектов SQL Server в виде путей, похожих на пути файловой системы. Используя SQL Server PowerShell, вы можете переходить по путям с помощью псевдонимов Windows PowerShell по аналогии с переходом по путям файловой системы с помощью команд. После перехода к целевому экземпляру и базе данных последующие командлеты будут использоваться в этой базе данных, как показано в следующем примере. 

> [!NOTE]
> Этот способ подключения к базе данных работает только для SQL Server (не поддерживается в базе данных SQL Azure).

```
# Import the SqlServer module.
Import-Module "SqlServer"
# Navigate to the database in the remote instance.
cd SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
# List column master keys in the above database.
Get-SqlColumnMasterKey
```

 
Кроме того, можно указать путь к базе данных с помощью универсального параметра **Path** , а не переходить к базе данных.


```
# Import the SqlServer module.
Import-Module "SqlServer" 
# List column master keys for the specified database.
Get-SqlColumnMasterKey -Path SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
```
 
## <a name="always-encrypted-tasks-using-powershell"></a>Задачи постоянного шифрования с использованием PowerShell

- [Подготовка ключей Always Encrypted с помощью PowerShell](configure-always-encrypted-keys-using-powershell.md)
- [Смена ключей постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [Шифрование, повторное шифрование или расшифровка столбцов с Always Encrypted через PowerShell](configure-column-encryption-using-powershell.md)


##  <a name="aecmdletreference"></a> Справочник по командлетам постоянного шифрования

Для постоянного шифрования доступны приведенные ниже командлеты PowerShell

|Командлет |Описание
|:---|:---
|**[Add-SqlAzureAuthenticationContext](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlazureauthenticationcontext)**   |Выполняет проверку подлинности в Azure и получает маркер проверки подлинности.
|**[Add-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlcolumnencryptionkeyvalue)**   |Добавляет новое зашифрованное значение для существующего объекта ключа шифрования столбца в базе данных.
|**[Complete-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/complete-sqlcolumnmasterkeyrotation)**   |Завершает смену главного ключа столбца.
|**[Get-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnencryptionkey)** |Возвращает все объекты ключа шифрования столбца, определенные в базе данных, или возвращает один объект ключа шифрования столбца с указанным именем.
|**[Get-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnmasterkey)** |Возвращает объекты главного ключа столбца, определенные в базе данных, или возвращает один объект главного ключа столбца с указанным именем.
|**[Invoke-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/invoke-sqlcolumnmasterkeyrotation)**   |Инициирует смену главного ключа столбца.
|**[New-SqlAzureKeyVaultColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlazurekeyvaultcolumnmasterkeysettings)**   |Создает объект SqlColumnMasterKeySettings, описывающий асимметричный ключ, который хранится в хранилище ключей Azure.
|**[New-SqlCngColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcngcolumnmasterkeysettings)**   |Создает объект SqlColumnMasterKeySettings, описывающий асимметричный ключ, который хранится в хранилище ключей, поддерживающем API CNG.
|**[New-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkey)** |Создает объект ключа шифрования столбца в базе данных.
|**[New-SqlColumnEncryptionKeyEncryptedValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkeyencryptedvalue)** |Выводит зашифрованное значение ключа шифрования столбца.
|**[New-SqlColumnEncryptionSettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionsettings)**   |Создает объект SqlColumnEncryptionSettings, который инкапсулирует сведения о шифровании одного столбца, включая CEK и тип шифрования.
|**[New-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkey)** |Создает объект главного ключа столбца в базе данных.
|**[New-SqlColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkeysettings)**|Создает объект SqlColumnMasterKeySettings для главного ключа столбца с указанным поставщиком и путем к ключу.
|**[New-SqlCspColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcspcolumnmasterkeysettings)**   |Создает объект SqlColumnMasterKeySettings, описывающий асимметричный ключ, который хранится в хранилище ключей с поставщиком CSP, поддерживающим CAPI.
|**[Remove-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkey)**   |Удаляет объект ключа шифрования столбца из базы данных.
|**[Remove-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkeyvalue)** |Удаляет зашифрованное значение из существующего объекта ключа шифрования столбца в базе данных.
|**[Remove-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnmasterkey)**   |Удаляет объект главного ключа столбца из базы данных.
|**[Set-SqlColumnEncryption](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/set-sqlcolumnencryption)**   |Шифрует, расшифровывает или повторно шифрует указанные столбцы в базе данных.



## <a name="see-also"></a>См. также:

- [Постоянное шифрование](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Общие сведения об управлении ключами для Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Настройка функции Always Encrypted с помощью SQL Server Management Studio](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)
- [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md)