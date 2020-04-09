---
title: sys.database_principals (Трансакт-СЗЛ) Документы Майкрософт
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: feed483cf3ee08c0652e55de51b1f73fc087ed39
ms.sourcegitcommit: 7ed12a64f7f76d47f5519bf1015d19481dd4b33a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80873120"
---
# <a name="sysdatabase_principals-transact-sql"></a>sys.database_principals (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке для каждого субъекта безопасности в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя участника, уникальное в пределах базы данных.|  
|**principal_id**|**Int**|Идентификатор участника, уникальный в пределах базы данных.|  
|**тип**|**символ (1)**|Тип участника:<br /><br /> A = роль приложения<br /><br /> C = пользователь сопоставлен с сертификатом<br /><br /> E - Внешний пользователь из active-каталога Azure<br /><br /> G = группа Windows<br /><br /> K = пользователь сопоставлен с асимметричным ключом<br /><br /> R = роль базы данных<br /><br /> S = пользователь SQL<br /><br /> U = пользователь Windows<br /><br /> X - Внешняя группа из группы или приложений Active Directory Azure|  
|**type_desc**|**nvarchar(60)**|Описание типа участника.<br /><br /> APPLICATION_ROLE<br /><br /> CERTIFICATE_MAPPED_USER<br /><br /> EXTERNAL_USER<br /><br /> WINDOWS_GROUP<br /><br /> ASYMMETRIC_KEY_MAPPED_USER<br /><br /> DATABASE_ROLE<br /><br /> SQL_USER<br /><br /> WINDOWS_USER<br /><br /> EXTERNAL_GROUPS|  
|**default_schema_name**|**sysname**|Имя, используемое в случае, когда схема не определяется именем SQL. NULL для участников с типами, отличными от S, U или A.|  
|**create_date**|**datetime**|Время создания участника.|  
|**modify_date**|**datetime**|Время последнего изменения участника.|  
|**owning_principal_id**|**Int**|Идентификатор участника, являющегося владельцем данного участника. Все фиксированные роли базы данных принадлежат **dbo** по умолчанию.|  
|**Sid**|**varbinary(85)**|SID (идентификатор защиты) участника.  NULL для SYS и INFORMATION SCHEMAS.|  
|**is_fixed_role**|**bit**|Если 1, эта строка представляет собой запись для одной из ролей фиксированной базы данных: db_owner, db_accessadmin, db_datareader, db_datawriter, db_ddladmin, db_securityadmin, db_backupoperator, db_denydatareader db_denydatawriter.|  
|**authentication_type**|**Int**|**Применяется**к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] : и позже.<br /><br /> Обозначает тип проверки подлинности. Ниже приведены возможные значения и их описания.<br /><br /> 0 : Нет аутентификации<br />1 : Проверка подлинности экземпляра<br />2 : Проверка подлинности базы данных<br />3 : Проверка подлинности Windows<br />4 : Активная аутентификация каталога Azure|  
|**authentication_type_desc**|**nvarchar(60)**|**Применяется**к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] : и позже.<br /><br /> Описание типа проверки подлинности. Ниже приведены возможные значения и их описания.<br /><br /> NONE : Нет аутентификации<br />INSTANCE : Проверка подлинности экземпляров<br />DATABASE : Проверка подлинности базы данных<br />WINDOWS : Проверка подлинности Windows<br />EXTERNAL: Активная аутентификация каталога Azure|  
|**default_language_name**|**sysname**|**Применяется**к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] : и позже.<br /><br /> Обозначает язык по умолчанию для участника.|  
|**default_language_lcid**|**Int**|**Применяется**к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] : и позже.<br /><br /> Обозначает код языка по умолчанию для участника.|  
|**allow_encrypted_value_modifications**|**bit**|**Применяется**к [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] : [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]и позже, .<br /><br /> Отключает проверки шифрованных метаданных на сервере в операциях массового копирования. Это позволяет пользователю навалом копировать данные, зашифрованные с помощью Always Encrypted, между таблицами или базами данных, без расшифровки данных. Значение по умолчанию — OFF. |      
  
## <a name="remarks"></a>Примечания  
 Свойства *PasswordLastSetTime* доступны во всех поддерживаемых конфигурациях сервера S'L, но другие свойства доступны только при запуске сервера S'L на Windows Server 2003 или позже, и как CHECK_POLICY, так и CHECK_EXPIRATION включены. Дополнительную информацию можно узнать из [политики паролей.](../../relational-databases/security/password-policy.md)
Значения principal_id могут быть использованы повторно в том случае, если принципы были сняты и, следовательно, не гарантировано будет постоянно возрастать.
  
## <a name="permissions"></a>Разрешения  
 Любой пользователь может видеть собственное имя пользователя, пользователей системы и предопределенные роли базы данных. Для просмотра данных других пользователей требуется разрешение ALTER ANY USER или разрешение на доступ к данным пользователя. Для просмотра определяемых пользователем ролей необходимо иметь разрешение ALTER ANY ROLE или быть членом роли.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-the-permissions-of-database-principals"></a>О: Перечисление всех разрешений директоров баз данных  
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
  
### <a name="b-listing-permissions-on-schema-objects-within-a-database"></a>B: Перечисление разрешений на объекты схемы в базе данных  
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
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-listing-all-the-permissions-of-database-principals"></a>C: Перечисление всех разрешений директоров баз данных  
 Следующий запрос перечисляет разрешения, явно предоставленные или отклоненные для участников базы данных.  
  
> [!IMPORTANT]  
>  Разрешения на фиксированные роли базы `sys.database_permissions`данных не отображаются в . Поэтому участники базы данных могут иметь дополнительные разрешения, не перечисленные здесь.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="d-listing-permissions-on-schema-objects-within-a-database"></a>D: Перечисление разрешений на объекты схемы в базе данных  
 Следующий запрос `sys.database_principals` присоединяется, `sys.objects` `sys.schemas` `sys.database_permissions` и перечислять разрешения, предоставленные или отклоненные определенным объектам схемы.  
  
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
  
## <a name="see-also"></a>См. также:  
 [&#40;&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals&#41;&#40;"Трансакт-СЗЛ"](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [Просмотры каталогов безопасности &#40;&#41;Transact-S'L](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Содержащиеся пользователи баз данных - сделать вашу базу данных портативной](../../relational-databases/security/contained-database-users-making-your-database-portable.md)   
 [Подключение к базе данных СЗЛ с помощью активной аутентификации каталогов Azure](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)  
  
  


