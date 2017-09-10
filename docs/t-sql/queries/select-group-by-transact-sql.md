---
title: "GROUP BY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GROUP
- CUBE
- ROLLUP
- GROUPING_SETS_TSQL
- GROUP BY
- GROUPING SETS
- GROUP_BY_TSQL
- GROUP_TSQL
- CUBE_TSQL
- ROLLUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GROUP BY clause, about GROUP BY clause
- dividing tables into groups
- GROUPING SETS
- GROUP BY clause
- table groups [SQL Server]
- groups [SQL Server], tables divided into groups
- summary values [SQL Server]
ms.assetid: 40075914-6385-4692-b4a5-62fe44ae6cb6
caps.latest.revision: 80
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 01e2c02cade5b84f3560fe5cb415cece4f815abf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="select---group-by--transact-sql"></a>ВЫБЕРИТЕ - GROUP BY - Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Предложение инструкции SELECT, которая разделяет результат запроса в группы строк, обычно с целью выполнение одного или нескольких статистических выражений в каждой группе. Инструкция SELECT возвращает одну строку для каждой группы.  
  
## <a name="syntax"></a>Синтаксис  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
```  
-- Syntax for SQL Server and Azure SQL Database   
-- ISO-Compliant Syntax  
  
GROUP BY {
      column-expression  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
    | GROUPING SETS ( <grouping_set> [ ,...n ]  )  
    | () --calculates the grand total 
} [ ,...n ] 
 
<group_by_expression> ::=  
      column-expression  
    | ( column-expression [ ,...n ] )    
   
<grouping_set> ::=  
      () --calculates the grand total  
    | <grouping_set_item>  
    | ( <grouping_set_item> [ ,...n ] )  
  
<grouping_set_item> ::=  
      <group_by_expression>  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
  

-- For backward compatibility only.
-- Non-ISO-Compliant Syntax for SQL Server and Azure SQL Database 
  
GROUP BY 
      [ ALL ] column-expression [ ,...n ] 
    | column-expression [ ,...n ] [ WITH { CUBE | ROLLUP } ]   

```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GROUP BY {
      column-name [ WITH (DISTRIBUTED_AGG) ]  
    | column-expression
} [ ,...n ]

```  
  
## <a name="arguments"></a>Аргументы 
 
### <a name="column-expression"></a>*выражение столбца*  
Указывает на столбец столбцом или нестатистическим вычисления. Этот столбец может принадлежать таблице, производную таблицу или представление. Столбец должен быть указан в предложении FROM инструкции SELECT, но не обязательно должен отображаться в списке ВЫБОРА. 

Допустимые выражения. в разделе [выражение](~/t-sql/language-elements/expressions-transact-sql.md).    

Столбец должен быть указан в предложении FROM инструкции SELECT, но не обязательно должен отображаться в списке ВЫБОРА. Однако каждая таблица или представление столбцов во всех нестатистических выражениях в \<выберите > список должны быть включены в список GROUP BY:  
  
Следующие инструкции являются допустимыми.  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + ColumnB + constant FROM T GROUP BY ColumnA, ColumnB;  
    ```  
  
Следующие инструкции не являются допустимыми.  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + constant + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    ```  
Не может содержать выражение столбца:

- Псевдоним столбца, определенный в списке ВЫБОРА. Его можно использовать псевдоним столбца для производной таблицы, определенные в предложении FROM.
- Столбец типа **текст**, **ntext**, или **изображения**. Тем не менее можно использовать как аргумент в функцию, возвращающую значение допустимый тип данных столбца text, ntext или image. Например выражение может использовать SUBSTRING() и CAST(). Это также относится к выражениям в предложении HAVING.
- методы типа данных XML. Он может включать определяемой пользователем функции, которая использует методы типа данных xml. Он может включать вычисляемый столбец, который использует методы типа данных xml. 
- Вложенный запрос. Возвращается ошибка 144. 
- Столбец из индексированного представления. 
 
### <a name="group-by-column-expression--n-"></a>GROUP BY *выражение столбца* [,.. .n] 

Группирует результаты инструкции SELECT в соответствии со значениями в списке один или несколько столбцов выражений. 

Например этот запрос создает таблицу Sales со столбцами для страны, региона и Sales. Он вставляет четыре строки и две строки имеют совпадающих значений для страны и региона.  

```
CREATE TABLE Sales ( Country varchar(50), Region varchar(50), Sales int );

