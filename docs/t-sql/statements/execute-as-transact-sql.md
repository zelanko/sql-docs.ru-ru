---
title: "EXECUTE AS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXECUTE AS
- EXECUTE_AS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REVERT statement
- WITH NO REVERT clause
- sessions [SQL Server], execution context
- EXECUTE AS
- execution context [SQL Server]
- switching execution context
ms.assetid: 613b8271-7f7d-4378-b7a2-5a7698551dbd
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e389fdc50da662deeab7eba030a367e5fc7e97cb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="execute-as-transact-sql"></a>EXECUTE AS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Задает контекст выполнения для сеанса.  
  
 По умолчанию сеанс запускается при входе пользователя в систему и завершается при выходе пользователя из системы. Все операции во время сеанса подлежат проверке на наличие у пользователя соответствующих разрешений. Когда **EXECUTE AS** выполняется инструкция, контекст выполнения сеанса переключается на указанное имя входа или пользователя. После переключения контекста, разрешения проверяются токены безопасности имени входа и пользователя для этой учетной записи, а не пользователь, вызвавший **EXECUTE AS** инструкции. В сущности, либо входная или пользовательская учетная запись олицетворяется на время сеанса или на время выполнения модуля, либо явно обращается переключение контекста.  
  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
{ EXEC | EXECUTE } AS <context_specification>  
[;]  
  
<context_specification>::=  
{ LOGIN | USER } = 'name'  
    [ WITH { NO REVERT | COOKIE INTO @varbinary_variable } ]   
