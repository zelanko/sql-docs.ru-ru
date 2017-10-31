---
title: "РОЛЬ DROP (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ROLE
- DROP_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting roles
- database roles [SQL Server], removing
- removing roles
- DROP ROLE statement
- roles [SQL Server], removing
- dropping roles
ms.assetid: 1f6f13ae-56a2-4ef1-93f5-8e6151b83e1d
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 41c2caf816ca412e4a6048713dc66f97da5155ae
ms.openlocfilehash: 86266835ec5d54ce08bdf7fe18d93dd9d4de1737
ms.contentlocale: ru-ru
ms.lasthandoff: 10/07/2017

---
# <a name="drop-role-transact-sql"></a>DROP ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Удаляет роль из базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
DROP ROLE [ IF EXISTS ] role_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP ROLE role_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно Удаляет роль только в том случае, если он уже существует.  
  
 *role_name*  
 Определяет роль, которую следует удалить из базы данных.  
  
## <a name="remarks"></a>Замечания  
 Роли, владеющие объектами защиты, не могут быть удалены из базы данных. Чтобы удалить из базы данных роль, владеющую объектами защиты, необходимо сначала передать эти объекты другому владельцу или удалить их из базы данных. Роли, владеющие объектами защиты, не могут быть удалены из базы данных. Чтобы удалить роль, имеющую члены, необходимо сначала удалить эти члены из данной роли.  
  
 Чтобы удалить членов из роли базы данных, используйте [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md).  
  
 Удаление предопределенной роли базы данных не может быть осуществлено с помощью инструкции DROP ROLE.  
  
 Сведения о членстве в роли можно просмотреть в представлении каталога sys.database_role_members.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
 Чтобы удалить роль сервера, используйте [DROP SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Требуется **ALTER ANY ROLE** разрешения в базе данных или **УПРАВЛЕНИЯ** разрешений на роль или членство в **db_securityadmin**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется роль базы данных `purchasing` из `AdventureWorks2012` базы данных.  
  
```  
DROP ROLE purchasing;  
GO  
```  
  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [ИЗМЕНИТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Функции безопасности &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  



