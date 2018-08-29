---
title: Роли уровня базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 09/22/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server 2014
f1_keywords:
- sql12.swb.roleproperties.database.f1
- sql12.swb.roleproperties.general.f1
- sql12.swb.roleproperties.object.f1
- SQL12.SWB.DBROLEPROPERTIES.GENERAL.F1
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 814b585d1ac15af1b083a3191ca44c32fe29e15e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027687"
---
# <a name="database-level-roles"></a>Роли уровня базы данных
  Для удобства управления разрешениями в базах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет несколько *ролей* , которые являются субъектами безопасности, группирующими других участников. Они подобны ***группам*** в операционной системе [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Разрешения ролей уровня базы данных распространяются на всю базу данных.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]существует два типа ролей уровня базы данных: *предопределенные роли базы данных* , являющиеся стандартными для базы данных, и *гибкие роли базы данных* , которые можно создавать.  
  
 Предопределенные роли базы данных задаются на уровне базы данных и предусмотрены в каждой базе данных. Члены ролей базы данных **db_owner** могут управлять членством в предопределенных ролях базы данных. Кроме того, в базе данных msdb имеются специальные предопределенные роли базы данных.  
  
 В роли уровня базы данных можно добавить любую учетную запись базы данных и другие роли [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Каждый член предопределенной роли базы данных может добавлять другие имена входа к той же роли.  
  
> [!IMPORTANT]  
>  Не добавляйте гибкие роли базы данных в качестве членов предопределенных ролей. Это может привести к непреднамеренному повышению прав доступа.  
  
 В следующей таблице представлены предопределенные роли уровня базы данных и их возможности. Эти роли существуют во всех базах данных.  
  
|Имя роли уровня базы данных|Описание|  
|-------------------------------|-----------------|  
|**db_owner**|Члены предопределенной роли базы данных **db_owner** могут выполнять все действия по настройке и обслуживанию базы данных, а также удалять базу данных.|  
|**db_securityadmin**|Элементы предопределенной роли базы данных **db_securityadmin** могут изменять членство в роли и управлять разрешениями. Добавление участников к этой роли может привести к непреднамеренному повышению прав доступа.|  
|**db_accessadmin**|Члены предопределенной роли базы данных **db_accessadmin** могут добавлять или удалять права удаленного доступа к базе данных для имен входа и групп Windows, а также имен входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|**db_backupoperator**|Члены предопределенной роли базы данных **db_backupoperator** могут создавать резервные копии базы данных.|  
|**db_ddladmin**|Члены предопределенной роли базы данных **db_ddladmin** могут выполнять любые команды языка определения данных (DDL) в базе данных.|  
|**db_datawriter**|Члены предопределенной роли базы данных **db_datawriter** могут добавлять, удалять или изменять данные во всех пользовательских таблицах.|  
|**db_datareader**|Элементы предопределенной роли базы данных **db_datareader** могут считывать все данные из всех пользовательских таблиц.|  
|**db_denydatawriter**|Члены предопределенной роли базы данных **db_denydatawriter** не могут добавлять, изменять или удалять данные в пользовательских таблицах базы данных.|  
|**db_denydatareader**|Члены предопределенной роли базы данных **db_denydatareader** не могут считывать данные из пользовательских таблиц базы данных.|  
  
## <a name="msdb-roles"></a>Роли базы данных msdb  
 База данных msdb содержит специальные роли, показанные в следующей таблице.  
  
|Имя роли базы данных msdb|Описание|  
|--------------------|-----------------|  
|`db_ssisadmin`<br /><br /> **db_ssisoperator**<br /><br /> **db_ssisltduser**|Члены этих ролей базы данных могут администрировать и использовать службы [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], обновленные с предыдущей версии, могут содержать более старую версию роли, имя которой присвоено с помощью служб DTS, а не служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Дополнительные сведения см. в разделе [Роли служб Integration Services (службы SSIS)](../../../integration-services/security/integration-services-roles-ssis-service.md).|  
|`dc_admin`<br /><br /> **dc_operator**<br /><br /> **dc_proxy**|Члены этих ролей базы данных могут администрировать и использовать сборщик данных. Дополнительные сведения см. в разделе [Data Collection](../../data-collection/data-collection.md).|  
|**PolicyAdministratorRole**|Члены роли базы данных **db_ PolicyAdministratorRole** могут выполнять все действия по настройке и обслуживанию политик и условий средства "Управление на основе политики". Дополнительные сведения см. в разделах [Администрирование серверов с помощью управления на основе политик](../../policy-based-management/administer-servers-by-using-policy-based-management.md).|  
|**ServerGroupAdministratorRole**<br /><br /> **ServerGroupReaderRole**|Члены этих ролей базы данных могут администрировать и использовать зарегистрированные группы серверов.|  
|**dbm_monitor**|Созданные в `msdb` базы данных во время первой базы данных регистрируется в мониторе зеркального отображения базы данных. Роль **dbm_monitor** не имеет членов до тех пор, пока системный администратор не назначит ее пользователям.|  
  
> [!IMPORTANT]  
>  Члены роли db_ssisadmin и роли dc_admin могут повышать свои права доступа до sysadmin. Такое повышение права доступа может произойти, так как эти роли могут изменять пакеты служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , а пакеты [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] могут выполняться [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при помощи контекста безопасности sysadmin агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы предотвратить такое повышение прав при выполнении планов обслуживания, наборов сбора данных и других пакетов служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], настройте задания агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], запускающие пакеты, на использование учетной записи-посредника с ограниченными правами или добавьте членов sysadmin в роли db_ssisadmin и dc_admin.  
  
