---
title: Параметр конфигурации сервера "xp_cmdshell" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5db62cf5c549d4bfbea98a6584f91171bd93afa7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192284"
---
# <a name="xpcmdshell-server-configuration-option"></a>Параметр конфигурации сервера «xp_cmdshell»
  Параметр **xp_cmdshell** — это параметр конфигурации сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который позволяет системным администраторам контролировать, можно ли выполнять в системе расширенную хранимую процедуру **xp_cmdshell** . По умолчанию в новых установках параметр **xp_cmdshell** отключен и может быть включен с помощью управления на основе политики или путем выполнения системной хранимой процедуры **sp_configure** , как показано в следующем примере кода:  
  
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
  
## <a name="see-also"></a>См. также  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  