INSERT INTO sales VALUES (N'Canada', N'Alberta', 100);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 200);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 300);
INSERT INTO sales VALUES (N'United States', N'Montana', 100);
```
Таблица Sales содержит эти строки.

| Страна | Регион | Продажи |
|---------|--------|-------|
| Canada | Альберта | 100 |
| Canada | Британская Колумбия | 200 |
| Canada | Британская Колумбия | 300 |
| United States | Монтана | 100 |

Этот следующий запрос группирует страны и региона и возвращает статистическую сумму для каждого сочетания значений.  
 
``` 
SELECT Country, Region, SUM(sales) AS TotalSales
FROM Sales
GROUP BY Country, Region;
```
Результат запроса имеет 3 строки, так как имеются 3 сочетаний значений для страны и региона. TotalSales для Канады и Британской Колумбии является суммой двух строк. 

| Страна | Регион | TotalSales |
|---------|--------|-------|
| Canada | Альберта | 100 |
| Canada | Британская Колумбия | 500 |
| United States | Монтана | 100 |

### <a name="group-by-rollup"></a>GROUP BY ROLLUP

Создает группу для каждого сочетания столбца выражений. Кроме того он «сведение» результаты в промежуточные и общие итоги. Чтобы сделать это, он перемещает справа налево, уменьшая число выражений столбца, за которые он создает группы и aggregation(s). 

Порядок столбцов влияет на вывод ROLLUP и может повлиять на количество строк в результирующем наборе.  

Например `GROUP BY ROLLUP (col1, col2, col3, col4)` создает группы для каждой комбинации столбцов выражений в следующих списках.  

- Col1, col2, col3, col4 
- Col1, col2, col3 NULL
- Col1, col2, NULL, значение NULL
- Col1, NULL, NULL, значение NULL
- Значение NULL, NULL, NULL, NULL — это общий итог

С помощью таблицы из предыдущего примера, этот код запускает операцию GROUP BY ROLLUP вместо простого предложения GROUP BY.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region);
```

Результат запроса имеет одинаковые статистические схемы как простое предложение GROUP BY без накопительный пакет обновления. Кроме того он создает подытоги для каждого значения страны. Наконец он предоставляет общий итог для всех строк. Результат выглядит следующим образом:

| Страна | Регион | TotalSales |
| :------ | :----- | ---------: |
| Canada | Альберта | 100 |
| Canada | Британская Колумбия | 500 |
| Canada | NULL | 600 |
| United States | Монтана | 100 |
| United States | NULL | 100 |
| NULL | NULL | 700 |

### <a name="group-by-cube--"></a>GROUP BY CUBE)  

GROUP BY CUBE создает группы для всех возможных сочетаний столбцов. Для GROUP BY CUBE (a, b) результаты имеет группы для уникальных значений (a, b) (значение NULL, b), (a, NULL) и (значение NULL, значение NULL).

С помощью таблицы из предыдущих примерах, этот код выполняется на GROUP BY CUBE операцию страны и региона. 

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region);
```

Результат запроса имеет группы для уникальных значений (Страна, регион), (значение NULL, регион), (Country, NULL) и (значение NULL, значение NULL). Результат будет выглядеть следующим образом:

| Страна | Регион | TotalSales |
|---------|--------|-------|
| Canada | Альберта | 100 |
| NULL | Альберта | 100 |
| Canada | Британская Колумбия | 500 |
| NULL | Британская Колумбия | 500 |
| United States | Монтана | 100 |
| NULL | Монтана | 100 |
| NULL | NULL | 700
| Canada | NULL | 600 |
| United States | NULL | 100 |
   
 ### <a name="group-by-grouping-sets--"></a>ГРУППЫ С ПОМОЩЬЮ ГРУППИРОВАНИЯ НАБОРОВ)  
 
Параметр GROUPING SETS позволяет объединять несколько предложений GROUP BY в одно предложение GROUP BY. Результаты эквивалентны тем, что формируются с применением конструкции UNION ALL к указанным группам. 

Например `GROUP BY ROLLUP (Country, Region)` и `GROUP BY GROUPING SETS ( ROLLUP (Country, Region) )` возвращают одинаковые результаты. 

Когда ГРУППИРУЮЩИХ НАБОРОВ имеет два или более элементов, результаты будут объединения элементов. Этот пример возвращает объединение результатов операторов ROLLUP и CUBE для страны и региона.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( ROLLUP (Country, Region), CUBE (Country, Region) );
```

