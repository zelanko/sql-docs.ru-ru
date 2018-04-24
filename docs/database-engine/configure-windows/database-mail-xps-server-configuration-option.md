---
title: Параметр конфигурации сервера "Database Mail XPs" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 13790fc4a22fbc990626161fc391786ecd7d8730
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="database-mail-xps-server-configuration-option"></a>Параметр конфигурации сервера «Database Mail XPs»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Используйте параметр **Расширенные хранимые процедуры компонента Database Mail** для включения компонента Database Mail на сервере. Возможные значения:  
  
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
  
  
