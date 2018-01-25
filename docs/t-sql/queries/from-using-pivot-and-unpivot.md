---
title: "Использование операторов PIVOT и UNPIVOT | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PIVOT_TSQL
helpviewer_keywords:
- FROM clause, UNPIVOT operator
- unpivoting tables
- table pivoting [SQL Server]
- UNPIVOT operator
- crosstab query
- PIVOT operator
- rotating table-valued expressions
- pivoting tables
- FROM clause, PIVOT operator
- rotating columns
ms.assetid: 24ba54fc-98f7-4d35-8881-b5158aac1d66
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1feee91c251b5c1f326e8e69569186c049007d9e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="from---using-pivot-and-unpivot"></a>ОТ - использование операторов PIVOT и UNPIVOT
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Можно использовать `PIVOT` и `UNPIVOT` реляционные операторы, чтобы изменить выражение, возвращающие табличные значения, в другую таблицу. `PIVOT`Поворачивает указано табличное выражение, преобразуя уникальные значения из одного столбца выражения в несколько столбцов в выходных данных и выполняет статистические функции, где это требуется в оставшихся значений столбца, которые требуются в окончательный результат. `UNPIVOT`выполняет обратную операцию для PIVOT, преобразуя столбцы возвращающего табличное значение выражения в значения столбца.  
  
 Синтаксис `PIVOT` предоставляет является более простым и понятным, чем синтаксис, который в противном случае может быть указан в сложных серии `SELECT...CASE` инструкции. Полное описание синтаксиса для `PIVOT`, в разделе [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
 Следующий синтаксис перечислены способы использования `PIVOT` оператор.  
  
```  
SELECT <non-pivoted column>,  
    [first pivoted column] AS <column name>,  
    [second pivoted column] AS <column name>,  
    ...  
    [last pivoted column] AS <column name>  
FROM  
    (<SELECT query that produces the data>)   
    AS <alias for the source query>  
PIVOT  
(  
    <aggregation function>(<column being aggregated>)  
FOR   
[<column that contains the values that will become column headers>]   
    IN ( [first pivoted column], [second pivoted column],  
    ... [last pivoted column])  
) AS <alias for the pivot table>  
<optional ORDER BY clause>;  
```  

## <a name="remarks"></a>Remarks  
Столбец идентификаторов в `UNPIVOT` предложение выполните параметров сортировки каталога. Для [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], параметры сортировки всегда является `SQL_Latin1_General_CP1_CI_AS`. Для [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] частично автономных баз данных, параметры сортировки всегда является `Latin1_General_100_CI_AS_KS_WS_SC`. Если столбец используется в сочетании с других столбцов, а затем предложение collate (`COLLATE DATABASE_DEFAULT`) требуется для предотвращения конфликтов.  

  
## <a name="basic-pivot-example"></a>Базовый пример PIVOT  
 В следующем примере создается таблица, включающая два столбца и четыре строки.  
  
```  
USE AdventureWorks2014 ;  
GO  
SELECT DaysToManufacture, AVG(StandardCost) AS AverageCost   
FROM Production.Product  
GROUP BY DaysToManufacture;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 DaysToManufacture AverageCost
 ----------------- -----------
 0                 5.0885
 1                 223.88
 2                 359.1082
 4                 949.4105
 ```
  
 Для значения `DaysToManufacture`, равного трем, продукты не определены.  
  
 Следующий код отображает тот же самый результат, сведенный так, что значения `DaysToManufacture` становятся заголовками. Для значения трех `[3]` дней приводится столбец, даже если результат равен `NULL`.  
  
```  
-- Pivot table with one row and five columns  
SELECT 'AverageCost' AS Cost_Sorted_By_Production_Days,   
[0], [1], [2], [3], [4]  
FROM  
(SELECT DaysToManufacture, StandardCost   
    FROM Production.Product) AS SourceTable  
PIVOT  
(  
AVG(StandardCost)  
FOR DaysToManufacture IN ([0], [1], [2], [3], [4])  
) AS PivotTable;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
Cost_Sorted_By_Production_Days 0           1           2           3           4         
------------------------------ ----------- ----------- ----------- ----------- -----------
AverageCost                    5.0885      223.88      359.1082    NULL        949.4105
```
  
## <a name="complex-pivot-example"></a>Сложный пример PIVOT  
 Обычно оператор `PIVOT` может быть полезен при создании отчетов с перекрестными ссылками для сведения данных. Например, пусть необходимо обратиться к таблице `PurchaseOrderHeader` образца базы данных `AdventureWorks2014` для определения количества заказов на покупку, размещенных некоторым сотрудником. Требуемые данные, отсортированные по поставщикам, можно извлечь при выполнении следующего запроса.  
  
```  
USE AdventureWorks2014;  
GO  
SELECT VendorID, [250] AS Emp1, [251] AS Emp2, [256] AS Emp3, [257] AS Emp4, [260] AS Emp5  
FROM   
(SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM Purchasing.PurchaseOrderHeader) p  
PIVOT  
(  
COUNT (PurchaseOrderID)  
FOR EmployeeID IN  
( [250], [251], [256], [257], [260] )  
) AS pvt  
ORDER BY pvt.VendorID;  
```  
  
 Здесь приводится частичный результирующий набор.  
  
```
VendorID    Emp1        Emp2        Emp3        Emp4        Emp5  
----------- ----------- ----------- ----------- ----------- -----------
1492        2           5           4           4           4
1494        2           5           4           5           4
1496        2           4           4           5           5
1498        2           5           4           4           4
1500        3           4           4           5           4
```
  
 Данные, возвращаемые в результате выполнения указанного подзапроса выборки, сводятся в столбец `EmployeeID`.  
  
```  
SELECT PurchaseOrderID, EmployeeID, VendorID  
FROM PurchaseOrderHeader;  
```  
  
 Это означает, что уникальные значения столбца `EmployeeID` становятся полями итогового результирующего набора. Поэтому имеется столбец, соответствующий каждому идентификатору `EmployeeID`, указанному в предложении PIVOT: в данном случае это сотрудники `164`, `198`, `223`, `231` и `233`. `PurchaseOrderID` служит столбцом значений, по которому группируются столбцы, возвращаемые в конечный вывод и называемые столбцами группирования. В этом случае значения столбцов группирования обрабатываются с помощью функции `COUNT`. Обратите внимание, что при вычислении функции `PurchaseOrderID` для каждого сотрудника выдается предупреждение, сообщающее, что пустые значения столбца `COUNT` не учитываются.  
  
> [!IMPORTANT]  
>  При использовании статистических функций с `PIVOT`, наличие значений null в столбце значений не учитываются при вычислении отдельного выражения.  
  
 `UNPIVOT`выполняет действия, обратные оператору из `PIVOT`, преобразуя столбцы в строки. Допустим, что таблица, созданная в ходе выполнения предыдущего примера, хранится в базе данных и имеет идентификатор `pvt`. Пусть необходимо преобразовать идентификаторы столбцов `Emp1`, `Emp2`, `Emp3`, `Emp4` и `Emp5` в строки данных, сгруппированные по поставщикам. В этом случае необходимо определить два дополнительных столбца. Столбец, содержащий значения поворачиваемых столбцов (`Emp1`, `Emp2`...), будет называться `Employee`, а столбец, который будет содержать значения, в данный момент расположенные в поворачиваемых столбцах, будет называться `Orders`. Эти столбцы соответствуют *pivot_column* и *value_column*, соответственно, в [!INCLUDE[tsql](../../includes/tsql-md.md)] определения. Запрос:  
  
```  
-- Create the table and insert values as portrayed in the previous example.  
CREATE TABLE pvt (VendorID int, Emp1 int, Emp2 int,  
    Emp3 int, Emp4 int, Emp5 int);  
GO  
INSERT INTO pvt VALUES (1,4,3,5,4,4);  
INSERT INTO pvt VALUES (2,4,1,5,5,5);  
INSERT INTO pvt VALUES (3,4,3,5,4,4);  
INSERT INTO pvt VALUES (4,4,2,5,5,4);  
INSERT INTO pvt VALUES (5,5,1,5,5,5);  
GO  
-- Unpivot the table.  
SELECT VendorID, Employee, Orders  
FROM   
   (SELECT VendorID, Emp1, Emp2, Emp3, Emp4, Emp5  
   FROM pvt) p  
UNPIVOT  
   (Orders FOR Employee IN   
      (Emp1, Emp2, Emp3, Emp4, Emp5)  
)AS unpvt;  
GO  
```  
  
 Здесь приводится частичный результирующий набор.  
  
```
VendorID    Employee    Orders
----------- ----------- ------
1            Emp1       4
1            Emp2       3 
1            Emp3       5
1            Emp4       4
1            Emp5       4
2            Emp1       4
2            Emp2       1
2            Emp3       5
2            Emp4       5
2            Emp5       5
...
```
  
 Обратите внимание, что `UNPIVOT` не является в точности обратным `PIVOT`. `PIVOT`выполняет статистическую обработку и слияние нескольких строк в одну строку в выходные данные. `UNPIVOT`не воспроизводится в исходном результирующем табличное выражение, так как строки были объединены. Кроме того, значения null в ввода `UNPIVOT` исчезают в выходных данных, тогда как возникли исходные значения null во входных данных перед `PIVOT` операции.  
  
 `Sales.vSalesPersonSalesByFiscalYears` Просмотра в [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] примере используется база данных `PIVOT` для возврата суммарный объем продаж для каждого менеджера по продажам для каждого финансового года. Чтобы просмотреть скрипт представления в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в **обозревателя объектов**, найдите представление в списке **представления** папку для [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных. Щелкните правой кнопкой мыши имя представления, а затем выберите **создать скрипт для представления**.  
  
## <a name="see-also"></a>См. также  
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)   
 [РЕГИСТР (Transact-SQL)](../../t-sql/language-elements/case-transact-sql.md)  
  
  
