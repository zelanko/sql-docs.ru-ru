---
title: ERROR_NUMBER (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ERROR_NUMBER_TSQL
- ERROR_NUMBER
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], numbers
- TRY...CATCH [SQL Server]
- ERROR_NUMBER function
- CATCH block
ms.assetid: 1de85fff-1ca2-4b31-841b-926e571cb150
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 388912c81c1ced9cc05c2b0c402e7a6141ce2452
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827024"
---
# <a name="errornumber-transact-sql"></a>ERROR_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает номер ошибки, которая вызвала выполнение блока CATCH конструкции TRY…CATCH.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ERROR_NUMBER ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
При вызове в блоке CATCH функция `ERROR_NUMBER` возвращает номер ошибки, вызвавшей выполнение блока CATCH.  

Функция `ERROR_NUMBER` возвращает значение NULL в случае вызова вне блока CATCH.  
  
## <a name="remarks"></a>Remarks  
Функцию `ERROR_NUMBER` можно вызывать в любом месте области действия блока CATCH.  
  
Функция `ERROR_NUMBER` возвращает соответствующий номер ошибки независимо от количества ее выполнений или от места ее вызова в области действия блока `CATCH`. В этом ее отличие от таких функций, как @@ERROR, которые возвращают номер ошибки только в той инструкции, которая непосредственно следует за инструкцией, вызвавшей ошибку.  

Во вложенном блоке `CATCH` функция `ERROR_NUMBER` возвращает номер ошибки, соответствующий области действия блока `CATCH`, который ссылался на данный блок `CATCH`. Например, блок `CATCH` внешней конструкции TRY...CATCH может содержать внутреннюю конструкцию `TRY...CATCH`. Во внутреннем блоке `CATCH` функция `ERROR_NUMBER` возвращает номер ошибки, вызвавшей внутренний блок `CATCH`. Если функция `ERROR_NUMBER` выполняется во внешнем блоке `CATCH`, она возвращает номер ошибки, вызвавшей внешний блок `CATCH`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-errornumber-in-a-catch-block"></a>A. Использование функции ERROR_NUMBER в блоке CATCH  
В приведенном ниже примере показана инструкция `SELECT`, вызывающая ошибку деления на ноль. Блок `CATCH` возвращает номер ошибки.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_NUMBER() AS ErrorNumber;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber
-----------
8134

(1 row(s) affected)

```  
  
### <a name="b-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>Б. Использование функции ERROR_NUMBER в блоке CATCH с другими средствами обработки ошибок  
В приведенном ниже примере показана инструкция `SELECT`, вызывающая ошибку деления на ноль. Вместе с номером ошибки блок `CATCH` возвращает сведения о ней.  

```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure   ErrorLine  ErrorMessage
----------- ------------- ----------- ---------------  ---------- ----------------------------------
8134        16            1           NULL             4          Divide by zero error encountered.

(1 row(s) affected)

```  
  
## <a name="see-also"></a>См. также:  
 [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH (Transact-SQL)](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE (Transact-SQL)](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE (Transact-SQL)](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE (Transact-SQL)](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE (Transact-SQL)](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

