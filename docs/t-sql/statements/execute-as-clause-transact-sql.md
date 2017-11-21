---
title: "EXECUTE AS, предложение (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AS
- AS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permission sets [SQL Server]
- queues [SQL Server]
- stored procedures [SQL Server], executing
- user-defined functions [SQL Server], execution context
- EXECUTE AS
- triggers [SQL Server], execution context
- execution context [SQL Server]
- switching execution context
- functions [SQL Server], execution context
ms.assetid: bd517aa3-f06e-4356-87d8-70de5df4494a
caps.latest.revision: 70
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b96757281a5b36755422346ef444136ad8702726
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="execute-as-clause-transact-sql"></a>EXECUTE AS, предложение (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно определять контекст выполнения для следующих определяемых пользователем модулей: функций (за исключением встроенных функций с табличным значением), процедур, очередей и триггеров.  
  
 Указывая контекст, в котором выполняется модуль, можно управлять тем, какую учетную запись компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует при проверке разрешений на объекты, на которые ссылается модуль. Это повышает гибкость и безопасность управления разрешениями на цепочки владения между пользовательскими модулями и объектами, на которые они ссылаются. Тогда пользователям необходимо будет предоставлять только разрешения на сам модуль, без выдачи явных разрешений на объекты, на которые он ссылается. Только пользователь, от имени которого выполняется модуль, должен будет иметь разрешения на объекты, к которым этот модуль обращается.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- SQL Server Syntax  
Functions (except inline table-valued functions), Stored Procedures, and DML Triggers  
{ EXEC | EXECUTE } AS { CALLER | SELF | OWNER | 'user_name' }   
  
DDL Triggers with Database Scope  
{ EXEC | EXECUTE } AS { CALLER | SELF | 'user_name' }   
  
DDL Triggers with Server Scope and logon triggers  
{ EXEC | EXECUTE } AS { CALLER | SELF | 'login_name' }   
  
Queues  
{ EXEC | EXECUTE } AS { SELF | OWNER | 'user_name' }   
```  
  
```  
  
-- Windows Azure SQL Database Syntax  
Functions (except inline table-valued functions), Stored Procedures, and DML Triggers  
  
{ EXEC | EXECUTE } AS { CALLER | SELF | OWNER | 'user_name' }   
  
DDL Triggers with Database Scope  
  
{ EXEC | EXECUTE } AS { CALLER | SELF | 'user_name' }  
  
```  
  
## <a name="arguments"></a>Аргументы  
 **ВЫЗЫВАЮЩИЙ ОБЪЕКТ**  
 Указывает, что инструкции, содержащиеся в модуле, выполняются в контексте пользователя, вызывающего этот модуль. Пользователь, выполняющий модуль, должен иметь соответствующие разрешения не только на сам модуль, но также и на объекты базы данных, на которые имеются ссылки из этого модуля.  
  
 Аргумент CALLER является значением по умолчанию для всех модулей, кроме очередей, и работает так же, как и в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Ключевое слово CALLER не может быть указано в инструкции CREATE QUEUE или ALTER QUEUE.  
  
 **САМООБСЛУЖИВАНИЯ**  
 Предложение EXECUTE AS SELF эквивалентно EXECUTE AS *имя_пользователя*, где указанный пользователь — пользователь создает или изменяет модуль. Фактический идентификатор создающего или изменяющего модуль хранится в **execute_as_principal_id** столбца в **sys.sql_modules** или **sys.service_queues** представления каталога.  
  
 Аргумент SELF является значением по умолчанию для очередей.  
  
> [!NOTE]  
>  Чтобы изменить идентификатор **execute_as_principal_id** в **sys.service_queues** представление каталога необходимо явно указать EXECUTE AS в инструкции ALTER QUEUE.  
  
 OWNER  
 Указывает, что инструкции, содержащиеся в модуле, выполняются в контексте текущего владельца этого модуля. Если для модуля не определен владелец, то подразумевается владелец схемы модуля. Ключевое слово OWNER не может указываться для триггеров DDL или триггеров входа.  
  
> [!IMPORTANT]  
>  OWNER должен быть сопоставлен с негрупповой учетной записью и не может быть ролью или группой.  
  
 **"** *имя_пользователя* **"**  
 Указывает, что операторы внутри модуля выполняются в контексте пользователя, указанного в *имя_пользователя*. Разрешения на объекты в модуле проверяться *имя_пользователя*. *имя_пользователя* не может быть указан для триггеров DDL в области сервера или входа триггеров. Используйте *login_name* вместо него.  
  
 *имя_пользователя* должен существовать в текущей базе данных и должен быть одиночной учетной записью. *имя_пользователя* не может быть группа, роль, сертификат, ключ или встроенной учетной записи, например NT AUTHORITY\LocalService, NT AUTHORITY\NetworkService или NT AUTHORITY\LocalSystem.  
  
 Идентификатор контекста выполнения хранится в метаданных и могут просматриваться в **execute_as_principal_id** столбца в **sys.sql_modules** или **sys.assembly_modules** представления каталога.  
  
 **"** *login_name* **"**  
 Указывает, что операторы внутри модуля выполняются в контексте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа, заданного в *login_name*. Разрешения на объекты в модуле проверяться *login_name*. *login_name* может быть указан только для триггеров DDL в области сервера или входа триггеров.  
  
 *login_name* не может быть группа, роль, сертификат, ключ или встроенной учетной записи, например NT AUTHORITY\LocalService, NT AUTHORITY\NetworkService или NT AUTHORITY\LocalSystem.  
  
## <a name="remarks"></a>Замечания  
 Способ, которым компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет разрешения на объекты, зависит от цепочки владения, связывающей модуль и объекты, на который он ссылается. В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] цепочки владения были единственным методом, который позволял избежать предоставления пользователю разрешений на все объекты, к которым модуль производит доступ.  
  
 Цепочки владения имеют следующие ограничения.  
  
-   Применяется только к инструкции DML: ВЫБЕРИТЕ, INSERT, UPDATE и DELETE.  
  
-   У вызывающего и вызываемого объекта должен быть один и тот же владелец.  
  
-   Не применяются к динамическим запросам в модуле.  
  
 Независимо от контекста выполнения, указанного в модуле, всегда выполняются следующие действия.  
  
-   Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] сначала проверяет, имеет ли пользователь, выполняющий модуль, разрешение EXECUTE на него.  
  
-   Применяются правила цепочки владения, то есть если вызывающий и вызываемый объекты имеют одного и того же владельца, разрешения на вложенные объекты не проверяются.  
  
 Если пользователь выполняет модуль, для которого определен запуск в контексте, отличном от CALLER, проверяются разрешения пользователя на выполнение модуля, а проверки разрешений на объекты, к которым модуль производит доступ, выполняются для учетной записи пользователя, указанной в предложении EXECUTE AS. Пользователь, выполняющий модуль, таким образом олицетворяет указанного пользователя.  
  
 Контекст, указанный в предложении EXECUTE AS, действует только до конца выполнения модуля, после чего производится возврат в исходный контекст.  
  
## <a name="specifying-a-user-or-login-name"></a>Указание имени пользователя или имени входа  
 Пользователь базы данных и имя входа сервера, указанные в предложении EXECUTE AS, не могут быть удалены до тех пор, пока модуль не будет изменен так, чтобы он выполнялся в другом контексте.  
  
 Имя пользователя или имя входа, указанное в предложении EXECUTE AS должен существовать в качестве участника **sys.database_principals** или **sys.server_principals**, соответственно, иначе создания или изменения модуля завершается ошибкой . К тому же пользователь, который создает или изменяет модуль, должен иметь разрешение IMPERSONATE на этого участника.  
  
 Если пользователь неявно имеет доступ к базе данных или экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через членство в группе Windows, то пользователь, указанный в предложении EXECUTE AS, неявно создается в момент создания модуля при соблюдении следующих условий.  
  
-   Указанный пользователь или имя входа является членом **sysadmin** предопределенной роли сервера.  
  
-   Пользователь, который создает модуль, имеет разрешение на создание участников.  
  
 Если какое-либо из этих условий не соблюдается, операция создания модуля завершается ошибкой.  
  
> [!IMPORTANT]  
>  Если служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) выполняется от имени локальной учетной записи (локальной службы или локального пользователя), она не будет иметь прав на членство в группах домена Windows, которые могут быть указаны в предложении EXECUTE AS. Это приведет к ошибке выполнения модуля.  
  
 Для примера рассмотрим следующие условия.  
  
-   **CompanyDomain\SQLUsers** группа имеет доступ к **Sales** базы данных.  
  
-   **CompanyDomain\SqlUser1** является членом **SQLUsers** и, следовательно, имеет доступ к **Sales** базы данных.  
  
-   Пользователь, который создает модуль, имеет разрешение на создание участников.  
  
 Когда следующее выражение `CREATE PROCEDURE` выполняется, выражение `CompanyDomain\SqlUser1` безоговорочно создается в качестве базы данных субъекта в базе данных `Sales` .  
  
```  
USE Sales;  
GO  
CREATE PROCEDURE dbo.usp_Demo  
WITH EXECUTE AS 'CompanyDomain\SqlUser1'  
AS  
SELECT user_name();  
GO  
```  
  
## <a name="using-execute-as-caller-stand-alone-statement"></a>Использование EXECUTE AS CALLER в качестве изолированной инструкции  
 EXECUTE AS CALLER можно выполнять в модуле в качестве изолированной инструкции для переключения контекста на пользователя, вызывающего модуль.  
  
 Рассмотрим следующую хранимую процедуру под названием `SqlUser2`.  
  
```  
CREATE PROCEDURE dbo.usp_Demo  
WITH EXECUTE AS 'SqlUser1'  
AS  
SELECT user_name(); -- Shows execution context is set to SqlUser1.  
EXECUTE AS CALLER;  
SELECT user_name(); -- Shows execution context is set to SqlUser2, the caller of the module.  
REVERT;  
SELECT user_name(); -- Shows execution context is set to SqlUser1.  
GO  
```  
  
## <a name="using-execute-as-to-define-custom-permission-sets"></a>Применение EXECUTE AS для определения пользовательских наборов разрешений  
 Выбор контекста выполнения в модуле может оказаться полезным в тех случаях, когда необходимо определить пользовательский набор разрешений. Для некоторых действий (например, TRUNCATE TABLE) соответствующие разрешения не реализованы. Включив инструкцию TRUNCATE TABLE в модуль и определив выполнение этого модуля от имени пользователя, который имеет разрешение на изменение таблицы, можно передавать возможность усечения таблицы другим пользователям, предоставляя им разрешение EXECUTE на этот модуль.  
  
 Для просмотра определения модуля вместе с указанием контекста выполнения, используйте [sys.sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) представления каталога.  
  
## <a name="best-practice"></a>Рекомендации  
 Указывайте имя входа или пользователя, имеющего минимальные права на выполнение операций, определенных в модуле. Например, указывайте учетную запись владельца базы данных только тогда, когда разрешения, которыми он обладает, действительно необходимы.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения модуля с указанным предложением EXECUTE AS пользователь должен иметь разрешение EXECUTE на модуль.  
  
 Для выполнения указанного с предложением EXECUTE AS модуля CLR, который производит доступ к ресурсам в другой базе данных или на другом сервере, целевым сервером или базой данных должно быть выдано удостоверение проверки подлинности для базы данных, в которой находится модуль (т.е. базы данных-источника).  
  
 Для указания предложения EXECUTE AS при создании или изменении модуля необходимо разрешение IMPERSONATE на указанного участника, а также разрешение на создание модуля. Пользователь всегда может олицетворять сам себя. Если контекст выполнения не указан или указано EXECUTE AS CALLER, разрешение IMPERSONATE не требуется.  
  
 Чтобы указать *login_name* или *имя_пользователя* , неявно имеет доступ к базе данных через членство в группе Windows, необходимо иметь разрешения на доступ в базе данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается хранимая процедура в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], которой затем назначается контекст выполнения `OWNER`.  
  
```  
CREATE PROCEDURE HumanResources.uspEmployeesInDepartment   
@DeptValue int  
WITH EXECUTE AS OWNER  
AS  
    SET NOCOUNT ON;  
    SELECT e.BusinessEntityID, c.LastName, c.FirstName, e.JobTitle  
    FROM Person.Person AS c   
    INNER JOIN HumanResources.Employee AS e  
        ON c.BusinessEntityID = e.BusinessEntityID  
    INNER JOIN HumanResources.EmployeeDepartmentHistory AS edh  
        ON e.BusinessEntityID = edh.BusinessEntityID  
    WHERE edh.DepartmentID = @DeptValue  
    ORDER BY c.LastName, c.FirstName;  
GO  
  
-- Execute the stored procedure by specifying department 5.  
EXECUTE HumanResources.uspEmployeesInDepartment 5;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.service_queues &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-service-queues-transact-sql.md)   
 [ВОССТАНОВИТЬ &#40; Transact-SQL &#41;](../../t-sql/statements/revert-transact-sql.md)   
 [ВЫПОЛНЕНИЕ AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  