| CALLER  
```  
  
## <a name="arguments"></a>Аргументы  
 Имя_для_входа  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает, что контекст выполнения олицетворения — это имя входа. Область олицетворения — это уровень сервера.  
  
> [!NOTE]  
>  Этот параметр доступен не в автономной базе данных или в базе данных SQL.  
  
 Пользователь  
 Определяет контекст для олицетворения пользователя в текущей базе данных. Область олицетворения ограничена текущей базой данных. При переключении контекста на пользователя базы данных разрешения уровня сервера этого пользователя не наследуются.  
  
> [!IMPORTANT]  
>  Пока переключение контекста на пользователя базы данных активно, любая попытка подключиться к ресурсам вне базы данных будет приводить к завершению инструкции с ошибками. Это включает использование *базы данных* инструкции, распределенные запросы и запросы, ссылающиеся на другую базу данных, используются идентификаторы трех или четырех частей.  
  
 **"** *имя* **"**  
 Допустимое имя пользователя или имя входа. *имя* необходимо быть членом **sysadmin** предопределенной роли сервера или участником в [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) или [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md), соответственно.  
  
 *имя* можно указать в качестве локальной переменной.  
  
 *имя* должен быть одиночной учетной записью и не может быть группа, роль, сертификат, ключ или встроенной учетной записи, например NT AUTHORITY\LocalService, NT AUTHORITY\NetworkService или NT AUTHORITY\LocalSystem.  
  
 Дополнительные сведения см. в разделе [Указание имени пользователя или имя входа](#_user) далее в этом разделе.  
  
 NO REVERT  
 Указывает, что переключение контекста нельзя вернуть к предыдущему контексту. **NO REVERT** параметр можно использовать только на нерегламентированном уровне.  
  
 Дополнительные сведения о переключении к предыдущему контексту см. в разделе [REVERT &#40; Transact-SQL &#41; ](../../t-sql/statements/revert-transact-sql.md).  
  
 Файл COOKIE в  **@**  *varbinary_variable*  
 Указывает, что контекст выполнения можно переключить обратно к предыдущему контексту, только при вызове инструкция REVERT WITH COOKIE содержит правильное  **@**  *varbinary_variable* значение. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Передает куки-файл для  **@**  *varbinary_variable*. **Файла COOKIE в** параметр можно использовать только на нерегламентированном уровне.  
  
 **@***varbinary_variable* — **varbinary(8000)**.  
  
> [!NOTE]  
>  Файл cookie **ВЫВОДА** параметр в настоящее время описан в документации как **varbinary(8000)** это правильный максимальную длину. Однако текущая реализация возвращает **varbinary(100)**. Должен быть зарезервирован **varbinary(8000)** , чтобы приложение продолжает работать неправильно, если в будущем выпуске увеличения размера возвращаемых куки-файлов.  
  
 CALLER  
 При использовании внутри модуля указывает, что инструкции модуля выполняются в контексте вызывающей стороны.  
  
 При использовании вне модуля инструкция не действует.  
  
## <a name="remarks"></a>Замечания  
 Изменение в контексте выполнения продолжает действовать до тех пор, пока не произойдет одно из следующих событий.  
  
-   Будет запущена еще одна инструкция EXECUTE AS.  
  
-   Будет запущена инструкция REVERT.  
  
-   Сеанс удаляется.  
  
-   Работа хранимой процедуры или триггера, где выполнялась команда, завершается.  
  
Набор контекстов выполнения может быть создан при помощи нескольких вызовов инструкции EXECUTE AS на нескольких участниках. При вызове инструкция REVERT производит переключение контекста на имя входа или на пользователя на более высоком уровне стека контекстов. Для демонстрации этого поведения, в разделе [пример A](#_exampleA).  
  
##  <a name="_user"></a>Указание имени пользователя или имени входа  
 Имя пользователя или имя входа, указанное в инструкции EXECUTE AS \<context_specification > должен существовать в качестве участника **sys.database_principals** или **sys.server_principals**соответственно, или Инструкция EXECUTE AS завершится ошибкой. Кроме того, этому участнику должны быть предоставлены разрешения IMPERSONATE. Если вызывающий объект является владельцем базы данных, или не является членом **sysadmin** предопределенной роли сервера, указанный участник должен существовать даже если пользователь производит доступ к базе данных или экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через Windows членство в группе. Для примера рассмотрим следующие условия. 
  
-   **CompanyDomain\SQLUsers** группа имеет доступ к **Sales** базы данных.  
  
-   **CompanyDomain\SqlUser1** является членом **SQLUsers** и поэтому имеет неявный доступ к **Sales** базы данных.  
  
 Несмотря на то что **CompanyDomain\SqlUser1** имеет доступ к базе данных посредством членства в **SQLUsers** группы инструкцию `EXECUTE AS USER = 'CompanyDomain\SqlUser1'` завершается ошибкой, поскольку `CompanyDomain\SqlUser1` не существует в качестве участника База данных.  
  
Если пользователь утратил связь (соответствующее имя входа больше не существует), и пользователь не был создан с **WITHOUT LOGIN**, **EXECUTE AS** для пользователя не удастся.  
  
## <a name="best-practice"></a>Рекомендации  
 Указывайте имя входа или пользователя, который имеет наименьшие права доступа, необходимые для выполнения операций в сеансе. Например, не указывайте имя входа с разрешениями уровня сервера, если требуются разрешения только уровня базы данных, а также не указывайте учетную запись владельца базы данных, если только эти разрешения не являются обязательными.  
  
> [!CAUTION]  
>  Инструкция EXECUTE AS может выполняться успешно, пока компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] может разрешить имя. Если пользователь в домене существует, Windows может разрешить доступ в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)] пользователю, даже если у пользователя Windows отсутствует доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Данное обстоятельство может привести к ситуации, когда пользователь, не имеющий доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сможет войти в систему, хотя олицетворенное имя входа будет иметь только те разрешения, которые предоставлены пользователю public или guest.  
  
## <a name="using-with-no-revert"></a>Применение WITH NO REVERT  
 Если инструкция EXECUTE AS содержит необязательное предложение WITH NO REVERT, то контекст выполнения для сеанса нельзя сбросить с помощью инструкции REVERT или путем выполнения другой инструкции EXECUTE AS. Контекст, заданный инструкцией, остается до удаления сеанса.  
  
 Когда WITH NO REVERT COOKIE = @*varbinary_variabl*указано предложение [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] передает значение файла cookie @*varbinary_variabl*e. Контекст выполнения, устанавливаемый данной инструкции можно возвратить только к предыдущему контексту, если вызывающий REVERT WITH COOKIE = @*varbinary_variable* инструкция содержит тот же  *@varbinary_variable*  значение.  
  
 Этот параметр может пригодиться в среде с организацией пула соединений. Организация пула соединений — это поддержка группы подключений к базе данных для повторного использования приложениями или сервером приложений. Так как значение, передаваемое  *@varbinary_variable*  известно только инициатору инструкции EXECUTE AS инструкции, вызывающий объект может гарантировать, что никто другой не может изменяться установленный им контекст выполнения.  
  
## <a name="determining-the-original-login"></a>Определение первоначального имени входа  
 Используйте [ORIGINAL_LOGIN](../../t-sql/functions/original-login-transact-sql.md) функция возвращает имя входа, связанное с экземпляром компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно использовать эту функцию для возврата идентификатора исходного имени входа в сеансах, содержащих множество явных и неявных переключений контекста.  
  
## <a name="permissions"></a>Permissions  
 Чтобы указать **EXECUTE AS** имени входа, вызывающая сторона должна иметь **IMPERSONATE** указанной учетной записи разрешение на имя и не должно быть запрещено **IMPERSONATE ANY LOGIN** разрешение . Чтобы указать **EXECUTE AS** на пользователя базы данных, вызывающий должен иметь **IMPERSONATE** разрешения для указанного имени пользователя. Когда **EXECUTE AS CALLER** указано, **IMPERSONATE** разрешения не требуются.  
  
## <a name="examples"></a>Примеры  
  
###  <a name="_exampleA"></a> A. Использование предложений EXECUTE AS и REVERT для переключения контекста  
 В приведенном примере создается стек контекстов выполнения с использованием нескольких участников. Затем инструкция `REVERT` используется для сброса контекста выполнения к предыдущему участнику. Инструкция `REVERT` выполняется множество раз, передвигаясь вверх по стеку до тех пор, пока контекст выполнения не будет установлен на первоначального участника.  
  
```  
USE AdventureWorks2012;  
GO  
--Create two temporary principals  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE LOGIN login2 WITH PASSWORD = 'Uor80$23b';  
GO  
CREATE USER user1 FOR LOGIN login1;  
CREATE USER user2 FOR LOGIN login2;  
GO  
--Give IMPERSONATE permissions on user2 to user1  
--so that user1 can successfully set the execution context to user2.  
GRANT IMPERSONATE ON USER:: user2 TO user1;  
GO  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- Set the execution context to login1.   
EXECUTE AS LOGIN = 'login1';  
--Verify the execution context is now login1.  
SELECT SUSER_NAME(), USER_NAME();  
--Login1 sets the execution context to login2.  
EXECUTE AS USER = 'user2';  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
-- The execution context stack now has three principals: the originating caller, login1 and login2.  
--The following REVERT statements will reset the execution context to the previous context.  
REVERT;  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
REVERT;  
--Display current execution context.  
SELECT SUSER_NAME(), USER_NAME();  
  
