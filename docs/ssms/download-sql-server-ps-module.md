---
title: "Загрузка модуля PowerShell (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords: "установка компонентов SQL Server PowerShell, загрузка компонентов SQL Server PowerShell"
ms.assetid: 
caps.latest.revision: "113"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 83b535f97682334f6a83f3eb58e2f673c2040b4c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="download-sql-server-powershell-module"></a>Загрузка модуля PowerShell (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]Модуль SQL Server PowerShell теперь поставляется через коллекцию PowerShell как часть выпуска SQL Server Management Studio 17.0.  В пакет установки SSMS этот модуль больше не входит. Чтобы использовать PowerShell с SSMS 17.0 и более поздних версий, необходимо дополнительно установить на компьютер модуль SQL Server.

Полную документацию по установке последней версии Windows Management Framework и общие инструкции по установке модулей PowerShell можно найти на веб-сайте [Коллекция PowerShell](https://www.powershellgallery.com/).

Команда PowerShell для установки модуля SQL Server:

> Install-Module -Name SqlServer

Эта команда устанавливает модуль для всех пользователей компьютера. Процесс PowerShell должен быть запущен от имени администратора.

> Install-Module -Name SqlServer -Scope CurrentUser

Эта команда устанавливает модуль для пользователя, выполняющего текущий процесс PowerShell. Процесс PowerShell не требуется выполнять с правами администратора.

Если на компьютере присутствуют предыдущие версии модулей SQL Server PowerShell, может также потребоваться указание параметра "-AllowClobber".  

При запуске от имени администратора и для установки модуля для всех пользователей компьютера:

> Install-Module -Name SqlServer -AllowClobber

Если запуск от имени администратора невозможен либо для установки только для текущего пользователя

> Install-Module -Name SqlServer -Scope CurrentUser -AllowClobber

Если доступны обновленные версии модуля SqlServer, вы сможете обновить версию с помощью команды Update-Module.

> Update-Module -Name SqlServer

Для просмотра версий модуля, установленных на компьютере и доступных для использования:

> Get-Module SqlServer -ListAvailable

Чтобы использовать конкретную версию модуля в скриптах, можно импортировать ее с помощью команды:

> Import-Module SqlServer -Version 21.0.17178

Версии модуля SQL Server PowerShell, предоставляемые в коллекции PowerShell, поддерживают управление версиями и требуют PowerShell 5.0 или более поздней версии. Модуль SqlServer можно найти в [коллекции PowerShell](https://www.powershellgallery.com/packages/Sqlserver/) 
