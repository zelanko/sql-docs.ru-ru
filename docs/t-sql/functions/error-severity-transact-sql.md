---
title: "ERROR_SEVERITY (Transact-SQL) | Документы Microsoft"
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
- ERROR_SEVERITY_TSQL
- ERROR_SEVERITY
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], severity
- messages [SQL Server], severity
- TRY...CATCH [SQL Server]
- CATCH block
- ERROR_SEVERITY function
ms.assetid: 50228f2f-6949-4d2e-8e43-fad11bf973ab
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 5c3cd713bcbb239c037ff0a43083058de117cb9b
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="errorseverity-transact-sql"></a>ERROR_SEVERITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает серьезность ошибки, вызвавшей запуск блока CATCH конструкции TRY...CATCH.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ERROR_SEVERITY ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
 При вызове в блоке CATCH возвращает серьезность сообщения об ошибке, вызвавшего запуск блока CATCH.  
  
 Возвращает значение NULL в случае вызова вне блока CATCH.  
  
## <a name="remarks"></a>Замечания  
 ERROR_SEVERITY может быть вызвана в любом месте в пределах области блока CATCH.  
  
 ERROR_SEVERITY возвращает серьезность ошибки независимо от того, сколько раз она выполняется или где именно она выполняется в пределах области блока CATCH. Этим она отличается от таких функций, как @@ERROR, которая только возвращает номер ошибки в инструкции сразу после того, который вызывает ошибку, или в первой инструкции блока CATCH.  
  
 Во вложенных блоках CATCH функция ERROR_SEVERITY возвращает серьезность ошибки специфично для области блока CATCH, в котором она представлена. Например, блок CATCH внешней конструкции TRY...CATCH может содержать вложенную конструкцию TRY...CATCH. В пределах вложенного блока CATCH функция ERROR_SEVERITY возвращает серьезность ошибки, вызвавшей выполнение вложенного блока CATCH. Если функция ERROR_SEVERITY запускается во внешнем блоке CATCH, она возвращает серьезность ошибки, вызвавшей выполнение внешнего блока CATCH.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-errorseverity-in-a-catch-block"></a>A. Использование ERROR_SEVERITY в блоке CATCH  
 В следующем примере приведена инструкция `SELECT`, вызывающая ошибку деления на ноль. Возвращается серьезность ошибки.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_SEVERITY() AS ErrorSeverity;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>Б. Использование ERROR_SEVERITY в блоке CATCH с другими инструментами обработки ошибок  
 В следующем примере приведена инструкция `SELECT`, вызывающая ошибку деления на ноль. Вместе с серьезностью возвращаются другие сведения относительно ошибки.  
  
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
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>В. Использование ERROR_SEVERITY в блоке CATCH с другими инструментами обработки ошибок  
 В следующем примере приведена инструкция `SELECT`, вызывающая ошибку деления на ноль. Вместе с серьезностью возвращаются другие сведения относительно ошибки.  
  
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
 [ERROR_PROCEDURE (Transact-SQL)](../../t-sql/functions/error-procedure-transact-sql.md)   
 [Функция ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  


