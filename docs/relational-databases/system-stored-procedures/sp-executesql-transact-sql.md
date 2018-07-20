---
title: sp_executesql (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_executesql
- sp_executesql_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_executesql
- dynamic SQL
ms.assetid: a8d68d72-0f4d-4ecb-ae86-1235b962f646
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 38c0cd9d348e78a10be4917172c149750da8a657
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083796"
---
# <a name="spexecutesql-transact-sql"></a>Хранимая процедура sp_executesql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Выполняет инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] или пакет инструкций, которые могут выполняться много раз или создаваться динамически. Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] или пакет инструкций могут содержать параметры.  
  
> [!IMPORTANT]  
>  Компиляция инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] во время выполнения подвергает приложения риску злонамеренного воздействия.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_executesql [ @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [ OUT | OUTPUT ][ ,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ \@stmt =] *инструкции*  
 Строка в Юникоде, содержащий [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции или пакета. \@stmt должен быть константой или переменной в Юникоде. Более сложные выражения Юникода, например объединение двух строк с помощью оператора +, недопустимы. Символьные константы недопустимы. Если указана константа Юникода, он должен начинаться с префикса **N**. Например, константа Юникода **N 'sp_who'** является допустимым, а символьная константа **'sp_who'** не является. Размер строки ограничивается только доступной серверу баз данных памятью. На 64-разрядных серверах, размер строки ограничен 2 ГБ, максимальный размер **nvarchar(max)**.  
  
> [!NOTE]  
>  \@stmt может содержать параметры, называющиеся аналогично как имя переменной, например: `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 Каждый параметр, включенный в \@stmt должен иметь соответствующую запись в \@список определений параметров params, а параметр списка значений.  
  
 [ \@params =] N'\@*parameter_name ** data_type* [,... *n* ] "  
 Строка, содержащая определения всех параметров, внедренных в \@stmt. Строка должна представлять собой константу в Юникоде либо переменную в этом же формате. Определение каждого параметра состоит из имени параметра и типа данных. *n* — заполнитель, указывающий Дополнительные определения параметра. Каждый параметр, указанный в \@stmtmust определяться в \@params. Если [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция или пакет в \@stmt не содержит параметров, \@params не является обязательным. Этот аргумент по умолчанию принимает значение NULL.  
  
 [ \@param1 =] '*значение1*"  
 Значение для первого параметра, определенного в строке параметров. Это значение может быть константой или переменной в Юникоде. Должно быть значение параметра, предоставленные каждому параметру в \@stmt. Значения не являются обязательными при [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция или пакет в \@stmt не имеет параметров.  
  
 [ OUT | OUTPUT ]  
 Показывает, что параметр процедуры является выходным. **текст**, **ntext**, и **изображение** параметров можно использовать в качестве ВЫХОДНЫХ параметров, если процедура не является общие процедуры языка среды выполнения (CLR). Выходным параметром с ключевым словом OUTPUT может быть заполнитель курсора, если процедура не является процедурой CLR.  
  
 *n*  
 Заполнитель для значений дополнительных параметров. Значения могут быть только константами и переменными. Значения не могут представлять собой сложные выражения, такие как функции или выражения, построенные с помощью операторов.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующие наборы всех заданных инструкций SQL, встроенные в строку SQL.  
  
## <a name="remarks"></a>Примечания  
 параметры процедуры sp_executesql должны вводиться в определенном порядке, как описано в разделе «Синтаксис» ранее в этом разделе. Если параметры вводятся не в этом порядке, будет выдано сообщение об ошибке.  
  
 Относительно пакетов инструкций, области имен и контекста базы данных процедура sp_executesql ведет себя аналогично инструкции EXECUTE. [!INCLUDE[tsql](../../includes/tsql-md.md)] Инструкция или пакет в sp_executesql \@stmt не компилируются до выполнения инструкции sp_executesql. Содержимое \@stmt затем компилируется и выполняется в качестве плана выполнения, отдельный от плана выполнения пакета, вызвавшего процедуру sp_executesql. Пакет, содержащийся в процедуре sp_executesql, не может ссылаться на переменные, объявленные в пакете, вызвавшем sp_executesql. Локальные курсоры или переменные в пакете sp_executesql недоступны пакету, вызвавшему sp_executesql. Изменения в контексте базы данных длятся только до завершения выполнения инструкции sp_executesql.  
  
 Процедура sp_executesql может использоваться вместо хранимых процедур для многократного выполнения инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], где единственные различия между инструкциями — значения параметров. Так как инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] сама остается неизменной и меняются только значения параметров, оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вероятнее всего, повторно использует план выполнения, сформированный перед первым выполнением.  
  
> [!NOTE]  
>  Для улучшения производительности используйте полные имена объектов в строке инструкции.  
  
 Хранимая процедура sp_executesql поддерживает задание значений параметрам отдельно от строки [!INCLUDE[tsql](../../includes/tsql-md.md)], как показано в следующем примере.  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
  
/* Build the SQL string one time.*/  
SET @SQLString =  
     N'SELECT BusinessEntityID, NationalIDNumber, JobTitle, LoginID  
       FROM AdventureWorks2012.HumanResources.Employee   
       WHERE BusinessEntityID = @BusinessEntityID';  
SET @ParmDefinition = N'@BusinessEntityID tinyint';  
/* Execute the string with the first parameter value. */  
SET @IntVariable = 197;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
/* Execute the same string with the second parameter value. */  
SET @IntVariable = 109;  
EXECUTE sp_executesql @SQLString, @ParmDefinition,  
                      @BusinessEntityID = @IntVariable;  
```  
  
 Выходные параметры также могут быть использованы sp_executesql. В следующем примере название задания получается из таблицы `AdventureWorks2012.HumanResources.Employee` и возвращается в выходном параметре `@max_title`.  
  
```  
DECLARE @IntVariable int;  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @max_title varchar(30);  
  
SET @IntVariable = 197;  
SET @SQLString = N'SELECT @max_titleOUT = max(JobTitle)   
   FROM AdventureWorks2012.HumanResources.Employee  
   WHERE BusinessEntityID = @level';  
SET @ParmDefinition = N'@level tinyint, @max_titleOUT varchar(30) OUTPUT';  
  
EXECUTE sp_executesql @SQLString, @ParmDefinition, @level = @IntVariable, @max_titleOUT=@max_title OUTPUT;  
SELECT @max_title;  
```  
  
 Возможность подставлять разные значения параметров в sp_executesql предоставляет следующие преимущества перед использованием инструкции EXECUTE.  
  
-   Так как собственно текст инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в строке sp_executesql не меняется между выполнениями, оптимизатор запросов, вероятнее всего, сопоставит инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] во время второго выполнения с планом выполнения, сформированным во время первого выполнения. Следовательно, компиляция второй инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обязательна.  
  
-   Строка [!INCLUDE[tsql](../../includes/tsql-md.md)] строится только один раз.  
  
-   Целочисленный параметр определен в собственном формате. Приведение к Юникоду не требуется.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-executing-a-simple-select-statement"></a>A. Выполнение простой инструкции SELECT  
 В следующем примере создается и выполняется простая инструкция `SELECT`, содержащая внедренный параметр с именем `@level`.  
  
```  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
          WHERE BusinessEntityID = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
### <a name="b-executing-a-dynamically-built-string"></a>Б. Выполнение динамически построенной строки  
 В следующем примере показано использование процедуры `sp_executesql` для выполнения динамически построенной строки. В этом примере хранимая процедура вставляет данные в набор таблиц, использующихся для секционирования данных о продажах по одному году. Для каждого месяца года создается одна таблица следующего формата:  
  
```  
CREATE TABLE May1998Sales  
    (OrderID int PRIMARY KEY,  
    CustomerID int NOT NULL,  
    OrderDate  datetime NULL  
        CHECK (DATEPART(yy, OrderDate) = 1998),  
    OrderMonth int  
        CHECK (OrderMonth = 5),  
    DeliveryDate datetime  NULL,  
        CHECK (DATEPART(mm, OrderDate) = OrderMonth)  
    )  
```  
  
 В этом образце хранимая процедура динамически строит и выполняет инструкцию `INSERT` для вставки новых заказов в соответствующую таблицу. В этом примере используется дата заказа для формирования имени таблицы, которая должна содержать данные, затем полученное имя вставляется в инструкцию `INSERT`.  
  
> [!NOTE]  
>  Это простой пример использования процедуры sp_executesql. Пример не включает в себя проверку ошибок и бизнес-правил, которые, например гарантируют то, что номера заказов не будут дублироваться в разных таблицах.  
  
```  
CREATE PROCEDURE InsertSales @PrmOrderID INT, @PrmCustomerID INT,  
                 @PrmOrderDate DATETIME, @PrmDeliveryDate DATETIME  
AS  
DECLARE @InsertString NVARCHAR(500)  
DECLARE @OrderMonth INT  
  
-- Build the INSERT statement.  
SET @InsertString = 'INSERT INTO ' +  
       /* Build the name of the table. */  
       SUBSTRING( DATENAME(mm, @PrmOrderDate), 1, 3) +  
       CAST(DATEPART(yy, @PrmOrderDate) AS CHAR(4) ) +  
       'Sales' +  
       /* Build a VALUES clause. */  
       ' VALUES (@InsOrderID, @InsCustID, @InsOrdDate,' +  
       ' @InsOrdMonth, @InsDelDate)'  
  
/* Set the value to use for the order month because  
   functions are not allowed in the sp_executesql parameter  
   list. */  
SET @OrderMonth = DATEPART(mm, @PrmOrderDate)  
  
EXEC sp_executesql @InsertString,  
     N'@InsOrderID INT, @InsCustID INT, @InsOrdDate DATETIME,  
       @InsOrdMonth INT, @InsDelDate DATETIME',  
     @PrmOrderID, @PrmCustomerID, @PrmOrderDate,  
     @OrderMonth, @PrmDeliveryDate  
  
GO  
```  
  
 Применение процедуры sp_executesql в этом случае более эффективно, чем использование инструкции EXECUTE для выполнения строки. При использовании процедуры sp_executesql формируется только 12 версий инструкции INSERT, по одной для таблицы каждого месяца. При использовании EXECUTE каждая инструкция INSERT должна быть уникальной, так как значения параметров будут различными. И хотя с помощью обоих методов будет создано одинаковое число пакетов, подобие инструкций INSERT, сформированных sp_executesql, увеличивает вероятность того, что оптимизатор запросов повторно использует планы выполнения.  
  
### <a name="c-using-the-output-parameter"></a>В. Использование параметра OUTPUT  
 В следующем примере используется `OUTPUT` параметр для хранения результирующего набора, формируемого `SELECT` инструкции в `@SQLString` параметра. Два `SELECT` затем выполняются инструкции, использующие значение `OUTPUT` параметра.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SQLString nvarchar(500);  
DECLARE @ParmDefinition nvarchar(500);  
DECLARE @SalesOrderNumber nvarchar(25);  
DECLARE @IntVariable int;  
SET @SQLString = N'SELECT @SalesOrderOUT = MAX(SalesOrderNumber)  
    FROM Sales.SalesOrderHeader  
    WHERE CustomerID = @CustomerID';  
SET @ParmDefinition = N'@CustomerID int,  
    @SalesOrderOUT nvarchar(25) OUTPUT';  
SET @IntVariable = 22276;  
EXECUTE sp_executesql  
    @SQLString  
    ,@ParmDefinition  
    ,@CustomerID = @IntVariable  
    ,@SalesOrderOUT = @SalesOrderNumber OUTPUT;  
-- This SELECT statement returns the value of the OUTPUT parameter.  
SELECT @SalesOrderNumber;  
-- This SELECT statement uses the value of the OUTPUT parameter in  
-- the WHERE clause.  
SELECT OrderDate, TotalDue  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderNumber = @SalesOrderNumber;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-executing-a-simple-select-statement"></a>Г. Выполнение простой инструкции SELECT  
 В следующем примере создается и выполняется простая инструкция `SELECT`, содержащая внедренный параметр с именем `@level`.  
  
```  
-- Uses AdventureWorks  
  
EXECUTE sp_executesql   
          N'SELECT * FROM AdventureWorksPDW2012.dbo.DimEmployee   
          WHERE EmployeeKey = @level',  
          N'@level tinyint',  
          @level = 109;  
```  
  
 Дополнительные примеры см. в разделе [sp_executesql (Transact-SQL)](http://msdn.microsoft.com/library/ms188001.aspx).  
  
## <a name="see-also"></a>См. также  
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