## <a name="working-with-database-level-roles"></a>Работа с ролями уровня базы данных  
 В следующей таблице описаны команды, представления и функции, предназначенные для работы с ролями уровня баз данных.  
  
|Компонент|Тип|Описание|  
|-------------|----------|-----------------|  
|[sp_helpdbfixedrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql)|Метаданные|Возвращает список всех предопределенных ролей базы данных.|  
|[sp_dbfixedrolepermission &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql)|Метаданные|Отображает разрешения предопределенной роли базы данных.|  
|[sp_helprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprole-transact-sql)|Метаданные|Возвращает информацию о ролях, относящихся к текущей базе данных.|  
|[sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)|Метаданные|Возвращает сведения о членах роли в текущей базе данных.|  
|[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)|Метаданные|Возвращает одну строку для каждого члена каждой роли базы данных.|  
|[IS_MEMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/is-member-transact-sql)|Метаданные|Указывает, является ли текущий пользователь членом указанной группы Microsoft Windows или роли базы данных Microsoft SQL Server.|  
|[CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql)|Command|Создает новую роль базы данных в текущей базе данных.|  
|[ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql)|Command|Изменяет имя роли базы данных.|  
|[DROP ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-role-transact-sql)|Command|Удаляет роль из базы данных.|  
|[sp_addrole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrole-transact-sql)|Command|Создает новую роль базы данных в текущей базе данных.|  
|[sp_droprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprole-transact-sql)|Command|Удаляет роль базы данных из текущей базы данных.|  
|[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)|Command|Добавляет пользователя базы данных, роль базы данных, имя входа Windows или группу Windows к роли текущей базы данных.|  
|[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)|Command|Удаляет учетную запись безопасности из роли SQL Server в текущей базе данных.|  
  
## <a name="public-database-role"></a>Роль базы данных public  
 Каждый пользователь базы данных является членом роли базы данных **public** . Если для пользователя не были предоставлены или запрещены конкретные разрешения на защищаемый объект, он наследует разрешения роли **public** на этот объект.  
  
## <a name="related-content"></a>См. также  
 [Представления каталога безопасности &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)  
  
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/security-stored-procedures-transact-sql)  
  
 [Функции безопасности &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql)  
  
 [Обеспечение безопасности SQL Server](../securing-sql-server.md)  
  
 [sp_helprotect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprotect-transact-sql)  
  
  
