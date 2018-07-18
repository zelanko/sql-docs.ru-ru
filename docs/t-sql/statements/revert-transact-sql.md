---
title: REVERT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c1f882cf07a504b63218862e79324c32b74b2628
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781805"
---
# <a name="revert-transact-sql"></a>REVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Переключает контекст выполнения в контекст участника, вызывавшего последнюю инструкцию EXECUTE AS.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVERT  
    [ WITH COOKIE = @varbinary_variable ]  
```  
  
## <a name="arguments"></a>Аргументы  
 WITH COOKIE = @*varbinary_variable*  
 Задает файл cookie, который был создан в соответствующей изолированной инструкции [EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md). *@varbinary_variable* — **varbinary(100)**.  
  
## <a name="remarks"></a>Remarks  
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
  
 Инструкция `REVERT`, определенная в модуле `usp_myproc`, переключает контекст выполнения, установленный внутри модуля, но не влияет на контекст выполнения, установленный снаружи модуля. Контекст выполнения для сеанса остается установленным в `login1`.  
  
 При указании в качестве отдельной инструкции REVERT применяется к инструкциям EXECUTE AS, определенным внутри пакета или сеанса. Инструкция REVERT не будет иметь эффекта, если соответствующая инструкция EXECUTE AS содержит предложение WITH NO REVERT. В этом случае контекст выполнения остается в силе до завершения сеанса.  
  
## <a name="using-revert-with-cookie"></a>Использование инструкции REVERT WITH COOKIE  
 Инструкция EXECUTE AS, которая используется для задания контекста выполнения для сеанса, может включать необязательное предложение WITH NO REVERT COOKIE = @*varbinary_variable*. При запуске этой инструкции компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] передает файлы cookie в переменную @*varbinary_variable*. Контекст выполнения, устанавливаемый данной инструкцией, можно возвратить только к предыдущему контексту, если вызов инструкции REVERT WITH COOKIE = @*varbinary_variable* содержит правильное значение *@varbinary_variable*.  
  
 Этот механизм полезен в окружениях, где используется пул соединений. Пул соединений — это поддержка группы подключений к базе данных для повторного использования приложениями нескольких конечных пользователей. Так как значение, переданное *@varbinary_variable*, известно только субъекту, вызывающему инструкцию EXECUTE AS (в данном случае приложению), вызывающий субъект может гарантировать, что контекст выполнения, установленный им, не будет изменен конечным пользователем, который использует приложение. После того как контекст выполнения возвращен, приложение может переключить контекст на другого участника.  
  
## <a name="permissions"></a>Разрешения  
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
 В следующем примере устанавливается контекст выполнения сеанса для определенного пользователя и указывается предложение WITH NO REVERT COOKIE = @*varbinary_variable*. Инструкция `REVERT` обязана указать значение, передаваемое переменной `@cookie` в `EXECUTE AS` инструкции, для успешного возвращения контекста обратно вызывающему. Чтобы запустить этот образец, должно существовать имя входа `login1` и пользователь `user1`, созданные в примере А.  
  
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
 [EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-transact-sql.md)   
 [Предложение EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [SUSER_NAME (Transact-SQL)](../../t-sql/functions/suser-name-transact-sql.md)   
 [USER_NAME (Transact-SQL)](../../t-sql/functions/user-name-transact-sql.md)   
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)  
  
  
