---
title: HAVING (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HAVING
- HAVING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restricting conditions for result set
- search conditions [SQL Server], HAVING clause
- HAVING clause
- HAVING clause, about HAVING clause
ms.assetid: 55650709-001e-42f4-902f-ead09a3c34af
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 72072a62ba6e7650791bfd1410682c112b95ee91
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906124"
---
# <a name="select---having-transact-sql"></a>SELECT — HAVING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет условие поиска для группы или статистического выражения. Предложение HAVING можно использовать только в инструкции SELECT. HAVING обычно используется с предложением GROUP BY. Если предложение GROUP BY не используется, имеется одна неявная агрегированная группа.   
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[ HAVING <search condition> ]  
```  
  
## <a name="arguments"></a>Аргументы  
\<search_condition> задает один или несколько предикатов, которые должны выполняться для групп или агрегатов. Дополнительные сведения об условиях поиска и предикатах см. в статье [Условие поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md).  
  
 Типы данных **text**, **image** и **ntext** нельзя использовать в предложении HAVING.  
  
## <a name="examples"></a>Примеры  
 В следующем примере, который использует простое предложение `HAVING`, из таблицы `SalesOrderID` извлекается сумма всех полей `SalesOrderDetail`, значение которых превышает `$100000.00`.  
  
```sql
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID  
HAVING SUM(LineTotal) > 100000.00  
ORDER BY SalesOrderID ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В приведенном ниже примере предложение `HAVING` используется с целью получения суммы для каждого `SalesAmount` в таблице `FactInternetSales`, для которого `OrderDateKey` относится к 2004 или более позднему году.  
  
```sql
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING SUM(SalesAmount) > 80000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>См. также:  
 [GROUP BY (Transact-SQL)](../../t-sql/queries/select-group-by-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)  
  
  

