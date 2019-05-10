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
ms.openlocfilehash: 73d9780e2980eeecf49cf420901e7e6f1dc4a669
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089372"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Управление SQL Server в Linux с помощью PowerShell в Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье рассматриваются [SQL Server PowerShell](../powershell/sql-server-powershell.md) и о том, как использовать его в SQL Server в Linux описывается несколько примеров. Поддержка PowerShell для SQL Server в настоящее время доступна в Windows, MacOS и Linux. В этой статье описывается с помощью компьютера Windows для подключения к удаленному экземпляру SQL Server в Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Установите последнюю версию SQL PowerShell на Windows

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) в Windows сохраняется в коллекции PowerShell. При работе с SQL Server, следует всегда использовать последнюю версию модуля SqlServer PowerShell.

## <a name="before-you-begin"></a>Перед началом

Чтение [известные проблемы](sql-server-linux-release-notes.md) для SQL Server в Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Запустите PowerShell и импортируйте *sqlserver* модуля

Давайте сперва запустите PowerShell на Windows. Используйте <kbd>выиграть</kbd>+<kbd>R</kbd>, на компьютере Windows и тип **PowerShell** запустить новый сеанс Windows PowerShell.

```
PowerShell
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

Давайте использовать PowerShell в Windows для подключения к экземпляру SQL Server в Linux и отобразить несколько свойств сервера.

Скопируйте и вставьте следующие команды в командной строке PowerShell. При выполнении этих команд PowerShell выполняются следующие действия:
- Отображает диалоговое окно с приглашением для имени узла или IP-адрес экземпляра
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, в котором будет предложено ввести учетные данные. Можно использовать ваши *имя пользователя SQL* и *пароль SQL* для подключения к экземпляру SQL Server в Linux
- Используйте **Get-SqlInstance** для подключения к **Server** и отобразить несколько свойств

При необходимости вы можете просто подставить `$serverInstance` переменной с IP-адрес или имя узла экземпляра SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
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

## <a name="using-the-sql-server-powershell-provider"></a>Использование поставщика SQL Server PowerShell

Другой вариант для подключения к экземпляру SQL Server является использование [поставщик SQL Server PowerShell](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).  Этот поставщик позволяет переходить экземпляр SQL Server, аналогичную так, как если бы вы Навигация по структуре дерева в обозревателе объектов, но в командную строку.  По умолчанию этот поставщик будет представлено как с именем PSDrive `SQLSERVER:\` которого можно использовать для подключения & ведет экземпляров SQL Server, к которым имеет доступ учетная запись домена.  См. в разделе [действия по настройке](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps) сведения о способах настройки проверки подлинности Active Directory для SQL Server в Linux.

Можно также использовать проверку подлинности SQL с помощью поставщика SQL Server PowerShell. Чтобы сделать это, используйте `New-PSDrive` командлет, чтобы создать новый PSDrive и задать соответствующие учетные данные для подключения.

В этом примере вы увидите один пример того, как создать новый PSDrive, используя проверку подлинности SQL.

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

Вот, как может выглядеть выходные данные.  Можно заметить, что результат аналогичен приведенному SSMS будет отображаться в узле базы данных.  Он отображает пользовательские базы данных, но не системных баз данных.

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

Если вам нужно увидеть все базы данных в экземпляре, один из вариантов является использование [Get-SqlDatabase](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlDatabase) командлета.

## <a name="examine-sql-server-error-logs"></a>Проверьте журналы ошибок SQL Server

Далее используется PowerShell на Windows для проверки ошибок, к которым подключаются журналы в экземпляре SQL Server в Linux. Мы также будем использовать **Out-GridView** регистрирует для отображения сведений из-за ошибки в окне представления сетки.

Скопируйте и вставьте следующие команды в командной строке PowerShell. Они может занять несколько минут. Эти команды выполняют следующее:
- Отображает диалоговое окно с приглашением для имени узла или IP-адрес экземпляра
- Отображение *запрос учетных данных Windows PowerShell* диалоговое окно, в котором будет предложено ввести учетные данные. Можно использовать ваши *имя пользователя SQL* и *пароль SQL* для подключения к экземпляру SQL Server в Linux
- Используйте **Get-SqlErrorLog** командлет для подключения к экземпляру SQL Server в Linux и получения ошибки журналы с момента **вчера**
- Выходные данные для **Out-GridView** командлета

При необходимости можно заменить `$serverInstance` переменной с IP-адрес или имя узла экземпляра SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>См. также
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
- [Командлеты SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
