---
title: Имитация предложения EXISTS в скомпилированной хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ed6265a67d32407b22c14f9f6b2b850a1421915
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281080"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>Имитация предложения EXISTS в скомпилированной в собственном коде хранимой процедуре
  Скомпилированные в собственном коде хранимые процедуры не поддерживают предложение `EXISTS`, однако эту проблему можно решить:  
  
```tsql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>См. также  
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
