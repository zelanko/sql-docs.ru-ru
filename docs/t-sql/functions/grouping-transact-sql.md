---
title: "ГРУППИРОВАНИЕ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GROUPING
- GROUPING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], GROUPING function
- grouping columns
- ROLLUP operator
- GROUP BY clause, GROUPING function
- GROUPING function
- CUBE operator
ms.assetid: 4efa3868-1fc4-4626-8fb1-e863cc03e422
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d83b68d9d5fb52c67ca3a1910fe9541dfd6f5552
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="grouping-transact-sql"></a>GROUPING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает, является ли указанное выражение столбца в списке GROUP BY статистическим или нет. В результирующем наборе функция GROUPING возвращает 1 (статистическое выражение) или ноль (нестатистическое выражение). ГРУППИРОВАНИЕ может использоваться только в инструкции SELECT \<выберите > список, HAVING и ORDER BY предложения, если указан GROUP BY.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GROUPING ( <column_expression> )  
```  
  
## <a name="arguments"></a>Аргументы  
 \<column_expression >  
 Столбец или выражение, которое содержит столбец в [GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md) предложения.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **tinyint**  
  
## <a name="remarks"></a>Замечания  
 GROUPING используется, чтобы различать значения NULL, возвращаемые операторами ROLLUP, CUBE или GROUPING SETS, и стандартные значения NULL. Возвращение NULL в качестве результата операции ROLLUP, CUBE или GROUPING SETS является особым случаем использования NULL. Значение служит заполнителем столбца в результирующем наборе и означает «все».  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится группирование `SalesQuota` и статистическая обработка сумм `SaleYTD` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Функция `GROUPING` применяется к столбцу `SalesQuota`.  
  
```  
SELECT SalesQuota, SUM(SalesYTD) 'TotalSalesYTD', GROUPING(SalesQuota) AS 'Grouping'  
FROM Sales.SalesPerson  
GROUP BY SalesQuota WITH ROLLUP;  
GO  
```  
  
 В результирующем наборе показаны два значения NULL в `SalesQuota`. Первый `NULL` представляет группу значений NULL из этого столбца в таблице. Второй `NULL` находится в строке итогов, добавленной операцией ROLLUP. Строка итогов показывает `TotalSalesYTD` сумм для всех `SalesQuota` групп и обозначается `1` в `Grouping` столбца.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 SalesQuota     TotalSalesYTD       Grouping  
------------   -----------------   --------  
NULL           1533087.5999          0  
250000.00      33461260.59           0  
300000.00      9299677.9445          0  
NULL           44294026.1344         1  

(4 row(s) affected)
```  
  
## <a name="see-also"></a>См. также:  
 [GROUPING_ID &#40; Transact-SQL &#41;](../../t-sql/functions/grouping-id-transact-sql.md)   
 [Предложение GROUP BY &#40; Transact-SQL &#41;](../../t-sql/queries/select-group-by-transact-sql.md)  
  
  

