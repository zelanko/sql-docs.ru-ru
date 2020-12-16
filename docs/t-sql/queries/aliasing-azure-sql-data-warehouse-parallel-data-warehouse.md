---
title: Псевдонимы
description: Псевдонимы в Azure Synapse Analytics и Parallel Data Warehouse.
titleSuffix: Azure Synapse Analytics
ms.custom: seo-lt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
author: shkale-msft
ms.author: shkale
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: a70959afb4e61f2049e19cfd1de96f0434abcb09
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97476675"
---
# <a name="aliasing-azure-synapse-analytics-parallel-data-warehouse"></a>Псевдонимы (Azure Synapse Analytics, Parallel Data Warehouse)

[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

За счет присвоения псевдонима можно временно подставлять короткие и легко запоминающиеся строки вместо имени таблицы или столбца в запросах [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)][!INCLUDE[DWsql](../../includes/dwsql-md.md)]. Псевдонимы таблиц часто используются в запросах JOIN, так как при ссылках на столбцы для синтаксиса JOIN требуются полные имена объектов.  

Псевдонимы должны быть отдельными словами, соответствующими правилам именования объектов. Дополнительные сведения см. в разделе "Правила именования объектов" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Псевдонимы не могут содержать пробелы и не могут заключаться в одинарные или двойные кавычки.  

## <a name="syntax"></a>Синтаксис

```tsql
object_source [ AS ] alias
```

## <a name="arguments"></a>Аргументы

*object_source*  
Имя исходной таблицы или столбца.  

AS  
Необязательная препозиция псевдонима. При работе с псевдонимами переменных диапазона ключевое слово AS запрещено использовать.  

*alias* Требуемое временное ссылочное имя для таблицы или столбца. Можно использовать любое допустимое имя объекта. Дополнительные сведения см. в разделе "Правила именования объектов" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  

## <a name="examples-sssdw-and-sspdw"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

В следующем примере показан запрос с несколькими соединениями. В этом примере демонстрируется присвоение псевдонимов для таблиц и столбцов.  

- Присвоение псевдонимов столбцам: в этом примере используются столбцы и выражения, включающие столбцы, в списке. `SalesTerritoryRegion AS SalesTR` демонстрирует простой псевдоним столбца. `Sum(SalesAmountQuota) AS TotalSales` демонстрирует  

- задание табличных псевдонимов: `dbo.DimSalesTerritory AS st`показывает создание псевдонима `st`для `dbo.DimSalesTerritory` таблицы.  

```tsql
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

```tsql
-- Uses AdventureWorks

SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```

## <a name="next-steps"></a>Дальнейшие действия

- [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)
- [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)
- [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)