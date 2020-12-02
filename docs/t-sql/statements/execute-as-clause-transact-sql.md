---
description: EXECUTE AS, предложение (Transact-SQL)
title: Предложение EXECUTE AS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e41272ce78e5bfb0dd1a0f746a11d6700ac11c59
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96131058"
---
# <a name="execute-as-clause-transact-sql"></a>EXECUTE AS, предложение (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно определять контекст выполнения для следующих определяемых пользователем модулей: функций (за исключением встроенных функций с табличным значением), процедур, очередей и триггеров.  
  
 Указывая контекст, в котором выполняется модуль, можно управлять тем, какую учетную запись компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует при проверке разрешений на объекты, на которые ссылается модуль. Это повышает гибкость и безопасность управления разрешениями на цепочки владения между пользовательскими модулями и объектами, на которые они ссылаются. Тогда пользователям необходимо будет предоставлять только разрешения на сам модуль, без выдачи явных разрешений на объекты, на которые он ссылается. Только пользователь, от имени которого выполняется модуль, должен будет иметь разрешения на объекты, к которым этот модуль обращается.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
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
  
```syntaxsql
-- Azure SQL Database Syntax  
Functions (except inline table-valued functions), Stored Procedures, and DML Triggers  
  
{ EXEC | EXECUTE } AS { CALLER | SELF | OWNER | 'user_name' }   
  
DDL Triggers with Database Scope  
  
{ EXEC | EXECUTE } AS { CALLER | SELF | 'user_name' }  
  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 **CALLER**  
 Указывает, что инструкции, содержащиеся в модуле, выполняются в контексте пользователя, вызывающего этот модуль. Пользователь, выполняющий модуль, должен иметь соответствующие разрешения не только на сам модуль, но также и на объекты базы данных, на которые имеются ссылки из этого модуля.  
  
 Аргумент CALLER является значением по умолчанию для всех модулей, кроме очередей, и работает так же, как и в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Ключевое слово CALLER не может быть указано в инструкции CREATE QUEUE или ALTER QUEUE.  
  
 **SELF**  
 EXECUTE AS SELF эквивалентно EXECUTE AS *user_name*, где указанный пользователь — это тот, кто создает или изменяет модуль. Фактический идентификатор пользователя, создающего или изменяющего модуль, хранится в столбце **execute_as_principal_id** в представлении каталога **sys.sql_modules** или **sys.service_queues**.  
  
 Аргумент SELF является значением по умолчанию для очередей.  
  
> [!NOTE]  
>  Чтобы изменить идентификатор пользователя в **execute_as_principal_id** представления каталога **sys.service_queues**, необходимо явно указать аргумент EXECUTE AS в инструкции ALTER QUEUE.  
  
 OWNER  
 Указывает, что инструкции, содержащиеся в модуле, выполняются в контексте текущего владельца этого модуля. Если для модуля не определен владелец, то подразумевается владелец схемы модуля. Ключевое слово OWNER не может указываться для триггеров DDL или триггеров входа.  
  
> [!IMPORTANT]  
>  OWNER должен быть сопоставлен с негрупповой учетной записью и не может быть ролью или группой.  
  
 **'** *user_name* **'**  
 Указывает, что инструкции, содержащиеся в модуле, выполняются в контексте пользователя, указываемого аргументом *user_name*. Разрешения на объекты, на которые ссылается модуль, проверяются для *user_name*. Аргумент *user_name* нельзя указывать для триггеров DDL в области сервера или триггеров входа. Вместо него следует использовать *login_name*.  
  
 Аргумент *user_name* должен присутствовать в текущей базе данных и не должен относиться к учетной записи группы. В качестве аргумента *user_name* не могут быть указаны роль, сертификат, ключ или встроенная учетная запись (например, NT AUTHORITY\LocalService, NT AUTHORITY\NetworkService или NT AUTHORITY\LocalSystem).  
  
 Идентификатор пользователя контекста выполнения хранится в метаданных, его можно получить из столбца **execute_as_principal_id** представления каталога **sys.sql_modules** или **sys.assembly_modules**.  
  
 **'** *login_name* **'**  
 Указывает, что инструкции, содержащиеся в модуле, выполняются в контексте имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указанного в аргументе *login_name*. Разрешения на объекты, на которые ссылается модуль, проверяются для *login_name*. Аргумент *login_name* можно указывать только для триггеров DDL в области сервера или триггеров входа.  
  
 В качестве аргумента *login_name* не могут быть указаны роль, сертификат, ключ или встроенная учетная запись (например, NT AUTHORITY\LocalService, NT AUTHORITY\NetworkService или NT AUTHORITY\LocalSystem).  
  
## <a name="remarks"></a>Комментарии  
 Способ, которым компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет разрешения на объекты, зависит от цепочки владения, связывающей модуль и объекты, на который он ссылается. В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] цепочки владения были единственным методом, который позволял избежать предоставления пользователю разрешений на все объекты, к которым модуль производит доступ.  
  
 Цепочки владения имеют следующие ограничения.  
  
-   Применяются только к инструкциям DML: SELECT, INSERT, UPDATE и DELETE.  
  
-   У вызывающего и вызываемого объекта должен быть один и тот же владелец.  
  
-   Не применяются к динамическим запросам в модуле.  
  
 Независимо от контекста выполнения, указанного в модуле, всегда выполняются следующие действия.  
  
-   Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] сначала проверяет, имеет ли пользователь, выполняющий модуль, разрешение EXECUTE на него.  
  
-   Применяются правила цепочки владения, то есть если вызывающий и вызываемый объекты имеют одного и того же владельца, разрешения на вложенные объекты не проверяются.  
  
 Если пользователь выполняет модуль, для которого определен запуск в контексте, отличном от CALLER, проверяются разрешения пользователя на выполнение модуля, а проверки разрешений на объекты, к которым модуль производит доступ, выполняются для учетной записи пользователя, указанной в предложении EXECUTE AS. Пользователь, выполняющий модуль, таким образом олицетворяет указанного пользователя.  
  
 Контекст, указанный в предложении EXECUTE AS, действует только до конца выполнения модуля, после чего производится возврат в исходный контекст.  
  
## <a name="specifying-a-user-or-login-name"></a>Указание имени пользователя или имени входа  
 Пользователь базы данных и имя входа сервера, указанные в предложении EXECUTE AS, не могут быть удалены до тех пор, пока модуль не будет изменен так, чтобы он выполнялся в другом контексте.  
  
 Имя пользователя или имя входа, указанное в предложении EXECUTE AS, должно присутствовать в качестве участника в **sys.database_principals** или **sys.server_principals** соответственно; в противном случае операция создания или изменения модуля завершается ошибкой. К тому же пользователь, который создает или изменяет модуль, должен иметь разрешение IMPERSONATE на этого участника.  
  
 Если пользователь неявно имеет доступ к базе данных или экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через членство в группе Windows, то пользователь, указанный в предложении EXECUTE AS, неявно создается в момент создания модуля при соблюдении следующих условий.  
  
-   Указанный пользователь или имя входа является членом предопределенной роли сервера **sysadmin**.  
  
-   Пользователь, который создает модуль, имеет разрешение на создание участников.  
  
 Если какое-либо из этих условий не соблюдается, операция создания модуля завершается ошибкой.  
  
> [!IMPORTANT]  
>  Если служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) выполняется от имени локальной учетной записи (локальной службы или локального пользователя), она не будет иметь прав на членство в группах домена Windows, которые могут быть указаны в предложении EXECUTE AS. Это приведет к ошибке выполнения модуля.  
  
 Для примера рассмотрим следующие условия.  
  
-   Группа **CompanyDomain\SQLUsers** имеет доступ к базе данных **Sales**.  
  
-   **CompanyDomain\SqlUser1** является членом **SQLUsers** и, таким образом, имеет доступ к базе данных **Sales**.  
  
-   Пользователь, который создает модуль, имеет разрешение на создание участников.  
  
 Когда следующее выражение `CREATE PROCEDURE` выполняется, выражение `CompanyDomain\SqlUser1` безоговорочно создается в качестве базы данных субъекта в базе данных `Sales` .  
  
```sql  
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
  
