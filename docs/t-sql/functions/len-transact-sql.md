---
title: LEN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/03/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LEN
- LEN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- LEN function
- characters [SQL Server], number of
- number of characters
ms.assetid: fa20fee4-884d-4301-891a-c03e901345ae
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 290d9b9ba27b5895cb9511220bbf7ef39bbb8025
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="len-transact-sql"></a>LEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает количество символов указанного строкового выражения, исключая конечные пробелы.  
  
> [!NOTE]  
>  Получить число байтов, используемых для представления выражения, можно с помощью функции [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
LEN ( string_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *string_expression*  
 Оцениваемое строковое [выражение](../../t-sql/language-elements/expressions-transact-sql.md). Аргумент *string_expression* может быть константой, переменной или столбцом символьных или двоичных данных.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **bigint**, если *expression* имеет тип данных **varchar(max)**, **nvarchar(max)** или **varbinary(max)**; в противном случае **int**.  
  
 Если используются параметры сортировки SC, то возвращаемое целое значение рассматривает суррогатные пары Юникода UTF-16 как один символ. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="remarks"></a>Remarks  
 Функция LEN исключает конечные пробелы. Если это может создать проблемы, рекомендуется использовать функцию [DATALENGTH (Transact-SQL)](../../t-sql/functions/datalength-transact-sql.md), которая не усекает строку. При обработке строки Юникода DATALENGTH возвращает удвоенное количество символов. В приведенном ниже примере демонстрируется работа функций LEN и DATALENGTH с конечным пробелом.  
  
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
 Следующий пример выбирает число символов и данные по имени людей `FirstName`, живущих в `Australia`. В примере используется база данных AdventureWorks.  
  
```  
SELECT LEN(FirstName) AS Length, FirstName, LastName   
FROM Sales.vIndividualCustomer  
WHERE CountryRegionName = 'Australia';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В приведенном ниже примере возвращается число символов в столбце `FirstName`, а также первое и последнее имена сотрудников в `Australia`.  
  
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
  
## <a name="see-also"></a>См. также:  
 [DATALENGTH (Transact-SQL)](../../t-sql/functions/datalength-transact-sql.md)   
 [CHARINDEX (Transact-SQL)](../../t-sql/functions/charindex-transact-sql.md)  
 [PATINDEX (Transact-SQL)](../../t-sql/functions/patindex-transact-sql.md)  
 [LEFT (Transact-SQL)](../../t-sql/functions/left-transact-sql.md)   
 [RIGHT (Transact-SQL)](../../t-sql/functions/right-transact-sql.md)  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
  
  