Результаты будут такими же, как этот запрос, которая возвращает объединение двух предложений GROUP BY.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region)
UNION ALL
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region)
;
```

SQL не консолидировать повторяющиеся группы, созданные для списка GROUPING SETS. Например, в `GROUP BY ( (), CUBE (Country, Region) )`, оба элемента возвращают строку для общего итога, и обе строки будут перечислены в списке результатов. 

 ### <a name="group-by-"></a>GROUP BY ()  
Указывает пустую группу, что приводит к созданию общего итога. Это полезно как один НАБОР ГРУППИРОВАНИЯ элементов. Например Эта инструкция предоставляет общий объем продаж для каждой страны и затем предоставляет общий итог для всех стран.

```
SELECT Country, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( Country, () );
```

### <a name="group-by--all--column-expression--n-"></a>GROUP BY [ALL]-выражение столбца [,.. .n] 

Применяется к: SQL Server и база данных Azure SQL

Примечание: Этот синтаксис предоставляется только для обратной совместимости. Он будет удален в будущей версии. Избегайте использования этого синтаксиса в новых разработках и запланируйте изменение приложений, которые в настоящее время используется следующий синтаксис.

Указывает, что включены все группы в результатах независимо от того, является ли они соответствуют критериям поиска в предложении WHERE. Группы, которые не соответствуют критериям поиска имеют значение NULL для статистической обработки. 

ГРУППИРОВКА ВСЕХ:
- Не поддерживается в запросах, обращающихся к удаленным таблицам, если в запросе присутствует также предложение WHERE.
- На столбцы, имеющие атрибут FILESTREAM завершится сбоем.
  
### <a name="with-distributedagg"></a>С ПОМОЩЬЮ (DISTRIBUTED_AGG)
Применяется к: хранилище данных Azure SQL и параллельные хранилища данных

Указание DISTRIBUTED_AGG запроса заставляет систему расширенной параллельной обработке (MPP), чтобы распространять для определенного столбца таблицы, прежде чем выполнять статистическое вычисление. Только один столбец в предложении GROUP BY может иметь DISTRIBUTED_AGG подсказки в запросе. После завершения запроса, распространяемых таблица удаляется. Исходная таблица не изменен.  

Примечание: Указание DISTRIBUTED_AGG запроса предоставляется для обеспечения обратной совместимости с более ранними версиями параллельного хранилища данных и не улучшит производительность для большинства запросов. По умолчанию MPP уже перераспределяет данные при необходимости для повышения производительности для агрегатов. 
  
## <a name="general-remarks"></a>Общие замечания

### <a name="how-group-by-interacts-with-the-select-statement"></a>Способ взаимодействия GROUP BY в инструкции SELECT
Список ВЫБОРА:
- Векторные статистические выражения. Если в списке SELECT включены агрегатные функции, GROUP BY вычисляет сводное значение для каждой группы. (Они известны как векторные статистические выражения.) 
- Ключевым словом DISTINCT. Статистические функции AVG (DISTINCT *column_name*), COUNT (DISTINCT *column_name*) и SUM (DISTINCT *column_name*) с ROLLUP, CUBE и GROUPING SETS поддерживаются.
  
Предложение WHERE:
- SQL удаляет строки, которые не соответствуют условиям в предложении WHERE перед выполнением любых операций группирования.  
  
Предложение HAVING:
- SQL используется в предложении having предложение для фильтрации групп в результирующем наборе. 
  
Предложение ORDER BY:
- Чтобы упорядочить результирующий набор, необходимо использовать предложение ORDER BY. Применение предложения GROUP BY не упорядочивает результирующий набор. 
  
Значения NULL:
- Если столбец группирования содержит значения NULL, все значения NULL считаются равными, и они будут собраны в одну группу.   
  
## <a name="limitations-and-restrictions"></a>Ограничения

Применяется к: SQL Server (начиная с 2008) и хранилище данных SQL Azure

### <a name="maximum-capacity"></a>Максимальная емкость

Для предложения GROUP BY, использующий ROLLUP, CUBE или GROUPING SETS максимальное количество выражений — 32. Максимальное число групп равно 4096 (2<sup>12</sup>). Следующие примеры сбоем, поскольку в предложении GROUP BY имеет более чем 4096 группы.  
 
-   В следующем примере формируются 4097 (2<sup>12</sup> + 1) группирующих наборов и завершится с ошибкой.  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), b )  
    ```  
  
