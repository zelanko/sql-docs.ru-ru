---
title: "Роли уровня базы данных | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.roleproperties.database.f1
- sql13.swb.roleproperties.object.f1
- SQL13.SWB.DBROLEPROPERTIES.GENERAL.F1
- sql13.swb.roleproperties.general.f1
helpviewer_keywords:
- db_denydatareader role
- users [SQL Server], database roles
- database-level roles [SQL Server]
- db_denydatawriter role
- roles [SQL Server], database
- principals [SQL Server], database-level
- db_backupoperator role
- credentials [SQL Server], roles
- db_accessadmin role
- schemas [SQL Server], roles
- permissions [SQL Server], roles
- database roles [SQL Server], listed
- db_datareader role
- db_ddladmin role
- db_datawriter role
- db_securityadmin role
- db_owner role
- database roles [SQL Server]
- fixed database roles [SQL Server]
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: 7f3fa5f6-6b50-43bb-9047-1544ade55e39
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 411da6974090c9ccad6aa6184c248537bfdebe79
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# <a name="database-level-roles"></a>Роли уровня базы данных
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  Для удобства управления разрешениями в базах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет несколько *ролей* , которые являются субъектами безопасности, группирующими других участников. Они подобны ***группам*** в операционной системе [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Разрешения ролей уровня базы данных распространяются на всю базу данных.  

Чтобы добавлять и удалять пользователей в роли базы данных, используйте параметры `ADD MEMBER` и `DROP MEMBER` инструкции [ALTER ROLE](../../../t-sql/statements/alter-role-transact-sql.md) . [!INCLUDE[ssPDW_md](../../../includes/sspdw-md.md)] не поддерживает такое использование `ALTER ROLE`. Используйте вместо этого более старые процедуры [sp_addrolemember](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) и [sp_droprolemember](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) .
  
 Существует два типа ролей уровня базы данных: *предопределенные роли базы данных* , являющиеся стандартными для базы данных, и *пользовательские роли базы данных* , которые можно создавать.  
  
 Предопределенные роли базы данных задаются на уровне базы данных и предусмотрены в каждой базе данных. Члены ролей базы данных **db_owner** могут управлять членством в предопределенных ролях базы данных. Кроме того, в базе данных msdb имеются специальные роли базы данных.  
  
 В роли уровня базы данных можно добавить любую учетную запись базы данных и другие роли [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Каждый член предопределенной роли базы данных может добавлять других пользователей в ту же самую роль.  
  
> [!TIP]  
>  Не добавляйте пользовательские роли базы данных в качестве членов предопределенных ролей. Это может привести к непреднамеренному повышению прав доступа.  

Разрешения пользовательских ролей базы данных можно настроить с помощью инструкций GRANT, DENY и REVOKE. Дополнительные сведения см. в разделе [Разрешения (компонент Database Engine)](../../../relational-databases/security/permissions-database-engine.md).

Список всех разрешений см. в афише с [разрешениями для ядра СУБД](http://go.microsoft.com/fwlink/?LinkId=229142) . (Разрешения уровня сервера нельзя предоставлять роли базы данных. Имена входа и другие субъекты уровня сервера (например, роли сервера) нельзя добавлять в роли базы данных. Для обеспечения безопасности на уровне сервера в [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)]используйте вместо этого [роли сервера](../../../relational-databases/security/authentication-access/server-level-roles.md) . Разрешения уровня сервера нельзя предоставлять посредством ролей в [!INCLUDE[ssSDS_md](../../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../../includes/sssdw-md.md)].)

## <a name="fixed-database-roles"></a>предопределенные роли базы данных
  
 В следующей таблице представлены предопределенные роли базы данных и их возможности. Эти роли существуют во всех базах данных. За исключением **открытый** роли базы данных, разрешения, назначенные ролям-database не может изменяться.   
  
|Имя предопределенной роли базы данных|Description|  
|-------------------------------|-----------------|  
|**db_owner**|Члены предопределенной роли базы данных **db_owner** могут выполнять все действия по настройке и обслуживанию базы данных, а также удалять базу данных в [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)]. (В [!INCLUDE[ssSDS_md](../../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../../includes/sssdw-md.md)]некоторые операции по обслуживанию требуют наличие разрешений на уровне сервера и не может быть выполнены членами **db_owner**.)|  
|**db_securityadmin**|Элементы предопределенной роли базы данных **db_securityadmin** могут изменять членство в роли и управлять разрешениями. Добавление участников к этой роли может привести к непреднамеренному повышению прав доступа.|  
|**db_accessadmin**|Члены предопределенной роли базы данных **db_accessadmin** могут добавлять или удалять права удаленного доступа к базе данных для имен входа и групп Windows, а также имен входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|**db_backupoperator**|Члены предопределенной роли базы данных **db_backupoperator** могут создавать резервные копии базы данных.|  
|**db_ddladmin**|Члены предопределенной роли базы данных **db_ddladmin** могут выполнять любые команды языка определения данных (DDL) в базе данных.|  
|**db_datawriter**|Члены предопределенной роли базы данных **db_datawriter** могут добавлять, удалять или изменять данные во всех пользовательских таблицах.|  
|**db_datareader**|Элементы предопределенной роли базы данных **db_datareader** могут считывать все данные из всех пользовательских таблиц.|  
|**db_denydatawriter**|Члены предопределенной роли базы данных **db_denydatawriter** не могут добавлять, изменять или удалять данные в пользовательских таблицах базы данных.|  
|**db_denydatareader**|Члены предопределенной роли базы данных **db_denydatareader** не могут считывать данные из пользовательских таблиц базы данных.|  

Нельзя изменить разрешения, назначенные предопределенным ролям базы данных. На следующем рисунке показаны разрешения, назначенные предопределенным ролям базы данных:

![fixed_database_role_permissions](../../../relational-databases/security/authentication-access/media/permissions-of-database-roles.png)

## <a name="special-roles-for-includesssdsmdincludessssds-mdmd-and-includesssdwmdincludessssdw-mdmd"></a>Специальные роли для [!INCLUDE[ssSDS_md](../../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../../includes/sssdw-md.md)]

Эти роли базы данных существуют только в виртуальной базе данных master. Их разрешения ограничены действиями, выполняемыми в базе данных master. В эти роли можно добавить только пользователей из базы данных master. Для этих ролей нельзя добавить имена входа, однако можно создать пользователей на основе имен входа, а затем добавить этих пользователей в роли. Кроме того, в эти роли можно добавить пользователей автономной базы данных из базы данных master.

|Имя роли|Description|  
|--------------------|-----------------|
**dbmanager** | Может создавать и удалять базы данных. Член роли dbmanager, который создает базу данных, становится ее владельцем, что позволяет ему подключиться к этой базе данных в качестве пользователя dbo. Пользователь dbo имеет все разрешения в этой базе данных. Члены роли dbmanager необязательно обладают разрешениями для доступа к базам данных, которые им не принадлежат.
**loginmanager** | Может создать и удалять имена входа в виртуальной базе данных master.  

> [!NOTE]
> Субъект на уровне сервера и администратор Azure Active Directory (если настроено) имеют все разрешения в [!INCLUDE[ssSDS_md](../../../includes/sssds-md.md)] и [!INCLUDE[ssSDW_md](../../../includes/sssdw-md.md)] без необходимости участия в каких-либо ролях. Дополнительные сведения см. в разделе [SQL Database Authentication and Authorization: Granting Access](https://azure.microsoft.com/documentation/articles/sql-database-manage-logins/)(Проверка подлинности и авторизация базы данных SQL: предоставление доступа). 
  
## <a name="msdb-roles"></a>Роли базы данных msdb  
 База данных msdb содержит специальные роли, показанные в следующей таблице.  
  
|Имя роли базы данных msdb|Description|  
|--------------------|-----------------|  
|**db_ssisadmin**<br /><br /> **db_ssisoperator**<br /><br /> **db_ssisltduser**|Члены этих ролей базы данных могут администрировать и использовать службы [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], обновленные с предыдущей версии, могут содержать более старую версию роли, имя которой присвоено с помощью служб DTS, а не служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Дополнительные сведения см. в разделе [Роли служб Integration Services (службы SSIS)](../../../integration-services/security/integration-services-roles-ssis-service.md).|  
|**dc_admin**<br /><br /> **dc_operator**<br /><br /> **dc_proxy**|Члены этих ролей базы данных могут администрировать и использовать сборщик данных. Дополнительные сведения см. в разделе [Data Collection](../../../relational-databases/data-collection/data-collection.md).|  
|**PolicyAdministratorRole**|Члены роли базы данных **db_ PolicyAdministratorRole** могут выполнять все действия по настройке и обслуживанию политик и условий средства "Управление на основе политики". Дополнительные сведения см. в разделах [Администрирование серверов с помощью управления на основе политик](../../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md).|  
|**ServerGroupAdministratorRole**<br /><br /> **ServerGroupReaderRole**|Члены этих ролей базы данных могут администрировать и использовать зарегистрированные группы серверов.|  
|**dbm_monitor**|Создается в базе данных **msdb** при регистрации в мониторе зеркального отображения базы данных первой базы данных. Роль **dbm_monitor** не имеет членов до тех пор, пока системный администратор не назначит ее пользователям.|  
  
> [!IMPORTANT]  
>  Члены роли **db_ssisadmin** и роли **dc_admin** могут повышать свои права доступа до sysadmin. Такое повышение права доступа может произойти, так как эти роли могут изменять пакеты служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , а пакеты [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] могут выполняться [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при помощи контекста безопасности sysadmin агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы предотвратить такое повышение прав доступа при выполнении планов обслуживания, наборов элементов сбора данных и других пакетов служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , настройте задания агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , запускающие пакеты, на использование учетной записи-посредника с ограниченными правами доступа или добавьте в роли **db_ssisadmin** и **dc_admin** только членов роли **sysadmin** .  

## <a name="working-with-r-services"></a>Работа со службами R Services  

**Область применения:** SQL Server, начиная с [!INCLUDE[ssSQLv14_md](../../../includes/sssqlv14-md.md)]   

При установке служб R Services доступны дополнительные роли базы данных для управления пакетами. Дополнительные сведения см. в разделе [Управление пакетами R для SQL Server](../../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).

|Имя роли |Description|  
|-------------|-----------------|
|**rpkgs-users** |Позволяет пользователям использовать любые общие пакеты, установленные членами роли rpkgs-shared.|
|**rpkgs-private** |Предоставляет доступ к общим пакетам с такими же разрешениями, как и роль rpkgs-users. Члены этой роли также могут устанавливать, удалять и использовать пакеты, относящиеся к частной области.|
|**rpkgs-shared** |Предоставляет такие же разрешения, как и роль rpkgs-private. Пользователи, являющиеся членами этой роли, также могут устанавливать и удалять общие пакеты.|
  
## <a name="working-with-database-level-roles"></a>Работа с ролями уровня базы данных  
 В следующей таблице описаны команды, представления и функции, предназначенные для работы с ролями уровня баз данных.  
  
|Компонент|Тип|Description|  
|-------------|----------|-----------------|  
|[sp_helpdbfixedrole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)|Метаданные|Возвращает список всех предопределенных ролей базы данных.|  
|[sp_dbfixedrolepermission &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md)|Метаданные|Отображает разрешения предопределенной роли базы данных.|  
|[sp_helprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)|Метаданные|Возвращает информацию о ролях, относящихся к текущей базе данных.|  
|[sp_helprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)|Метаданные|Возвращает сведения о членах роли в текущей базе данных.|  
|[sys.database_role_members &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)|Метаданные|Возвращает одну строку для каждого члена каждой роли базы данных.|  
|[IS_MEMBER &#40;Transact-SQL&#41;](../../../t-sql/functions/is-member-transact-sql.md)|Метаданные|Указывает, является ли текущий пользователь членом указанной группы Microsoft Windows или роли базы данных Microsoft SQL Server.|  
|[CREATE ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-role-transact-sql.md)|Command|Создает новую роль базы данных в текущей базе данных.|  
|[ALTER ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-role-transact-sql.md)|Command|Изменяет имя или членство роли базы данных.|  
|[DROP ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-role-transact-sql.md)|Command|Удаляет роль из базы данных.|  
|[sp_addrole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)|Command|Создает новую роль базы данных в текущей базе данных.|  
|[sp_droprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)|Command|Удаляет роль базы данных из текущей базы данных.|  
|[sp_addrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)|Command|Добавляет пользователя базы данных, роль базы данных, имя входа Windows или группу Windows к роли текущей базы данных. Все платформы, за исключением [!INCLUDE[ssPDW_md](../../../includes/sspdw-md.md)], должны использовать вместо этого `ALTER ROLE`.|  
|[sp_droprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)|Command|Удаляет учетную запись безопасности из роли SQL Server в текущей базе данных. Все платформы, за исключением [!INCLUDE[ssPDW_md](../../../includes/sspdw-md.md)] , должны использовать вместо этого `ALTER ROLE` .|
|[GRANT](../../../t-sql/statements/grant-transact-sql.md)| Permissions | Добавляет разрешение для роли.
|[DENY](../../../t-sql/statements/deny-transact-sql.md)| Permissions | Запрещает разрешение для роли.
|[REVOKE](../../../t-sql/statements/revoke-transact-sql.md)| Permissions | Удаляет разрешения, выданные или запрещенные ранее.
  
  
## <a name="public-database-role"></a>Роль базы данных public  
 Каждый пользователь базы данных является членом роли базы данных **public** . Если для пользователя не были предоставлены или запрещены конкретные разрешения на защищаемый объект, он наследует разрешения роли **public** на этот объект. Пользователей базы данных нельзя удалить из роли **public** . 
  
## <a name="related-content"></a>См. также  
 [Представления каталога безопасности &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
  
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
 [Функции безопасности &#40;Transact-SQL&#41;](../../../t-sql/functions/security-functions-transact-sql.md)  
  
 [Обеспечение безопасности SQL Server](../../../relational-databases/security/securing-sql-server.md)  
  
 [sp_helprotect &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)  
  
  

