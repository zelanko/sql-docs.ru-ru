---
title: Управление SQL Server в Linux с использованием PowerShell Core | Документация Майкрософт
description: В этой статье описывается с помощью PowerShell Core с SQL Server в Linux.
ms.date: 04/22/2019
ms.reviewer: jroth
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
manager: craigg
ms.openlocfilehash: 17858877efbb3f421f95b19e4b2eb66bfde5dbb4
ms.sourcegitcommit: 02df4e7965b2a858030bb508eaf8daa9bc10b00b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265346"
---
# <a name="manage-sql-server-on-linux-with-powershell-core"></a>Управление SQL Server в Linux с использованием PowerShell Core

В этой статье рассматриваются [SQL Server PowerShell](../powershell/sql-server-powershell.md) и описывается несколько примеров, о том, как использовать его в PowerShell Core (ядро PS) на macOS и Linux. PowerShell Core теперь включен проект с открытым кодом [GitHub](https://github.com/powershell/powershell).

## <a name="cross-platform-editor-options"></a>Параметры редактора кросс платформенные

Все действия PowerShell Core ниже будет работать в терминале регулярных или их можно запускать из терминала в VS Code или Azure Data Studio.  VS Code и Azure Data Studio доступны в macOS и Linux.  Дополнительные сведения об Azure Data Studio, см. в разделе [в этом кратком руководстве](https://docs.microsoft.com/sql/azure-data-studio/quickstart-sql-server).  Можно также рассмотреть возможность использования [расширение PowerShell](https://docs.microsoft.com/sql/azure-data-studio/powershell-extension) для него.

## <a name="installing-powershell-core"></a>Установка PowerShell Core

Дополнительные сведения об установке PowerShell Core на различных платформах, поддерживаемых и экспериментальных см. в разделе со следующими статьями:

- [Установка PowerShell Core в Windows](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6)
- [Установка PowerShell Core в Linux](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [Установка PowerShell Core в macOS](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)
- [Установка PowerShell Core в ARM](https://docs.microsoft.com/powershell/scripting/install/powershell-core-on-arm?view=powershell-6)

## <a name="install-the-sqlserver-module"></a>Установите модуль SqlServer

`SqlServer` Модуля сохраняется в [коллекции PowerShell](https://www.powershellgallery.com/packages/SqlServer/). При работе с SQL Server, следует всегда использовать последнюю версию модуля SqlServer PowerShell.

Чтобы установить модуль SqlServer, откройте сеанс PowerShell Core и выполните следующий код:

```powerhsell
Install-Module -Name SqlServer
```

Дополнительные сведения о том, как установить модуль SqlServer в коллекции PowerShell см. в этом [страницы](../powershell/download-sql-server-ps-module.md).

## <a name="using-the-sqlserver-module"></a>С помощью модуля SqlServer

Давайте сперва запустите PowerShell Core.  Если вы используете macOS или Linux, откройте *сеанс терминала* на компьютере, а также тип **pwsh** для запуска нового сеанса PowerShell Core.  На Windows, с помощью <kbd>выиграть</kbd>+<kbd>R</kbd>и тип `pwsh` для запуска нового сеанса PowerShell Core.

```
pwsh
```

SQL Server предоставляет модуль PowerShell, называемый **SqlServer**. Можно использовать **SqlServer** модуль для импорта компонентов SQL Server (SQL Server поставщика и командлетов) в среде PowerShell или скрипт.

Скопируйте и вставьте следующую команду в командной строке PowerShell для импорта **SqlServer** модуля в текущем сеансе PowerShell:

```powershell
Import-Module SqlServer
```

Введите следующую команду в командной строке PowerShell, чтобы убедиться, что **SqlServer** модуль был импортирован правильно:

```powershell
Get-Module -Name SqlServer
```

PowerShell должна отображать сведения, аналогичные приведенным ниже:

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     21.1.18102 SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Подключиться к SQL Server и получить сведения о сервере

В следующих действиях используется PowerShell Core для подключения к экземпляру SQL Server в Linux и отобразить несколько свойств сервера.

Скопируйте и вставьте следующие команды в командной строке PowerShell. При выполнении этих команд PowerShell выполняются следующие действия:
- Отображает диалоговое окно с приглашением для имени узла или IP-адрес экземпляра
- Отображение *запрос учетных данных PowerShell* диалоговое окно, в котором будет предложено ввести учетные данные. Можно использовать ваши *имя пользователя SQL* и *пароль SQL* для подключения к экземпляру SQL Server в Linux
- Используйте **Get-SqlInstance** для подключения к **Server** и отобразить несколько свойств

При необходимости вы можете просто подставить `$serverInstance` переменной с IP-адрес или имя узла экземпляра SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Connect to the Server and return a few properties
Get-SqlInstance -ServerInstance $serverInstance -Credential $credential
# done
```

PowerShell должна отображать сведения, аналогичные приведенным ниже:

```
Instance Name                   Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------                   -------    ------------ -----------  ------------ ----------------
your_server_instance            14.0.3048  RTM          CU13         Linux        Ubuntu
```

> [!NOTE]
> Если ничего не отображается для этих значений, скорее всего сбой подключения к целевому экземпляру SQL Server. Убедитесь, что можно использовать одни сведения о подключении для подключения из SQL Server Management Studio. Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="using-the-sql-server-powershell-provider"></a>Использование поставщика SQL Server PowerShell

Другой вариант для подключения к экземпляру SQL Server является использование [поставщик SQL Server PowerShell](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).  С помощью поставщика можно перейти в экземпляре SQL Server, аналогичную так, как если бы вы Навигация по структуре дерева в обозревателе объектов, но в командную строку.  По умолчанию этот поставщик будет представлено как с именем PSDrive `SQLSERVER:\` которого можно использовать для подключения & ведет экземпляров SQL Server, к которым имеет доступ учетная запись домена.  См. в разделе [действия по настройке](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps) сведения о способах настройки проверки подлинности Active Directory для SQL Server в Linux.

Можно также использовать проверку подлинности SQL с помощью поставщика SQL Server PowerShell. Чтобы сделать это, используйте `New-PSDrive` командлет, чтобы создать новый PSDrive и задать соответствующие учетные данные для подключения.

В этом примере вы увидите пример того, как создать новый PSDrive, используя проверку подлинности SQL.

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.

New-PSDrive -Name SQLonDocker -PSProvider SqlServer -Root 'SQLSERVER:\SQL\localhost,10002\Default\' -Credential $credential
```

Убедитесь, что диск был создан путем запуска `Get-PSDrive` командлета.

```powershell
Get-PSDrive
```

После создания ваш новый PSDrive, можно запустить их.

```powershell
dir SQLonDocker:\Databases
```

Вот, как может выглядеть выходные данные.  Можно заметить, этот результат аналогичен приведенному SSMS будет отображаться в узле базы данных.  Он отображает пользовательские базы данных, но не системных баз данных.

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.76 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.57 MB Simple       140 sa
```

Если вам нужно увидеть все базы данных в экземпляре, один из вариантов является использование `Get-SqlDatabase` командлета.

## <a name="get-databases"></a>Получение баз данных

— Важный командлет знать `Get-SqlDatabase`.  Для многих операций, которые включают в себя базу данных или объекты в базе данных `Get-SqlDatabase` можно использовать командлет.  Если необходимо указать значения для обоих `-ServerInstance` и `-Database` параметров, только этот объект одной базы данных будут извлекаться.  Тем не менее если указать только `-ServerInstance` параметр, возвращается полный список всех баз данных на этом экземпляре.

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.

# Connect to the Instance and retrieve all databases
Get-SqlDatabase -ServerInstance ServerB -Credential $credential
```

Ниже приведен пример что возвращаемые приведенной выше команде Get-SqlDatabase.

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.88 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.63 MB Simple       140 sa
master               Normal        6.00 MB  600.00 KB Simple       140 sa
model                Normal       16.00 MB    5.70 MB Full         140 sa
msdb                 Normal       15.50 MB    1.14 MB Simple       140 sa
tempdb               Normal       16.00 MB    5.49 MB Simple       140 sa

```

## <a name="examine-sql-server-error-logs"></a>Проверьте журналы ошибок SQL Server

В следующих действиях используется PowerShell Core для изучения ошибок, к которым подключаются журналы в экземпляре SQL Server в Linux.

Скопируйте и вставьте следующие команды в командной строке PowerShell. Они может занять несколько минут. Эти команды выполняют следующие действия:
- Отображает диалоговое окно с приглашением для имени узла или IP-адрес экземпляра
- Отображение *запрос учетных данных PowerShell* диалоговое окно, которое запрашивает учетные данные. Можно использовать ваши *имя пользователя SQL* и *пароль SQL* для подключения к экземпляру SQL Server в Linux
- Используйте **Get-SqlErrorLog** командлет для подключения к экземпляру SQL Server в Linux и получения ошибки журналы с момента **вчера**

При необходимости можно заменить `$serverInstance` переменной с IP-адрес или имя узла экземпляра SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday
# done
```

## <a name="explore-cmdlets-currently-available-in-ps-core"></a>Изучите командлетов, доступных в PS Core
Хотя модуль SqlServer в настоящее время имеет 106 командлетов, доступных в Windows PowerShell, в PSCore доступны только 59 из 106. Полный список доступных 59 командлетов приведены ниже.  Подробная документация по всех командлетов в модуле SqlServer, см. в разделе SqlServer [Справочник по командлетам](https://docs.microsoft.com/powershell/module/sqlserver/).

Следующая команда будут показаны все доступных командлетов на версии PowerShell, вы используете.

```powershell
Get-Command -Module SqlServer -CommandType Cmdlet |
SORT -Property Noun |
SELECT Name
```

- ConvertFrom-EncodedSqlName
- ConvertTo-EncodedSqlName
- Get-SqlAgent
- Get-SqlAgentJob
- Get-SqlAgentJobHistory
- Get-SqlAgentJobSchedule
- Get-SqlAgentJobStep
- Get-SqlAgentSchedule
- Remove-SqlAvailabilityDatabase
- Resume-SqlAvailabilityDatabase
- Add-SqlAvailabilityDatabase
- Suspend-SqlAvailabilityDatabase
- New-SqlAvailabilityGroup
- Set-SqlAvailabilityGroup
- Remove-SqlAvailabilityGroup
- Switch-SqlAvailabilityGroup
- Join-SqlAvailabilityGroup
- REVOKE-SqlAvailabilityGroupCreateAnyDatabase
- GRANT-SqlAvailabilityGroupCreateAnyDatabase
- New-SqlAvailabilityGroupListener
- Set-SqlAvailabilityGroupListener
- Add-SqlAvailabilityGroupListenerStaticIp
- Set-SqlAvailabilityReplica
- Remove-SqlAvailabilityReplica
- New-SqlAvailabilityReplica
- SET-SqlAvailabilityReplicaRoleToSecondary.
- Новый SqlBackupEncryptionOption
- Get-SqlBackupHistory
- Invoke-Sqlcmd
- New-SqlCngColumnMasterKeySettings
- Remove-SqlColumnEncryptionKey
- Get-SqlColumnEncryptionKey
- Remove-SqlColumnEncryptionKeyValue
- Add-SqlColumnEncryptionKeyValue
- Get-SqlColumnMasterKey
- Remove-SqlColumnMasterKey
- New-SqlColumnMasterKey
- Get-SqlCredential
- Set-SqlCredential
- New-SqlCredential
- Remove-SqlCredential
- New-SqlCspColumnMasterKeySettings
- Get-SqlDatabase.
- Restore-SqlDatabase
- Backup-SqlDatabase
- SET-SqlErrorLog
- Get-SqlErrorLog
- New-SqlHADREndpoint
- Set-SqlHADREndpoint
- Get-SqlInstance
- Добавить SqlLogin
- Remove-SqlLogin
- Get-SqlLogin
- Set-SqlSmartAdmin
- Get-SqlSmartAdmin
- Read-SqlTableData
- Write-SqlTableData
- Read-SqlViewData
- Convert-UrnToPath

## <a name="see-also"></a>См. также
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
