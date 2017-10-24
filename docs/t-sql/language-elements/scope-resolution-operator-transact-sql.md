---
title: "Оператор разрешения (Transact-SQL) области | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
dev_langs:
- TSQL
ms.assetid: 764d8f91-957b-4037-997b-a9b6b533c504
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f03f0c8274d52f61e5db2d75fe21e3fe90a4ce26
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="scope-resolution-operator-transact-sql"></a>Оператор разрешения области (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Оператор разрешения области **::** предоставляет доступ к статическим элементам составного типа данных. Составной тип данных содержит несколько простых типов данных и методов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как применять оператор разрешения области для доступа к элементу `GetRoot()` типа данных `hierarchyid`.  
  
```  
DECLARE @hid hierarchyid;  
SELECT @hid = hierarchyid::GetRoot();  
PRINT @hid.ToString();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `/`  
  
## <a name="see-also"></a>См. также:  
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

