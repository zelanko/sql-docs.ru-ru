---
title: sp_helpuser (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpuser
- sp_helpuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpuser
ms.assetid: 9c70b41d-ef4c-43df-92da-bd534c287ca1
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 343439dd04f9f74c0a5444afef25921072d9d14c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpuser-transact-sql"></a>sp_helpuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об основных участниках уровня базы данных.  
  
> [!IMPORTANT]  
>  **sp_helpuser** не возвращает сведения о защищаемых объектах, появившихся в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Используйте [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpuser [ [ @name_in_db = ] 'security_account' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@name_in_db =** ] **"***security_account***"**  
 Имя пользователя или роли в текущей базе данных. *security_account* должен существовать в текущей базе данных. *security_account* — **sysname**, значение по умолчанию NULL. Если *security_account* не указан, **sp_helpuser** возвращает сведения обо всех участниках базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 В следующей таблице показаны результирующий набор, если ни одна учетная запись пользователя, ни [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или пользователя Windows, указанных в *security_account*.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**UserName**|**sysname**|Пользователи текущей базы данных.|  
|**RoleName**|**sysname**|Роли, к которым **UserName** принадлежит.|  
|**LoginName**|**sysname**|Имя входа для **UserName**.|  
|**DefDBName**|**sysname**|База данных по умолчанию **UserName**.|  
|**DefSchemaName**|**sysname**|Установленная по умолчанию схема пользователя базы данных.|  
|**UserID**|**smallint**|Идентификатор **UserName** в текущей базе данных.|  
|**SID**|**smallint**|Идентификатор безопасности вошедшего в систему пользователя.|  
  
 В следующей таблице приведен результирующий набор для случая, когда не задана учетная запись пользователя, а в текущей базе данных существуют псевдонимы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Имена входа, назначенные пользователям текущей базы данных.|  
|**UserNameAliasedTo**|**sysname**|Имя пользователя текущей базы данных, которому присвоено данное имя входа.|  
  
 В следующей таблице показаны результирующий набор, если роль указан для *security_account*.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**role_name**|**sysname**|Имя роли в текущей базе данных.|  
|**Role_id**|**smallint**|Идентификатор роли в текущей базе данных.|  
|**Users_in_role**|**sysname**|Член роли в текущей базе данных.|  
|**идентификатор пользователя**|**smallint**|Идентификатор пользователя для члена роли.|  
  
## <a name="remarks"></a>Замечания  
 Чтобы просмотреть сведения о членстве в ролях базы данных, используйте [sys.database_role_members](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md). Чтобы просмотреть сведения о членстве в ролях сервера, используйте [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)и для отображения сведений об объектах уровня сервера, используйте [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public** .  
  
 Полученные данные подлежат ограничениям на доступ к метаданным. Сущности, на которые участник не имеет разрешения, не показаны. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-users"></a>A. Перечисление всех пользователей  
 В следующем примере отображается список всех пользователей текущей базы данных.  
  
```  
EXEC sp_helpuser;  
```  
  
### <a name="b-listing-information-for-a-single-user"></a>Б. Перечисление сведений об одном пользователе  
 В следующем примере отображается информация о владельце базы данных пользователей (`dbo`).  
  
```  
EXEC sp_helpuser 'dbo';  
```  
  
### <a name="c-listing-information-for-a-database-role"></a>В. Перечисление сведений о роли базы данных  
 В следующем примере отображается информация о предопределенной роли базы данных `db_securityadmin`.  
  
```  
EXEC sp_helpuser 'db_securityadmin';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
  
