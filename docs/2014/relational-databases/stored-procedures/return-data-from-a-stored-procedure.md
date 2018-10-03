---
title: Возврат данных из хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], returning data
- returning data from stored procedure
ms.assetid: 7a428ffe-cd87-4f42-b3f1-d26aa8312bf7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b11f924ce5692378896f1fd7d50186861abf223
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220534"
---
# <a name="return-data-from-a-stored-procedure"></a>Возврат данных из хранимой процедуры
  Существует два способа возврата результирующих наборов или данных из процедуры вызывающей программе: параметры вывода и коды возврата. В этом разделе приводятся сведения по обоим способам.  
  
## <a name="returning-data-using-an-output-parameter"></a>Возврат данных с помощью выходного параметра  
 Процедура может возвращать текущее значение параметра в вызываемой программе при завершении работы при указании ключевого слова OUTPUT для параметра в определении процедуры. Чтобы сохранить значение параметра в переменной, которая может быть использована в вызываемой программе, при выполнении процедуры вызываемая программа должна использовать ключевое слово OUTPUT. Дополнительные сведения о том, какие типы данных могут использоваться в качестве выходных параметров, см. в разделе [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql).  
  
### <a name="examples-of-output-parameter"></a>Примеры выходного параметра  
 Следующий пример представляет процедуру с входным и выходным параметрами. Параметр `@SalesPerson` получает входное значение, указанное вызывающей программой. Инструкция SELECT использует значение, переданное входному параметру для получения верного значения `SalesYTD` . Инструкция SELECT также присваивает это значение выходному параметру `@SalesYTD` , который возвращает значение вызывающей программе при завершении процедуры.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetEmployeeSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetEmployeeSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetEmployeeSalesYTD  
@SalesPerson nvarchar(50),  
@SalesYTD money OUTPUT  
AS    
  
    SET NOCOUNT ON;  
    SELECT @SalesYTD = SalesYTD  
    FROM Sales.SalesPerson AS sp  
    JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
    WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 В следующем примере вызывается процедура, которая была создана в первом примере и сохраняет выходное значение, возвращенное вызванной процедурой в переменной `@SalesYTD` , являющейся локальной в вызывающей программе.  
  
```  
-- Declare the variable to receive the output value of the procedure.  
DECLARE @SalesYTDBySalesPerson money;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTDBySalesPerson  
EXECUTE Sales.uspGetEmployeeSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDBySalesPerson OUTPUT;  
-- Display the value returned by the procedure.  
PRINT 'Year-to-date sales for this employee is ' +   
    convert(varchar(10),@SalesYTDBySalesPerson);  
GO  
  
```  
  
 Входные значения также могут быть указаны для параметров OUTPUT при выполнении процедуры. Это позволяет хранимой процедуре получать значение из вызываемой программы, изменять его или выполнять операции с этим значением, а затем возвращать новое значение вызываемой программе. В предыдущем примере переменной `@SalesYTDBySalesPerson` может быть присвоено значение прежде, чем программа вызовет процедуру `Sales.uspGetEmployeeSalesYTD` . Эта инструкция передает значение переменной `@SalesYTDBySalesPerson` выходному параметру `@SalesYTD` . Далее в тексте процедуры значение можно использовать для вычислений, формирующих новое значение. Новое значение передается обратно из процедуры через выходной параметр, обновляя значение в переменной `@SalesYTDBySalesPerson` при завершении процедуры. Часто это называется «возможностью передачи по ссылке».  
  
 Если при вызове процедуры указано ключевое слово OUTPUT для параметра, а параметр не определен при помощи OUTPUT в определении процедуры, выдается сообщение об ошибке. Однако процедуру можно выполнить с выходными параметрами, не указывая OUTPUT при выполнении процедуры. Сообщение об ошибке не будет выдаваться, но нельзя будет использовать выходное значение в вызываемой программе.  
  
### <a name="using-the-cursor-data-type-in-output-parameters"></a>Использование типа данных Cursor в выходных параметрах  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] можно использовать процедуры `cursor` тип данных только для ВЫХОДНЫХ параметров. Если `cursor` указан тип данных для параметра, для этого параметра в определении процедуры необходимо указать ключевые слова VARYING и выходных данных. Параметр может быть указан только как ВЫХОДНОЙ, но если в объявлении параметра указано ключевое слово VARYING, тип данных должен быть `cursor` и также должно быть указано ключевое слово OUTPUT.  
  
