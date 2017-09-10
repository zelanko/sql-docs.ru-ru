---
title: "ВЕРНУТЬ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERT_TSQL
- REVERT
dev_langs:
- TSQL
helpviewer_keywords:
- REVERT statement
- context switching [SQL Server], reverting
- reverting execution context
- REVERT WITH COOKIE statement
- execution context [SQL Server]
- COOKIE clause
ms.assetid: 4688b17a-dfd1-4f03-8db4-273a401f879f
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2074ef0a9e434ac5c427c5438633c61ead0eb25a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="revert-transact-sql"></a>REVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Переключает контекст выполнения в контекст участника, вызывавшего последнюю инструкцию EXECUTE AS.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVERT  
    [ WITH COOKIE = @varbinary_variable ]  
```  
  
## <a name="arguments"></a>Аргументы  
 WITH COOKIE = @*varbinary_variable*  
 Задает куки-файл, который был создан в соответствующей [EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md) изолированной инструкции. *@varbinary_variable*— **varbinary(100)**.  
  
## <a name="remarks"></a>Замечания  
 Инструкцию REVERT можно указывать внутри модуля, такого как хранимая процедура или определяемая пользователем функция, или в качестве изолированной инструкции. При указании внутри модуля инструкция REVERT применима только к инструкциям EXECUTE AS, определенным в модуле. Например, следующая хранимая процедура выполняет инструкцию `EXECUTE AS`, за которой следует инструкция `REVERT`.  
  
```  
CREATE PROCEDURE dbo.usp_myproc   
  WITH EXECUTE AS CALLER  
AS   
    SELECT SUSER_NAME(), USER_NAME();  
    EXECUTE AS USER = 'guest';  
    SELECT SUSER_NAME(), USER_NAME();  
    REVERT;  
    SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
 Предположим, что в сеансе, в котором работает хранимая процедура, контекст выполнения сеанса явно изменен на `login1`, как показано в следующем примере.  
  
```  
  -- Sets the execution context of the session to 'login1'.  
EXECUTE AS LOGIN = 'login1';  
GO  
EXECUTE dbo.usp_myproc;   
```  
  
 Инструкция `REVERT`, определенная в модуле `usp`_`myproc`, переключает контекст выполнения, установленный внутри модуля, но не влияет на контекст выполнения, установленный снаружи модуля. Контекст выполнения для сеанса остается установленным в `login1`.  
  
 При указании в качестве отдельной инструкции REVERT применяется к инструкциям EXECUTE AS, определенным внутри пакета или сеанса. Инструкция REVERT не будет иметь эффекта, если соответствующая инструкция EXECUTE AS содержит предложение WITH NO REVERT. В этом случае контекст выполнения остается в силе до завершения сеанса.  
  
## <a name="using-revert-with-cookie"></a>Использование инструкции REVERT WITH COOKIE  
 ВЫПОЛНЕНИЕ в инструкцию, которая используется для задания контекста выполнения сеанса может включать необязательное предложение WITH NO REVERT COOKIE = @*varbinary_variabl*e. При выполнении этой инструкции [!INCLUDE[ssDE](../../includes/ssde-md.md)] передает куки-файл @*varbinary_variabl*e. Контекст выполнения, устанавливаемый данной инструкции можно возвратить только к предыдущему контексту, если вызывающий REVERT WITH COOKIE = @*varbinary_variable* инструкция содержит правильное  *@varbinary_variable*  значение.  
  
 Этот механизм полезен в окружениях, где используется пул соединений. Пул соединений — это поддержка группы подключений к базе данных для повторного использования приложениями нескольких конечных пользователей. Так как значение, передаваемое  *@varbinary_variable*  известного только код, вызывающий выполнение инструкции (в данном случае приложение), вызывающий объект может гарантировать, что установленный им контекст выполнения не может изменяться конечным пользователем приложения, который вызывает. После того как контекст выполнения возвращен, приложение может переключить контекст на другого участника.  
  
## <a name="permissions"></a>Permissions  
 Разрешения не требуются.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-execute-as-and-revert-to-switch-context"></a>A. Использование предложений EXECUTE AS и REVERT для переключения контекста  
 В следующем примере создается стек контекста выполнения при помощи нескольких участников. Затем используется инструкция REVERT для переустановки контекста выполнения на предыдущего участника. Инструкция REVERT выполняется множество раз, передвигаясь вверх по стеку, до тех пор, пока не будет установлен контекст выполнения первоначального участника.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create two temporary principals.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE LOGIN login2 WITH PASSWORD = 'Uor80$23b';  
GO  
CREATE USER user1 FOR LOGIN login1;  
CREATE USER user2 FOR LOGIN login2;  
GO  
-- Give IMPERSONATE permissions on user2 to user1  
-- so that user1 can successfully set the execution context to user2.  
GRANT IMPERSONATE ON USER:: user2 TO user1;  
GO  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- Set the execution context to login1.   
EXECUTE AS LOGIN = 'login1';  
-- Verify that the execution context is now login1.  
SELECT SUSER_NAME(), USER_NAME();  
-- Login1 sets the execution context to login2.  
EXECUTE AS USER = 'user2';  
-- Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- The execution context stack now has three principals: the originating caller, login1, and login2.  
-- The following REVERT statements will reset the execution context to the previous context.  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
REVERT;  
-- Display the current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
  
-- Remove the temporary principals.  
DROP LOGIN login1;  
DROP LOGIN login2;  
DROP USER user1;  
DROP USER user2;  
GO  
```  
  
### <a name="b-using-the-with-cookie-clause"></a>Б. Использование предложения WITH COOKIE  
 Следующий пример устанавливает контекст выполнения сеанса для указанного пользователя и указывает WITH NO REVERT COOKIE = @*varbinary_variabl*предложение. Инструкция `REVERT` обязана указать значение, передаваемое переменной `@cookie` в `EXECUTE AS` инструкции, для успешного возвращения контекста обратно вызывающему. Чтобы запустить этот образец, должно существовать имя входа `login1` и пользователь `user1`, созданные в примере А.  
  
```  
DECLARE @cookie varbinary(100);  
EXECUTE AS USER = 'user1' WITH COOKIE INTO @cookie;  
-- Store the cookie somewhere safe in your application.  
-- Verify the context switch.  
SELECT SUSER_NAME(), USER_NAME();  
--Display the cookie value.  
SELECT @cookie;  
GO  
-- Use the cookie in the REVERT statement.  
DECLARE @cookie varbinary(100);  
-- Set the cookie value to the one from the SELECT @cookie statement.  
SET @cookie = <value from the SELECT @cookie statement>;  
REVERT WITH COOKIE = @cookie;  
-- Verify the context switch reverted.  
SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ВЫПОЛНЕНИЕ AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)   
 [Предложение EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [SUSER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/suser-name-transact-sql.md)   
 [Имя_пользователя &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)  
  
  

