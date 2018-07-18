---
title: Управление SQL Server в Linux с помощью PowerShell | Документация Майкрософт
description: В этой статье описывается с помощью PowerShell в Windows с помощью SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: a1b6b4bb4c99a3b991120d57b8cf25cc91686957
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982146"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Управление SQL Server в Linux с помощью PowerShell в Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье рассматриваются [SQL Server PowerShell](https://msdn.microsoft.com/library/mt740629.aspx) и о том, как использовать его в SQL Server 2017 в Linux описывается несколько примеров. Поддержка PowerShell для SQL Server на Windows, поэтому его можно использовать, если используется компьютер Windows, который может подключиться к удаленному экземпляру SQL Server в Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Установите последнюю версию SQL PowerShell на Windows

[SQL PowerShell](https://msdn.microsoft.com/library/mt740629.aspx) на Windows входит в состав [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md). При работе с SQL Server, следует всегда использовать самую последнюю версию SSMS и SQL PowerShell. Последняя версия SSMS постоянно обновляется и оптимизированных для операций и в настоящее время работает с SQL Server 2017 на базе Linux. Чтобы загрузить и установить последнюю версию, см. в разделе [скачивание SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). В курсе событий, последняя версия SSMS предлагает при появлении новой версии, можно загрузить.

## <a name="before-you-begin"></a>Перед началом

Чтение [известные проблемы](sql-server-linux-release-notes.md) для SQL Server 2017 в Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Запустите PowerShell и импортируйте *sqlserver* модуля

Давайте сперва запустите PowerShell на Windows. Откройте *командной* на компьютере Windows и тип **PowerShell** запустить новый сеанс Windows PowerShell.

```
PowerShell
```

SQL Server входит модуль Windows PowerShell, называемый **SqlServer** можно использовать для импорта компонентов SQL Server (SQL Server поставщика и командлетов) в среде PowerShell или скрипт.

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
Script     0.0        SqlServer
Manifest   20.0       SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Подключиться к SQL Server и получить сведения о сервере

Давайте использовать PowerShell в Windows для подключения к экземпляру SQL Server 2017 в Linux и отображения несколько свойств сервера.

Скопируйте и вставьте следующие команды в командной строке PowerShell. При выполнении этих команд PowerShell выполняются следующие действия:
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, которое запрашивает учетные данные (*имя пользователя SQL* и *пароль SQL*) для подключения к SQL Server 2017 экземпляр в Linux
- Загрузить сборку объекты управления SQL Server (SMO)
- Создайте экземпляр [Server](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.server.aspx) объекта
- Подключение к **Server** и отобразить несколько свойств

Не забудьте заменить **\<your_server_instance\>** с IP-адрес или имя узла экземпляра SQL Server 2017 в Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Load the SMO assembly and create a Server object
[System.Reflection.Assembly]::LoadWithPartialName('Microsoft.SqlServer.SMO') | out-null
$server = New-Object ('Microsoft.SqlServer.Management.Smo.Server') $serverInstance

# Set credentials
$server.ConnectionContext.LoginSecure=$false
$server.ConnectionContext.set_Login($credential.UserName)
$server.ConnectionContext.set_SecurePassword($credential.Password)

# Connect to the Server and get a few properties
$server.Information | Select-Object Edition, HostPlatform, HostDistribution | Format-List
# done
```

PowerShell должна отображать сведения, аналогичные приведенным ниже:

```
Edition          : Developer Edition (64-bit)
HostPlatform     : Linux
HostDistribution : Ubuntu
```
> [!NOTE]
> Если ничего не отображается для этих значений, скорее всего сбой подключения к целевому экземпляру SQL Server. Убедитесь, что можно использовать одни сведения о подключении для подключения из SQL Server Management Studio. Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="examine-sql-server-error-logs"></a>Проверьте журналы ошибок SQL Server

Давайте PowerShell на Windows, чтобы проверить журналы ошибок подключения в экземпляре SQL Server 2017 в Linux. Мы также будем использовать **Out-GridView** регистрирует для отображения сведений из-за ошибки в окне представления сетки.

Скопируйте и вставьте следующие команды в командной строке PowerShell. Они может занять несколько минут. Эти команды выполняют следующее:
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, которое запрашивает учетные данные (*имя пользователя SQL* и *пароль SQL*) для подключения к SQL Server 2017 экземпляр в Linux
- Используйте **Get-SqlErrorLog** командлет, чтобы подключиться к экземпляру SQL Server 2017 на Linux и получения ошибки журналы с момента **вчера**
- Выходные данные для **Out-GridView** командлета

Не забудьте заменить **\<your_server_instance\>** с IP-адрес или имя узла экземпляра SQL Server 2017 в Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>См. также
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
