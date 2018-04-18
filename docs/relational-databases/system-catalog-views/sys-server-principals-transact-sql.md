---
title: sys.server_principals (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_principals
- sys.server_principals_TSQL
- sys.server_principals
- server_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_principals catalog view
ms.assetid: c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3705caa0221d2e0f4a6b93b6d2ffffb9b2fcb9e4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysserverprincipals-transact-sql"></a>sys.server_principals (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Содержит одну строку для каждого участника уровня сервера.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя участника. Уникален в пределах сервера.|  
|**principal_id**|**int**|Идентификатор участника. Уникален в пределах сервера.|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор SID (Security-IDentifier, идентификатор защиты) участника. Для участника Windows соответствует идентификатору SID Windows.|  
|**type**|**char(1)**|Тип участника:<br /><br /> S = имя входа SQL<br /><br /> U = имя входа Windows<br /><br /> G = группа Windows<br /><br /> R = роль сервера<br /><br /> C = имя входа, сопоставленное сертификату<br /><br /> K = имя входа, сопоставленное асимметричному ключу|  
|**type_desc**|**nvarchar(60)**|Описание типа участника:<br /><br /> SQL_LOGIN<br /><br /> WINDOWS_LOGIN<br /><br /> WINDOWS_GROUP<br /><br /> SERVER_ROLE<br /><br /> CERTIFICATE_MAPPED_LOGIN<br /><br /> ASYMMETRIC_KEY_MAPPED_LOGIN|  
|**is_disabled**|**int**|1 = имя входа отключено.|  
|**create_date**|**datetime**|Время создания участника.|  
|**modify_date**|**datetime**|Время последнего изменения определения участника.|  
|**default_database_name**|**sysname**|База данных участника по умолчанию.|  
|**default_language_name**|**sysname**|Язык участника по умолчанию.|  
|**credential_id**|**int**|Идентификатор учетных данных, связанный с участником. Если с участником не связаны никакие учетные данные, идентификатор credential_id будет иметь значение NULL.|  
|**owning_principal_id**|**int**|**Principal_id** владельца роли сервера. NULL, если участник не является ролью сервера.|  
|**is_fixed_role**|**бит**|Возвращает 1, если участник является одной из предопределенных ролей сервера. Дополнительные сведения см. в статье [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md).|  
  
## <a name="permissions"></a>Разрешения  
 Любое имя входа может видеть собственное имя входа, системные имена входа и предопределенные роли сервера. Для просмотра других имен входа требуется разрешение ALTER ANY LOGIN или разрешение на имя входа. Для просмотра определяемых пользователем ролей сервера необходимо иметь разрешение ALTER ANY SERVER ROLE или быть членом роли.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 Следующий запрос перечисляет разрешения, явно предоставленные или отклоненные для участников на уровне сервера.  
  
> [!IMPORTANT]  
>  Разрешения предопределенных ролей сервера не отображаются в sys.server_permissions. Поэтому участники на уровне сервера могут иметь дополнительные разрешения, не перечисленные здесь.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>См. также  
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Иерархия разрешений (компонент Database Engine)](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
