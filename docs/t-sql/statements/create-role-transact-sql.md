---
title: "Создание РОЛИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE ROLE
- DATABASE ROLE
- ROLE_TSQL
- DATABASE_ROLE_TSQL
- CREATE_ROLE_TSQL
- CREATE DATABASE ROLE
- ROLE
- CREATE_DATABASE_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], creating
- CREATE DATABASE ROLE statement
- roles [SQL Server], creating
- CREATE ROLE statement
ms.assetid: b0cd54ad-e81d-4d71-acec-8a6d7261ca08
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21e3cca3d07d7f53d646b5dd052fd40d0fa2cc1a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-role-transact-sql"></a>CREATE ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Создает новую роль базы данных в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE ROLE role_name [ AUTHORIZATION owner_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *role_name*  
 Имя создаваемой роли.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Пользователь (или роль) базы данных, который станет владельцем новой роли. Если пользователь не указан, владельцем роли станет пользователь, выполнивший инструкцию CREATE ROLE.  
  
## <a name="remarks"></a>Замечания  
 Роли — это сущности, защищаемые на уровне базы данных. После создания роли необходимо настроить для нее разрешения уровня базы данных при помощи инструкций GRANT, DENY и REVOKE. Чтобы добавить членов роли базы данных, используйте [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md). Дополнительные сведения см. в разделе [роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 Роли базы данных видны в представлениях каталога sys.database_role_members и sys.database_principals.  
  
 Сведения о проектировании системы разрешений см. в статье [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Требуется **CREATE ROLE** разрешений в базе данных или членство в группе **db_securityadmin** предопределенной роли базы данных. При использовании **АВТОРИЗАЦИИ** параметр, необходимы следующие разрешения также:  
  
-   Для передачи роли во владение другому пользователю необходимо связанное с этим пользователем разрешение IMPERSONATE.  
  
-   Для передачи роли во владение другой роли необходимо членство в роли-получателе или связанное с этой ролью разрешение ALTER.  
  
-   Для передачи роли во владение роли приложения необходимо связанное с прикладной ролью разрешение ALTER.  
  
## <a name="examples"></a>Примеры  
Всех последующих примерах используется база данных AdventureWorks.   

### <a name="a-creating-a-database-role-that-is-owned-by-a-database-user"></a>A. Создание роли базы данных, принадлежащей пользователю базы данных  
 Следующий пример создает роль базы данных `buyers`, принадлежащую пользователю `BenMiller`.  
  
```  
CREATE ROLE buyers AUTHORIZATION BenMiller;  
GO  
```  
  
### <a name="b-creating-a-database-role-that-is-owned-by-a-fixed-database-role"></a>Б. Создание роли базы данных, принадлежащей предопределенной роли базы данных  
 Следующий пример создает роль базы данных `auditors`, принадлежащую предопределенной роли базы данных `db_securityadmin`.  
  
```  
CREATE ROLE auditors AUTHORIZATION db_securityadmin;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [ИЗМЕНИТЬ РОЛИ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [УДАЛИТЬ РОЛЬ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Хранимая процедура sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Приступая к работе с разрешениями Database Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  



