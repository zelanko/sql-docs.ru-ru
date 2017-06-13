---
title: "Настройка постоянного шифрования с помощью PowerShell | Документация Майкрософт"
ms.custom: 
ms.date: 05/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-security
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12f2bde5-e100-41fa-b474-2d2332fc7650
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: c4cd6d86cdcfe778d6b8ba2501ad4a654470bae7
ms.openlocfilehash: dcd6c2dc9c489a888c647a77c27ce9694d154699
ms.contentlocale: ru-ru
ms.lasthandoff: 05/18/2017

---
# <a name="configure-always-encrypted-using-powershell"></a>Настройка постоянного шифрования с помощью PowerShell
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Модуль SqlServer в PowerShell предоставляет командлеты для настройки параметра [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) как в базе данных SQL Azure, так и в SQL Server 2016.

Всегда зашифровано командлеты в модуле SqlServer работает с ключи или конфиденциальные данные, поэтому очень важно выполнять командлеты на защищенном компьютере. При управлении постоянным шифрованием, выполните командлеты на другом компьютере, отличном от компьютера, на котором размещен экземпляр SQL Server.

Поскольку основной задачей функции постоянного шифрования является обеспечение зашифрованных конфиденциальных данных безопасен, даже в случае компрометации системы базы данных, выполнение скрипта PowerShell, обрабатывающего ключи или конфиденциальные данные на сервере SQL Server может снизить или вообще отменить эффект действия функции. Дополнительные рекомендации по безопасности см. в разделе [Security Considerations for Key Management](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md#SecurityForKeyManagement)(Вопросы безопасности для управления ключами).

Ссылки на статьи, посвященные отдельным командлетам, указаны [внизу страницы](#aecmdletreference).

## <a name="prerequisites"></a>Предварительные требования

Установите [модуль SqlServer](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/sqlserver) на защищенном компьютере, который НЕ является компьютером с экземпляром SQL Server. Модуль можно установить непосредственно из коллекции PowerShell.  В разделе [загрузки](../../../ssms/download-sql-server-ps-module.md) инструкции для получения дополнительных сведений.


## <a name="importsqlservermodule"></a> Импорт модуля SqlServer 

Загрузка модуля SqlServer

1.    Чтобы установить соответствующую политику выполнения скриптов, используйте командлет **Set-ExecutionPolicy** .
2.    Для импорта модуля SqlServer используйте командлет **Import-Module** .

В этом примере показана загрузка модуля SqlServer.

```
# Import the SQL Server Module.  
Import-Module "SqlServer" 
```

## <a name="connectingtodatabase"></a> Соединение с базой данных

Некоторые командлеты постоянного шифрования работают с данными или метаданными в базе данных и требуют сначала выполнить соединение с базой данных. При настройке постоянного шифрования с помощью модуля SqlServer подключиться к базе данных можно двумя рекомендуемыми способами: 
1. Подключение с помощью SQL Server PowerShell.
2. Подключение с помощью управляющих объектов SQL Server (SMO).

### <a name="using-sql-server-powershell"></a>Использование SQL Server PowerShell

Этот способ работает только для SQL Server (не поддерживается в базе данных SQL Azure).

Используя SQL Server PowerShell, вы можете переходить по путям с помощью псевдонимов Windows PowerShell по аналогии с переходом по путям файловой системы с помощью команд. После перехода к целевому экземпляру и базе данных, последующие командлеты целевого эту базу данных, как показано в следующем примере:

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
 
### <a name="using-smo"></a>Использование SMO

Этот способ работает для базы данных SQL Azure и SQL Server.
С помощью SMO можно создать объект [Класс Database](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.database.aspx), а затем передать его с использованием параметра **InputObject** командлета, который подключается к базе данных.


```
# Import the SqlServer module
Import-Module "SqlServer"  

# Connect to your database (Azure SQL database).
$serverName = "<Azure SQL server name>.database.windows.net"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Authentication = Active Directory Integrated"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName] 

# List column master keys for the specified database.
Get-SqlColumnMasterKey -InputObject $database
```


Кроме того, можно применить перенаправление:


```
$database | Get-SqlColumnMasterKey
```

## <a name="always-encrypted-tasks-using-powershell"></a>Задачи постоянного шифрования с использованием PowerShell

- [Настройка ключей постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md) 
- [Смена ключей постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [Настройка шифрования столбцов с помощью PowerShell](../../../relational-databases/security/encryption/configure-column-encryption-using-powershell.md)


##  <a name="aecmdletreference"></a> Справочник по командлетам постоянного шифрования

Для постоянного шифрования доступны приведенные ниже командлеты PowerShell

|Командлет    |Описание
|:---|:---
|**[Add-SqlAzureAuthenticationContext](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlazureauthenticationcontext)**    |Выполняет проверку подлинности в Azure и получает маркер проверки подлинности.
|**[Add-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlcolumnencryptionkeyvalue)**    |Добавляет новое зашифрованное значение для существующего объекта ключа шифрования столбца в базе данных.
|**[Complete-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/complete-sqlcolumnmasterkeyrotation)**    |Завершает смену главного ключа столбца.
|**[Get-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnencryptionkey)**    |Возвращает все объекты ключа шифрования столбца, определенные в базе данных, или возвращает один объект ключа шифрования столбца с указанным именем.
|**[Get-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnmasterkey)**    |Возвращает объекты главного ключа столбца, определенные в базе данных, или возвращает один объект главного ключа столбца с указанным именем.
|**[Invoke-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/invoke-sqlcolumnmasterkeyrotation)**    |Инициирует смену главного ключа столбца.
|**[New-SqlAzureKeyVaultColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlazurekeyvaultcolumnmasterkeysettings)**    |Создает объект SqlColumnMasterKeySettings, описывающий асимметричный ключ, который хранится в хранилище ключей Azure.
|**[New-SqlCngColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcngcolumnmasterkeysettings)**    |Создает объект SqlColumnMasterKeySettings, описывающий асимметричный ключ, который хранится в хранилище ключей, поддерживающем API CNG.
|**[New-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkey)**    |Создает объект ключа шифрования столбца в базе данных.
|**[New-SqlColumnEncryptionKeyEncryptedValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkeyencryptedvalue)**    |Выводит зашифрованное значение ключа шифрования столбца.
|**[New-SqlColumnEncryptionSettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionsettings)**    |Создает объект SqlColumnEncryptionSettings, который инкапсулирует сведения о шифровании одного столбца, включая CEK и тип шифрования.
|**[New-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkey)**    |Создает объект главного ключа столбца в базе данных.
|**[Новый SqlColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkeysettings)**|Создает объект SqlColumnMasterKeySettings для главного ключа столбца с указанным поставщиком и путем к ключу.
|**[New-SqlCspColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcspcolumnmasterkeysettings)**    |Создает объект SqlColumnMasterKeySettings, описывающий асимметричный ключ, который хранится в хранилище ключей с поставщиком CSP, поддерживающим CAPI.
|**[Remove-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkey)**    |Удаляет объект ключа шифрования столбца из базы данных.
|**[Remove-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkeyvalue)**    |Удаляет зашифрованное значение из существующего объекта ключа шифрования столбца в базе данных.
|**[Remove-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnmasterkey)**    |Удаляет объект главного ключа столбца из базы данных.
|**[Set-SqlColumnEncryption](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/set-sqlcolumnencryption)**    |Шифрует, расшифровывает или повторно шифрует указанные столбцы в базе данных.



## <a name="additional-resources"></a>Дополнительные ресурсы

- [Always Encrypted (ядро СУБД)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Общие сведения об управлении ключами для постоянного шифрования](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Using Always Encrypted with .NET Framework Data Provider for SQL Server (Использование постоянного шифрования с поставщиком данных .NET Framework для SQL Server)](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [Configure Always Encrypted using SQL Server Management Studio (Настройка постоянного шифрования с помощью среды SQL Server Management Studio)](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)