> [!NOTE]  
>  `cursor` Тип данных нельзя связать с переменными приложения через API, таких как OLE DB, ODBC, ADO и DB-Library базы данных. Поскольку ВЫХОДНЫЕ параметры должны быть привязаны прежде, чем приложение может выполнить процедуру, хранимые процедуры с `cursor` ВЫХОДНЫХ параметров не может вызываться из API базы данных. Эти процедуры могут быть вызваны из [!INCLUDE[tsql](../../../includes/tsql-md.md)] пакетов, процедур или триггеров, только если `cursor` ВЫХОДНОЙ переменной назначается [!INCLUDE[tsql](../../../includes/tsql-md.md)] локального `cursor` переменной.  
  
### <a name="rules-for-cursor-output-parameters"></a>Правила для выходных параметров курсора  
 Следующие правила относятся к `cursor` выходные параметры при выполнении процедуры:  
  
-   Для курсора последовательного доступа в результирующий набор курсора будут возвращены только строки с текущей позиции курсора до конца курсора. Текущая позиция курсора определяется при окончании выполнения процедуры. Например:  
  
    -   Непрокручиваемый курсор открыт в процедуре на результирующем наборе по имени RS из 100 строк.  
  
    -   Процедура выбирает первые 5 строк результирующего набора RS.  
  
    -   Процедура возвращает результат участнику.  
  
    -   Результирующий набор RS, возвращенный участнику, состоит из строк с 6 по 100 из набора RS, и курсор в участнике позиционирован перед первой строкой RS.  
  
-   Для курсора последовательного доступа, если курсор позиционирован перед первой строкой после завершения хранимой процедуры, весь результирующий набор будет возвращен к вызывающему пакету, процедуре или триггеру. После возврата позиция курсора будет установлена перед первой строкой.  
  
-   Для курсора последовательного доступа, если курсор позиционирован за концом последней строки после завершения хранимой процедуры, вызывающему пакету, процедуре или триггеру будет возвращен пустой результирующий набор.  
  
    > [!NOTE]  
    >  Пустой результирующий набор отличается от значения NULL.  
  
-   Для прокручиваемого курсора все строки в результирующем наборе будут возвращены к вызывающему пакету, процедуре или триггеру после выполнения процедуры. При возврате позиция курсора остается в позиции последней выборки, выполненной в процедуре.  
  
-   Для любого типа курсора, если курсор закрыт, вызывающему пакету, процедуре или триггеру будет возвращено значение NULL. Это же произойдет в случае, если курсор присвоен параметру, но этот курсор никогда не открывался.  
  
    > [!NOTE]  
    >  Закрытое состояние имеет значение только во время возврата. Например, можно при выполнении процедуры закрыть курсор, снова открыть его позже в процедуре и возвратить этот результирующий набор курсора в вызывающий пакет, процедуру или триггер.  
  
### <a name="examples-of-cursor-output-parameters"></a>Примеры выходных параметров курсора  
 В следующем примере создается процедура, которая указывает выходной параметр, `@currency`_`cursor` с помощью `cursor` тип данных. Процедура затем будет вызвана из пакета.  
  
 Сначала создайте процедуру, которая объявляет и затем открывает курсор в таблице Currency.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspCurrencyCursor', 'P' ) IS NOT NULL  
    DROP PROCEDURE dbo.uspCurrencyCursor;  
GO  
CREATE PROCEDURE dbo.uspCurrencyCursor   
    @CurrencyCursor CURSOR VARYING OUTPUT  
AS  
    SET NOCOUNT ON;  
    SET @CurrencyCursor = CURSOR  
    FORWARD_ONLY STATIC FOR  
      SELECT CurrencyCode, Name  
      FROM Sales.Currency;  
    OPEN @CurrencyCursor;  
GO  
  
```  
  
 Затем выполните пакет, который объявляет локальную переменную курсора, выполняет процедуру, присваивающую курсор локальной переменной, и затем выбирает строки из курсора.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyCursor CURSOR;  
EXEC dbo.uspCurrencyCursor @CurrencyCursor = @MyCursor OUTPUT;  
WHILE (@@FETCH_STATUS = 0)  
BEGIN;  
     FETCH NEXT FROM @MyCursor;  
END;  
CLOSE @MyCursor;  
DEALLOCATE @MyCursor;  
GO  
  
```  
  
