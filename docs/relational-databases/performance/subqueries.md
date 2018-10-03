---
title: Вложенные запросы (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 02/18/2018
ms.prod: sql
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Subquery
- Subqueries
- subqueries [SQL Server], fundamentals
- subqueries [SQL Server], correlated
- subqueries [SQL Server], types
ms.assetid: bfc97432-c14c-4768-9dc5-a9c512f6b2bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 42ea4207746b3933c550ab1e93a3cc3666a060dc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835512"
---
# <a name="subqueries-sql-server"></a>Вложенные запросы (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 
Вложенный запрос — это запрос, который используется внутри инструкции `SELECT`, `INSERT`, `UPDATE` или `DELETE` или внутри другого вложенного запроса. Подзапрос может быть использован везде, где разрешены выражения. В данном примере вложенный запрос используется в качестве выражения для столбца MaxUnitPrice в инструкции SELECT.

```sql
USE AdventureWorks2016;
GO
SELECT Ord.SalesOrderID, Ord.OrderDate,
    (SELECT MAX(OrdDet.UnitPrice)
     FROM Sales.SalesOrderDetail AS OrdDet
     WHERE Ord.SalesOrderID = OrdDet.SalesOrderID) AS MaxUnitPrice
FROM Sales.SalesOrderHeader AS Ord;
GO
```

## <a name="fundamentals"></a> Основы вложенных запросов
Вложенный запрос по-другому называют внутренним запросом или внутренней операцией выбора, в то время как инструкцию, содержащую вложенный запрос, называют внешним запросом или внешней операцией выбора.   

Многие инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], включающие подзапросы, можно записать в виде соединений. Другие запросы могут быть осуществлены только с помощью подзапросов. В языке [!INCLUDE[tsql](../../includes/tsql-md.md)] обычно не бывает разницы в производительности между инструкцией, включающей вложенный запрос, и семантически эквивалентной версией без вложенного запроса. Однако в некоторых случаях, когда проверяется существование, соединения показывают лучшую производительность. В противном случае для устранения дубликатов вложенный запрос должен обрабатываться для получения каждого результата внешнего запроса. В таких случаях метод работы соединений дает лучшие результаты. В следующем примере используются вложенный запрос `SELECT` и соединение `SELECT`, которые возвращают один и тот же результирующий набор:

```sql
USE AdventureWorks2016;
GO

/* SELECT statement built using a subquery. */
SELECT Name
FROM Production.Product
WHERE ListPrice =
    (SELECT ListPrice
     FROM Production.Product
     WHERE Name = 'Chainring Bolts' );
GO

/* SELECT statement built using a join that returns
   the same result set. */
SELECT Prd1. Name
FROM Production.Product AS Prd1
     JOIN Production.Product AS Prd2
       ON (Prd1.ListPrice = Prd2.ListPrice)
WHERE Prd2. Name = 'Chainring Bolts';
GO
```

Вложенный во внешнюю инструкцию SELECT запрос, имеет следующие компоненты:    
-   обычный запрос `SELECT`, включающий обычные компоненты списка выборки;   
-   обычное предложение `FROM`, включающее одно или несколько имен таблиц или представлений.   
-   Необязательное предложение `WHERE`.   
-   Необязательное предложение `GROUP BY`.   
-   Необязательное предложение `HAVING`.   

Запрос SELECT вложенного запроса всегда заключен в скобки. Он не может включать предложения `COMPUTE` или `FOR BROWSE` и может включать предложение `ORDER BY` только вместе с предложением TOP.   

Вложенный запрос может быть включен в предложение `WHERE` или `HAVING` внешней инструкции `SELECT`, `INSERT`, `UPDATE` или `DELETE` или в другой вложенный запрос. Возможно создавать вложенность до 32-го уровня, хотя ограничения меняются в зависимости от объема доступной памяти и сложности других выражений в запросе. Отдельные запросы могут не поддерживать вложенность до 32-го уровня. Подзапрос может появляться везде, где может использоваться выражение, если он возвращает одно значение.   

Если таблица появляется только во вложенном запросе, а не во внешнем запросе, в этом случае столбцы данной таблицы не могут быть включены в выходные данные (список выборки внешнего запроса).   

Инструкции, включающие вложенные запросы, обычно имеют один из следующих форматов:   
-   WHERE выражение \[NOT] IN (вложенный запрос)
-   WHERE выражение оператор_сравнения \[ANY | ALL] (вложенный запрос)
-   WHERE \[NOT] EXISTS (вложенный запрос)   

