---
title: "ERROR_STATE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_STATE_TSQL
- ERROR_STATE
dev_langs:
- TSQL
helpviewer_keywords:
- messages [SQL Server], state
- ERROR_STATE function
- errors [SQL Server], state
- TRY...CATCH [SQL Server]
- CATCH block
- states [SQL Server], error numbers
ms.assetid: 6059af00-83fe-409f-ab7c-daad111bc671
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07caa8a60512f507c9ad1003c864680e82d48870
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="errorstate-transact-sql"></a>ERROR_STATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает номер состояния для ошибки, вызвавшей запуск блока CATCH в конструкции TRY…CATCH.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ERROR_STATE ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
 При вызове в блоке CATCH возвращает номер состояния сообщения об ошибке, вызвавшей запуск блока CATCH.  
  
 Возвращает значение NULL в случае вызова вне блока CATCH.  
  
## <a name="remarks"></a>Замечания  
 Некоторые сообщения об ошибках могут возникнуть в нескольких точках кода для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, в нескольких различных ситуациях может возникнуть ошибка «1105». Каждому определенному условию, вызывающему ошибку, назначен уникальный код состояния.  
  
 При просмотре баз данных известных проблем, например базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)], можно по номеру состояния выяснить, соответствует ли запись о проблеме той ошибке, которая возникла. Например, если в статье базы знаний рассматривается сообщение об ошибке 1105 с состоянием 2, а полученное сообщение об ошибке 1105 имеет состояние 3, то в этом случае ошибка произошла по иной причине, чем ошибка, описанная в статье.  
  
 Кроме того, сотрудник службы поддержки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может использовать код состояния ошибки для поиска в исходном коде места, где произошла ошибка, это поможет ему в диагностировании неполадки.  
  
 Функцию ERROR_STATE можно вызывать в любом месте области видимости блока CATCH.  
  
 Функция ERROR_STATE возвращает состояние ошибки вне зависимости от числа ее запусков или места запуска в области видимости блока CATCH. Этим она отличается от таких функций, как @@ERROR, которая только возвращает номер ошибки в инструкции сразу после того, который вызывает ошибку, или в первой инструкции блока CATCH.  
  
 Во вложенных блоках CATCH функция ERROR_STATE возвращает состояние ошибки, относящееся к области видимости блока CATCH, в которой она вызвана. Например, блок CATCH внешней конструкции TRY...CATCH может содержать вложенную конструкцию TRY...CATCH. Во вложенном блоке CATCH функция ERROR_STATE возвращает состояние ошибки, вызвавшей вложенный блок CATCH. Если функция ERROR_STATE запускается во внешнем блоке CATCH, то она возвращает состояние ошибки, вызвавшей внешний блок CATCH.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-errorstate-in-a-catch-block"></a>A. Использование функции ERROR_STATE в блоке CATCH  
 В следующем примере приведена инструкция `SELECT`, вызывающая ошибку деления на ноль. Возвращается состояние ошибки.  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>Б. Использование функции ERROR_STATE в блоке CATCH вместе с другими средствами обработки ошибок  
 В следующем примере приведена инструкция `SELECT`, вызывающая ошибку деления на ноль. Вместе с состоянием ошибки возвращаются сведения, относящиеся к этой ошибке.  
  
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
  
### <a name="c-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>В. Использование функции ERROR_STATE в блоке CATCH вместе с другими средствами обработки ошибок  
 В следующем примере приведена инструкция `SELECT`, вызывающая ошибку деления на ноль. Вместе с состоянием ошибки возвращаются сведения, относящиеся к этой ошибке.  
  
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
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

