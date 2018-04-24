---
title: Присвоение псевдонима (хранилище данных SQL Azure или Parallel Data Warehouse) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
caps.latest.revision: 11
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3699b5ea6399acb5c0824b1100c82e0473d8c737
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="aliasing-azure-sql-data-warehouse-parallel-data-warehouse"></a>Присвоение псевдонима (хранилище данных SQL Azure или Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  За счет присвоения псевдонима можно временно подставлять короткие и легко запоминающиеся строки вместо имени таблицы или столбца в запросах [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)][!INCLUDE[DWsql](../../includes/dwsql-md.md)]. Псевдонимы таблиц часто используются в запросах JOIN, так как при ссылках на столбцы для синтаксиса JOIN требуются полные имена объектов.  
  
 Псевдонимы должны быть отдельными словами, соответствующими правилам именования объектов. Дополнительные сведения см. в разделе "Правила именования объектов" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Псевдонимы не могут содержать пробелы и не могут заключаться в одинарные или двойные кавычки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
object_source [ AS ] alias  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_source*  
 Имя исходной таблицы или столбца.  
  
 AS  
 Необязательная препозиция псевдонима. При работе с псевдонимами переменных диапазона ключевое слово AS запрещено использовать.  
  
 *alias*  
 Нужное временное ссылочное имя для таблицы или столбца. Можно использовать любое допустимое имя объекта. Дополнительные сведения см. в разделе "Правила именования объектов" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере показан запрос с несколькими соединениями. В этом примере демонстрируется присвоение псевдонимов для таблиц и столбцов.  
  
-   Присвоение псевдонимов столбцам: в этом примере используются столбцы и выражения, включающие столбцы, в списке. `SalesTerritoryRegion AS SalesTR` демонстрирует простой псевдоним столбца. `Sum(SalesAmountQuota) AS TotalSales` демонстрирует  
  
-   задание табличных псевдонимов: `dbo.DimSalesTerritory AS st`показывает создание псевдонима `st`для `dbo.DimSalesTerritory` таблицы.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion AS SalesTR,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
  
```  
  
 Ключевое слово можно исключить, как показано ниже, но для удобства чтения оно часто остается.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
## <a name="see-also"></a>См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)  
  
  
