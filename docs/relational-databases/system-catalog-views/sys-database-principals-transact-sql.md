---
title: sys.database_principals (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_principals
- database_principals_TSQL
- sys.database_principals
- sys.database_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_principals catalog view
ms.assetid: 8cb239e9-eb8c-4109-9cec-0d35de95fa0e
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 411d5af51163124448823c2fda553a5b294c4368
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43066974"
---
# <a name="sysdatabaseprincipals-transact-sql"></a>sys.database_principals (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке для каждого субъекта безопасности в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя участника, уникальное в пределах базы данных.|  
|**principal_id**|**int**|Идентификатор участника, уникальный в пределах базы данных.|  
|**type**|**char(1)**|Тип участника:<br /><br /> A = роль приложения<br /><br /> C = пользователь сопоставлен с сертификатом<br /><br /> E = внешнего пользователя из Azure Active Directory<br /><br /> G = группа Windows<br /><br /> K = пользователь сопоставлен с асимметричным ключом<br /><br /> R = роль базы данных<br /><br /> S = пользователь SQL<br /><br /> U = пользователь Windows<br /><br /> X = внешней группы из группы Azure Active Directory или приложения|  
|**type_desc**|**nvarchar(60)**|Описание типа участника.<br /><br /> APPLICATION_ROLE<br /><br /> CERTIFICATE_MAPPED_USER<br /><br /> EXTERNAL_USER<br /><br /> WINDOWS_GROUP<br /><br /> ASYMMETRIC_KEY_MAPPED_USER<br /><br /> DATABASE_ROLE<br /><br /> SQL_USER<br /><br /> WINDOWS_USER<br /><br /> EXTERNAL_GROUPS|  
|**default_schema_name**|**sysname**|Имя, используемое в случае, когда схема не определяется именем SQL. NULL для участников с типами, отличными от S, U или A.|  
|**create_date**|**datetime**|Время создания участника.|  
|**modify_date**|**datetime**|Время последнего изменения участника.|  
|**owning_principal_id**|**int**|Идентификатор участника, являющегося владельцем данного участника. Владельцем всех участников, кроме ролей баз данных **dbo**.|  
|**ИД безопасности**|**varbinary(85)**|SID (идентификатор защиты) участника.  NULL для SYS и INFORMATION SCHEMAS.|  
|**is_fixed_role**|**bit**|Если значение равно 1, в данной строке представляется запись для одной из предопределенных ролей базы данных: db_owner, db_accessadmin, db_datareader, db_datawriter, db_ddladmin, db_securityadmin, db_backupoperator, db_denydatareader, db_denydatawriter.|  
|**authentication_type**|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Обозначает тип проверки подлинности. Ниже приведены возможные значения и их описания.<br /><br /> 0: без проверки подлинности<br />1: проверка подлинности экземпляра<br />2: проверка подлинности базы данных<br />3: проверка подлинности Windows|  
|**authentication_type_desc**|**nvarchar(60)**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Описание типа проверки подлинности. Ниже приведены возможные значения и их описания.<br /><br /> NONE: Проверка подлинности<br />ЭКЗЕМПЛЯР: Проверка подлинности экземпляра<br />База данных: Проверка подлинности базы данных<br />WINDOWS: Проверка подлинности Windows|  
|**default_language_name**|**sysname**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Обозначает язык по умолчанию для участника.|  
|**default_language_lcid**|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Обозначает код языка по умолчанию для участника.|  
|**allow_encrypted_value_modifications**|**bit**|**Применимо к**: с [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Отключает проверки шифрованных метаданных на сервере в операциях массового копирования. Это позволяет пользователю массово копировать данные, зашифрованные с помощью Always Encrypted, между таблицами или базами данных, не расшифровывая данные. Значение по умолчанию — OFF. |      
  
## <a name="remarks"></a>Примечания  
 *PasswordLastSetTime* доступны во всех поддерживаемых конфигурациях SQL Server, но другие свойства доступны только в случае, когда SQL Server работает на Windows Server 2003 или более поздней версии и CHECK_POLICY и CHECK_ Срок действия включены. См. в разделе [ןאנמכוי](../../relational-databases/security/password-policy.md) Дополнительные сведения.  
  
## <a name="permissions"></a>Разрешения  
 Любой пользователь может видеть собственное имя пользователя, пользователей системы и предопределенные роли базы данных. Для просмотра данных других пользователей требуется разрешение ALTER ANY USER или разрешение на доступ к данным пользователя. Для просмотра определяемых пользователем ролей необходимо иметь разрешение ALTER ANY ROLE или быть членом роли.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-the-permissions-of-database-principals"></a>А. Перечисление всех разрешений участников базы данных  
 Следующий запрос перечисляет разрешения, явно предоставленные или отклоненные для участников базы данных.  
  
> [!IMPORTANT]  
>  Разрешения предопределенных ролей базы данных не отображаются в sys.database_permissions. Поэтому участники базы данных могут иметь дополнительные разрешения, не перечисленные здесь.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="b-listing-permissions-on-schema-objects-within-a-database"></a>Б. список разрешений для объектов схемы в базу данных  
 Следующий запрос объединяет sys.database_principals и sys.database_permissions с sys.objects и sys.schemas, чтобы перечислить разрешения, предоставленные или отклоненные для определенных объектов схемы.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc,   
    pe.permission_name, s.name + '.' + o.name AS ObjectName  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id  
JOIN sys.objects AS o  
    ON pe.major_id = o.object_id  
JOIN sys.schemas AS s  
    ON o.schema_id = s.schema_id;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-listing-all-the-permissions-of-database-principals"></a>C: перечисление всех разрешений участников базы данных  
 Следующий запрос перечисляет разрешения, явно предоставленные или отклоненные для участников базы данных.  
  
> [!IMPORTANT]  
>  Разрешения предопределенных ролей базы данных не отображаются в `sys.database_permissions`. Поэтому участники базы данных могут иметь дополнительные разрешения, не перечисленные здесь.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="d-listing-permissions-on-schema-objects-within-a-database"></a>D:. список разрешений для объектов схемы в базу данных  
 В следующем запросе соединения `sys.database_principals` и `sys.database_permissions` для `sys.objects` и `sys.schemas` Чтобы перечислить разрешения, предоставленные или отклоненные для определенных объектов схемы.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc,   
    pe.permission_name, s.name + '.' + o.name AS ObjectName  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id  
JOIN sys.objects AS o  
    ON pe.major_id = o.object_id  
JOIN sys.schemas AS s  
    ON o.schema_id = s.schema_id;  
```  
  
## <a name="see-also"></a>См. также  
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Пользователи автономной базы данных — создание переносимой базы данных](../../relational-databases/security/contained-database-users-making-your-database-portable.md)   
 [Подключение к базе данных SQL с использованием аутентификации Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)  
  
  


