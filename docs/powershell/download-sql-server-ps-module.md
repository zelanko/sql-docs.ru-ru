---
title: Загрузка модуля PowerShell (SQL Server)
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.custom: ''
ms.date: 01/23/2020
ms.openlocfilehash: 99976a12ae76254da5b50c5467df9d9e42fdbbce
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "76920349"
---
# <a name="install-the-sql-server-powershell-module"></a>Установка модуля SQL Server PowerShell

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Эта статья содержит инструкции по установке модуля **SqlServer** PowerShell.

## <a name="powershell-modules-for-sql-server"></a>Модули PowerShell для SQL Server

Существует два модуля PowerShell SQL Server.

- **SqlServer**. Модуль SqlServer содержит новые командлеты для поддержки новейших функций SQL. Этот модуль также содержит обновленные версии командлетов в **SQLPS**. Чтобы скачать модуль SqlServer, перейдите к странице [модуля SqlServer в коллекции PowerShell](https://www.powershellgallery.com/packages/Sqlserver).
- **SQLPS**. Модуль SQLPS входит в состав установки SQL Server (для обеспечения обратной совместимости), но больше не обновляется. Самым актуальным модулем PowerShell является модуль **SqlServer**.

> [!NOTE]
> Версии модуля **SqlServer** PowerShell в коллекции PowerShell поддерживают управление версиями и требуют PowerShell 5.0 или более поздней версии.

Разделы справки можно найти здесь:

- Командлеты [SqlServer](https://docs.microsoft.com/powershell/module/sqlserver).
- Командлеты [SQLPS](https://docs.microsoft.com/powershell/module/sqlps).

## <a name="sql-server-management-studio"></a>SQL Server Management Studio

SQL Server Management Studio (SSMS), начиная с версии 17.0, не устанавливает ни один из модулей PowerShell. Для работы PowerShell с SSMS установите модуль **SqlServer** из [коллекции PowerShell](https://www.powershellgallery.com/packages/Sqlserver).

> [!NOTE]
> В SQL Server Management Studio (SSMS) версии 16.x входит более ранняя версия модуля **SqlServer**.

## <a name="azure-data-studio"></a>Azure Data Studio

Azure Data Studio не устанавливает ни один из модулей PowerShell. Для работы PowerShell с Azure Data Studio установите модуль **SqlServer** из [коллекции PowerShell](https://www.powershellgallery.com/packages/Sqlserver).

Можно использовать [расширение PowerShell](../azure-data-studio/powershell-extension.md), которое обеспечивает полноценную поддержку редактора PowerShell в Azure Data Studio.

## <a name="installing-or-updating-the-sqlserver-module"></a>Установка или обновление модуля SqlServer

Чтобы установить модуль **SqlServer** из коллекции PowerShell, запустите сеанс [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting) с правами администратора. Вы также можете запустить Azure Data Studio от имени администратора и выполнить эти команды в сеансе PowerShell во встроенном терминале.

### <a name="install-the-sqlserver-module"></a>Установка модуля SqlServer

Чтобы установить модуль SqlServer для всех пользователей, выполните следующую команду в сеансе PowerShell:

```powershell
Install-Module -Name SqlServer
```

### <a name="to-view-the-versions-of-the-sqlserver-module-installed"></a>Просмотр установленных версий модуля SqlServer

Выполните следующую команду, чтобы просмотреть установленные версии модуля SqlServer.

```powershell
Get-Module SqlServer -ListAvailable
```

### <a name="install-for-the-current-user-rather-than-as-an-administrator"></a>Установка для текущего пользователя (не администратора)

Если не удается запустить сеанс PowerShell от имени администратора, можно выполнить установку для текущего пользователя, используя следующую команду:

```powershell
Install-Module -Name SqlServer -Scope CurrentUser
```

### <a name="to-overwrite-a-previous-version-of-the-sqlserver-module"></a>Перезапись предыдущей версии модуля SqlServer

Вы можете перезаписать предыдущую версию с помощью команды `Install-Module`.

```powershell
Install-Module -Name SqlServer -AllowClobber
```

> [!Note]
> PowerShell всегда использует последний установленный модуль.

### <a name="update-the-installed-version-of-the-sqlserver-module"></a>Обновление установленной версии модуля SqlServer

Если доступны обновленные версии модуля **SqlServer**, можно установить более новую версию с помощью следующей команды:

```powershell
Install-Module -Name SqlServer -AllowClobber
```

Вы можете использовать команду `Update-Module`, чтобы установить последнюю версию модуля SQLServer PowerShell, но это не приведет к удалению предыдущих версий. Эта команда устанавливает более новую версию параллельно, чтобы вы могли экспериментировать с последней версией, но по-прежнему иметь предыдущие модули.

Однако если вы не хотите сохранять предыдущие версии модулей, можно удалить их с помощью команды `Uninstall-Module`.

Если установлено более одной версии, можно вывести их список с помощью следующей команды:

```powershell
Get-Module SqlServer -ListAvailable
```

Чтобы удалить предыдущие версии, выполните следующую команду:

```powershell
Uninstall-module -Name SQLServer -RequiredVersion "<version number>" -AllowClobber
```

### <a name="troubleshooting"></a>Устранение неполадок

Если при установке возникли проблемы, см. [документацию по Install-Module](https://www.powershellgallery.com/packages/PowerShellGet/2.2.1) и [справочник по Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module).

## <a name="using-a-specific-version-of-the-sqlserver-module"></a>Использование конкретной версии модуля SqlServer

Чтобы использовать конкретную версию модуля, импортируйте ее с определенным номером версии, как показано в следующей команде:

```powershell
Import-Module SqlServer -Version 21.1.18080
```

## <a name="pre-release-versions-of-the-sqlserver-module"></a>Предварительные версии модуля SqlServer

Предварительные (или preview) версии модуля SqlServer могут быть доступны в коллекции PowerShell.

> [!IMPORTANT]
> Их можно найти и установить с помощью обновленных командлетов *Find-Module* и *Install-Module*, которые входят в модуль [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet), передав параметр *-AllowPrerelease*. Чтобы использовать эти командлеты, установите модуль PowerShellGet, а затем откройте новый сеанс.

### <a name="to-discover-pre-release-versions-of-the-sqlserver-module"></a>Обнаружение предварительных версий модуля SqlServer

Чтобы найти предварительные версии модуля SqlServer, выполните следующую команду:

```powershell
Find-Module SqlServer -AllowPrerelease
```

### <a name="to-install-a-specific-pre-release-version-of-the-sqlserver-module"></a>Установка конкретной предварительной версии модуля SqlServer

Чтобы установить конкретную предварительную версию модуля, укажите при установке конкретный номер версии.

Используйте для этого следующую команду:

```powershell
Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease
```

## <a name="sql-server-powershell-on-linux"></a>SQL Server PowerShell в Linux

Сведения об установке SQL Server PowerShell в Linux см. в [этой статье](../linux/sql-server-linux-manage-powershell-core.md).
