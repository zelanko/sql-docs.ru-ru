---
title: Имитация предложения EXISTs в скомпилированной в собственном код хранимой процедуре | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b16491b9a3729ad4df71c7ddceaee6db21777ff
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049950"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>Имитация предложения EXISTS в скомпилированной в собственном коде хранимой процедуре
  Скомпилированные в собственном коде хранимые процедуры не поддерживают предложение `EXISTS`, однако эту проблему можно решить:  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>См. также:  
 [Проблемы миграции для хранимых процедур, скомпилированных в собственном виде](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
