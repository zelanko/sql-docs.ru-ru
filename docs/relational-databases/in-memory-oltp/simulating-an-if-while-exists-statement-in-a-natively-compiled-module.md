---
title: Имитация инструкции IF-WHILE EXISTS в модуле, скомпилированном в собственном коде | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ba51c9b18d41dcbb0313fe6b9f7814678e50a3f9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>Имитация инструкции IF-WHILE EXISTS в модуле, скомпилированном в собственном коде
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Скомпилированные в собственном коде хранимые процедуры не поддерживают предложение **EXISTS** в условных инструкциях, таких как IF и WHILE.  
  
 В следующем примере показано обходное решение, заключающееся в использовании переменной BIT с инструкцией SELECT для имитации предложения EXISTS:  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>См. также:  
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
