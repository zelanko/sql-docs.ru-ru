---
title: "Изменение РОЛИ сервера (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_ROLE_TSQL
- ALTER SERVER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, ALTER
- ALTER SERVER ROLE statement
ms.assetid: 7a4db7bb-c442-4e12-9a8a-114da5bc7710
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f88c9aaf3e541d4213a3adeb77a0e457deb7c06
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-role-transact-sql"></a>ALTER SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

Изменяет членство в роли сервера или изменяет имя определяемой пользователем роли сервера. Предопределенные роли сервера нельзя переименовывать.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
ALTER SERVER ROLE server_role_name   
{  
    [ ADD MEMBER server_principal ]  
  | [ DROP MEMBER server_principal ]  
  | [ WITH NAME = new_server_role_name ]  
} [ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
ALTER SERVER ROLE  server_role_name  ADD MEMBER login;  
  
ALTER SERVER ROLE  server_role_name  DROP MEMBER login;  
```  
  
## <a name="arguments"></a>Аргументы  
*имя_роли_сервера*  
Имя роли сервера, подлежащей изменению.  
  
Добавить ЧЛЕН *server_principal*  
Добавляет указанный сервер-участник к роли сервера. *server_principal* может быть именем входа или роли сервера, определяемой пользователем. *server_principal* не может быть предопределенной ролью сервера, роли базы данных или sa.  
  
DROP MEMBER *server_principal*  
Удаляет указанный сервер-участник из роли сервера. *server_principal* может быть именем входа или роли сервера, определяемой пользователем. *server_principal* не может быть предопределенной ролью сервера, роли базы данных или sa.  
  
С ИМЕНЕМ  **=**  *new_server_role_name*  
Задает новое имя определяемой пользователем роли сервера. Это имя не должно быть занято на сервере.  
  
## <a name="remarks"></a>Замечания  
Изменение имени определяемой пользователем роли сервера не изменяет идентификационный номер, владельца или разрешения роли.  
  
Для изменения членства в роли, `ALTER SERVER ROLE` заменяет sp_addsrvrolemember и sp_dropsrvrolemember. Эти хранимые процедуры являются устаревшими.  
  
Для просмотра ролей сервера выполните запрос к представлениям каталога `sys.server_role_members` и `sys.server_principals`.  
  
Чтобы изменить владельца роли сервера, определяемых пользователем, используйте [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
Требуется `ALTER ANY SERVER ROLE` разрешение на сервере, чтобы изменить имя роли сервера, определяемого пользователем.  
  
**Предопределенные роли сервера**  
  
Для добавления нового члена в предопределенную роль сервера пользователь должен быть членом этой предопределенной роли сервера или членом роли сервера `sysadmin`.  
  
> [!NOTE]  
>  `CONTROL SERVER` И `ALTER ANY SERVER ROLE` разрешений недостаточно для выполнения `ALTER SERVER ROLE` для фиксированной серверной роли, и `ALTER` предопределенной роли сервера не может быть предоставлено разрешение.  
  
**Определяемых пользователем ролей сервера**  
  
Добавление члена к роли сервера, определяемых пользователем, необходимо быть членом `sysadmin` предопределенной роли сервера или иметь `CONTROL SERVER` или `ALTER ANY SERVER ROLE` разрешение. Либо необходимо иметь `ALTER` с этой ролью разрешение.  
  
> [!NOTE]  
>  В отличие от предопределенных ролей сервера, члены определяемой пользователем роли по сути не имеют разрешения на добавление членов в эту роль.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-the-name-of-a-server-role"></a>A. Изменение имени роли сервера  
В следующем примере создается роль сервера с именем `Product`, затем имя роли сервера изменяется на `Production`.  
  
```  
CREATE SERVER ROLE Product ;  
ALTER SERVER ROLE Product WITH NAME = Production ;  
GO  
```  
  
### <a name="b-adding-a-domain-account-to-a-server-role"></a>Б. Добавление учетной записи домена к роли сервера  
Следующий пример добавляет учетную запись домена с именем `adventure-works\roberto0` определяемой пользователем роли сервера с именем `Production`.  
  
```  
ALTER SERVER ROLE Production ADD MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="c-adding-a-sql-server-login-to-a-server-role"></a>В. Добавление имени входа SQL Server к роли сервера  
В следующем примере добавляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа с именем `Ted` для `diskadmin` предопределенной роли сервера.  
  
```  
ALTER SERVER ROLE diskadmin ADD MEMBER Ted ;  
GO  
```  
  
### <a name="d-removing-a-domain-account-from-a-server-role"></a>Г. Удаление учетной записи домена из роли сервера  
Следующий пример удаляет учетную запись домена с именем `adventure-works\roberto0` из определяемой пользователем роли сервера с именем `Production`.  
  
```  
ALTER SERVER ROLE Production DROP MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="e-removing-a-sql-server-login-from-a-server-role"></a>Д. Удаление имени входа SQL Server из роли сервера  
В следующем примере удаляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа `Ted` из `diskadmin` предопределенной роли сервера.  
  
```  
ALTER SERVER ROLE Production DROP MEMBER Ted ;  
GO  
```  
  
### <a name="f-granting-a-login-the-permission-to-add-logins-to-a-user-defined-server-role"></a>Е. Предоставление имени входа разрешения на добавление имен входа к определяемой пользователем роли сервера  
В следующем примере пользователь `Ted` получает разрешение добавлять другие имена входа к определяемой пользователем роли сервера с именем `Production`.  
  
```  
GRANT ALTER ON SERVER ROLE::Production TO Ted ;  
GO  
```  
  
### <a name="g-to-view-role-membership"></a>Ж. Просмотр членства в роли  
Чтобы просмотреть членство в роли, используйте **роль сервера (члены)** страницы в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или выполните следующий запрос:  
  
```  
SELECT SRM.role_principal_id, SP.name AS Role_Name,   
SRM.member_principal_id, SP2.name  AS Member_Name  
FROM sys.server_role_members AS SRM  
JOIN sys.server_principals AS SP  
    ON SRM.Role_principal_id = SP.principal_id  
JOIN sys.server_principals AS SP2   
    ON SRM.member_principal_id = SP2.principal_id  
ORDER BY  SP.name,  SP2.name  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-basic-syntax"></a>З. Базовый синтаксис  
В следующем примере добавляется имя входа `Anna` для `LargeRC` роли сервера.  
  
```  
ALTER SERVER ROLE LargeRC ADD MEMBER Anna;  
```  
  
### <a name="i-remove-a-login-from-a-resource-class"></a>И. Удалите имя входа из класса ресурсов.  
В следующем примере удаляется Анна членства `LargeRC` роли сервера.  
  
```  
ALTER SERVER ROLE LargeRC DROP MEMBER Anna;  
```  
  
## <a name="see-also"></a>См. также:  
[СОЗДАТЬ РОЛЬ сервера &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
[УДАЛИТЬ РОЛЬ сервера &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
[СОЗДАТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
[ИЗМЕНИТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
[УДАЛИТЬ РОЛЬ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
[Безопасность хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
[Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md)   
[Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
[sys.server_role_members &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
[sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  

