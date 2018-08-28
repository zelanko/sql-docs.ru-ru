---
title: TOP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TOP_TSQL
- TOP
dev_langs:
- TSQL
helpviewer_keywords:
- TOP clause
- first set of query result rows [SQL Server]
- TOP clause, about TOP clause
- queries [SQL Server], results
ms.assetid: da983c0a-06c5-4cf8-a6a4-7f9d66f34f2c
caps.latest.revision: 60
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da512cee0b29c2ffec319d16280d2880817cd97a
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43098219"
---
# <a name="top-transact-sql"></a>TOP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Ограничивает число строк, возвращаемых в результирующем наборе запроса до заданного числа или процентного значения в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Когда TOP используется в сочетании с предложением ORDER BY, результирующий набор ограничивается первыми *N* заказанными строками; в противном случае возвращаются первые *N* строк в неопределенном порядке. Это предложение позволяет указать число строк, возвращаемых инструкцией SELECT или обработанных инструкциями INSERT, UPDATE, MERGE и DELETE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[   
    TOP (expression) [PERCENT]  
    [ WITH TIES ]  
]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
[   
    TOP ( expression )   
    [ WITH TIES ]  
]  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Числовое выражение, определяющее количество возвращаемых строк. При указании PERCENT аргумент *expression* неявно преобразуется в тип **float**; в противном случае он преобразуется в тип **bigint**.  
  
 PERCENT  
 Указывает на то, что запрос возвращает только первые *expression* процентов строк из результирующего набора. Дробные значения округляются до следующего целого числа.  
  
 WITH TIES  
 Используется, если требуется вернуть две или более строки, которые совместно занимают последнее место в ограниченном результирующем наборе. Требуется использовать с предложением **ORDER BY**. **WITH TIES** может привести к тому, что будет возвращено строк больше, чем указано в значении *expression*. Например, если *expression* имеет значение 5, но еще 2 строки соответствуют значениям в столбцах **ORDER BY** в строке 5, то результирующий набор будет содержать 7 строк.  
  
 Предложение TOP...WITH TIES может быть задано только в инструкциях SELECT, и только если указано предложение ORDER BY. Порядок возврата связанных записей произволен. ORDER BY не влияет на это правило.  
  
