---
title: "DATEDIFF (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEDIFF_TSQL
- DATEDIFF
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATEDIFF function [SQL Server]
- time [SQL Server], crossed boundaries
- differences in date and time [SQL Server]
- counting crossed date time boundaries [SQL Server]
- date and time [SQL Server], DATEDIFF
- dates [SQL Server], crossed boundaries
- boundary differences date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- interval dates [SQL Server]
- time [SQL Server], functions
- crossing date time boundaries [SQL Server]
- calculating dates times [SQL Server]
ms.assetid: eba979f2-1a8d-4cce-9d75-b74f9b519b37
caps.latest.revision: 52
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: dba834b51bab48c2bd30d1bbbb4abe11694ab321
ms.contentlocale: ru-ru
ms.lasthandoff: 10/05/2017

---
# <a name="datediff-transact-sql"></a>DATEDIFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает число (целое число со знаком) указанного *datepart* пересекаемых границ между указанным *startdate* и *enddate*.
  
Более значительная разница в разделе [DATEDIFF_BIG &#40; Transact-SQL &#41; ](../../t-sql/functions/datediff-big-transact-sql.md). Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATEDIFF ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Аргументы  
*часть_даты*  
— Это часть *startdate* и *enddate* , указывающий тип пересекаемых границ. В следующей таблице перечислены все допустимые *datepart* аргументы. Эквивалентные переменные, определяемые пользователем, являются недопустимыми.
  
|*часть_даты*|Сокращения|  
|---|---|
|**год**|**yy, yyyy**|  
|**квартал**|**б, q**|  
|**месяц**|**mm, m**|  
|**день года**|**dy, y**|  
|**день**|**дд, d**|  
|**Неделя**|**нед ww**|  
|**час**|**чч**|  
|**минуты**|**mi, n**|  
|**второй**|**ss, s**|  
|**миллисекунды**|**MS**|  
|**микросекунды**|**MCS**|  
|**наносекундных**|**NS**|  
  
*startdate*  
Выражение, которое разрешается к **время**, **даты**, **smalldatetime**, **datetime**, **datetime2**, или **datetimeoffset** значение. *Дата* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом. *StartDate* вычитается из *enddate*.
  
Во избежание неоднозначности используйте четырехзначную запись года. Сведения о двух цифр года см. в разделе [Настройка two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*Дата окончания*  
В разделе *startdate*.
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
  
-   Каждый *datepart* и его краткие формы возвращают одинаковое значение.  
  
Если возвращаемое значение вне допустимого диапазона для **int** (-2147483648 использовать +2,147,483,647), возвращается сообщение об ошибке. Для **миллисекунды** максимальная разница между *startdate* и *enddate* составляет 24 дня 20 часов 31 минута и 23647 секунд. Для **секунды** максимальная разница составляет 68 лет.
  
Если *startdate* и *enddate* оба назначаются только значение времени и *datepart* времени *datepart*, возвращается значение 0.
  
Компонент смещения часового пояса *startdate* или *endate* не используется в вычислении возвращаемого значения.
  
Поскольку [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) имеет точность до минуты, когда **smalldatetime** значение используется для *startdate* или *enddate*, секунд и миллисекунды всегда равны 0, в возвращаемом значении.
  
Если только значение времени будет назначен переменной типа данных date, отсутствует часть даты значение по умолчанию: 1900-01-01. Значение типа date присвоено переменной типа данных даты и времени, если только недостающей части времени значение по умолчанию: 00:00:00. Если параметр *startdate* или *enddate* имеют только время, а другие — только часть даты, времени отсутствует и частей даты устанавливаются значения по умолчанию.
  
Если *startdate* и *enddate* имеют разные типы данных даты и один имеет больше частей времени или другого точность в долях секунды, значениям недостающих частей другого устанавливаются в значение 0.
  
## <a name="datepart-boundaries"></a>границы DatePart  
Следующие операторы с одинаковым *startdate* и тот же *endate*. Указанные даты являются соседними, а временная разница между ними составляет 0,0000001 секунды. Разница между *startdate* и *endate* в каждой инструкции пересекает одну календарную или временную границу его *datepart*. Каждое выражение возвращает значение 1. Если в этом примере указаны различные года и оба *startdate* и *endate* находятся в пределах одной календарной недели, возвращаемое значение для **недели** будет равно 0.
  
```sql
SELECT DATEDIFF(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Замечания  
Функция DATEDIFF может использоваться в предложениях WHERE, HAVING, GROUP BY и ORDER BY, а также при составлении списка выбора.
  
Функция DATEDIFF неявно приводит строковые литералы в качестве **datetime2** типа. Это означает, что при передаче даты в виде строки DATEDIFF не поддерживает формат ГЧМ (год, число, месяц). Необходимо явно привести строку к **datetime** или **smalldatetime** тип, используемый формат ГДМ.
  
Указание SET DATEFIRST не влияет на DATEDIFF. DATEDIFF всегда считает воскресенье первым днем недели, чтобы обеспечить детерминистичность работы функции.
  
## <a name="examples"></a>Примеры  
В следующих примерах выражения различного типа используются как аргументы для *startdate* и *enddate* параметров.
  
### <a name="a-specifying-columns-for-startdate-and-enddate"></a>A. Указание столбцов в качестве начальной и конечной даты  
В следующем примере подсчитывается количество границ дней, пересекаемых между двумя датами, указанных в столбцах таблицы.
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="b-specifying-user-defined-variables-for-startdate-and-enddate"></a>Б. Указание определенных пользователем переменных в качестве начальной и конечной даты  
В следующем примере используется определенных пользователем переменных в качестве аргументов для *startdate* и *enddate*.
  
```sql
DECLARE @startdate datetime2 = '2007-05-05 12:10:09.3312722';  
DECLARE @enddate datetime2 = '2007-05-04 12:10:09.3312722';   
SELECT DATEDIFF(day, @startdate, @enddate);  
```  
  
### <a name="c-specifying-scalar-system-functions-for-startdate-and-enddate"></a>В. Указание скалярных системных функций в качестве начальной и конечной даты  
В следующем примере используется скалярных системных функций в качестве аргументов для *startdate* и *enddate*.
  
```sql
SELECT DATEDIFF(millisecond, GETDATE(), SYSDATETIME());  
```  
  
### <a name="d-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>Г. Указание скалярных вложенных запросов и скалярных функций в качестве начальной и конечной даты  
В следующем примере скалярные вложенные запросы и скалярных функций в качестве аргументов для *startdate* и *enddate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day,(SELECT MIN(OrderDate) FROM Sales.SalesOrderHeader),  
    (SELECT MAX(OrderDate) FROM Sales.SalesOrderHeader));  
```  
  
### <a name="e-specifying-constants-for-startdate-and-enddate"></a>Д. Указание констант в качестве начальной и конечной даты  
В следующем примере используется символьные константы в качестве аргументов для *startdate* и *enddate*.
  
```sql
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635');  
```  
  
### <a name="f-specifying-numeric-expressions-and-scalar-system-functions-for-enddate"></a>Е. Указание числовых выражений и скалярных системных функций в качестве конечной даты  
В следующем примере используется числовое выражение, `(GETDATE ()+ 1)`и скалярные системные функции `GETDATE` и `SYSDATETIME`, как аргументы для *enddate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', GETDATE()+ 1)   
    AS NumberOfDays  
FROM Sales.SalesOrderHeader;  
GO  
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', DATEADD(day,1,SYSDATETIME())) AS NumberOfDays  
FROM Sales.SalesOrderHeader;  
GO  
```  
  
### <a name="g-specifying-ranking-functions-for-startdate"></a>Ж. Указание ранжирующих функций в качестве начальной даты  
В следующем примере используется Ранжирующая функция в качестве аргумента для *startdate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName  
    ,DATEDIFF(day,ROW_NUMBER() OVER (ORDER BY   
        a.PostalCode),SYSDATETIME()) AS 'Row Number'  
FROM Sales.SalesPerson s   
    INNER JOIN Person.Person p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
```  
  
### <a name="h-specifying-an-aggregate-window-function-for-startdate"></a>З. Указание агрегатной оконной функции в качестве начальной даты  
В следующем примере используется Агрегатная оконная функция в качестве аргумента для *startdate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT soh.SalesOrderID, sod.ProductID, sod.OrderQty,soh.OrderDate  
    ,DATEDIFF(day,MIN(soh.OrderDate)   
        OVER(PARTITION BY soh.SalesOrderID),SYSDATETIME() ) AS 'Total'  
FROM Sales.SalesOrderDetail sod  
    INNER JOIN Sales.SalesOrderHeader soh  
        ON sod.SalesOrderID = soh.SalesOrderID  
WHERE soh.SalesOrderID IN(43659,58918);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
В следующих примерах выражения различного типа используются как аргументы для *startdate* и *enddate* параметров.
  
### <a name="i-specifying-columns-for-startdate-and-enddate"></a>И. Указание столбцов в качестве начальной и конечной даты  
В следующем примере подсчитывается количество границ дней, пересекаемых между двумя датами, указанных в столбцах таблицы.
  
```sql
CREATE TABLE dbo.Duration (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT TOP(1) DATEDIFF(day,startDate,endDate) AS Duration  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="j-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>К. Указание скалярных вложенных запросов и скалярных функций в качестве начальной и конечной даты  
В следующем примере скалярные вложенные запросы и скалярных функций в качестве аргументов для *startdate* и *enddate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day,(SELECT MIN(HireDate) FROM dbo.DimEmployee),  
    (SELECT MAX(HireDate) FROM dbo.DimEmployee))   
FROM dbo.DimEmployee;  
  
```  
  
### <a name="k-specifying-constants-for-startdate-and-enddate"></a>Л. Указание констант в качестве начальной и конечной даты  
В следующем примере используется символьные константы в качестве аргументов для *startdate* и *enddate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635') FROM DimCustomer;  
```  
  
### <a name="l-specifying-ranking-functions-for-startdate"></a>М. Указание ранжирующих функций в качестве начальной даты  
В следующем примере используется Ранжирующая функция в качестве аргумента для *startdate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
,DATEDIFF(day,ROW_NUMBER() OVER (ORDER BY   
        DepartmentName),SYSDATETIME()) AS RowNumber  
FROM dbo.DimEmployee;  
```  
  
### <a name="m-specifying-an-aggregate-window-function-for-startdate"></a>Н. Указание агрегатной оконной функции в качестве начальной даты  
В следующем примере используется Агрегатная оконная функция в качестве аргумента для *startdate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, DepartmentName  
    ,DATEDIFF(year,MAX(HireDate)  
             OVER (PARTITION BY DepartmentName),SYSDATETIME()) AS SomeValue  
FROM dbo.DimEmployee  
```  
  
## <a name="see-also"></a>См. также:
[DATEDIFF_BIG &#40; Transact-SQL &#41;](../../t-sql/functions/datediff-big-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  



