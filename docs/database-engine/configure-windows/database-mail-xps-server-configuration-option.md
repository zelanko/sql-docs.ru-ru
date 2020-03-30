---
title: Параметр конфигурации сервера "Database Mail XPs" | Документы Майкрософт
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e16286e558d860a346ba8fff366009f064e65f91
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68011958"
---
# <a name="database-mail-xps-server-configuration-option"></a>Параметр конфигурации сервера «Database Mail XPs»

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Используйте параметр **Расширенные хранимые процедуры компонента Database Mail** для включения компонента Database Mail на сервере. Вы можете выбрать  
  
- `0`: компонент Database Mail не доступен (по умолчанию).  
  
- `1`: компонент Database Mail доступен.  
  
 Новые настройки вступают в силу сразу же, без остановки или перезапуска сервера.  
  
 После активации компонента Database Mail необходимо настроить базу данных обслуживания почты, чтобы использовать службу Database Mail.  
  
 Настройка компонента Database Mail при помощи **мастера настройки компонента Database Mail** разрешает использование расширенных хранимых процедур компонента Database Mail в базе данных `msdb`. При использовании **мастера настройки компонента Database Mail** можно не применять пример с `sp_configure`, приведенный ниже.  
  
 Установка параметра **Database Mail XPs** в значение `0` не допускает запуска компонента Database Mail. Если же в момент установки параметра в значение `0` этот компонент уже запущен, он продолжает работать и отсылать письма до начала периода простоя, указанного в параметре `DatabaseMailExeMinimumLifeTime`.  
  
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

В следующем примере активируются расширенные хранимые процедуры компонента Database Mail, если они еще не включены.

```sql
IF EXISTS (
    SELECT 1 FROM sys.configurations 
    WHERE NAME = 'Database Mail XPs' AND VALUE = 0)
BEGIN
  PRINT 'Enabling Database Mail XPs'
  EXEC sp_configure 'show advanced options', 1;  
  RECONFIGURE
  EXEC sp_configure 'Database Mail XPs', 1;  
  RECONFIGURE  
END
```

## <a name="see-also"></a>См. также:
[Database Mail](../../relational-databases/database-mail/database-mail.md)  
