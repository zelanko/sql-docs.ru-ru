---
title: "УДАЛИТЬ РОЛЬ сервера (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SERVER ROLE
- DROP_SERVER_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, DROP
- DROP SERVER ROLE statement
ms.assetid: a2a1e6e6-e40c-4d6a-81be-d197b80bf226
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c493ed6556bde690f6b4a9ec6b46aeb3ceb59ae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-server-role-transact-sql"></a>DROP SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

  Удаляет определяемую пользователем роль сервера.  
  
 Определяемые пользователем роли сервера впервые появились в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP SERVER ROLE role_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *role_name*  
 Задает определяемую пользователем роль сервера для удаления с сервера.  
  
## <a name="remarks"></a>Замечания  
 Определяемые пользователем роли сервера, владеющие защищаемыми объектами, не могут быть удалены с сервера. Чтобы удалить определяемую пользователем роль сервера, владеющую защищаемыми объектами, необходимо сначала передать эти объекты другому владельцу или удалить их.  
  
 Определяемые пользователем роли сервера, у которых есть члены, нельзя удалить. Чтобы удалить роль сервера, определяемых пользователем, содержит члены, необходимо сначала удалить члены роли с помощью [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Предопределенные роли сервера нельзя удалять.  
  
 Можно просмотреть сведения о членстве в роли с помощью запроса к [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md) представления каталога.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL для роли сервера или разрешение ALTER ANY SERVER ROLE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-to-drop-a-server-role"></a>A. Удаление роли сервера  
 В следующем примере удаляется роль сервера `purchasing`.  
  
```  
DROP SERVER ROLE purchasing;  
GO  
```  
  
### <a name="b-to-view-role-membership"></a>Б. Просмотр членства в роли  
 Чтобы просмотреть членство в роли, используйте **роли сервера (члены**) страницы в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или выполните следующий запрос:  
  
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
  
### <a name="c-to-view-role-membership"></a>В. Просмотр членства в роли  
 Чтобы определить, принадлежит ли роли сервера другая роль сервера, выполните следующий запрос:  
  
```  
SELECT SP1.name AS RoleOwner, SP2.name AS Server_Role  
FROM sys.server_principals AS SP1  
JOIN sys.server_principals AS SP2  
    ON SP1.principal_id = SP2.owning_principal_id   
ORDER BY SP1.name ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ИЗМЕНИТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [СОЗДАТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [УДАЛИТЬ РОЛЬ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  

