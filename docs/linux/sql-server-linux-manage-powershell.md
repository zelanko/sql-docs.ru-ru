---
title: Управление SQL Server в Linux с помощью PowerShell | Документация Майкрософт
description: В этой статье описывается с помощью PowerShell в Windows с помощью SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 903d2d89ca0d551cbb78cfb69dd305f852f62313
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158770"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Управление SQL Server в Linux с помощью PowerShell в Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье рассматриваются [SQL Server PowerShell](../powershell/sql-server-powershell.md) и о том, как использовать его в SQL Server в Linux описывается несколько примеров. Поддержка PowerShell для SQL Server на Windows, поэтому его можно использовать, если используется компьютер Windows, который может подключиться к удаленному экземпляру SQL Server в Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Установите последнюю версию SQL PowerShell на Windows

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) в Windows сохраняется в коллекции PowerShell. При работе с SQL Server, следует всегда использовать последнюю версию модуля SqlServer PowerShell.

## <a name="before-you-begin"></a>Перед началом

Чтение [известные проблемы](sql-server-linux-release-notes.md) для SQL Server в Linux.

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
Script     21.1.18102 SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Подключиться к SQL Server и получить сведения о сервере

Давайте использовать PowerShell в Windows для подключения к экземпляру SQL Server в Linux и отобразить несколько свойств сервера.

Скопируйте и вставьте следующие команды в командной строке PowerShell. При выполнении этих команд PowerShell выполняются следующие действия:
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, которое запрашивает учетные данные (*имя пользователя SQL* и *пароль SQL*) для подключения к серверу SQL Server экземпляр в Linux
- Создайте экземпляр [Server](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.server.aspx) объекта
- Подключение к **Server** и отобразить несколько свойств

Не забудьте заменить **\<your_server_instance\>** с IP-адрес или имя узла экземпляра SQL Server в Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Connect to the Server and get a few properties
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

## <a name="examine-sql-server-error-logs"></a>Проверьте журналы ошибок SQL Server

Давайте PowerShell на Windows, чтобы проверить журналы ошибок подключения в экземпляре SQL Server в Linux. Мы также будем использовать **Out-GridView** регистрирует для отображения сведений из-за ошибки в окне представления сетки.

Скопируйте и вставьте следующие команды в командной строке PowerShell. Они может занять несколько минут. Эти команды выполняют следующее:
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, которое запрашивает учетные данные (*имя пользователя SQL* и *пароль SQL*) для подключения к серверу SQL Server экземпляр в Linux
- Используйте **Get-SqlErrorLog** командлет для подключения к экземпляру SQL Server в Linux и получения ошибки журналы с момента **вчера**
- Выходные данные для **Out-GridView** командлета

Не забудьте заменить **\<your_server_instance\>** с IP-адрес или имя узла экземпляра SQL Server в Linux.

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
