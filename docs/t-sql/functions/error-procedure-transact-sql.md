---
title: "Функция ERROR_PROCEDURE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_PROCEDURE_TSQL
- ERROR_PROCEDURE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_PROCEDURE function
- messages [SQL Server], trigger where occurred
- errors [SQL Server], stored procedure where occurred
- TRY...CATCH [SQL Server]
- CATCH block
- messages [SQL Server], stored procedure where occurred
- errors [SQL Server], trigger where occurred
ms.assetid: b81edbf0-856a-498f-ba87-48ff1426d980
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd5bd076bd3ee690d834c27f37544b8fd4ab6402
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="errorprocedure-transact-sql"></a>ERROR_PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает имя хранимой процедуры или триггера, в которых произошла ошибка, вызвавшая запуск блока CATCH конструкции TRY…CATCH.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ERROR_PROCEDURE ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(128)**  
  
## <a name="return-value"></a>Возвращаемое значение  
 При вызове в блоке CATCH возвращает имя хранимой процедуры, в которой произошла ошибка.  
  
 Возвращает значение NULL, если внутри хранимой процедуры или триггера не произошла ошибка.  
  
 Возвращает значение NULL в случае вызова вне блока CATCH.  
  
## <a name="remarks"></a>Замечания  
 Функция ERROR_PROCEDURE может быть вызвана в любом месте области блока CATCH.  
  
 Функция ERROR_PROCEDURE возвращает имя хранимой процедуры или триггера, в которых произошла ошибка, независимо от числа вызовов или места вызова в области блока CATCH. Это отличается от таких функций, таких как@ERROR, который возвращает номер ошибки в инструкции сразу после того, который вызвал ошибку, или в первой инструкции блока CATCH.  
  
 Во вложенных блоках CATCH функция ERROR_PROCEDURE возвращает имя хранимой процедуры или триггера, связанных с областью блока CATCH, в которой содержится ссылка на него. Например: блок CATCH конструкции TRY…CATCH может иметь вложенную конструкцию TRY…CATCH. Внутри вложенного блока CATCH функция ERROR_PROCEDURE возвращает имя хранимой процедуры или триггера, в которых произошла ошибка, вызвавшая вложенный блок CATCH. Если функция ERROR_PROCEDURE выполняется во внешнем блоке CATCH, то возвращается имя хранимой процедуры или триггера, в которых произошла ошибка, вызвавшая вложенный блок CATCH.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-errorprocedure-in-a-catch-block"></a>A. Использование функции ERROR_PROCEDURE в блоке CATCH  
 В следующем фрагменте кода показана хранимая процедура, которая формирует ошибку деления на 0. Функция `ERROR_PROCEDURE` возвращает имя хранимой процедуры, в которой произошла ошибка.  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_PROCEDURE() AS ErrorProcedure;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorprocedure-in-a-catch-block-with-other-error-handling-tools"></a>Б. Использование функции ERROR_PROCEDURE в блоке CATCH вместе с другими средствами обработки ошибок  
 В следующем фрагменте кода показана хранимая процедура, которая формирует ошибку деления на 0. Наряду с именем хранимой процедуры, в которой произошла ошибка, возвращаются данные, связанные с ошибкой.  
  
```  
  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT   
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage,  
        ERROR_LINE() AS ErrorLine;  
        END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errorprocedure-in-a-catch-block"></a>В. Использование функции ERROR_PROCEDURE в блоке CATCH  
 В следующем фрагменте кода показана хранимая процедура, которая формирует ошибку деления на 0. Функция `ERROR_PROCEDURE` возвращает имя хранимой процедуры, в которой произошла ошибка.  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_PROCEDURE() AS ErrorProcedure;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errorprocedure-in-a-catch-block-with-other-error-handling-tools"></a>Г. Использование функции ERROR_PROCEDURE в блоке CATCH вместе с другими средствами обработки ошибок  
 В следующем фрагменте кода показана хранимая процедура, которая формирует ошибку деления на 0. Наряду с именем хранимой процедуры, в которой произошла ошибка, возвращаются данные, связанные с ошибкой.  
  
```  
  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT   
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage;  
        END CATCH;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH (Transact-SQL)](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE (Transact-SQL)](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE (Transact-SQL)](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER (Transact-SQL)](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [Функция ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  