## <a name="returning-data-using-a-return-code"></a>Возврат данных с использованием кода возврата  
 Процедура может возвращать целочисленное значение, называемое кодом возврата, чтобы указать состояние выполнения процедуры. Код возврата для процедуры указывается при помощи инструкции RETURN. Как и выходные параметры, при выполнении процедуры код возврата необходимо сохранить в переменной, чтобы использовать это значение в вызывающей программе. Например, переменная `@result` типа данных `int` используется для хранения кода возврата из процедуры `my_proc`, такие как:  
  
```  
DECLARE @result int;  
EXECUTE @result = my_proc;  
```  
  
 Коды возврата часто применяются в блоках управления потоком процедур для присвоения кода возврата каждой из возможных ошибок. Чтобы выяснить, произошла ли во время выполнения инструкции ошибка, запустите функцию @@ERROR после инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
### <a name="examples-of-return-codes"></a>Примеры кодов возврата  
 В следующем примере показана процедура `usp_GetSalesYTD` с обработкой ошибок, устанавливающей специальные значения кода возврата для различных ошибок. В следующей таблице показано целое число, которое назначается процедурой каждой возможной ошибке, и соответствующее значение каждого числа.  
  
|Значения кодов возврата|Значение|  
|-----------------------|-------------|  
|0|Выполнено успешно.|  
|1|Требуемое значение параметра не указано.|  
|2|Требуемое значение параметра не допустимо.|  
|3|Произошла ошибка при получении значения продаж.|  
|4|Найдено значение NULL для продаж данного менеджера.|  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.usp_GetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.usp_GetSalesYTD;  
GO  
CREATE PROCEDURE Sales.usp_GetSalesYTD  
@SalesPerson nvarchar(50) = NULL,  -- NULL default value  
@SalesYTD money = NULL OUTPUT  
AS    
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
   BEGIN  
       PRINT 'ERROR: You must specify a last name for the sales person.'  
       RETURN(1)  
   END  
ELSE  
   BEGIN  
   -- Make sure the value is valid.  
   IF (SELECT COUNT(*) FROM HumanResources.vEmployee  
          WHERE LastName = @SalesPerson) = 0  
      RETURN(2)  
   END  
-- Get the sales for the specified name and   
-- assign it to the output parameter.  
SELECT @SalesYTD = SalesYTD   
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
-- Check for SQL Server errors.  
IF @@ERROR <> 0   
   BEGIN  
      RETURN(3)  
   END  
ELSE  
   BEGIN  
   -- Check to see if the ytd_sales value is NULL.  
     IF @SalesYTD IS NULL  
       RETURN(4)   
     ELSE  
      -- SUCCESS!!  
        RETURN(0)  
   END  
-- Run the stored procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the stored procedure with an input value.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTD  
EXECUTE Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
PRINT N'Year-to-date sales for this employee is ' +  
    CONVERT(varchar(10), @SalesYTDForSalesPerson);  
  
```  
  
 Следующий пример создает программу обработки кодов возврата, которые возвращаются процедурой `usp_GetSalesYTD` .  
  
```  
-- Declare the variables to receive the output value and return code   
-- of the procedure.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
  
-- Execute the procedure with a title_id value  
-- and save the output value and return code in variables.  
EXECUTE @ret_code = Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
--  Check the return codes.  
IF @ret_code = 0  
BEGIN  
   PRINT 'Procedure executed successfully'  
   -- Display the value returned by the procedure.  
   PRINT 'Year-to-date sales for this employee is ' + CONVERT(varchar(10),@SalesYTDForSalesPerson)  
END  
ELSE IF @ret_code = 1  
   PRINT 'ERROR: You must specify a last name for the sales person.'  
ELSE IF @ret_code = 2   
   PRINT 'EERROR: You must enter a valid last name for the sales person.'  
ELSE IF @ret_code = 3  
   PRINT 'ERROR: An error occurred getting sales value.'  
ELSE IF @ret_code = 4  
   PRINT 'ERROR: No sales recorded for this employee.'     
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [DECLARE @local_variable (Transact-SQL)](/sql/t-sql/language-elements/declare-local-variable-transact-sql)   
 [PRINT (Transact-SQL)](/sql/t-sql/language-elements/print-transact-sql)   
 [SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql)   
 [Курсоры](../cursors.md)   
 [RETURN (Transact-SQL)](/sql/t-sql/language-elements/return-transact-sql)   
 [@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql)  
  
  
