---
title: Параметр конфигурации сервера "xp_cmdshell" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6d403205c3fc3ef57fcfa7e566f0913f00604862
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="xpcmdshell-server-configuration-option"></a>Параметр конфигурации сервера «xp_cmdshell»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **xp_cmdshell** — это параметр конфигурации сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который позволяет системным администраторам контролировать, можно ли выполнять в системе расширенную хранимую процедуру **xp_cmdshell** . По умолчанию параметр **xp_cmdshell** отключен в новых установках. Перед его включением важно учесть возможные проблемы безопасности, связанные с использованием этого параметра. В новом коде этот параметр не используется, так как обычно он отключен. Его требуется включать в некоторых нерекомендуемых приложениях. Если этого невозможно избежать, можно включить параметр с помощью управления на основе политик или путем запуска хранимой процедуры системы **sp_configure**, как показано в следующем примере кода.  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
