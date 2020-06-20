---
title: Параметр конфигурации сервера "Database Mail XPs" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 83e91bf5070362b1db56907a1c5b016cf816b968
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935365"
---
# <a name="database-mail-xps-server-configuration-option"></a>Параметр конфигурации сервера «Database Mail XPs»
  Используйте параметр **Расширенные хранимые процедуры компонента Database Mail** для включения компонента Database Mail на сервере. Вы можете выбрать  
  
-   **0** означает, что компонент Database Mail не доступен (по умолчанию).  
  
-   **1** означает, что компонент Database Mail доступен.  
  
 Новые настройки вступают в силу сразу же, без остановки или перезапуска сервера.  
  
 После активации компонента Database Mail необходимо настроить базу данных обслуживания почты, чтобы использовать службу Database Mail.  
  
 Настройка компонента Database Mail при помощи **мастера настройки компонента Database Mail** разрешает использование расширенных хранимых процедур компонента Database Mail в базе данных **msdb** . При использовании **мастера настройки компонента Database Mail**можно не применять пример с **sp_configure** , приведенный ниже.  
  
 Установка параметра **Database Mail XPs** в 0 не допускает запуска компонента Database Mail. Если же в момент установки параметра в 0 этот компонент уже запущен, он продолжает работать и отсылать письма до начала периода простоя, указанного в параметре **DatabaseMailExeMinimumLifeTime** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере активируются расширенные хранимые процедуры компонента Database Mail.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
