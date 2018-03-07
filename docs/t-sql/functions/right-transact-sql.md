---
title: "СПРАВА (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RIGHT_TSQL
- RIGHT
dev_langs:
- TSQL
helpviewer_keywords:
- rightmost character of expression
- RIGHT function
- character strings [SQL Server], RIGHT
ms.assetid: 43f1fe1f-aa18-47e3-ba20-e03e32254a6d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b6680078aff2e103655a94ec157371a0d09f79be
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="right-transact-sql"></a>RIGHT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает указанное число символов символьной строки справа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
RIGHT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьных или двоичных данных. *character_expression* может быть константой, переменной или столбцом. *character_expression* может иметь любой тип данных, кроме **текст** или **ntext**, который может быть неявно преобразован в **varchar** или  **nvarchar**. В противном случае используйте [ПРИВЕДЕНИЯ](../../t-sql/functions/cast-and-convert-transact-sql.md) для явного преобразования *character_expression*.  
  
 *integer_expression*  
 Положительное целое число, указывающее, сколько символов *character_expression* будут возвращены. Если *integer_expression* имеет отрицательное значение, возвращается сообщение об ошибке. Если *integer_expression* — тип **bigint** и содержит большое значение *character_expression* должен быть типа больших объемов данных, например **varchar(max)**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает **varchar** при *character_expression* имеет символьный тип данных не в Юникоде.  
  
 Возвращает **nvarchar** при *character_expression* имеет символьный тип данных Юникода.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 При использовании параметров сортировки SC функция Right рассматривает суррогатную пару UTF-16 как один символ. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-right-with-a-column"></a>Ответ с помощью СПРАВА, со столбцом  
 В следующем примере возвращаются пять правых символов от имени каждого из людей в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT RIGHT(FirstName, 5) AS 'First Name'  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
First Name  
----------  
Ken  
Terri  
berto  
Rob  
  
(4 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-right-with-a-column"></a>Б. С помощью СПРАВА, со столбцом  
 В следующем примере возвращается пять правых символов от каждого фамилию в `DimEmployee` таблицы.  
  
```  
-- Uses AdventureWorks  
  
SELECT RIGHT(LastName, 5) AS Name  
FROM dbo.DimEmployee  
ORDER BY EmployeeKey;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
 ```
Name
-----
lbert
Brown
rello
lters
 ```  
  
### <a name="c-using-right-with-a-character-string"></a>В. С помощью вправо с символьной строкой  
 В следующем примере используется `RIGHT` для возврата две правых символов символьной строки `abcdefg`.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) RIGHT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-------  
fg
```  
  
## <a name="see-also"></a>См. также  
 [Левый &#40; Transact-SQL &#41;](../../t-sql/functions/left-transact-sql.md)  
 [Функция LTRIM &#40; Transact-SQL &#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RTRIM &#40; Transact-SQL &#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40; Transact-SQL &#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [ПОДСТРОКА &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
 [Функция TRIM &#40; Transact-SQL &#41;](../../t-sql/functions/trim-transact-sql.md)  
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