--Remove temporary principals.  
DROP LOGIN login1;  
DROP LOGIN login2;  
DROP USER user1;  
DROP USER user2;  
GO  
```  
  
### <a name="b-using-the-with-cookie-clause"></a>Б. Использование предложения WITH COOKIE  
 Следующий пример устанавливает контекст выполнения сеанса для указанного пользователя и указывает WITH NO REVERT COOKIE = @*varbinary_variabl*предложение. Инструкция `REVERT` обязана указать значение, передаваемое переменной `@cookie` в `EXECUTE AS` инструкции, для успешного возвращения контекста обратно вызывающему. Чтобы запустить этот образец, должно существовать имя входа `login1` и пользователь `user1`, созданные в примере А.  
  
```  
DECLARE @cookie varbinary(8000);  
EXECUTE AS USER = 'user1' WITH COOKIE INTO @cookie;  
-- Store the cookie in a safe location in your application.  
-- Verify the context switch.  
SELECT SUSER_NAME(), USER_NAME();  
--Display the cookie value.  
SELECT @cookie;  
GO  
-- Use the cookie in the REVERT statement.  
DECLARE @cookie varbinary(8000);  
-- Set the cookie value to the one from the SELECT @cookie statement.  
SET @cookie = <value from the SELECT @cookie statement>;  
REVERT WITH COOKIE = @cookie;  
-- Verify the context switch reverted.  
SELECT SUSER_NAME(), USER_NAME();  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ВОССТАНОВИТЬ &#40; Transact-SQL &#41;](../../t-sql/statements/revert-transact-sql.md)   
 [EXECUTE AS предложение &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)  
  
  


