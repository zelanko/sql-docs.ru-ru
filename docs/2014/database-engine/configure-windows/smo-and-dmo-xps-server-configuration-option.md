---
title: Параметр конфигурации сервера "SMO and DMO XPs" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fe06dd6034c8ada7c5b702655304fc245bb9d8b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189578"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>Параметр конфигурации сервера «SMO and DMO XPs»
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
  
## <a name="see-also"></a>См. также  
 [Учебник по программированию управляющих объектов SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  