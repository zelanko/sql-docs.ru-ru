---
title: Управление SQL Server на Linux с помощью PowerShell
description: В этой статье приводятся общие сведения об использовании PowerShell в Windows для работы с SQL Server на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 52db0986bb6af34e1dc034d95146a96d3fdcf246
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68000129"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Использование PowerShell в Windows для управления SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье рассматривается модуль [SQL Server PowerShell](../powershell/sql-server-powershell.md) и приводится несколько примеров того, как можно использовать его для работы с SQL Server на Linux. На данный момент поддержка PowerShell для SQL Server реализована в Windows, MacOS и Linux. В этой статье описывается использование компьютера под управлением Windows для подключения к удаленному экземпляру SQL Server на Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Установка последней версии SQL PowerShell в Windows

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) в Windows находится в коллекции PowerShell. При работе с SQL Server следует всегда использовать последнюю версию модуля SqlServer PowerShell.

## <a name="before-you-begin"></a>Перед началом

Ознакомьтесь с [известными проблемами](sql-server-linux-release-notes.md), связанными с работой с SQL Server на Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Запуск PowerShell и импорт модуля *sqlserver*

Для начала запустим PowerShell в Windows. Нажмите клавиши <kbd>Win</kbd>+<kbd>R</kbd> на компьютере под управлением Windows и введите **PowerShell**, чтобы запустить новый сеанс Windows PowerShell.

```
PowerShell
```

В SQL Server представлен модуль PowerShell под названием **SqlServer**. Вы можете использовать модуль **SqlServer** для импорта компонентов SQL Server (поставщик и командлеты SQL Server) в скрипт или среду PowerShell.

Скопируйте следующую команду и вставьте ее в командную строку PowerShell, чтобы импортировать модуль **SqlServer** в текущий сеанс PowerShell:

```powershell
Import-Module SqlServer
```

Введите следующую команду в командной строке PowerShell, чтобы убедиться в том, что модуль **SqlServer** был импортирован правильно:

```powershell
Get-Module -Name SqlServer
```

В PowerShell должны отображаться данные примерно следующего вида:

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     21.1.18102 SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Подключение к SQL Server и получение сведений о сервере

Теперь мы используем PowerShell в Windows для подключения к вашему экземпляру SQL Server на Linux и просмотра некоторых свойств сервера.

Скопируйте следующие команды и вставьте их в командную строку PowerShell. При запуске этих команд в PowerShell будут выполнены следующие действия:
- Отображение диалогового окна с запросом на ввод имени узла и IP-адреса экземпляра
- Откройте диалоговое окно *Запрос учетных данных Windows PowerShell*, в котором необходимо ввести соответствующие сведения. Для подключения к экземпляру SQL Server на Linux вы можете использовать свои *имя пользователя SQL* и *пароль SQL*
- Использование командлета **Get-SqlInstance** для подключения к **серверу** и просмотра некоторых свойств

При необходимости можно заменить переменную `$serverInstance` IP-адресом или именем узла вашего экземпляра SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Connect to the Server and get a few properties
Get-SqlInstance -ServerInstance $serverInstance -Credential $credential
# done
```

В PowerShell должны отображаться данные примерно следующего вида:

```
Instance Name                   Version    ProductLevel UpdateLevel  HostPlatform HostDistribution                
-------------                   -------    ------------ -----------  ------------ ----------------                
your_server_instance            14.0.3048  RTM          CU13         Linux        Ubuntu 
```
> [!NOTE]
> Если эти значения не отображаются, скорее всего, подключение к целевому экземпляру SQL Server установить не удалось. Убедитесь в том, что эти же данные можно использовать для подключения из SQL Server Management Studio. Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="using-the-sql-server-powershell-provider"></a>Использование поставщика SQL Server для PowerShell

В качестве альтернативы для подключения к экземпляру SQL Server можно использовать [поставщик SQL Server PowerShell](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).  Этот поставщик позволяет работать с экземпляром SQL Server из командной строки так же, как с древовидной структурой в обозревателе объектов.  По умолчанию этот поставщик представлен в виде диска PSDrive с именем `SQLSERVER:\`, который может использоваться для подключения к экземплярам SQL Server, доступным вашей учетной записи домена, и работы с ними.  Дополнительные сведения о настройке проверки подлинности Active Directory для SQL Server на Linux см. в разделе [Шаги настройки](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps).

Также вы можете использовать проверку подлинности SQL в поставщике SQL Server PowerShell. Для этого с помощью командлета `New-PSDrive` создайте новый диск PSDrive и укажите учетные данные для подключения.

В приведенном ниже примере демонстрируется создание нового диска PSDrive с использованием проверки подлинности SQL.

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.
New-PSDrive -Name SQLonDocker -PSProvider SqlServer -Root 'SQLSERVER:\SQL\localhost,10002\Default\' -Credential $credential
```

Чтобы убедиться в том, что диск был создан, выполните командлет `Get-PSDrive`.

```powershell
Get-PSDrive
```

После создания нового диска PSDrive вы можете начать работу с ним.

```powershell
dir SQLonDocker:\Databases
```

Выходные данные могут выглядеть следующим образом.  Обратите внимание, что эти данные аналогичны тем, которые SSMS отображает в узле "Базы данных".  В нем представлены пользовательские, а не системные базы данных.

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

Чтобы просмотреть все базы данных в вашем экземпляре, можно использовать командлет [Get-SqlDatabase](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlDatabase).

## <a name="examine-sql-server-error-logs"></a>Проверка журналов ошибок SQL Server

Далее описывается использование PowerShell в Windows для проверки журналов ошибок подключения в вашем экземпляре SQL Server на Linux. Кроме того, мы будем использовать командлет **Out-GridView** для просмотра журналов ошибок в представлении сетки.

Скопируйте следующие команды и вставьте их в командную строку PowerShell. Это может занять несколько минут. Эти команды выполняют следующие действия:
- Отображение диалогового окна с запросом на ввод имени узла и IP-адреса экземпляра
- Откройте диалоговое окно *Запрос учетных данных Windows PowerShell*, в котором необходимо ввести соответствующие сведения. Для подключения к экземпляру SQL Server на Linux вы можете использовать свои *имя пользователя SQL* и *пароль SQL*
- Использование командлета **Get-SqlErrorLog** для подключения к экземпляру SQL Server на Linux и извлечения журналов ошибок, обнаруженных со **вчерашнего дня**
- Передача выходных данных в командлет **Out-GridView**

При необходимости можно заменить переменную `$serverInstance` IP-адресом или именем узла вашего экземпляра SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>См. также раздел
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
- [Командлеты SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
