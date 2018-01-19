---
title: "Функция LEN (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LEN
- LEN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- LEN function
- characters [SQL Server], number of
- number of characters
ms.assetid: fa20fee4-884d-4301-891a-c03e901345ae
caps.latest.revision: "47"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4f81bca5986279d53ea1fce44c50ab400ad03d50
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="len-transact-sql"></a>LEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает количество символов указанного строкового выражения, исключая конечные пробелы.  
  
> [!NOTE]  
>  Получить число байтов, используемых для представления выражения, с помощью [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md) функции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
LEN ( string_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *string_expression*  
 Строка, [выражение](../../t-sql/language-elements/expressions-transact-sql.md) для оценки. *String_Expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **bigint** Если *выражение* имеет **varchar(max)**, **nvarchar(max)** или **varbinary(max)** типов данных; в противном случае **int**.  
  
 Если используются параметры сортировки SC, то возвращаемое целое значение рассматривает суррогатные пары Юникода UTF-16 как один символ. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="remarks"></a>Remarks  
 Функция LEN исключает конечные пробелы. Если это проблемы, рассмотрите возможность использования [DATALENGTH &#40; Transact-SQL &#41; ](../../t-sql/functions/datalength-transact-sql.md) функцию, в которой не усекал строку. При обработке строки в Юникоде, DATALENGTH возвращает вдвое превышает число символов. В следующем примере показано LEN и DATALENGTH с пробелом.  
  
```  
DECLARE @v1 varchar(40),  
    @v2 nvarchar(40);  
SELECT   
@v1 = 'Test of 22 characters ',   
@v2 = 'Test of 22 characters ';  
SELECT LEN(@v1) AS [varchar LEN] , DATALENGTH(@v1) AS [varchar DATALENGTH];  
SELECT LEN(@v2) AS [nvarchar LEN], DATALENGTH(@v2) AS [nvarchar DATALENGTH];  
  
```  
  
## <a name="examples"></a>Примеры  
 Следующий пример выбирает число символов и данные по имени людей `FirstName`, живущих в `Australia`. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT LEN(FirstName) AS Length, FirstName, LastName   
FROM Sales.vIndividualCustomer  
WHERE CountryRegionName = 'Australia';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример возвращает количество символов в столбце `FirstName` и имена и фамилии сотрудников, расположенных в `Australia`.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT LEN(FirstName) AS FNameLength, FirstName, LastName   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.DimGeography AS g   
    ON e.SalesTerritoryKey = g.SalesTerritoryKey   
WHERE EnglishCountryRegionName = 'Australia';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FNameLength  FirstName  LastName  
-----------  ---------  ---------------  
4            Lynn       Tsoflias
```  
  
## <a name="see-also"></a>См. также  
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [Функция CHARINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/charindex-transact-sql.md)  
 [Функция PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)  
 [Левый &#40; Transact-SQL &#41;](../../t-sql/functions/left-transact-sql.md)   
 [ПРАВО &#40; Transact-SQL &#41;](../../t-sql/functions/right-transact-sql.md)  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
  
  