## <a name="best-practices"></a>Рекомендации  
 В инструкции SELECT всегда указывайте ORDER BY вместе с предложением TOP. Это единственный способ предсказуемым образом отметить строки, которые были обработаны предложением TOP.  
  
 Для реализации решения разбиения на страницы пользуйтесь предложениями OFFSET и FETCH в предложении ORDER BY, а не предложением TOP. Решение разбиения на страницы (т.е. постраничной выдачи данных клиенту) проще реализовать с помощью предложений OFFSET и FETCH. Дополнительные сведения см. в разделе [Предложение ORDER BY (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md).  
  
 Для ограничения числа возвращаемых строк пользуйтесь TOP (или OFFSET и FETCH), а не SET ROWCOUNT. Эти методы предпочтительнее, чем SET ROWCOUNT, по следующим причинам:  
  
-   Являясь частью инструкции SELECT, оптимизатор запросов может принимать значение *expression* в предложениях TOP или FETCH во время оптимизации запроса. Поскольку SET ROWCOUNT используется вне инструкции, выполняющей запрос, его значение не может быть учтено при создании плана запроса.  
  
## <a name="compatibility-support"></a>Поддержка совместимости  
 В целях обратной совместимости скобки в инструкции SELECT необязательны. Рекомендуется всегда заключать TOP в скобки в инструкциях SELECT, чтобы обеспечить согласованность его использования с инструкциями INSERT, UPDATE, MERGE и DELETE, где они являются обязательными.  
  
## <a name="interoperability"></a>Совместимость  
 Выражение TOP в запросе не влияет на инструкции, которые могут быть выполнены из-за срабатывания триггера. Таблицы **inserted** и **deleted** в триггерах возвращают только те строки, которые реально обработаны инструкциями INSERT, UPDATE, MERGE или DELETE. Например, если триггер INSERT сработал в результате выполнения инструкции INSERT с предложением TOP,  
  
 то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет обновлять строки через представления. Так как в определение представления может быть включено предложение TOP, определенные строки могут исчезнуть из представления из-за обновления, если строки больше не соответствуют требованиям выражения TOP.  
  
 Если предложение TOP указано в инструкции MERGE, то применяется *после* соединения всей исходной таблицы и всей целевой таблицы и удаления соединенных строк, которые не рассматриваются как предназначенные для выполнения операций вставки, обновления или удаления. Предложение TOP дополнительно сокращает количество соединенных строк до указанного значения, а затем к оставшимся соединенным строкам применяются операции вставки, обновления или удаления без учета порядка. Иными словами, порядок, в котором строки подвергаются операциям, определенным в предложениях WHEN, не задан. Например, указание значения TOP (10) затрагивает 10 строк. Из них 7 могут быть обновлены и 3 вставлены или одна строка может быть удалена, 5 обновлено, 4 вставлено и т. д. Инструкция MERGE выполняет полный просмотр исходной и целевой таблиц, поэтому при использовании предложения TOP для изменения большой таблицы путем создания нескольких пакетов производительность ввода-вывода может снизиться. В этом случае необходимо обеспечить, чтобы во всех подряд идущих пакетах осуществлялась обработка новых строк.  
  
 Указывайте предложение TOP в запросе, содержащем операторы UNION, UNION ALL, EXCEPT и INTERSECT, с осторожностью. Существует возможность, что написанный вложенный запрос вернут непредвиденные результаты, поскольку порядок, в котором логически обрабатываются предложения TOP и ORDER BY, не всегда интуитивно понятен, когда эти операторы используются в операции выбора. Например, исходя из следующих таблиц и данных, предположим, что необходимо вернуть самый недорогой красный и синий автомобили. Иными словами, красный седан и синий фургон.  
  
```sql  
CREATE TABLE dbo.Cars(Model varchar(15), Price money, Color varchar(10));  
INSERT dbo.Cars VALUES  
    ('sedan', 10000, 'red'), ('convertible', 15000, 'blue'),   
    ('coupe', 20000, 'red'), ('van', 8000, 'blue');  
```  
  
 Чтобы получить такие результаты, можно написать следующий запрос.  
  
```sql  
SELECT TOP(1) Model, Color, Price  
FROM dbo.Cars  
WHERE Color = 'red'  
UNION ALL  
SELECT TOP(1) Model, Color, Price  
FROM dbo.Cars  
WHERE Color = 'blue'  
ORDER BY Price ASC;  
GO    
```  
  
 Ниже приводится результирующий набор.  
  
 ```
 Model         Color      Price  
 ------------- ---------- -------  
 sedan         red        10000.00  
 convertible   blue       15000.00
 ```  
  
 Возвращаются непредвиденные результаты, поскольку инструкция TOP логически выполняется раньше, чем предложение ORDER BY, которое сортирует результаты оператора (в данном случае UNION ALL). Таким образом, предыдущие запросы вернут произвольный красный и произвольный синий автомобили, а затем отсортируют результат объединения по цене. Следующий пример показывает, как правильно написать запрос, который позволит получить нужный результат.  
  
```sql  
SELECT Model, Color, Price  
FROM (SELECT TOP(1) Model, Color, Price  
      FROM dbo.Cars  
      WHERE Color = 'red'  
      ORDER BY Price ASC) AS a  
UNION ALL  
SELECT Model, Color, Price  
FROM (SELECT TOP(1) Model, Color, Price  
      FROM dbo.Cars  
      WHERE Color = 'blue'  
      ORDER BY Price ASC) AS b;  
GO    
```  
  
 Использование TOP и ORDER BY во вложенной операции выбора гарантирует, что результаты предложения ORDER BY применяются к инструкции TOP, а не к сортировке результата операции UNION.  
  
 Ниже приводится результирующий набор.  
  
 ```
 Model         Color      Price  
 ------------- ---------- -------  
 sedan         red        10000.00  
 van           blue        8000.00
 ```  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 При использовании TOP в инструкциях INSERT, UPDATE, MERGE и DELETE указанные строки никак не упорядочены и предложение ORDER BY не может быть прямо указано в этих инструкциях. Если необходимо использовать TOP при вставке, удалении или изменении строк в определенном хронологическом порядке, необходимо использовать TOP в сочетании с предложением ORDER BY, указанным в инструкции подзапроса выборки. См. подраздел «Примеры» далее в этом разделе.  
  
 Предложение TOP не может быть использовано вместе с инструкциями UPDATE и DELETE для секционированных представлений.  
  
 TOP нельзя сочетать с OFFSET и FETCH в одном выражении запроса (в той же области запроса). Дополнительные сведения см. в разделе [Предложение ORDER BY (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
|Категория|Используемые элементы синтаксиса|  
|--------------|------------------------------|  
|[Основной синтаксис](#BasicSyntax)|TOP • PERCENT|  
|[Включить равные значения](#tie)|WITH TIES|  
|[Ограничение числа строк, обрабатываемых инструкциями DELETE, INSERT и UPDATE](#DML)|DELETE • INSERT • UPDATE|  
  
###  <a name="BasicSyntax"></a> Основной синтаксис  
 В примерах этого раздела показана базовая функциональность предложения ORDER BY с использованием минимально необходимого синтаксиса.  
  
#### <a name="a-using-top-with-a-constant-value"></a>A. Использование ключевого слова TOP со значением константы  
 В следующих примерах константа указывает число сотрудников, возвращаемых в результирующем наборе запроса. В первом примере возвращаются 10 произвольных строк, так как отсутствует предложение ORDER BY. Во втором примере предложение ORDER BY возвращает 10 сотрудников, последними принятых на работу.  
  
```sql  
USE AdventureWorks2012;  
GO  
-- Select the first 10 random employees.  
SELECT TOP(10)JobTitle, HireDate  
FROM HumanResources.Employee;  
GO  
-- Select the first 10 employees hired most recently.  
SELECT TOP(10)JobTitle, HireDate  
FROM HumanResources.Employee  
ORDER BY HireDate DESC;  
GO  
```  
  
#### <a name="b-using-top-with-a-variable"></a>Б. Использование ключевого слова TOP с переменной  
 В следующем примере переменная указывает число сотрудников, возвращаемых в результирующем наборе запроса.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @p AS int = 10;  
SELECT TOP(@p)JobTitle, HireDate, VacationHours  
FROM HumanResources.Employee  
ORDER BY VacationHours DESC;  
GO  
```  
  
#### <a name="c-specifying-a-percentage"></a>В. Указание процентов  
 В следующем примере PERCENT указывает число сотрудников, возвращаемых в результирующем наборе запроса. В таблице `HumanResources.Employee` содержится 290 сотрудников. Поскольку 5% от 290 является дробным числом, значение округляется до следующего целого числа.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT TOP(5)PERCENT JobTitle, HireDate  
FROM HumanResources.Employee  
ORDER BY HireDate DESC;  
GO    
```  
  
###  <a name="tie"></a> Включить равные значения  
  
#### <a name="a-using-with-ties-to-include-rows-that-match-the-values-in-the-last-row"></a>A. Использование ключевого слова WITH TIES для включения строк, соответствующих значениям в последней строке  
 Следующий пример извлекает первые `10` процентов работников с наибольшей зарплатой и возвращает их в порядке убывания размера зарплаты. Указание параметра `WITH TIES` позволяет быть уверенным в том, что все работники с зарплатой, равной минимальной возвращенной зарплате (последняя строка), включены в результирующий набор, даже если это приведет к превышению ограничения в `10` процентов работников.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT TOP(10) PERCENT WITH TIES  
pp.FirstName, pp.LastName, e.JobTitle, e.Gender, r.Rate  
FROM Person.Person AS pp   
    INNER JOIN HumanResources.Employee AS e  
        ON pp.BusinessEntityID = e.BusinessEntityID  
    INNER JOIN HumanResources.EmployeePayHistory AS r  
        ON r.BusinessEntityID = e.BusinessEntityID  
ORDER BY Rate DESC;  
GO    
```  
  
###  <a name="DML"></a> Ограничение числа строк, обрабатываемых инструкциями DELETE, INSERT и UPDATE  
  
#### <a name="a-using-top-to-limit-the-number-of-rows-deleted"></a>A. Ограничение числа удаляемых строк с помощью ключевого слова TOP  
 Если с инструкцией DELETE применяется предложение TOP (*n*), то операция удаления производится с произвольной выборкой из *n* строк. Таким образом, инструкция DELETE выбирает любое число (*n*) строк, которые удовлетворяют условию, указанному в предложении WHERE. Следующий пример удаляет `20` строк из таблицы `PurchaseOrderDetail`, имеющих дату ранее 1 июля 2002 г.  
  
```sql  
USE AdventureWorks2012;  
GO  
DELETE TOP (20)   
FROM Purchasing.PurchaseOrderDetail  
WHERE DueDate < '20020701';  
GO  
```  
  
 Если необходимо с помощью предложения TOP удалять строки в значимом хронологическом порядке, то вместе с ним в инструкции вложенного запроса выборки следует использовать ORDER BY. Следующий запрос удаляет из таблицы `PurchaseOrderDetail` 10 строк, имеющих самую раннюю дату. Чтобы гарантировать удаление только 10 строк, столбец, указанный в инструкции подзапроса выборки (`PurchaseOrderID`) должен являться первичным ключом таблицы. Использование неключевого столбца в инструкции подзапроса выборки может привести к удалению более чем 10 строк, если указанный столбец содержит повторяющиеся значения.  
  
```sql  
USE AdventureWorks2012;  
GO  
DELETE FROM Purchasing.PurchaseOrderDetail  
WHERE PurchaseOrderDetailID IN  
   (SELECT TOP 10 PurchaseOrderDetailID   
    FROM Purchasing.PurchaseOrderDetail   
    ORDER BY DueDate ASC);  
GO  
```  
  
#### <a name="b-using-top-to-limit-the-number-of-rows-inserted"></a>Б. Ограничение числа вставляемых строк с помощью ключевого слова TOP  
 В следующем примере создается таблица `EmployeeSales` и вставляется имя и данные о продажах за текущий год для 5 наиболее успешных сотрудников, случайно выбираемых в таблице `HumanResources.Employee`. Инструкция INSERT выбирает любые 5 строк, возвращаемых инструкцией `SELECT`, удовлетворяющих определенному условию в предложении WHERE.  Предложение OUTPUT отображает строки, вставляемые в таблицу `EmployeeSales`. Обратите внимание, что предложение ORDER BY в инструкции SELECT не используется для определения 5 наиболее успешных сотрудников.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
IF OBJECT_ID ('dbo.EmployeeSales', 'U') IS NOT NULL  
    DROP TABLE dbo.EmployeeSales;  
GO  
CREATE TABLE dbo.EmployeeSales  
( EmployeeID   nvarchar(11) NOT NULL,  
  LastName     nvarchar(20) NOT NULL,  
  FirstName    nvarchar(20) NOT NULL,  
  YearlySales  money NOT NULL  
 );  
GO  
INSERT TOP(5)INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, inserted.LastName, inserted.YearlySales  
    SELECT sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
GO    
```  
  
 Если для вставки строк в значимом хронологическом порядке решено использовать предложение TOP, вместе с ним в инструкции подзапроса выборки следует использовать предложение ORDER BY, как показано в следующем примере. Предложение OUTPUT отображает строки, вставляемые в таблицу `EmployeeSales`. Обратите внимание, что вставка данных пяти наиболее успешных сотрудников выполняется теперь на основе результатов предложения ORDER BY, а не произвольных строк.  
  
```sql  
INSERT INTO dbo.EmployeeSales  
    OUTPUT inserted.EmployeeID, inserted.FirstName, inserted.LastName, inserted.YearlySales  
    SELECT TOP (5) sp.BusinessEntityID, c.LastName, c.FirstName, sp.SalesYTD   
    FROM Sales.SalesPerson AS sp  
    INNER JOIN Person.Person AS c  
        ON sp.BusinessEntityID = c.BusinessEntityID  
    WHERE sp.SalesYTD > 250000.00  
    ORDER BY sp.SalesYTD DESC;  
GO    
```  
  
#### <a name="c-using-top-to-limit-the-number-of-rows-updated"></a>В. Ограничение числа обновляемых строк с помощью ключевого слова TOP  
 В следующем примере предложение TOP используется для обновления строк в таблице. Если предложение TOP (*n*) используется с инструкцией UPDATE, то операция обновления выполняется для произвольного подмножества строк. Таким образом, инструкция UPDATE выбирает любое число (*n*) строк, которые удовлетворяют условию, указанному в предложении WHERE. В следующем примере 10 случайно выбранных заказчиков переназначаются от одного менеджера по продажам к другому.  
  
```sql  
USE AdventureWorks2012;  
UPDATE TOP (10) Sales.Store  
SET SalesPersonID = 276  
WHERE SalesPersonID = 275;  
GO  
```  
  
 Если нужно применить изменения с предложением TOP в определенной последовательности, укажите во вложенном запросе SELECT предложение ORDER BY. В следующем примере изменяется длительность отпуска для 10 сотрудников, имеющих наибольший стаж работы.  
  
```sql  
UPDATE HumanResources.Employee  
SET VacationHours = VacationHours + 8  
FROM (SELECT TOP 10 BusinessEntityID FROM HumanResources.Employee  
     ORDER BY HireDate ASC) AS th  
WHERE HumanResources.Employee.BusinessEntityID = th.BusinessEntityID;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В приведенном ниже примере возвращаются первые строки (31), соответствующие условию запроса. Предложение **ORDER BY** гарантирует, что возвращаемые строки — это первые строки из столбца `LastName` с сортировкой по алфавиту.  
  
 Использование **TOP** без указания равных элементов.  
  
```sql  
SELECT TOP (31) FirstName, LastName   
FROM DimEmployee ORDER BY LastName;  
```  
  
 Результат: возвращается 31 строка.  
  
 Использование TOP с указанием WITH TIES.  
  
```sql  
SELECT TOP (31) WITH TIES FirstName, LastName   
FROM DimEmployee ORDER BY LastName;  
```  
  
 Результат: возвращаются 33 строки, так как 31-й строке соответствуют 3 сотрудника с именем Brown.  
  
## <a name="see-also"></a>См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [Предложение ORDER BY &#40;Transact-SQL&#41;](../../t-sql/queries/select-order-by-clause-transact-sql.md)   
 [SET ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/statements/set-rowcount-transact-sql.md)   
 [MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)  
  
 
