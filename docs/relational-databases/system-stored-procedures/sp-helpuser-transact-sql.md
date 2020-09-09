---
description: sp_helpuser (Transact-SQL)
title: sp_helpuser (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpuser
- sp_helpuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpuser
ms.assetid: 9c70b41d-ef4c-43df-92da-bd534c287ca1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e9ea3b0b0b6d1700c486514c29f889cc7beb3566
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546045"
---
# <a name="sp_helpuser-transact-sql"></a>sp_helpuser (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения об основных участниках уровня базы данных.  
  
> [!IMPORTANT]  
>  **sp_helpuser** не возвращает сведения о защищаемых объектах, которые появились в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] . Вместо этого используйте представление [sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpuser [ [ @name_in_db = ] 'security_account' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name_in_db = ] 'security_account'` Имя пользователя базы данных или роли базы данных в текущей базе данных. *security_account* должен существовать в текущей базе данных. Аргумент *security_account* имеет тип **sysname**и значение по умолчанию NULL. Если *security_account* не указан, **sp_helpuser** возвращает сведения обо всех участниках базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 В следующей таблице показан результирующий набор, если для security_account не указаны ни учетная запись пользователя, ни [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь Windows. *security_account*  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**UserName**|**sysname**|Пользователи текущей базы данных.|  
|**RoleName**|**sysname**|Роли, к которым принадлежит **имя пользователя** .|  
|**LoginName**|**sysname**|Имя входа **пользователя**.|  
|**DefDBName**|**sysname**|База данных по умолчанию для **имени пользователя**.|  
|**DefSchemaName**|**sysname**|Установленная по умолчанию схема пользователя базы данных.|  
|**UserID**|**smallint**|Идентификатор **имени пользователя** в текущей базе данных.|  
|**SID**|**smallint**|Идентификатор безопасности вошедшего в систему пользователя.|  
  
 В следующей таблице приведен результирующий набор для случая, когда не задана учетная запись пользователя, а в текущей базе данных существуют псевдонимы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Имена входа, назначенные пользователям текущей базы данных.|  
|**UserNameAliasedTo**|**sysname**|Имя пользователя текущей базы данных, которому присвоено данное имя входа.|  
  
 В следующей таблице показан результирующий набор, если для *security_account*указана роль.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Role_name**|**sysname**|Имя роли в текущей базе данных.|  
|**Role_id**|**smallint**|Идентификатор роли в текущей базе данных.|  
|**Users_in_role**|**sysname**|Член роли в текущей базе данных.|  
|**UserID**|**smallint**|Идентификатор пользователя для члена роли.|  
  
## <a name="remarks"></a>Примечания  
 Чтобы просмотреть сведения о членстве в ролях базы данных, используйте представление [sys. database_role_members](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md). Чтобы просмотреть сведения о членах роли сервера, используйте представление [sys. server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md), а чтобы просмотреть сведения об участниках уровня сервера, используйте представление [sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
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
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)  
  
  
