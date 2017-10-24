---
title: "ПРОБЕЛ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SPACE_TSQL
- SPACE
dev_langs:
- TSQL
helpviewer_keywords:
- strings [SQL Server], repeated spaces
- repeated spaces
- SPACE function
ms.assetid: b4fac3b8-2d47-4c11-a6a6-009e5a538f40
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f5de41d3d7619af5f83fa2bee8cd30f980f291b7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="space-transact-sql"></a>SPACE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строку пробелов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SPACE ( integer_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *integer_expression*  
 Положительное целое число, определяющее количество пробелов в строке. Если *integer_expression* имеет отрицательное значение, возвращается пустая строка.  
  
 Дополнительные сведения см. в разделе [выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varchar**  
  
## <a name="remarks"></a>Замечания  
 Чтобы включить в строку пробелы в формате Юникод или возвратить более 8000 пробелов, используйте вместо функции SPACE функцию REPLICATE.  
  
## <a name="examples"></a>Примеры  
 Следующий пример исключает пробелы из фамилий людей, указанных в таблице `Person` базы данных `AdventureWorks2012`, и дополняет их фамилии запятой, двумя пробелами и именами.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM Person.Person  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример исключает пробелы из фамилий людей, указанных в таблице `DimCustomer` базы данных `AdventureWorksPDW2012`, и дополняет их фамилии запятой, двумя пробелами и именами.  
  
```  
-- Uses AdventureWorks  
  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM dbo.DimCustomer  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [REPLICATE &#40; Transact-SQL &#41;](../../t-sql/functions/replicate-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  



