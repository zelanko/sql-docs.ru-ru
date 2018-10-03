---
title: Загрузка модуля PowerShell (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 01/05/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
keywords:
- установка компонентов SQL Server PowerShell, загрузка компонентов SQL Server PowerShell
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d41d03c3bba51b919a71f195de75a7ec29f51b7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621562"
---
# <a name="install-sql-server-powershell-module"></a>Установка модуля SQL Server PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Эта статья содержит инструкции по установке модуля **SqlServer** PowerShell.

> [!NOTE]
> Существует два модуля SQL Server PowerShell — **SqlServer** и **SQLPS**. Модуль **SQLPS** входит в состав установки SQL Server (для обеспечения обратной совместимости), но больше не обновляется. Самым актуальным модулем PowerShell является модуль **SqlServer**. Модуль **SqlServer** содержит обновленные версии командлетов в **SQLPS**, а также новые командлеты для поддержки последних функций SQL. Предыдущие версии модуля **SqlServer** *входили* в состав среды SQL Server Management Studio (SSMS), но только с SSMS версий 16.x. Для работы PowerShell с SSMS 17.0 и более поздних версий необходимо установить модуль **SqlServer** из коллекции PowerShell.

Чтобы установить модуль **SqlServer** из коллекции PowerShell, запустите сеанс [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting) и выполните следующие команды. Если при установке возникли проблемы, см. [документацию по Install-Module](https://docs.microsoft.com/powershell/gallery/psget/module/psget_install-module) и [справочник по Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module).

Чтобы установить модуль **SqlServer**, выполните следующую команду.

```Install-Module -Name SqlServer```

Если на компьютере установлены предыдущие версии модуля **SqlServer**, воспользуйтесь командой `Update-Module` (далее в этой статье) или укажите параметр `-AllowClobber`.  

```Install-Module -Name SqlServer -AllowClobber```

Если не удается запустить сеанс PowerShell от имени администратора, можно выполнить установку для текущего пользователя.

```Install-Module -Name SqlServer -Scope CurrentUser```

Если доступны обновленные версии модуля **SqlServer**, можно обновить версию с помощью команды `Update-Module`.

```Update-Module -Name SqlServer```

Чтобы просмотреть установленные версии модуля.

```Get-Module SqlServer -ListAvailable```

Чтобы использовать конкретную версию модуля, ее можно импортировать с определенным номером версии, как показано далее.

```Import-Module SqlServer -Version 21.0.17178```


Версии модуля **SqlServer** PowerShell в коллекции PowerShell поддерживают управление версиями и требуют PowerShell 5.0 или более поздней версии. 

* [Модуль SqlServer в коллекции PowerShell](https://www.powershellgallery.com/packages/Sqlserver) 
* [Командлеты SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
* [Командлеты SQLPS](https://docs.microsoft.com/powershell/module/sqlps)
