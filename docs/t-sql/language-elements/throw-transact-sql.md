---
title: "THROW (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- THROW_TSQL
- THROW
dev_langs:
- TSQL
helpviewer_keywords:
- THROW statement
ms.assetid: 43661b89-8f13-4480-ad53-70306cbb14c5
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 919d12395255bc754fe89a20659576435ab51e9e
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="throw-transact-sql"></a>THROW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Вызывает исключение и передает выполнение блоку CATCH конструкции TRY…CATCH в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
THROW [ { error_number | @local_variable },  
        { message | @local_variable },  
        { state | @local_variable } ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ERROR_NUMBER*  
 Константа или переменная, представляющая исключение. *ERROR_NUMBER* — **int** и должно быть больше или равен 50 000 и меньше или равно 2147483647.  
  
 *Сообщение*  
 Строка или переменная, описывающая исключение. *сообщение* — **nvarchar(2048)**.  
  
 *состояние*  
 Константа или переменная со значением в диапазоне от 0 до 255, указывающие состояние, которое должно быть связано с сообщением. *состояние* — **tinyint**.  
  
## <a name="remarks"></a>Замечания  
 В инструкции, выполняемой до инструкции THROW, должен использоваться признак конца инструкции — точка с запятой (;).  
  
 Если конструкция TRY…CATCH недоступна, то сеанс будет завершен. Задаются номер строки и процедура, где вызывается исключение. Серьезности задается значение 16.  
  
 Если инструкция THROW указана без параметров, то она должна находиться внутри блока CATCH. Результатом этого будет вызов возникшего исключения. Любая ошибка, возникающая в инструкции THROW, приведет к завершению пакета инструкций.  
  
 % является зарезервированным символом в тексте сообщения инструкции THROW, и его необходимо экранировать. Дважды укажите знак %, чтобы получить % в тексте сообщения, например: "Увеличение превышает 15 %% исходного значения."  
  
## <a name="differences-between-raiserror-and-throw"></a>Различия между инструкциями RAISERROR и THROW  
 В следующей таблице приведены некоторые различия между инструкциями RAISERROR и THROW.  
  
|RAISERROR, инструкция|Инструкция THROW|  
|-------------------------|---------------------|  
|Если *msg_id* передается инструкции RAISERROR, идентификатор должен быть определен в представлении каталога sys.messages.|*Error_number* параметров не должны быть определены в представлении каталога sys.messages.|  
|*Msg_str* параметр может содержать **printf** стили форматирования.|*Сообщение* параметр не может принимать **printf** стиль форматирования.|  
|*Серьезность* указывает серьезность исключения.|Имеется не *серьезность* параметра. Серьезности исключения всегда задается значение 16.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-throw-to-raise-an-exception"></a>A. Использование инструкции THROW для вызова исключения  
 В следующем примере показано использование инструкции `THROW` для вызова исключения.  
  
```tsql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Msg 51000, Level 16, State 1, Line 1  
  
 The record does not exist.
 ```  
  
### <a name="b-using-throw-to-raise-an-exception-again"></a>Б. Использование инструкции THROW для повторного вызова исключения  
 В следующем примере показано использование инструкции `THROW` для повторного вызова последнего исключения.  
  
```tsql  
USE tempdb;  
GO  
CREATE TABLE dbo.TestRethrow  
(    ID INT PRIMARY KEY  
);  
BEGIN TRY  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
--  Force error 2627, Violation of PRIMARY KEY constraint to be raised.  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
END TRY  
BEGIN CATCH  
  
    PRINT 'In catch block.';  
    THROW;  
END CATCH;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 PRINT 'In catch block.';  
 Msg 2627, Level 14, State 1, Line 1  
 Violation of PRIMARY KEY constraint 'PK__TestReth__3214EC272E3BD7D3'. Cannot insert duplicate key in object 'dbo.TestRethrow'.  
 The statement has been terminated.
 ```  
  
### <a name="c-using-formatmessage-with-throw"></a>В. Использование инструкции FORMATMESSAGE с ключевым словом THROW  
 В следующем примере показано использование функции `FORMATMESSAGE` с ключевым словом `THROW` для вызова настроенных сообщений об ошибке. В данном примере сначала создается определяемое пользователем сообщение об ошибке с помощью `sp_addmessage`. Поскольку инструкция THROW не позволяет задать параметры подстановки для *сообщение* параметр образом делает инструкция RAISERROR, функция FORMATMESSAGE используется для передачи трех значений параметров, ожидаемых по сообщению об ошибке 60000.  
  
```tsql  
EXEC sys.sp_addmessage  
     @msgnum   = 60000  
,@severity = 16  
,@msgtext  = N'This is a test message with one numeric parameter (%d), one string parameter (%s), and another string parameter (%s).'  
    ,@lang = 'us_english';   
GO  
  
DECLARE @msg NVARCHAR(2048) = FORMATMESSAGE(60000, 500, N'First string', N'second string');   
  
THROW 60000, @msg, 1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Msg 60000, Level 16, State 1, Line 2  
 This is a test message with one numeric parameter (500), one string parameter (First string), and another string parameter (second string).
 ```  
  
## <a name="see-also"></a>См. также:  
 [Функция FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)   
 [Уровни серьезности ошибок ядра базы данных](../../relational-databases/errors-events/database-engine-error-severities.md)   
 [ERROR_LINE (Transact-SQL)](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE (Transact-SQL)](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER (Transact-SQL)](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE (Transact-SQL)](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [Функция ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [Перейти к &#40; Transact-SQL &#41;](../../t-sql/language-elements/goto-transact-sql.md)   
 [BEGIN... КОНЕЦ &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [Функция XACT_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/xact-state-transact-sql.md)   
 [Инструкция SET XACT_ABORT &#40; Transact-SQL &#41;](../../t-sql/statements/set-xact-abort-transact-sql.md)  
  
  


