---
title: "Параметр конфигурации сервера \"SMO and DMO XPs\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 26b79d125d64a1c262c28b71d4c17bbc1824bf6f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>Параметр конфигурации сервера «SMO and DMO XPs»
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  С помощью параметра «SMO and DMO XPs» включите расширенные хранимые процедуры управляющих объектов (SMO) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом сервере.  
  
 Обратите внимание, что, начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], объекты DMO были удалены из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Возможные значения описаны в следующей таблице:  
  
|Значение|Значение|  
|-----------|-------------|  
|0|Расширенные хранимые процедуры объектов SMO недоступны.|  
|1|Расширенные хранимые процедуры объектов SMO доступны. Это значение по умолчанию.|  
  
 Изменение этой настройки вступает в силу немедленно.  
  
## <a name="examples"></a>Примеры  
 В следующем примере активируются расширенные хранимые процедуры объектов SMO.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Учебник по программированию управляющих объектов SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
