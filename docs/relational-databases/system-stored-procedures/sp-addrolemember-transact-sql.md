---
title: Хранимая процедура sp_addrolemember (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addrolemember_TSQL
- sp_addrolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrolemember
ms.assetid: a583c087-bdb3-46d2-b9e5-3921b3e6d10b
caps.latest.revision: 59
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 147547c7392acaf528b7aef98c88affb8487fe99
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239824"
---
# <a name="spaddrolemember-transact-sql"></a>Хранимая процедура sp_addrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Добавляет пользователя базы данных, роль базы данных, имя входа Windows или группу Windows к роли текущей базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
sp_addrolemember [ @rolename = ] 'role',  
    [ @membername = ] 'security_account'  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_addrolemember 'role', 'security_account'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @rolename=] '*роль*"  
 Имя роли базы данных в текущей базе данных. *роль* — **sysname**, не имеет значения по умолчанию.  
  
 [ @membername=] '*security_account*"  
 Учетная запись безопасности, добавляемая к роли. *security_account* — **sysname**, не имеет значения по умолчанию. *security_account* может быть пользователем базы данных, роли базы данных, имя входа Windows или группы Windows.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Член роли, добавляемый с помощью процедуры sp_addrolemember, наследует разрешения этой роли. Если добавляемый член — участник уровня Windows, не имеющий соответствующего пользователя базы данных, этот пользователь будет создан, но может быть не полностью сопоставлен с именем входа. Всегда проверяйте, существует ли имя входа, и предоставлен ли ему доступ к базе данных.  
  
 Роль не может быть членом самой себя. Такие «циклические» определения недопустимы, даже если подразумевается только косвенное членство через несколько промежуточных ролей.  
  
 sp_addrolemember невозможно Добавление роли предопределенной роли базы данных, предопределенной роли сервера или dbo. Хранимая процедура sp_addrolemember не может выполняться внутри пользовательской транзакции.  
  
 Процедура sp_addrolemember используется только для добавления нового члена к роли базы данных. Добавление члена к роли сервера, используйте [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Для добавления члена к гибким ролям базы данных необходимо выполнение одного из следующих условий.  
  
-   Членство в роли базы данных db_securityadmin или db_owner.  
  
-   Членство в роли, которой принадлежит эта роль.  
  
-   **Разрешение ALTER ANY ROLE** разрешение или **ALTER** разрешение для роли.  
  
 Для добавления членов в предопределенную роль базы данных необходимо быть членом предопределенной роли базы данных db_owner.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-windows-login"></a>A. Добавление имени входа Windows  
 В следующем примере добавляется имя входа Windows `Contoso\Mary5` для `AdventureWorks2012` базы данных как пользователь `Mary5`. Затем пользователь `Mary5` добавляется к роли `Production`.  
  
> [!NOTE]  
>  Так как `Contoso\Mary5` известен как пользователь базы данных `Mary5` в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] , имя пользователя `Mary5` должно быть определено. Выражение будет завершаться с ошибкой `Contoso\Mary5` , пока существует имя для входа. Можно проверить, используя имя входа в домене.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE USER Mary5 FOR LOGIN [Contoso\Mary5] ;  
GO  
```  
  
### <a name="b-adding-a-database-user"></a>Б. Добавление пользователя базы данных  
 В следующем примере пользователь базы данных `Mary5` добавляется к роли базы данных `Production` текущей базы данных.  
  
```  
EXEC sp_addrolemember 'Production', 'Mary5';  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-adding-a-windows-login"></a>В. Добавление имени входа Windows  
 В следующем примере добавляется имя входа `LoginMary` для `AdventureWorks2008R2` базы данных как пользователь `UserMary`. Затем пользователь `UserMary` добавляется к роли `Production`.  
  
> [!NOTE]  
>  Так как имя входа `LoginMary` известен как пользователь базы данных `UserMary` в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных, имя пользователя `UserMary` должен быть указан. Выражение будет завершаться с ошибкой `Mary5` , пока существует имя для входа. Имена входа и пользователи обычно имеют то же имя. Этот пример использует разные имена, чтобы различать действия, влияющие на имя входа или пользователя.  
  
```  
-- Uses AdventureWorks  
  
CREATE USER UserMary FOR LOGIN LoginMary ;  
GO  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
### <a name="d-adding-a-database-user"></a>Г. Добавление пользователя базы данных  
 В следующем примере пользователь базы данных `UserMary` добавляется к роли базы данных `Production` текущей базы данных.  
  
```  
EXEC sp_addrolemember 'Production', 'UserMary'  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_grantdbaccess (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  