В некоторых инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)] вложенный запрос может рассматриваться как отдельный запрос. Обычно результаты вложенного запроса подставляются во внешний запрос (хотя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может обрабатывать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] с вложенными запросами и по-другому).    

Существуют три основных типа подзапросов, которые: 
-   работают в списках, указанных с помощью ключевого слова `IN`, или тех, которые оператор сравнения изменил с помощью ключевого слова `ANY` или `ALL`;
-   вставлены оператором немодифицированных сравнений и должны возвращать одно значение;
-   являются проверками на существование, начинающимися с ключевого слова `EXISTS`.

## <a name="rules"></a> Правила вложенных запросов
На вложенный запрос распространяются следующие ограничения: 
-   Список выбора вложенного запроса, начинающийся с оператора сравнения, может включать только одно выражение или имя столбца (за исключением операторов `EXISTS` и `IN` в инструкции `SELECT *` или в списке соответственно).   
-   Если предложение `WHERE` внешнего запроса включает имя столбца, оно должно быть совместимо для соединения со столбцом в списке выбора вложенного запроса.   
-   Типы данных **ntext**, **text** и **image** не могут быть использованы в списке выбора вложенных запросов.   
-   Вложенные запросы, представленные оператором неизмененного сравнения (после которого нет ключевого слова ANY или ALL), не могут включать предложения `GROUP BY` и `HAVING`.   
-   Ключевое слово `DISTINCT` не может быть использовано во вложенном запросе, включающем предложение GROUP BY.
-   Предложения `COMPUTE` и `INTO` не могут быть указаны.   
-   Предложение `ORDER BY` может быть указано только вместе с предложением `TOP`.   
-   Представление, созданное с помощью вложенного запроса, не может быть обновлено.   
-   Список выбора вложенного запроса, начинающегося с предложения `EXISTS`, по соглашению содержит звездочку (\*) вместо отдельного имени столбца. Правила для вложенного запроса, начинающегося с предложения `EXISTS`, являются такими же, как для стандартного списка выбора, поскольку вложенный запрос, начинающийся с предложения `EXISTS`, проводит проверку на существование и возвращает TRUE или FALSE вместо данных.   

## <a name="qualifying"></a> Уточнение имен столбцов во вложенных запросах
В следующем примере столбец *CustomerID* в предложении `WHERE` внешнего запроса неявно уточняется именем таблицы, используемой в предложении `FROM` внешнего запроса (*Sales.Store*). Ссылка на столбец *CustomerID* в списке выборки вложенного запроса уточняется именем таблицы с помощью предложения `FROM` вложенного запроса, то есть *Sales.Customer*.

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Sales.Store
WHERE BusinessEntityID NOT IN
    (SELECT CustomerID
     FROM Sales.Customer
     WHERE TerritoryID = 5);
GO
```

Общее правило состоит в том, что имена столбцов в инструкции неявно уточняются именем таблицы, указанной в предложении `FROM` того же уровня вложенности. Если столбец не существует в таблице, на которую ссылается предложение `FROM` вложенного запроса, он неявно уточняется именем таблицы, указанной в предложении `FROM` внешнего запроса.   

Вот как выглядит этот запрос с явно указанными неявными соглашениями:

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Sales.Store
WHERE Sales.Store.BusinessEntityID NOT IN
    (SELECT Sales.Customer.CustomerID
     FROM Sales.Customer
     WHERE TerritoryID = 5);
GO
```

Никогда не будет ошибочным явно указать имя таблицы; также всегда можно перекрыть неявные соглашения об именах таблиц полностью уточненными именами столбцов   

> [!IMPORTANT]
> Если столбец, на который есть ссылка во вложенном запросе, не существует в таблице, указанной в предложении `FROM` вложенного запроса, но существует в таблице, на которую ссылается предложение `FROM` внешнего запроса, запрос будет выполнен без ошибок. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявно уточнит имя столбца во вложенном запросе с помощью имени таблицы внешнего запроса.   

## <a name="nesting"></a> Множественные уровни вложенности
Каждый вложенный запрос, в свою очередь, может содержать один или более вложенных запросов. В инструкцию можно вложить любое количество вложенных запросов.   

Следующий запрос осуществляет поиск сотрудников, занимающих должность менеджера по продажам.   

