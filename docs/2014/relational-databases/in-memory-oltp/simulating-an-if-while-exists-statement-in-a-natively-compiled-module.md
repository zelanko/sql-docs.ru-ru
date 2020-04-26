---
title: Имитация предложения EXISTs в скомпилированной в собственном код хранимой процедуре | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac041e19aeb5948a644a9fcf82b3e687472b7259
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "62468297"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>Имитация предложения EXISTS в скомпилированной в собственном коде хранимой процедуре
  Скомпилированные в собственном коде хранимые процедуры не поддерживают предложение `EXISTS`, однако эту проблему можно решить:  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>См. также  
 [Проблемы миграции для хранимых процедур, скомпилированных в собственном виде](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