-   В следующем примере формируются 4097 (2<sup>12</sup> + 1) группы и завершится ошибкой. И функция `CUBE ()`, и группирующий набор `()` формируют строку общего итога, а повторяющиеся группирующие наборы не устраняются.  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), ())  
    ```  

-   В этом примере используется синтаксис обратную совместимость. Он создает 8192 (2<sup>13</sup>) группирующих наборов и завершится с ошибкой.  
  
    ```  
    GROUP BY CUBE (a1, ..., a13)   
    GROUP BY a1, ..., a13 WITH CUBE   
    ```    
    Для обратной совместимости предложений GROUP BY, не содержащие CUBE или ROLLUP номер группы, элементы, ограничивается размером столбцов GROUP BY, статистически обрабатываемых столбцов и статистических значений, включенных в запрос. Это объясняется ограничением размера промежуточной рабочей таблицы (8 060 байт), необходимой для хранения промежуточных результатов запроса. При указании CUBE или ROLLUP максимально разрешенное количество выражений группирования равно 12.

### <a name="support-for-iso-and-ansi-sql-2006-group-by-features"></a>Поддержка функций предложения GROUP BY, совместимых с ISO и ANSI SQL-2006

В предложении GROUP BY поддерживаются все функции GROUP BY, включенные в стандарте SQL-2006, со следующими исключениями синтаксис:  
  
-   Применение группирующих наборов в предложении GROUP BY недопустимо, если они не составляют часть явного списка GROUPING SETS. Например `GROUP BY Column1, (Column2, ...ColumnN`) допустимо в стандарте, но не в Transact-SQL.  Transact-SQL поддерживает `GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))` и `GROUP BY Column1, Column2, ... ColumnN`, которые семантически эквивалентны. Эти инструкции семантически эквивалентны предыдущему примеру предложения `GROUP BY`. Это позволяет избежать возможности, `GROUP BY Column1, (Column2, ...ColumnN`) может быть ошибочно интерпретирована как `GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))`, не являющихся семантически эквивалентны.  
  
-   Применение группирующих наборов внутри группирующих наборов не допускается. Например `GROUP BY GROUPING SETS (A1, A2,…An, GROUPING SETS (C1, C2, ...Cn))` допустимо в стандарте SQL-2006, но не в Transact-SQL. Transact-SQL позволяет `GROUP BY GROUPING SETS( A1, A2,...An, C1, C2, ...Cn )` или `GROUP BY GROUPING SETS( (A1), (A2), ... (An), (C1), (C2), ... (Cn) )`, которые семантически эквивалентны в первом примере GROUP BY и имеют более четко синтаксис.  
  
-   GROUP BY [ALL/DISTINCT] допускается только в простого предложения GROUP BY, содержит столбец выражения. Не допускается с конструкции GROUPING SETS, ROLLUP, CUBE, WITH CUBE или WITH ROLLUP. Ключевое слово ALL применяется по умолчанию и задано неявно. Допускается только в обратной совместимости синтаксиса.
  
### <a name="comparison-of-supported-group-by-features"></a>Сравнение поддерживаемых функций предложения GROUP BY  
 В следующей таблице описаны функции GROUP BY, которые поддерживаются на основе версии SQL и уровень совместимости базы данных.  
  
|Компонент|службы SQL Server Integration Services|Уровень совместимости SQL Server — 100 или более|Уровень совместимости SQL Server 2008 или более поздней версии — 90.|  
|-------------|-------------------------------------|--------------------------------------------------|-----------------------------------------------------------|  
|Статистические функции DISTINCT|Не поддерживаются для конструкций WITH CUBE или WITH ROLLUP.|Поддерживаются для конструкций WITH CUBE, WITH ROLLUP, GROUPING SETS, CUBE или ROLLUP.|Аналогично уровню совместимости 100.|  
|Определяемая пользователем функция с именем CUBE или ROLLUP в предложении GROUP BY|Определяемая пользователем функция **dbo.cube (***arg1***,***.. .argN***)** или  **dbo.ROLLUP (***arg1***,**... *argN***)** предложение допустимо в GROUP BY.<br /><br /> Например: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`.|Определяемая пользователем функция **dbo.cube (***arg1***,**.. .argN**)** или **dbo.rollup (**arg1**,***.. .argN***)** в GROUP BY предложение не допускается.<br /><br /> Например: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`.<br /><br /> Возвращается сообщение об ошибке: «неправильный синтаксис около ключевого слова «куба» &#124; " Свертка ".»<br /><br /> Чтобы избежать этой проблемы, замените конструкцию `dbo.cube` на `[dbo].[cube]` или конструкцию `dbo.rollup` на `[dbo].[rollup]`.<br /><br /> Следующий пример является допустимым:`SELECT SUM (x) FROM T  GROUP BY [dbo].[cube](y);`|Определяемая пользователем функция **dbo.cube (***arg1***,***.. .argN*) или **dbo.rollup (** *arg1***,***.. .argN***)** предложение допустимо в GROUP BY<br /><br /> Например: `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`.|  
|GROUPING SETS|Не поддерживается|Поддерживается|Поддерживается|  
|CUBE|Не поддерживается|Поддерживается|Не поддерживается|  
|ROLLUP|Не поддерживается|Поддерживается|Не поддерживается|  
|Общий итог, такой как GROUP BY ()|Не поддерживается|Поддерживается|Поддерживается|  
|GROUPING_ID, функция|Не поддерживается|Поддерживается|Поддерживается|  
|GROUPING, функция|Поддерживается|Поддерживается|Поддерживается|  
|WITH CUBE|Поддерживается|Поддерживается|Поддерживается|  
|WITH ROLLUP|Поддерживается|Поддерживается|Поддерживается|  
|Удаление «повторяющегося» группирования с помощью конструкции WITH CUBE или WITH ROLLUP|Поддерживается|Поддерживается|Поддерживается| 
 
  
## <a name="examples"></a>Примеры  
  
### <a name="a-use-a-simple-group-by-clause"></a>A. Использование простого предложения GROUP BY  
 В следующем примере извлекается сумма для каждого `SalesOrderID` из таблицы `SalesOrderDetail`. В этом примере используется AdventureWorks.  
  
```  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail AS sod  
GROUP BY SalesOrderID  
ORDER BY SalesOrderID;  
```  
  
### <a name="b-use-a-group-by-clause-with-multiple-tables"></a>Б. Использование предложения GROUP BY с несколькими таблицами  
 В следующем примере из таблицы `City`, соединенной с таблицей `Address`, получается количество работников для каждого города `EmployeeAddress`. В этом примере используется AdventureWorks. 
  
```  
SELECT a.City, COUNT(bea.AddressID) EmployeeCount  
FROM Person.BusinessEntityAddress AS bea   
    INNER JOIN Person.Address AS a  
        ON bea.AddressID = a.AddressID  
