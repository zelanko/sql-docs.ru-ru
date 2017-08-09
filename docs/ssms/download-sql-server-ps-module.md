---
title: "Загрузка модуля PowerShell (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "установка компонентов SQL Server PowerShell, загрузка компонентов SQL Server PowerShell"
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="download-sql-server-powershell-module"></a>Загрузка модуля PowerShell (SQL Server)
Модуль SQL Server PowerShell теперь поставляется через коллекцию PowerShell как часть выпуска SQL Server Management Studio 17.0.  В пакет установки SSMS этот модуль больше не входит. Чтобы использовать PowerShell с SSMS 17.0 и более поздних версий, необходимо дополнительно установить на компьютер модуль SQL Server.

Полную документацию по установке последней версии Windows Management Framework и общие инструкции по установке модулей PowerShell можно найти на веб-сайте [Коллекция PowerShell](https://www.powershellgallery.com/).

Команда PowerShell для установки модуля SQL Server:

> Install-module -Name SqlServer -Scope CurrentUser

Если на компьютере присутствуют предыдущие версии модулей SQL Server PowerShell, может также потребоваться указание параметра "-AllowClobber".  

Версии модуля SQL Server PowerShell, предоставляемые в коллекции PowerShell, поддерживают управление версиями и требуют PowerShell 5.0 или более поздней версии.

