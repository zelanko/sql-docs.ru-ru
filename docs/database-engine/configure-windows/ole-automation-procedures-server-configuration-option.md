---
title: Параметр конфигурации сервера "Ole Automation Procedures" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cb13d9b50c78ff3d067d97b2d5dd1b763e024608
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67997962"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>Параметр конфигурации сервера «Ole Automation Procedures»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  C помощью параметра **Ole Automation Procedures** можно указать возможность создания экземпляров объектов OLE-автоматизации в пакетах [!INCLUDE[tsql](../../includes/tsql-md.md)] . Этот параметр также можно настроить с помощью управления на основе политики или с помощью хранимой процедуры **sp_configure** . Дополнительные сведения см. в разделе [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 Параметр **Ole Automation Procedures** может принимать следующие значения:  
  
 0  
 Процедуры OLE-автоматизации отключены. По умолчанию для новых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 Процедуры OLE-автоматизации включены.  
  
 После включения процедур OLE-автоматизации процедура **sp_OACreate** запустит общую среду выполнения OLE.  
  
 Текущее значение параметра **Ole Automation Procedures** можно просмотреть и изменить с помощью системной хранимой процедуры **sp_configure** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показан просмотр текущего значения параметра OLE Automation procedures.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 В следующем примере показано включение процедур OLE-автоматизации.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