```sql
USE AdventureWorks2016;
GO
SELECT LastName, FirstName
FROM Person.Person
WHERE BusinessEntityID IN
    (SELECT BusinessEntityID
     FROM HumanResources.Employee
     WHERE BusinessEntityID IN
        (SELECT BusinessEntityID
         FROM Sales.SalesPerson)
    );
GO
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
LastName                                           FirstName
-------------------------------------------------- -----------------------
Jiang                                              Stephen
Abbas                                              Syed
Alberts                                            Amy
Ansman-Wolfe                                       Pamela
Campbell                                           David
Carson                                             Jillian
Ito                                                Shu
Mitchell                                           Linda
Reiter                                             Tsvi
Saraiva                                            Jos
Vargas                                             Garrett
Varkey Chudukatil                                  Ranjit
Valdez                                             Rachel
Tsoflias                                           Lynn
Pak                                                Jae
Blythe                                             Michael
Mensa-Annan                                        Tete

(17 row(s) affected)
```

Самый глубоко вложенный запрос возвращает идентификаторы указанных сотрудников. Запрос уровнем выше оперирует с полученными идентификаторами и возвращает контактные идентификаторы сотрудников. Наконец, во внешнем запросе по полученным контактным идентификаторам извлекаются имена сотрудников.   

Этот запрос также можно выразить с помощью соединения:

```sql
USE AdventureWorks2016;
GO
SELECT LastName, FirstName
FROM Person.Person c
INNER JOIN HumanResources.Employee e
ON c.BusinessEntityID = e.BusinessEntityID
JOIN Sales.SalesPerson s 
ON e.BusinessEntityID = s.BusinessEntityID;
GO
```

## <a name="correlated"></a> Связанные вложенные запросы
Результат для нескольких запросов может быть получен путем выполнения одного вложенного запроса и подстановки полученного результата или результатов в предложение `WHERE` внешнего запроса. В запросах, содержащих коррелированные вложенные запросы (также называемые повторяющимися вложенными запросами), вложенный запрос зависит по значению от внешнего запроса. Это означает, что выполнение вложенного запроса повторяется по одному разу для каждой строки, которая может быть выбрана внешним запросом.
Такой запрос получает по одной записи для имени и фамилии каждого сотрудника, который в таблице *SalesPerson* имеет сумму премиальных, равную 5000, с соответствующими идентификаторами сотрудников в таблицах *Employee* и *SalesPerson*.

```sql
USE AdventureWorks2016;
GO
SELECT DISTINCT c.LastName, c.FirstName, e.BusinessEntityID 
FROM Person.Person AS c JOIN HumanResources.Employee AS e
ON e.BusinessEntityID = c.BusinessEntityID 
WHERE 5000.00 IN
    (SELECT Bonus
    FROM Sales.SalesPerson sp
    WHERE e.BusinessEntityID = sp.BusinessEntityID) ;
GO
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
LastName FirstName BusinessEntityID
-------------------------- ---------- ------------
Ansman-Wolfe Pamela 280
Saraiva José 282

(2 row(s) affected)
```

Предыдущий вложенный запрос данной инструкции не может быть выполнен независимо от внешнего запроса. В нем необходимо указать значение *Employee.BusinessEntityID*, однако это значение изменяется каждый раз, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет различные строки в таблице *Employee*.   
Результат запроса определяется следующим образом: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассматривает каждую строку таблицы Employee на предмет включения в результаты, подставляя значение в каждой из строк во вложенный запрос.
Например, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сначала выполняет проверку строки для сотрудника `Syed Abbas`, переменная *Employee.BusinessEntityID* принимает значение 285, которое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и подставляет во вложенный запрос.

```sql
USE AdventureWorks2016;
GO
SELECT Bonus
FROM Sales.SalesPerson
WHERE BusinessEntityID = 285;
GO
```

Результатом является 0 (`Syed Abbas` не получал премиальных, потому что не является менеджером по продажам), поэтому выполнение внешнего запроса приводит к следующему результату:

```sql
USE AdventureWorks2016;
GO
SELECT LastName, FirstName
FROM Person.Person AS c JOIN HumanResources.Employee AS e
ON e.BusinessEntityID = c.BusinessEntityID 
WHERE 5000 IN (0.00);
GO
```

Поскольку условие не выполнено, строка для сотрудника `Syed Abbas` не включается в результат. То же самое действие выполняется со строкой для сотрудника `Pamela Ansman-Wolfe`. Из примера видно, что данная строка будет включена в результат.     

