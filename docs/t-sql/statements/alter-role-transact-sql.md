---
title: "РОЛИ ALTER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ROLE_TSQL
- ALTER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database roles
- ALTER ROLE statement
- renaming database roles
- database roles [SQL Server], modifying
- names [SQL Server], database roles
ms.assetid: e1e83caa-17cc-4871-b2db-2711339fb64f
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3eaee2d346eda964545caa60cd7168b531f47ad9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-role-transact-sql"></a>ALTER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Добавляет или удаляет членов из роли базы данных или изменяет имя роли базы данных, определяемых пользователем.  
  
> [!NOTE]  
>  Для изменения ролей в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте [sp_addrolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) и [sp_droprolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server (starting with 2012) and Azure SQL Database  
  
ALTER ROLE  role_name  
{  
       ADD MEMBER database_principal  
    |  DROP MEMBER database_principal  
    |  WITH NAME = new_name  
}  
[;]  
```  
  
 
```  
-- Syntax for SQL Server 2008 only  
  
-- Change the name of a user-defined database role  
ALTER ROLE role_name   
    WITH NAME = new_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *role_name*  
 **ПРИМЕНЯЕТСЯ к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2008)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает роль базы данных для изменения.  
  
 Добавить ЧЛЕН *database_principal*l  
 **ПРИМЕНЯЕТСЯ к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2012)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает, чтобы добавить участника базы данных членства в роли базы данных.  
  
-   *database_principal* пользователя базы данных или роли базы данных, определяемых пользователем.  
  
-   *database_principal* не может быть фиксированной роли базы данных или сервера-участника.  
  
DROP MEMBER *database_principal*  
 **ПРИМЕНЯЕТСЯ к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2012)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает удаляемый участник базы данных через членство в роли базы данных.  
  
-   *database_principal* пользователя базы данных или роли базы данных, определяемых пользователем.  
  
-   *database_principal* не может быть фиксированной роли базы данных или сервера-участника.  
  
NAME = *новое_имя*  
 **ПРИМЕНЯЕТСЯ к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2008)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 Указывает, чтобы изменить имя роли базы данных, определяемых пользователем. Новое имя должно еще не существует в базе данных.  
  
 Изменение имени роли базы данных не изменяет идентификационный номер, владельца или разрешения роли.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения этой команды необходимо одно или несколько из этих разрешений или членства:  
  
-   **ALTER** разрешение для роли  
-   **Разрешение ALTER ANY ROLE** разрешения в базе данных  
-   Членство в **db_securityadmin** предопределенной роли базы данных  
  
Кроме того чтобы изменить членство в предопределенной роли базы данных необходимо:  
  
-   Членство в **db_owner** предопределенной роли базы данных  
  
## <a name="limitations-and-restrictions"></a>ограничения  
 Не удается изменить имя предопределенной роли базы данных.  
  
## <a name="metadata"></a>Метаданные  
 Следующие системные представления содержат сведения о роли базы данных и участниками базы данных.  
  
-   [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
-   [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-change-the-name-of-a-database-role"></a>A. Изменение имени роли базы данных  
 **ПРИМЕНЯЕТСЯ к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2008)  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 В следующем примере изменяется имя роли `buyers` на `purchasing`. [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
ALTER ROLE buyers WITH NAME = purchasing;  
```  
  
### <a name="b-add-or-remove-role-members"></a>Б. Добавление или удаление членов роли  
 **ПРИМЕНЯЕТСЯ к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с 2012)  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 Этот пример создает роль базы данных с именем `Sales`. Добавляет пользователя базы данных с именем Барри членство и демонстрируется удаление члена Барри. [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
CREATE ROLE Sales;  
ALTER ROLE Sales ADD MEMBER Barry;  
ALTER ROLE Sales DROP MEMBER Barry;  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [УДАЛИТЬ РОЛЬ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  