GROUP BY a.City  
ORDER BY a.City;  
```  
  
### <a name="c-use-a-group-by-clause-with-an-expression"></a>В. Использовать предложение GROUP BY с выражением  
 В следующем примере показано, как извлечь данные об общем объеме продаж за каждый год с помощью функции `DATEPART`. Одно и то же выражение должно присутствовать как в списке `SELECT`, так и в предложении `GROUP BY`.  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
### <a name="d-use-a-group-by-clause-with-a-having-clause"></a>Г. Использование предложения GROUP BY с предложением HAVING  
 В следующем примере используется предложение `HAVING`, чтобы указать, какая из групп, сформированная в предложении `GROUP BY`, должна быть включена в результирующий набор.  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
HAVING DATEPART(yyyy,OrderDate) >= N'2003'  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
## <a name="examples-sql-data-warehouse-and-parallel-data-warehouse"></a>Примеры: Хранилище данных SQL и параллельные хранилища данных  
  
### <a name="e-basic-use-of-the-group-by-clause"></a>Д. Использование предложения GROUP BY  
 В следующем примере вычисляется общая сумма всех продаж за каждый день. Возвращается одна строка, содержащая сумму всех продаж за каждый день.  
  
```  
-- Uses AdventureWorksDW  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales FROM FactInternetSales  
GROUP BY OrderDateKey ORDER BY OrderDateKey;  
```  
  
### <a name="f-basic-use-of-the-distributedagg-hint"></a>Е. Использование указания DISTRIBUTED_AGG  
 В этом примере показано использование указания запроса DISTRIBUTED_AGG принудительно устройства, в таблице в случайном порядке на `CustomerKey` столбца перед выполнением статистической обработки.  
  
```  
-- Uses AdventureWorksDW  
  