Коррелированные вложенные запросы могут также включать в предложение `FROM` функции с табличным значением, указывая для них в качестве аргументов столбцы таблиц из внешнего запроса. В этом случае для каждой строки внешнего запроса выполняется функция с табличным значением, как и в случае с вложенным запросом.    
  
## <a name="types"></a> Типы вложенных запросов
Вложенные запросы могут быть указаны во многих местах: 
-   С псевдонимами. Дополнительные сведения см. в разделе [Вложенные запросы с псевдонимами](#aliases).
-   С `IN` или `NOT IN`. Дополнительные сведения см. в разделах [Вложенные запросы с ключевым словом IN](#in) и [Вложенные запросы с ключевым словом NOT IN](#notin).
-   В инструкциях `UPDATE`, `DELETE` и `INSERT`. Дополнительные сведения см. в разделе [Вложенные запросы в инструкциях UPDATE, DELETE и INSERT](#upsert).
-   С операторами сравнения. Дополнительные сведения см. в разделе [Вложенные запросы с операторами сравнения](#comparison).
-   С `ANY`, `SOME` или `ALL`. Дополнительные сведения см. в разделе [Операторы сравнения с модификаторами ANY, SOME или ALL](#comparison_modified).
-   С `EXISTS` или `NOT EXISTS`. Дополнительные сведения см. в разделах [Вложенные запросы с оператором EXISTS](#exists) и [Вложенные запросы с оператором NOT EXISTS](#notexists).
-   Вместо выражения. Дополнительные сведения см. в разделе [Вложенные запросы, используемые вместо выражений](#expression).

### <a name="aliases"></a> Вложенные запросы с псевдонимами
Многие инструкции, где вложенный и внешний запросы ссылаются на одну и ту же таблицу, могут быть переформулированы как самосоединения (соединения таблицы с самой собой). Например, можно найти адреса сотрудников из конкретного региона с помощью вложенного запроса:   

```sql
USE AdventureWorks2016;
GO
SELECT StateProvinceID, AddressID
FROM Person.Address
WHERE AddressID IN
    (SELECT AddressID
     FROM Person.Address
     WHERE StateProvinceID = 39);
GO
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```
StateProvinceID AddressID
----------- -----------
39 942
39 955
39 972
39 22660

(4 row(s) affected)
```   

Можно также использовать самосоединение:   

```sql
USE AdventureWorks2016;
GO
SELECT e1.StateProvinceID, e1.AddressID
FROM Person.Address AS e1
INNER JOIN Person.Address AS e2
ON e1.AddressID = e2.AddressID
AND e2.StateProvinceID = 39;
GO
```

Псевдонимы таблиц здесь необходимы, так как соединенная сама с собой таблица выступает в двух ролях. Псевдонимы можно также использовать во вложенных запросах, где и внешний, и внутренний запросы ссылаются на одну и ту же таблицу.    

```sql
USE AdventureWorks2016;
GO
SELECT e1.StateProvinceID, e1.AddressID
FROM Person.Address AS e1
WHERE e1.AddressID IN
    (SELECT e2.AddressID
     FROM Person.Address AS e2
     WHERE e2.StateProvinceID = 39);
GO
```

При использовании явных псевдонимов понятно, что ссылка на *Person.Address* во вложенном запросе означает не то же, что и ссылка во внешнем запросе.   

### <a name="in"></a> Вложенные запросы с ключевым словом IN
Результат вложенного запроса, в котором присутствует ключевое слово `IN` (или `NOT IN`) — это список из нуля или более значений. После того как вложенный запрос вернул результат, он используется внешним запросом.    
Следующий запрос ищет названия всех колес, произведенных компанией Adventure Works Cycles.     

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ProductSubcategoryID IN
    (SELECT ProductSubcategoryID
     FROM Production.ProductSubcategory
     WHERE Name = 'Wheels');
GO
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]     

```
Name
----------------------------
LL Mountain Front Wheel
ML Mountain Front Wheel
HL Mountain Front Wheel
LL Road Front Wheel
ML Road Front Wheel
HL Road Front Wheel
Touring Front Wheel
LL Mountain Rear Wheel
ML Mountain Rear Wheel
HL Mountain Rear Wheel
LL Road Rear Wheel
ML Road Rear Wheel
HL Road Rear Wheel
Touring Rear Wheel

(14 row(s) affected)
```

Эта инструкция выполняется в два шага. Сначала внутренний запрос возвращает номер идентификатора подкатегории по соответствию названию «Wheel» (17). Затем это значение подставляется во внешний запрос, который находит все названия изделий, имеющих соответствующие идентификаторы подкатегорий в столбце "Product".     

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ProductSubcategoryID IN ('17');
GO
```

Единственная разница в использовании соединения и вложенного запроса для этой и аналогичных задач заключается в том, что объединение позволяет включить в результат столбцы, содержащиеся в нескольких таблицах. Например: если нужно включить в результат название подкатегории, следует пользоваться соединением:    

```sql
USE AdventureWorks2016;
GO
SELECT p.Name, s.Name
FROM Production.Product p
INNER JOIN Production.ProductSubcategory s
ON p.ProductSubcategoryID = s.ProductSubcategoryID
AND s.Name = 'Wheels';
GO
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]    

```
Name
LL Mountain Front Wheel Wheels
ML Mountain Front Wheel Wheels
HL Mountain Front Wheel Wheels
LL Road Front Wheel Wheels
ML Road Front Wheel Wheels
HL Road Front Wheel Wheels
Touring Front Wheel Wheels
LL Mountain Rear Wheel Wheels
ML Mountain Rear Wheel Wheels
HL Mountain Rear Wheel Wheels
LL Road Rear Wheel Wheels
ML Road Rear Wheel Wheels
HL Road Rear Wheel Wheels
Touring Rear Wheel Wheels

(14 row(s) affected)
```    

Следующий запрос ищет названия всех поставщиков, имеющих высокий кредитный рейтинг, у которых компания Adventure Works Cycles заказала как минимум 20 позиций, и средний срок поставки у которых не превышает 16 дней.    

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Purchasing.Vendor
WHERE CreditRating = 1
AND BusinessEntityID IN
    (SELECT BusinessEntityID
     FROM Purchasing.ProductVendor
     WHERE MinOrderQty >= 20
     AND AverageLeadTime < 16);
GO
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
Name
--------------------------------------------------
Compete Enterprises, Inc
International Trek Center
First National Sport Co.
Comfort Road Bicycles
Circuit Cycles
First Rate Bicycles
Jeff's Sporting Goods
Competition Bike Training Systems
Electronic Bike Repair & Supplies
Crowley Sport
Expert Bike Co
Team Athletic Co.
Compete, Inc.   

(13 row(s) affected)
```   

Выполняется внутренний запрос и возвращаются номера идентификаторов поставщиков, которые соответствуют определениям вложенного запроса. Затем выполняется внешний запрос. Обратите внимание, что в предложение WHERE как внутреннего, так и внешнего запроса может быть включено несколько условий.   

При использовании соединения тот же запрос будет выражен так:

```sql
USE AdventureWorks2016;
GO
SELECT DISTINCT Name
FROM Purchasing.Vendor v
INNER JOIN Purchasing.ProductVendor p
ON v.BusinessEntityID = p.BusinessEntityID
WHERE CreditRating = 1
  AND MinOrderQty >= 20
  AND AverageLeadTime < 16;
GO
```

Соединение всегда может быть выражено в виде вложенного запроса. Вложенный запрос часто, но не всегда может быть выражен в виде соединения. Это происходит потому, что соединения симметричны: можно соединить таблицы A и B в любом порядке и получить одинаковый результат. Для вложенных запросов это не всегда справедливо.    

### <a name="notin"></a> Вложенные запросы с ключевым словом NOT IN
Вложенные запросы с ключевым словом NOT IN также возвращают список из нуля или более значений.   
В следующем запросе выполняется поиск названий продуктов, не являющихся готовыми велосипедами.   

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ProductSubcategoryID NOT IN
    (SELECT ProductSubcategoryID
     FROM Production.ProductSubcategory
     WHERE Name = 'Mountain Bikes' 
        OR Name = 'Road Bikes'
        OR Name = 'Touring Bikes');
GO
```

Эту инструкцию нельзя преобразовать в соединение. Аналогичное соединение по неравенству имеет другой смысл: оно находит названия продуктов, которые принадлежат какой-либо подкатегории, отличной от готового велосипеда.      

### <a name="upsert"></a> Вложенные запросы в инструкциях UPDATE, DELETE и INSERT
Вложенные запросы могут использоваться в инструкциях языка `UPDATE`, `DELETE`, `INSERT` и `SELECT `.    

В следующем примере удваивается значение столбца *ListPrice* таблицы *Production.Product*. Вложенный запрос в предложении `WHERE` ссылается на таблицу *Purchasing.ProductVendor* для ограничения количества обновляемых строк таблицы *Product* только теми, у которых идентификатор *BusinessEntity* равен 1540.

```sql
USE AdventureWorks2016;
GO 
UPDATE Production.Product
SET ListPrice = ListPrice * 2
WHERE ProductID IN
    (SELECT ProductID 
     FROM Purchasing.ProductVendor
     WHERE BusinessEntityID = 1540);
GO
```

Ниже приведена эквивалентная инструкция `UPDATE`, использующая соединение:

```sql
USE AdventureWorks2016;
GO 
UPDATE Production.Product
SET ListPrice = ListPrice * 2
FROM Production.Product AS p
INNER JOIN Purchasing.ProductVendor AS pv
    ON p.ProductID = pv.ProductID AND BusinessEntityID = 1540;
GO   
```

### <a name="comparison"></a> Вложенные запросы с операторами сравнения
Вложенные запросы могут начинаться с одного из операторов сравнения (=, < >, >, > =, <, ! >, ! <, or < =).   

Вложенный запрос, указанный с помощью неизмененного оператора сравнения (оператора сравнения, за которым не следуют ключевые слова `ANY` или `ALL`), должен возвратить одиночное значение, а не список значений как вложенные запросы, указанные с помощью `IN`. Если такой вложенный запрос возвращает более одного значения, SQL Server отображает сообщение об ошибке.    

Чтобы использовать подзапрос, начинающийся с немодифицированного оператора сравнения, необходимо достаточно хорошо знать свои данные и природу проблемы, чтобы быть уверенным, что вложенный запрос возвратит точно одно значение.     

Например, если предполагается, что каждый менеджер по продажам отвечает только за одну территорию продаж, и нужно найти клиентов, расположенных на территории, за которую отвечает `Linda Mitchell`, можно написать инструкцию с вложенным запросом, начинающимся с простого оператора сравнения =.    

```sql
USE AdventureWorks2016;
GO
SELECT CustomerID
FROM Sales.Customer
WHERE TerritoryID =
    (SELECT TerritoryID
     FROM Sales.SalesPerson
     WHERE BusinessEntityID = 276);
GO
```

Однако если сотрудник `Linda Mitchell` работал более чем с одной территорией продаж, вы получите сообщение об ошибке. Вместо оператора сравнения = может использоваться формулировка `IN` (также может использоваться = ANY).    

Вложенные запросы, начинающиеся с немодифицированных операторов сравнения, часто включают агрегатные функции, потому что они возвращают одиночное значение. Например, следующая инструкция находит названия всех продуктов, у которых цена по прейскуранту больше, чем средняя цена по прейскуранту.     

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ListPrice >
    (SELECT AVG (ListPrice)
     FROM Production.Product);
GO
```     

Поскольку вложенные запросы, начинающиеся с неизмененных операторов сравнения, должны возвращать одиночное значение, они не могут включать предложения `GROUP BY` или `HAVING` (за исключением случаев, когда достоверно известно, что предложение GROUP BY или HAVING возвратит одиночное значение). Например, следующий запрос находит продукты, оцененные выше, чем самый дешевый продукт, который находится в подкатегории 14.     

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ListPrice >
    (SELECT MIN (ListPrice)
     FROM Production.Product
     GROUP BY ProductSubcategoryID
     HAVING ProductSubcategoryID = 14);
GO
```

### <a name="comparison_modified"></a> Операторы сравнения с модификаторами ANY, SOME или ALL
Операторы сравнения с вложенными запросами могут быть уточнены с помощью ключевых слов ALL или ANY. Модификатор SOME является эквивалентом модификатора `ANY` в стандарте ISO.     

Вложенные запросы с измененными операторами сравнения возвращают список из нуля или более значений и могут включать предложения `GROUP BY` или `HAVING`. Эти вложенные запросы могут быть переформулированы с использованием ключевого слова `EXISTS`.     

Рассмотрим, например оператор сравнения >: `>ALL` будет означать "больше любого значения". Другими словами, это сравнение с максимальным значением. Например, `>ALL (1, 2, 3)` означает "больше 3". `>ANY` означает "больше по крайней мере одного значения", т. е. "больше минимума". Поэтому `>ANY (1, 2, 3)` означает "больше 1".
Чтобы строка результата вложенного запроса с `>ALL` удовлетворяла условию, заданному внешним запросом, значение в столбце, для которого вводится вложенный запрос, должно быть больше каждого значения из списка, возвращаемого вложенным запросом.    

Аналогичным образом, чтобы строка результата вложенного запроса с `>ANY` удовлетворяла условию, заданному внешним запросом, значение в столбце, для которого вводится вложенный запрос, должно быть больше хотя бы одного значения из списка, возвращаемого вложенным запросом.    

Следующий запрос сдержит пример вложенного запроса, используемого оператором сравнения с модификатором ANY. Он вернет все продукты, цены на которые больше или равны максимальной цене в любой подкатегории продуктов.    

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ListPrice >= ANY
    (SELECT MAX (ListPrice)
     FROM Production.Product
     GROUP BY ProductSubcategoryID);
GO
```    

Для каждой подкатегории продуктов внутренний запрос найдет максимальную цену. Внешний запрос получит эти значения и определит, какие цены отдельных продуктов больше или равны максимальной цене в любой из подкатегорий продуктов. Если ключевое слово `ANY` заменить на `ALL`, запрос вернет только те продукты, цена которых больше или равна всем ценам, возвращаемым внутренним запросом.    

Если вложенный запрос не возвращает значений, весь запрос не возвратит никаких значений.    

Оператор `=ANY` эквивалентен оператору `IN`. Например, чтобы найти названия всех колес, производимых компанией Adventure Works Cycle, можно использовать `IN` или `=ANY`.

```sql
--Using =ANY
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ProductSubcategoryID =ANY
    (SELECT ProductSubcategoryID
     FROM Production.ProductSubcategory
     WHERE Name = 'Wheels');
GO

--Using IN
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ProductSubcategoryID IN
    (SELECT ProductSubcategoryID
     FROM Production.ProductSubcategory
     WHERE Name = 'Wheels');
GO
```

Вот результирующий набор, возвращаемый любым из этих запросов:

```
Name
--------------------------------------------------
LL Mountain Front Wheel
ML Mountain Front Wheel
HL Mountain Front Wheel
LL Road Front Wheel
ML Road Front Wheel
HL Road Front Wheel
Touring Front Wheel
LL Mountain Rear Wheel
ML Mountain Rear Wheel
HL Mountain Rear Wheel
LL Road Rear Wheel
ML Road Rear Wheel
HL Road Rear Wheel
Touring Rear Wheel

(14 row(s) affected)
```    

Однако оператор `<>ANY` отличается от `NOT IN`: `<>ANY` означает "не равно a или не равно b или не равно c". `NOT IN` означает "не равно a и не равно b и не равно c". `<>ALL` означает то же, что и `NOT IN`.     

Например, следующий запрос отобразит заказчиков, находящихся на территории, где не работает ни один менеджер по продажам.     

```sql
USE AdventureWorks2016;
GO
SELECT CustomerID
FROM Sales.Customer
WHERE TerritoryID <> ANY
    (SELECT TerritoryID
     FROM Sales.SalesPerson);
GO
```    

В результат включены все заказчики, кроме тех, чьим территориям продаж соответствует NULL, так как любая территория, назначенная заказчику, обслуживается менеджером по продажам. Внутренний запрос находит все территории продаж, обслуживаемые менеджерами по продажам, а затем для каждой территории внешний запрос находит заказчиков, которые ей не принадлежат.    

По этой же причине, если использовать `NOT IN` в этом запросе, в результат не войдет ни один из заказчиков.      

Те же результаты можно получить с помощью оператора `<>ALL`, который эквивалентен `NOT IN`.   

### <a name="exists"></a> Вложенные запросы с ключевым словом EXISTS
Если вложенный запрос указывается с помощью ключевого слова `EXISTS`, он выступает в роли проверки на существование. В предложении `WHERE` внешнего запроса проверяется факт существования строк, возвращенных вложенным запросом. Вложенный запрос не выдает никаких данных, а возвращает значение TRUE или FALSE.   

Вложенный запрос, созданный с помощью ключевого слова EXISTS, имеет следующий синтаксис:   

`WHERE [NOT] EXISTS (subquery)`    

Следующий запрос ищет названия всех продуктов, которые находятся в подкатегории Wheels:    

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE EXISTS
    (SELECT * 
     FROM Production.ProductSubcategory
     WHERE ProductSubcategoryID = 
            Production.Product.ProductSubcategoryID
        AND Name = 'Wheels');
GO
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]    

```
Name
--------------------------------------------------
LL Mountain Front Wheel
ML Mountain Front Wheel
HL Mountain Front Wheel
LL Road Front Wheel
ML Road Front Wheel
HL Road Front Wheel
Touring Front Wheel
LL Mountain Rear Wheel
ML Mountain Rear Wheel
HL Mountain Rear Wheel
LL Road Rear Wheel
ML Road Rear Wheel
HL Road Rear Wheel
Touring Rear Wheel

(14 row(s) affected)
```    

Чтобы понять результаты данного запроса, необходимо рассмотреть наименование каждого продукта. Это позволит узнать, возвращается ли в результате выполнения данного вложенного запроса хотя бы одна строка. Иными словами, выдается ли в результате проверки на существование значение TRUE.   

Обратите внимание на то, что вложенные запросы, введенные с помощью ключевого слова EXISTS, отличаются от других вложенных запросов следующим образом. 
-   Перед ключевым словом `EXISTS` не ставится имя столбца, константы или другого выражения.     
-   Список выборки для вложенного запроса, указанного с помощью ключевого слова `EXISTS`, практически всегда состоит из знака "звездочка" (*). Так как производится проверка только на предмет существования строк, удовлетворяющих заданным во вложенном запросе условиям, то нет необходимости выводить имена найденных столбцов.    

Важность ключевого слова `EXISTS` обусловлена тем, что часто без него невозможно найти иное решение без вложенных запросов. Хотя некоторые запросы, созданные с помощью ключевого слова EXISTS, не могут быть выражены по-другому, многие запросы для достижения подобных результатов используют IN или оператор сравнения, измененный с помощью `ANY` или `ALL`.     

Например, предыдущий запрос может быть задан с использованием оператора IN:   

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE ProductSubcategoryID IN
    (SELECT ProductSubcategoryID
     FROM Production.ProductSubcategory
     WHERE Name = 'Wheels');
GO
```   

### <a name="notexists"></a> Вложенные запросы с оператором NOT EXISTS
Оператор `NOT EXISTS` работает так же, как и оператор `EXISTS`, за исключением того, что предложение `WHERE`, в котором используется этот оператор, выполняется, если вложенный запрос не возвращает ни одной строки.    

Например чтобы найти имена продуктов, не находящихся в подкатегории wheels:   

```sql
USE AdventureWorks2016;
GO
SELECT Name
FROM Production.Product
WHERE NOT EXISTS
    (SELECT * 
     FROM Production.ProductSubcategory
     WHERE ProductSubcategoryID = 
            Production.Product.ProductSubcategoryID
        AND Name = 'Wheels');
GO
```   

### <a name="expression"></a> Вложенные запросы, используемые вместо выражения
В языке [!INCLUDE[tsql](../../includes/tsql-md.md)] вложенный запрос может быть заменен в любом месте, где выражение может использоваться в инструкциях `SELECT`, `UPDATE`, `INSERT` и `DELETE`, за исключением списка `ORDER BY`.    

Следующий пример показывает, как можно использовать это улучшение. Запрос находит цены на все горные велосипеды, их среднюю цену и разницу между средней ценой и ценой каждого горного велосипеда.    

```sql
USE AdventureWorks2016;
GO
SELECT Name, ListPrice, 
(SELECT AVG(ListPrice) FROM Production.Product) AS Average, 
    ListPrice - (SELECT AVG(ListPrice) FROM Production.Product)
    AS Difference
FROM Production.Product
WHERE ProductSubcategoryID = 1;
GO
```   

## <a name="see-also"></a>См. также:  
[IN (Transact-SQL)](../../t-sql/language-elements/in-transact-sql.md)       
[EXISTS (Transact-SQL)](../../t-sql/language-elements/exists-transact-sql.md)     
[ALL (Transact-SQL)](../../t-sql/language-elements/all-transact-sql.md)     
[SOME | ANY (Transact-SQL)](../../t-sql/language-elements/some-any-transact-sql.md)     
[Соединения](../../relational-databases/performance/joins.md)    
[Операторы сравнения (Transact-SQL)](../../t-sql/language-elements/comparison-operators-transact-sql.md)       
  
