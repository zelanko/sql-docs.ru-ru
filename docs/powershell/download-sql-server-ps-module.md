---
title: Загрузка модуля PowerShell (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 10/08/2018
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
ms.openlocfilehash: 40873fe63b897da52fc9a7d440a8568872431d72
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851759"
---
# <a name="install-sql-server-powershell-module"></a>Установка модуля SQL Server PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Эта статья содержит инструкции по установке модуля **SqlServer** PowerShell.
> [!NOTE]
> Существует два модуля PowerShell SQL Server. 
> * Модуль **SQLPS** входит в состав установки SQL Server (для обеспечения обратной совместимости), но больше не обновляется. Самым актуальным модулем PowerShell является модуль **SqlServer**.
> * Модуль **SqlServer** содержит новые командлеты для поддержки новейших функций SQL. Этот модуль также содержит обновленные версии командлетов в **SQLPS**. 

Предыдущие версии модуля **SqlServer** *входили* в состав среды SQL Server Management Studio (SSMS), но только с SSMS версий 16.x. Для работы PowerShell с SSMS 17.0 и более поздних версий необходимо установить модуль **SqlServer** из [коллекции PowerShell](https://www.powershellgallery.com/packages/Sqlserver).
Текущая версия модуля **SqlServer** — 21.0.17279. Она построена на версии v140 Microsoft.SQLServer.SMO.  
Если вы ищете версию модуля, которая поддерживает следующую версию SQL Server (на основе версии v150 Microsoft.SQLServer.SMO), см. в разделе внизу этой страницы сведения о том, как получить предварительные версии модуля. Последняя предварительная версия модуля — 21.1.18040-preview.

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

> [!NOTE]
> Предварительные (или "preview") версии модуля могут быть доступны в коллекции PowerShell. Их можно найти и установить с помощью обновленных командлетов *Find-Module* и *Install-Module*, которые входят в модуль [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet), передав параметр *-AllowPrerelease*.
>
> Чтобы найти предварительный выпуск или предварительную версию модуля, выполните следующую команду:
>
> ```Find-Module SqlServer -AllowPrerelease```
>
> Чтобы установить конкретную предварительную версию или предварительный выпуск модуля, укажите при установке конкретный номер версии, как показано далее.
>
> ```Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease```
> 

Версии модуля **SqlServer** PowerShell в коллекции PowerShell поддерживают управление версиями и требуют PowerShell 5.0 или более поздней версии. 

* [Модуль SqlServer в коллекции PowerShell](https://www.powershellgallery.com/packages/Sqlserver) 
* [Командлеты SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
* [Командлеты SQLPS](https://docs.microsoft.com/powershell/module/sqlps)
