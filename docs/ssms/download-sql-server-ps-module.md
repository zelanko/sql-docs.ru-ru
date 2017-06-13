---
title: "Загрузите модуль PowerShell для SQL Server | Документы Microsoft"
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
- "Установка компонентов sql server powershell, загрузить sql server powershell"
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: ru-ru
ms.lasthandoff: 04/26/2017

---
# <a name="download-sql-server-powershell-module"></a>Загрузите модуль PowerShell для SQL Server
Модуль SQL Server PowerShell как часть 17,0 выпуска SQL Server Management Studio, теперь поставляется через коллекцию PowerShell.  Модуль больше не включены в пакет установки SSMS. Чтобы использовать PowerShell с помощью SSMS 17.0 и более поздних, модуль SQL Server должен быть установлен на компьютере как дополнительный шаг.

Полная документация по установке последней версии Windows Management Framework и как установить модули PowerShell обычно можно найти на [коллекции PowerShell](https://www.powershellgallery.com/) сайта.

— Команды PowerShell, чтобы установить модуль SQL Server:

> Install-module-Name SqlServer-области CurrentUser

Если предыдущих версий SQL Server PowerShell модулей на компьютере, может оказаться необходимым для предоставления «-AllowClobber» параметра.  

Модуль SQL Server PowerShell, поставляемых в коллекции PowerShell поддерживают управление версиями и требуется PowerShell версии 5.0 или более поздней.