```sql  
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
  
 Для просмотра определения модуля вместе с указанием контекста выполнения воспользуйтесь представлением каталога [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
## <a name="best-practice"></a>Рекомендации  
 Указывайте имя входа или пользователя, имеющего минимальные права на выполнение операций, определенных в модуле. Например, указывайте учетную запись владельца базы данных только тогда, когда разрешения, которыми он обладает, действительно необходимы.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения модуля с указанным предложением EXECUTE AS пользователь должен иметь разрешение EXECUTE на модуль.  
  
 Для выполнения указанного с предложением EXECUTE AS модуля CLR, который производит доступ к ресурсам в другой базе данных или на другом сервере, целевым сервером или базой данных должно быть выдано удостоверение проверки подлинности для базы данных, в которой находится модуль (т.е. базы данных-источника).  
  
 Для указания предложения EXECUTE AS при создании или изменении модуля необходимо разрешение IMPERSONATE на указанного участника, а также разрешение на создание модуля. Пользователь всегда может олицетворять сам себя. Если контекст выполнения не указан или указано EXECUTE AS CALLER, разрешение IMPERSONATE не требуется.  
  
 Для указания *login_name* или *user_name*, которые неявно имеют доступ к базе данных посредством членства в группе Windows, требуется разрешение CONTROL в базе данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается хранимая процедура в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], которой затем назначается контекст выполнения `OWNER`.  
  
```sql  
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
  
## <a name="see-also"></a>См. также  
 [sys.assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.service_queues (Transact-SQL)](../../relational-databases/system-catalog-views/sys-service-queues-transact-sql.md)   
 [REVERT (Transact-SQL)](../../t-sql/statements/revert-transact-sql.md)   
 [EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