SELECT CustomerKey, SUM(SalesAmount) AS sas  
FROM FactInternetSales  
GROUP BY CustomerKey WITH (DISTRIBUTED_AGG)  
ORDER BY CustomerKey DESC;  
```  
  
### <a name="g-syntax-variations-for-group-by"></a>Ж. Варианты синтаксиса для GROUP BY  
 Когда список выбора нет агрегатов, каждый столбец в списке выбора должен включаться в списке GROUP BY. Вычисляемые столбцы в списке выборки можно указать, но не являются обязательными в списке GROUP BY. Ниже приведены примеры синтаксически правильные инструкции SELECT:  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, FirstName FROM DimCustomer GROUP BY LastName, FirstName;  
SELECT NumberCarsOwned FROM DimCustomer GROUP BY YearlyIncome, NumberCarsOwned;  
SELECT (SalesAmount + TaxAmt + Freight) AS TotalCost FROM FactInternetSales GROUP BY SalesAmount, TaxAmt, Freight;  
SELECT SalesAmount, SalesAmount*1.10 SalesTax FROM FactInternetSales GROUP BY SalesAmount;  
SELECT SalesAmount FROM FactInternetSales GROUP BY SalesAmount, SalesAmount*1.10;  
```  
  
### <a name="h-using-a-group-by-with-multiple-group-by-expressions"></a>З. Использование GROUP BY с несколькими выражениями группы  
 Следующий пример группирует результаты с помощью нескольких `GROUP BY` критериев. Если внутри каждого `OrderDateKey` группы есть подгрупп, которые могут отличаться друг от друга `DueDateKey`, нового группирования будут определены для результирующего набора.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, DueDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSalesGROUP BY OrderDateKey, DueDateKey   
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-a-group-by-clause-with-a-having-clause"></a>И. Использование предложения GROUP BY с предложением HAVING  
 В следующем примере используется `HAVING` предложение для указания групп, сформированная в `GROUP BY` предложения, которые должны быть включены в результирующий набор. В результаты будут включены только те группы дат заказов в 2004 г. или более поздней версии.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING OrderDateKey > 20040000   
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>См. также:  
 [GROUPING_ID &#40; Transact-SQL &#41;](~/t-sql/functions/grouping-id-transact-sql.md)   
 [ГРУППИРОВАНИЕ &#40; Transact-SQL &#41;](~/t-sql/functions/grouping-transact-sql.md)   
 [SELECT (Transact-SQL)](~/t-sql/queries/select-transact-sql.md)   
 [Предложение SELECT &#40; Transact-SQL &#41;](~/t-sql/queries/select-clause-transact-sql.md)  
  
  





