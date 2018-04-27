---
title: Управление SQL Server в Linux с помощью PowerShell | Документы Microsoft
description: Это статье представлен обзор использования PowerShell в Windows с помощью SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.workload: Inactive
ms.openlocfilehash: 8869f87ec6e69844155a2bf0361a90e07b30de24
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Использование PowerShell в Windows для управления SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описаны [SQL Server PowerShell](https://msdn.microsoft.com/en-us/library/mt740629.aspx) и будет выполнено несколько примеров о том, как использовать его с 2017 г. SQL Server в Linux. Поддержка PowerShell для SQL Server в настоящее время доступен в Windows, поэтому можно использовать, если используется компьютер Windows, можно подключиться к удаленному экземпляру SQL Server в Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Установите последнюю версию SQL PowerShell в Windows

[SQL PowerShell](https://msdn.microsoft.com/en-us/library/mt740629.aspx) в Windows входит в состав [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md). При работе с SQL Server, следует всегда использовать последнюю версию SSMS и SQL PowerShell. Последнюю версию SSMS постоянно обновляется и оптимизированы и в настоящее время работает с SQL Server 2017 в Linux. Чтобы загрузить и установить последнюю версию, в разделе [загрузка SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Быть в курсе событий, последняя версия SSMS предлагает при наличии доступного для загрузки новой версии.

## <a name="before-you-begin"></a>Перед началом

Чтение [известные проблемы](sql-server-linux-release-notes.md) для SQL Server 2017 г. в Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Запустите PowerShell и импорт *sqlserver* модуля

Давайте начнем путем запуска PowerShell в Windows. Откройте *командной строки* на компьютере Windows и тип **PowerShell** для запуска нового сеанса Windows PowerShell.

```
PowerShell
```

SQL Server предоставляет модуль Windows PowerShell с именем **SqlServer** , можно использовать для импорта компонентов SQL Server (SQL Server поставщика и командлетов) в среде PowerShell или скрипт.

Скопируйте и вставьте следующую команду в командной строке PowerShell для импорта **SqlServer** модуля в текущем сеансе PowerShell:

```powershell
Import-Module SqlServer
```

Введите следующую команду в командной строке PowerShell, чтобы убедиться, что **SqlServer** модуль был импортирован правильно:

```powershell
Get-Module -Name SqlServer
```

PowerShell следует отображать информацию, аналогичную следующие данные:

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     0.0        SqlServer
Manifest   20.0       SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Подключение к SQL Server и получить сведения о сервере

Воспользуемся PowerShell в Windows для подключения к экземпляру 2017 г. SQL Server в Linux и отобразить несколько свойств сервера.

Скопируйте и вставьте следующие команды в командной строке PowerShell. При выполнении этих команд PowerShell выполняет следующие действия:
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, которое запрашивает учетные данные (*имя пользователя SQL* и *пароль SQL*) для подключения к вашей 2017 г. SQL Server экземпляр в Linux
- Загружать сборки управляющих объектов SQL Server (SMO)
- Создайте экземпляр класса [сервера](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.smo.server.aspx) объекта
- Подключиться к **сервера** и отобразить несколько свойств

Не забудьте заменить **\<your_server_instance\>** с IP-адрес или имя узла экземпляра 2017 г. SQL Server в Linux.

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

PowerShell следует отображать информацию, аналогичную следующие данные:

```
Edition          : Developer Edition (64-bit)
HostPlatform     : Linux
HostDistribution : Ubuntu
```
> [!NOTE]
> Если ничего не отображается для этих значений, скорее всего ошибка подключения к целевому экземпляру SQL Server. Убедитесь в том, можно использовать одни сведения о подключении для подключения из среды SQL Server Management Studio. Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="examine-sql-server-error-logs"></a>Проверьте журналы ошибок SQL Server

Давайте PowerShell в Windows, чтобы проверить журналы ошибок подключения на экземпляре 2017 г. SQL Server в Linux. Мы будем использовать **Out-GridView** журналы для отображения сведений из-за ошибки в показано представление сетки.

Скопируйте и вставьте следующие команды в командной строке PowerShell. Они может занять несколько минут. Эти команды выполните следующие действия.
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, которое запрашивает учетные данные (*имя пользователя SQL* и *пароль SQL*) для подключения к вашей 2017 г. SQL Server экземпляр в Linux
- Используйте **Get SqlErrorLog** журналы, чтобы соединиться с экземпляром 2017 г. SQL Server в Linux и получает ошибку с момента **за вчерашний день**
- Выходные данные для **Out-GridView** командлета

Не забудьте заменить **\<your_server_instance\>** с IP-адрес или имя узла экземпляра 2017 г. SQL Server в Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>См. также:
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
