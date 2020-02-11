---
title: sp_addrolemember (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrolemember_TSQL
- sp_addrolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrolemember
ms.assetid: a583c087-bdb3-46d2-b9e5-3921b3e6d10b
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c9e0d3152c6d60faff4c1c42410374287bd7d111
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030906"
---
# <a name="sp_addrolemember-transact-sql"></a>Хранимая процедура sp_addrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Добавляет пользователя базы данных, роль базы данных, имя входа Windows или группу Windows к роли текущей базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте [инструкцию ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```
sp_addrolemember [ @rolename = ] 'role', [ @membername = ] 'security_account'  

```    
  
## <a name="arguments"></a>Аргументы  
 [ @rolename= ] "*Role*"  
 Имя роли базы данных в текущей базе данных. *Role* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [ @membername= ] "*security_account*"  
 Учетная запись безопасности, добавляемая к роли. *security_account* имеет тип **sysname**и не имеет значения по умолчанию. *security_account* может быть пользователь базы данных, роль базы данных, имя входа Windows или группа Windows.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="remarks"></a>Remarks  
 Член роли, добавляемый с помощью процедуры sp_addrolemember, наследует разрешения этой роли. Если добавляемый член — участник уровня Windows, не имеющий соответствующего пользователя базы данных, этот пользователь будет создан, но может быть не полностью сопоставлен с именем входа. Всегда проверяйте, существует ли имя входа, и предоставлен ли ему доступ к базе данных.  
  
 Роль не может быть членом самой себя. Такие «циклические» определения недопустимы, даже если подразумевается только косвенное членство через несколько промежуточных ролей.  
  
 sp_addrolemember не может добавлять предопределенную роль базы данных, роль сервера или dbo в роль.
  
 Процедура sp_addrolemember используется только для добавления нового члена к роли базы данных. Чтобы добавить члена в роль сервера, используйте [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Для добавления члена к гибким ролям базы данных необходимо выполнение одного из следующих условий.  
  
-   Членство в предопределенной роли базы данных db_securityadmin или db_owner.  
  
-   Членство в роли, которой принадлежит эта роль.  
  
-   Разрешение **ALTER ANY ROLE** или разрешение **ALTER** на роль.  
  
 Для добавления членов в предопределенную роль базы данных необходимо быть членом предопределенной роли базы данных db_owner.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-adding-a-windows-login"></a>A. Добавление имени входа Windows  
 В следующем примере имя входа `Contoso\Mary5` Windows добавляется в `AdventureWorks2012` базу данных в `Mary5`качестве пользователя. Затем пользователь `Mary5` добавляется к роли `Production`.  
  
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
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-adding-a-windows-login"></a>В. Добавление имени входа Windows  
 В следующем примере имя входа `LoginMary` добавляется в `AdventureWorks2008R2` базу данных от `UserMary`имени пользователя. Затем пользователь `UserMary` добавляется к роли `Production`.  
  
> [!NOTE]  
>  Так как имя `LoginMary` входа известно как пользователь `UserMary` базы данных в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базе данных, `UserMary` необходимо указать его. Выражение будет завершаться с ошибкой `Mary5` , пока существует имя для входа. Имена входа и пользователи обычно имеют одинаковые имена. В этом примере используются разные имена для различения действий, влияющих на имя входа и пользователя.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  
