---
title: DATEDIFF (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: be399382bedbcdd97c90db6bd83d70d01056ab59
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="datediff-transact-sql"></a>DATEDIFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает количество пересеченных границ (целое число со знаком), указанных в аргументе *datepart*, за период времени, указанный в аргументах *startdate* и *enddate*.
  
Сведения о более значительной разнице см. в разделе [DATEDIFF_BIG (Transact-SQL)](../../t-sql/functions/datediff-big-transact-sql.md). Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATEDIFF ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Аргументы  
*datepart*  
Часть аргументов *startdate* и *enddate*, которая задает тип пересекаемых границ. В приведенной ниже таблице перечислены все допустимые аргументы *datepart*. Эквивалентные переменные, определяемые пользователем, являются недопустимыми.
  
|*datepart*|Сокращения|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**чч**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
Выражение, которое можно привести к значению типа **time**, **date**, **smalldatetime**, **datetime**, **datetime2** или **datetimeoffset**. Аргумент *date* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом. *startdate* вычитается из *enddate*.
  
Во избежание неоднозначности используйте четырехзначную запись года. Сведения о двузначном обозначении года см. в статье [Настройка параметра конфигурации сервера two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*enddate*  
См. описание аргумента *startdate*.
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
  
-   Каждое выражение *datepart* и его краткие формы возвращают одно и то же значение.  
  
Если возвращаемое значение лежит вне допустимого диапазона для **int** (от –2 147 483 648 до +2 147 483 647), возвращается сообщение об ошибке. Для **миллисекунды** максимальная разница между *startdate* и *enddate* составляет 24 дня 20 часов 31 минута и 23 647 секунд. Для **секунды** максимальная разница составляет 68 лет.
  
Если обоим аргументам *startdate* и *enddate* присвоено только значение времени, а аргумент *datepart* не содержит значения времени *datepart*, то возвращается значение 0.
  
При вычислении возвращаемого значения смещение часовых поясов для аргументов *startdate* или *enddate* не учитывается.
  
Так как значение типа [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) имеет точность до минуты, то при использовании в аргументах *startdate* и *enddate* значения типа **smalldatetime** секунды и миллисекунды всегда равны 0.
  
Если переменной типа данных date присвоено только значение времени, в качестве недостающей части даты используется значение по умолчанию: 1900-01-01. Если переменой типа данных time или date присвоено только значение даты, в качестве недостающей части времени используется значение по умолчанию: 00:00:00. Если в одном из аргументов *startdate* или *enddate* указано только время, а в другом только дата, в качестве недостающей информации используются значения по умолчанию.
  
Если аргументы *startdate* и *enddate* имеют разные типы данных даты, но при этом один из них имеет больше частей времени или обладает более высокой точностью, значениям недостающих частей другого аргумента присваиваются значения 0.
  
## <a name="datepart-boundaries"></a>Границы, задаваемые аргументом datepart  
Приведенные ниже инструкции имеют одинаковые значения аргументов *startdate* и *enddate*. Указанные даты являются соседними, а временная разница между ними составляет 0,0000001 секунды. Разница между аргументами *startdate* и *enddate* в каждой инструкции пересекает одну календарную или временную границу аргумента *datepart*. Каждое выражение возвращает значение 1. Если в этом примере в аргументах *startdate* и *enddate* указаны различные года и при этом указанные границы находятся в пределах одной календарной недели, то для значения **week** будет возвращено значение 0.
  
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
  
## <a name="remarks"></a>Remarks  
Функция DATEDIFF может использоваться в предложениях WHERE, HAVING, GROUP BY и ORDER BY, а также при составлении списка выбора.
  
Функция DATEDIFF неявно приводит строковые литералы к типу **datetime2**. Это означает, что при передаче даты в виде строки DATEDIFF не поддерживает формат ГЧМ (год, число, месяц). Для использования формата ГЧМ (год, число, месяц) необходимо явно привести строку к типу **datetime** или **smalldatetime**.
  
Указание SET DATEFIRST не влияет на DATEDIFF. DATEDIFF всегда считает воскресенье первым днем недели, чтобы обеспечить детерминизм работы функции.
  
## <a name="examples"></a>Примеры  
В приведенных ниже примерах выражения различного типа используются в качестве аргументов для параметров *startdate* и *enddate*.
  
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
В следующем примере в качестве аргументов *startdate* и *enddate* выступают определенные пользователем переменные.
  
```sql
DECLARE @startdate datetime2 = '2007-05-05 12:10:09.3312722';  
DECLARE @enddate datetime2 = '2007-05-04 12:10:09.3312722';   
SELECT DATEDIFF(day, @startdate, @enddate);  
```  
  
### <a name="c-specifying-scalar-system-functions-for-startdate-and-enddate"></a>В. Указание скалярных системных функций в качестве начальной и конечной даты  
В следующем примере в качестве аргументов *startdate* и *enddate* выступают скалярные системные функции.
  
```sql
SELECT DATEDIFF(millisecond, GETDATE(), SYSDATETIME());  
```  
  
### <a name="d-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>Г. Указание скалярных вложенных запросов и скалярных функций в качестве начальной и конечной даты  
В следующем примере в качестве аргументов *startdate* и *enddate* выступают скалярные вложенные запросы.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day,(SELECT MIN(OrderDate) FROM Sales.SalesOrderHeader),  
    (SELECT MAX(OrderDate) FROM Sales.SalesOrderHeader));  
```  
  
### <a name="e-specifying-constants-for-startdate-and-enddate"></a>Д. Указание констант в качестве начальной и конечной даты  
В следующем примере в качестве аргументов *startdate* и *enddate* используются символьные константы.
  
```sql
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635');  
```  
  
### <a name="f-specifying-numeric-expressions-and-scalar-system-functions-for-enddate"></a>Е. Указание числовых выражений и скалярных системных функций в качестве конечной даты  
В следующем примере в качестве аргумента *enddate* используются числовое выражение `(GETDATE ()+ 1)` и скалярные системные функции `GETDATE` и `SYSDATETIME`.
  
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
В следующем примере в качестве аргумента *startdate*. используется ранжирующая функция.
  
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
В следующем примере в качестве аргумента *startdate* используется агрегатная оконная функция.
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
В приведенных ниже примерах выражения различного типа используются в качестве аргументов для параметров *startdate* и *enddate*.
  
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
В следующем примере в качестве аргументов *startdate* и *enddate* выступают скалярные вложенные запросы.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day,(SELECT MIN(HireDate) FROM dbo.DimEmployee),  
    (SELECT MAX(HireDate) FROM dbo.DimEmployee))   
FROM dbo.DimEmployee;  
  
```  
  
### <a name="k-specifying-constants-for-startdate-and-enddate"></a>Л. Указание констант в качестве начальной и конечной даты  
В следующем примере в качестве аргументов *startdate* и *enddate* используются символьные константы.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635') FROM DimCustomer;  
```  
  
### <a name="l-specifying-ranking-functions-for-startdate"></a>М. Указание ранжирующих функций в качестве начальной даты  
В следующем примере в качестве аргумента *startdate*. используется ранжирующая функция.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
,DATEDIFF(day,ROW_NUMBER() OVER (ORDER BY   
        DepartmentName),SYSDATETIME()) AS RowNumber  
FROM dbo.DimEmployee;  
```  
  
### <a name="m-specifying-an-aggregate-window-function-for-startdate"></a>Н. Указание агрегатной оконной функции в качестве начальной даты  
В следующем примере в качестве аргумента *startdate* используется агрегатная оконная функция.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, DepartmentName  
    ,DATEDIFF(year,MAX(HireDate)  
             OVER (PARTITION BY DepartmentName),SYSDATETIME()) AS SomeValue  
FROM dbo.DimEmployee  
```  
  
## <a name="see-also"></a>См. также раздел
[DATEDIFF_BIG (Transact-SQL)](../../t-sql/functions/datediff-big-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


