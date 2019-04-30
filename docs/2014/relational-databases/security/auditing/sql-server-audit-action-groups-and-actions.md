---
title: Действия и группы действий подсистемы аудита SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 10/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- audit
helpviewer_keywords:
- audit actions [SQL Server]
- audits [SQL Server], groups
- server-level audit actions [SQL Server]
- SQL Server Audit
- audit-level audit actions [SQL Server]
- database-level audit actions [SQL Server]
- audit action groups [SQL Server]
- audits [SQL Server], actions
ms.assetid: b7422911-7524-4bcd-9ab9-e460d5897b3d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: e204a1865c2a928079fcd9b32b31a8ae0c0bd0a8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238136"
---
# <a name="sql-server-audit-action-groups-and-actions"></a>Действия и группы действий подсистемы аудита SQL Server
  Подсистема аудита [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет производить аудит групп событий или отдельных событий на уровне сервера или базы данных. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (ядро СУБД)](sql-server-audit-database-engine.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может содержать ноль или более элементов действий аудита. Эти элементы действий аудита могут быть как группами действий, например Server_Object_Change_Group, так и отдельными действиями, например операциями SELECT для таблицы.  
  
> [!NOTE]  
>  Server_Object_Change_Group включает операции CREATE, ALTER и DROP для любого серверного объекта (базы данных или конечной точки).  
  
 У операций аудита могут быть следующие категории действий.  
  
-   Уровня сервера. Эти действия включают серверные операции, например изменения управления и операции входа и выхода из системы.  
  
-   Уровень базы данных. Эти действия включают в себя операции языка обработки данных (DML) и языка DDL.  
  
-   Уровня аудита. Эти действия включают в себя действия, происходящие во время аудита.  
  
 Некоторые действия, выполняемые в компонентах подсистемы аудита [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , подлежат внутреннему аудиту; в этом случае действия аудита происходят автоматически, поскольку событие происходит в родительском объекте.  
  
 Следующие действия подлежат аудиту по своей природе.  
  
-   Изменение состояния подсистемы аудита сервера (включение или отключение)  
  
 Это событие по своей природе не подлежат аудиту.  
  
-   CREATE SERVER AUDIT SPECIFICATION  
  
-   ALTER SERVER AUDIT SPECIFICATION  
  
-   DROP SERVER AUDIT SPECIFICATION  
  
-   CREATE DATABASE AUDIT SPECIFICATION  
  
-   ALTER DATABASE AUDIT SPECIFICATION  
  
-   DROP DATABASE AUDIT SPECIFICATION  
  
 Все операции аудита отключаются при первоначальном создании.  
  
## <a name="server-level-audit-action-groups"></a>Группы действий аудита уровня сервера  
 Группы действий аудита уровня сервера — это действия, похожие на классы событий аудита безопасности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [SQL Server Event Class Reference](../../event-classes/sql-server-event-class-reference.md).  
  
 В следующей таблице приведены группы действий аудита уровня сервера и представлены эквивалентные классы событий SQL Server (если возможно).  
  
|Имя группы действий|Описание|  
|-----------------------|-----------------|  
|APPLICATION_ROLE_CHANGE_PASSWORD_GROUP|Это событие появляется при изменении пароля для роли приложения. Эквивалентно [Audit App Role Change Password Event Class](../../event-classes/audit-app-role-change-password-event-class.md).|  
|AUDIT_CHANGE_GROUP|Это событие возникает при создании, изменении или удалении любого аудита. Это событие возникает при создании, изменении или удалении спецификации любого аудита. Аудит любых изменений в аудите производится в этом аудите. Эквивалентно [Audit Change Audit Event Class](../../event-classes/audit-change-audit-event-class.md).|  
|BACKUP_RESTORE_GROUP|Это событие вызывается командой резервного копирования или восстановления. Эквивалент [класса событий Audit Backup и Restore](../../event-classes/audit-backup-and-restore-event-class.md).|  
|BROKER_LOGIN_GROUP|Это событие вызывается для составления отчета о сообщениях аудита, связанных с механизмом обеспечения безопасности транспорта компонента Service Broker. Эквивалентно [Audit Broker Login Event Class](../../event-classes/audit-broker-login-event-class.md).|  
|DATABASE_CHANGE_GROUP|Это событие вызывается при создании, изменении или удалении базы данных. Это событие возникает при создании, изменении или удалении любой базы данных. Эквивалентно [Audit Database Management Event Class](../../event-classes/audit-database-management-event-class.md).|  
|DATABASE_LOGOUT_GROUP|Это событие возникает при выходе пользователя автономной базы данных из базы данных. Эквивалентно классу событий Audit Database Logout.|  
|DATABASE_MIRRORING_LOGIN_GROUP|Это событие вызывается для составления отчета о сообщениях аудита, связанных с механизмом обеспечения безопасности транспорта зеркального отображения базы данных. Эквивалентно [Audit Database Mirroring Login Event Class](../../event-classes/audit-database-mirroring-login-event-class.md).|  
|DATABASE_OBJECT_ACCESS_GROUP|Это событие вызывается каждый раз при обращении к типам сообщений, сборкам и контрактам.<br /><br /> Это событие возникает при любом доступе к любой базе данных. **Примечание.**  Это может привести к большого количества записей аудита. <br /><br /> Эквивалентно [Audit Database Object Access Event Class](../../event-classes/audit-database-object-access-event-class.md).|  
|DATABASE_OBJECT_CHANGE_GROUP|Это событие вызывается в тот момент, когда для объекта базы данных (например, для схемы) выполняется инструкция CREATE, ALTER или DROP. Это событие возникает при создании, изменении или удалении любого объекта базы данных. **Примечание.**  Это может привести к очень большому количеству записей аудита. <br /><br /> Эквивалентно [Audit Database Object Management Event Class](../../event-classes/audit-database-object-management-event-class.md).|  
|DATABASE_OBJECT_OWNERSHIP_CHANGE_GROUP|Это событие возникает при изменении владельца объекта в области базы данных. Это событие возникает при любом изменении владельца объекта в любой базе данных на сервере. Эквивалентно [Audit Database Object Take Ownership Event Class](../../event-classes/audit-database-object-take-ownership-event-class.md).|  
|DATABASE_OBJECT_PERMISSION_CHANGE_GROUP|Это событие возникает в тот момент, когда для объекта базы данных (например, сборки или схемы) выполняется инструкция GRANT, REVOKE или DENY. Это событие возникает при любом изменении разрешения на объект для любой базы данных на сервере. Эквивалентно [Audit Database Object GDR Event Class](../../event-classes/audit-database-object-gdr-event-class.md).|  
|DATABASE_OPERATION_GROUP|Это событие вызывается при выполнении различных операций в базе данных, например при создании контрольной точки или уведомлении о запросе подписки. Это событие возникает при любой операции с базой данных в любой базе данных. Эквивалентно [Audit Database Operation Event Class](../../event-classes/audit-database-operation-event-class.md).|  
|DATABASE_OWNERSHIP_CHANGE_GROUP|Это событие вызывается при смене владельца базы данных инструкцией ALTER AUTHORIZATION в момент проверки разрешений на эту операцию. Это событие возникает при любом изменении владельца базы данных в любой базе данных на сервере. Эквивалентно [Audit Change Database Owner Event Class](../../event-classes/audit-change-database-owner-event-class.md).|  
|DATABASE_PERMISSION_CHANGE_GROUP|Это событие возникает в случае, когда инструкции GRANT, REVOKE или DENY выдаются для разрешения на выполнение инструкции любым участником [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (применяется только к событиям базы данных, например предоставлению разрешений на базу данных).<br /><br /> Это событие возникает при любом изменении разрешения базы данных (GDR) для любой базы данных на сервере. Эквивалентно [Audit Database Scope GDR Event Class](../../event-classes/audit-database-scope-gdr-event-class.md).|  
|DATABASE_PRINCIPAL_CHANGE_GROUP|Это событие создается при создании, изменении или удалении из базы данных участников, таких как пользователи. Эквивалентно [Audit Database Principal Management Event Class](../../event-classes/audit-database-principal-management-event-class.md). (Также эквивалентно классу событий подсистемы аудита «Add DB Principal», вызываемому устаревшими хранимыми процедурами sp_grantdbaccess, sp_revokedbaccess, sp_addPrincipal и sp_dropPrincipal).<br /><br /> Это событие возникает при создании или удалении роли базы данных с помощью хранимых процедур sp_addrole или sp_droprole. Это событие возникает при создании, изменении или удалении любых участников базы данных из любой базы данных. Эквивалентно [Класс событий Audit Add Role](../../event-classes/audit-add-role-event-class.md).|  
|DATABASE_PRINCIPAL_IMPERSONATION_GROUP|Это событие возникает при использовании в области базы данных операции олицетворения, например EXECUTE AS \<субъект> или SETPRINCIPAL. Это событие возникает при использовании олицетворения в любой базе данных. Эквивалентно [Audit Database Principal Impersonation Event Class](../../event-classes/audit-database-principal-impersonation-event-class.md).|  
|DATABASE_ROLE_MEMBER_CHANGE_GROUP|Это событие вызывается каждый раз, когда имя входа добавляется в роль базы данных или удаляется из нее. Этот класс событий вызывается хранимыми процедурами sp_addrolemember, sp_changegroup и sp_droprolemember. Это событие появляется при изменении члена любой роли базы данных в любой базе данных. Эквивалентно [Audit Add Member to DB Role, класс событий](../../event-classes/audit-add-member-to-db-role-event-class.md).|  
|DBCC_GROUP|Это событие появляется при вызове участником любой команды DBCC. Эквивалентно [Audit DBCC Event Class](../../event-classes/audit-dbcc-event-class.md).|  
|FAILED_DATABASE_AUTHENTICATION_GROUP|Указывает, что попытка участника войти в автономную базу данных завершилась ошибкой. События этого класса вызываются новыми соединениями или соединениями, которые многократно используются в пуле соединений. Эквивалентно [Audit Login Failed Event Class](../../event-classes/audit-login-failed-event-class.md).|  
|FAILED_LOGIN_GROUP|Указывает, что участник выполнил попытку входа в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которая завершилась неудачно. События этого класса вызываются новыми соединениями или соединениями, которые многократно используются в пуле соединений. Эквивалентно [Audit Login Failed Event Class](../../event-classes/audit-login-failed-event-class.md).|  
|FULLTEXT_GROUP|Указывает, что произошло полнотекстовое событие. Эквивалентно [Audit Fulltext Event Class](../../event-classes/audit-fulltext-event-class.md).|  
|LOGIN_CHANGE_PASSWORD_GROUP|Это событие появляется при изменении пароля входа с помощью инструкции ALTER LOGIN или хранимой процедуры sp_password. Эквивалентно [Audit Login Change Password Event Class](../../event-classes/audit-login-change-password-event-class.md).|  
|LOGOUT_GROUP|Указывает, что участник отключился от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. События этого класса вызываются новыми соединениями или соединениями, которые многократно используются в пуле соединений. Эквивалентно [Audit Logout Event Class](../../event-classes/audit-logout-event-class.md).|  
|SCHEMA_OBJECT_ACCESS_GROUP|Это событие возникает при применении разрешения на объект в схеме. Эквивалентно [Audit Schema Object Access Event Class](../../event-classes/audit-schema-object-access-event-class.md).|  
|SCHEMA_OBJECT_CHANGE_GROUP|Это событие вызывается в момент выполнения для схемы операции CREATE, ALTER или DROP. Эквивалентно [Audit Schema Object Management Event Class](../../event-classes/audit-schema-object-management-event-class.md).<br /><br /> Это событие вызывается для объектов схемы. Эквивалентно [Audit Object Derived Permission Event Class](../../event-classes/audit-object-derived-permission-event-class.md).<br /><br /> Это событие возникает при изменении любой схемы любой базы данных. Эквивалентно [Audit Statement Permission Event Class](../../event-classes/audit-statement-permission-event-class.md).|  
|SCHEMA_OBJECT_OWNERSHIP_CHANGE_GROUP|Это событие возникает при проверке разрешений на смену владельца объекта схемы (таблицы, процедуры, функции и т. д.). Возникает, когда объекту назначается владелец при помощи инструкции ALTER AUTHORIZATION. Это событие возникает при любом изменении владельца схемы в любой базе данных на сервере. Эквивалентно [Audit Schema Object Take Ownership Event Class](../../event-classes/audit-schema-object-take-ownership-event-class.md).|  
|SCHEMA_OBJECT_PERMISSION_CHANGE_GROUP|Это событие возникает при выполнении инструкции GRANT, REVOKE или DENY для объекта схемы. Эквивалентно [Audit Schema Object GDR Event Class](../../event-classes/audit-schema-object-gdr-event-class.md).|  
|SERVER_OBJECT_CHANGE_GROUP|Это событие возникает при выполнении операций CREATE, ALTER или DROP с объектами сервера. Эквивалентно [Audit Server Object Management Event Class](../../event-classes/audit-server-object-management-event-class.md).|  
|SERVER_OBJECT_OWNERSHIP_CHANGE_GROUP|Это событие возникает при изменении владельца объектов в области сервера. Эквивалентно [Audit Server Object Take Ownership Event Class](../../event-classes/audit-server-object-take-ownership-event-class.md).|  
|SERVER_OBJECT_PERMISSION_CHANGE_GROUP|Это событие возникает в случае, когда инструкции GRANT, REVOKE или DENY выдаются для разрешений на объекты сервера любым участником [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Эквивалентно [Audit Server Object GDR Event Class](../../event-classes/audit-server-object-gdr-event-class.md).|  
|SERVER_OPERATION_GROUP|Это событие возникает при использовании таких операций аудита безопасности, как изменение параметров, ресурсов, внешнего доступа или авторизации. Эквивалентно [Audit Server Operation Event Class](../../event-classes/audit-server-operation-event-class.md).|  
|SERVER_PERMISSION_CHANGE_GROUP|Это событие возникает в случае, когда инструкции GRANT, REVOKE или DENY выдаются для разрешений в области действия сервера, например для создания имени входа. Эквивалентно [Audit Server Scope GDR Event Class](../../event-classes/audit-server-scope-gdr-event-class.md).|  
|SERVER_PRINCIPAL_CHANGE_GROUP|Это событие возникает при создании, изменении и удалении участников на уровне сервера. Эквивалентно [Audit Server Principal Management Event Class](../../event-classes/audit-server-principal-management-event-class.md).<br /><br /> Это событие возникает при вызове участником хранимых процедур sp_defaultdb или sp_defaultlanguage или инструкций ALTER LOGIN. Эквивалентно [Audit Addlogin Event Class](../../event-classes/audit-addlogin-event-class.md).<br /><br /> Это событие вызывается хранимыми процедурами sp_addlogin и sp_droplogin. Также эквивалентно [Audit Login Change Property Event Class](../../event-classes/audit-login-change-property-event-class.md).<br /><br /> Это событие возникает sp_grantlogin или sp_revokelogin хранимых процедур. Эквивалентно [Audit Login GDR Event Class](../../event-classes/audit-login-gdr-event-class.md).|  
|SERVER_PRINCIPAL_IMPERSONATION_GROUP|Это событие возникает при использовании в области действия сервера олицетворения, например команды EXECUTE AS \<имя_для_входа>. Эквивалентно [Audit Server Principal Impersonation Event Class](../../event-classes/audit-server-principal-impersonation-event-class.md).|  
|SERVER_ROLE_MEMBER_CHANGE_GROUP|Это событие появляется при добавлении или удалении имени входа из предопределенной роли сервера. Это событие вызывается хранимыми процедурами sp_addsrvrolemember и sp_dropsrvrolemember. Эквивалентно [Класс событий Audit Add Login to Server Role](../../event-classes/audit-add-login-to-server-role-event-class.md).|  
|SERVER_STATE_CHANGE_GROUP|Это событие возникает при изменении состояния службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Эквивалентно [Audit Server Starts and Stops Event Class](../../event-classes/audit-server-starts-and-stops-event-class.md).|  
|SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP|Указывает, что участник успешно выполнил вход в автономную базу данных. Эквивалентно классу событий Audit Successful Database Authentication.|  
|SUCCESSFUL_LOGIN_GROUP|Указывает, что участник успешно выполнил вход на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. События этого класса вызываются новыми соединениями или соединениями, которые многократно используются в пуле соединений. Эквивалентно [Audit Login Event Class](../../event-classes/audit-login-event-class.md).|  
|TRACE_CHANGE_GROUP|Это событие вызывается для всех инструкций, выполняющих проверку на разрешение ALTER TRACE. Эквивалентно [Audit Server Alter Trace Event Class](../../event-classes/audit-server-alter-trace-event-class.md).|  
|USER_CHANGE_PASSWORD_GROUP|Это событие возникает при изменении пароля пользователя автономной базы данных с помощью инструкции ALTER USER.|  
|USER_DEFINED_AUDIT_GROUP|Эта группа наблюдает за событиями, вызываемыми с помощью процедуры [sp_audit_write (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-audit-write-transact-sql). Как правило, триггеры или хранимые процедуры включают вызовы процедуры `sp_audit_write` для включения аудита важных событий.|  
  
### <a name="considerations"></a>Замечания  
 Группы действий уровня сервера охватывают действия, происходящие на всем экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Например, если соответствующая группа будет возвращена в спецификацию аудита сервера, то будет производиться запись любой проверки доступа к объекту схемы в любой базе данных. В спецификации аудита базы данных производится запись доступа только к объектам схемы этой базе данных.  
  
 Действия уровня сервера не позволяют проводить подробную фильтрацию действий уровня базы данных. Для точной фильтрации действий необходим аудит уровня базы данных, например аудит действий SELECT в таблице Customers, производимых от лица имен входа в группе Employee. Не включайте объекты области сервера, такие как системные представления, в пользовательскую спецификацию аудита базы данных.  
  
## <a name="database-level-audit-action-groups"></a>Группы действий аудита уровня базы данных  
 Группы действий аудита уровня базы данных — это действия, похожие на классы событий аудита безопасности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения о классах событий см. в разделе [SQL Server Event Class Reference](../../event-classes/sql-server-event-class-reference.md).  
  
 В следующей таблице описываются группы действий аудита уровня базы данных и предоставляются эквивалентные классы событий SQL Server (где возможно).  
  
|Имя группы действий|Описание|  
|-----------------------|-----------------|  
|APPLICATION_ROLE_CHANGE_PASSWORD_GROUP|Это событие появляется при изменении пароля для роли приложения. Эквивалентно [Audit App Role Change Password Event Class](../../event-classes/audit-app-role-change-password-event-class.md).|  
|AUDIT_CHANGE_GROUP|Это событие возникает при создании, изменении или удалении любого аудита. Это событие возникает при создании, изменении или удалении спецификации любого аудита. Аудит любых изменений в аудите производится в этом аудите. Эквивалентно [Audit Change Audit Event Class](../../event-classes/audit-change-audit-event-class.md).|  
|BACKUP_RESTORE_GROUP|Это событие вызывается командой резервного копирования или восстановления. Эквивалент [класса событий Audit Backup и Restore](../../event-classes/audit-backup-and-restore-event-class.md).|  
|DATABASE_CHANGE_GROUP|Это событие вызывается при создании, изменении или удалении базы данных. Эквивалентно [Audit Database Management Event Class](../../event-classes/audit-database-management-event-class.md).|  
|DATABASE_LOGOUT_GROUP|Это событие возникает при выходе пользователя автономной базы данных из базы данных. Эквивалент [класса событий Audit Backup и Restore](../../event-classes/audit-backup-and-restore-event-class.md).|  
|DATABASE_OBJECT_ACCESS_GROUP|Это событие вызывается каждый раз, когда производится доступ к сертификатам, асимметричным ключам и другим объектам базы данных. Эквивалентно [Audit Database Object Access Event Class](../../event-classes/audit-database-object-access-event-class.md).|  
|DATABASE_OBJECT_CHANGE_GROUP|Это событие вызывается в тот момент, когда для объекта базы данных (например, для схемы) выполняется инструкция CREATE, ALTER или DROP. Эквивалентно [Audit Database Object Management Event Class](../../event-classes/audit-database-object-management-event-class.md).|  
|DATABASE_OBJECT_OWNERSHIP_CHANGE_GROUP|Это событие возникает при изменении владельца объектов в области базы данных. Эквивалентно [Audit Database Object Take Ownership Event Class](../../event-classes/audit-database-object-take-ownership-event-class.md).|  
|DATABASE_OBJECT_PERMISSION_CHANGE_GROUP|Это событие возникает в тот момент, когда для объекта базы данных (например, сборки или схемы) выполняется инструкция GRANT, REVOKE или DENY. Эквивалентно [Audit Database Object GDR Event Class](../../event-classes/audit-database-object-gdr-event-class.md).|  
|DATABASE_OPERATION_GROUP|Это событие вызывается при выполнении различных операций в базе данных, например при создании контрольной точки или уведомлении о запросе подписки. Эквивалентно [Audit Database Operation Event Class](../../event-classes/audit-database-operation-event-class.md).|  
|DATABASE_OWNERSHIP_CHANGE_GROUP|Это событие вызывается при смене владельца базы данных инструкцией ALTER AUTHORIZATION в момент проверки разрешений на эту операцию. Эквивалентно [Audit Change Database Owner Event Class](../../event-classes/audit-change-database-owner-event-class.md).|  
|DATABASE_PERMISSION_CHANGE_GROUP|Это событие возникает в случае, когда инструкции GRANT, REVOKE или DENY выдаются для разрешения на выполнение инструкции любым пользователем [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (применяется только к событиям базы данных, например предоставлению разрешений на базу данных). Эквивалентно [Audit Database Scope GDR Event Class](../../event-classes/audit-database-scope-gdr-event-class.md).|  
|DATABASE_PRINCIPAL_CHANGE_GROUP|Это событие создается при создании, изменении или удалении из базы данных участников, таких как пользователи. Эквивалентно [Audit Database Principal Management Event Class](../../event-classes/audit-database-principal-management-event-class.md). Также эквивалентно [классу событий Audit Add DB User](../../event-classes/audit-add-db-user-event-class.md), вызываемому устаревшими хранимыми процедурами sp_grantdbaccess, sp_revokedbaccess, sp_adduser и sp_dropuser.<br /><br /> Это событие возникает при создании или удалении роли базы данных с помощью устаревших хранимых процедур sp_addrole и sp_droprole. Эквивалентно [Класс событий Audit Add Role](../../event-classes/audit-add-role-event-class.md).|  
|DATABASE_PRINCIPAL_IMPERSONATION_GROUP|Это событие возникает, когда выполняется олицетворение в области базы данных, например через EXECUTE AS \<пользователя > или SETUSER. Эквивалентно [Audit Database Principal Impersonation Event Class](../../event-classes/audit-database-principal-impersonation-event-class.md).|  
|DATABASE_ROLE_MEMBER_CHANGE_GROUP|Это событие вызывается каждый раз, когда имя входа добавляется в роль базы данных или удаляется из нее. Этот класс событий вызывается хранимыми процедурами sp_addrolemember, sp_changegroup и sp_droprolemember. Он эквивалентен [классу событий Audit Add Member to DB Role](../../event-classes/audit-add-member-to-db-role-event-class.md).|  
|DBCC_GROUP|Это событие появляется при вызове участником любой команды DBCC. Эквивалентно [Audit DBCC Event Class](../../event-classes/audit-dbcc-event-class.md).|  
|FAILED_DATABASE_AUTHENTICATION_GROUP|Указывает, что попытка участника войти в автономную базу данных завершилась ошибкой. События этого класса вызываются новыми соединениями или соединениями, которые многократно используются в пуле соединений. Вызывается событие.|  
|SCHEMA_OBJECT_ACCESS_GROUP|Это событие возникает при применении разрешения на объект в схеме. Эквивалентно [Audit Schema Object Access Event Class](../../event-classes/audit-schema-object-access-event-class.md).|  
|SCHEMA_OBJECT_CHANGE_GROUP|Это событие вызывается в момент выполнения для схемы операции CREATE, ALTER или DROP. Эквивалентно [Audit Schema Object Management Event Class](../../event-classes/audit-schema-object-management-event-class.md).<br /><br /> Это событие вызывается для объектов схемы. Эквивалентно [Audit Object Derived Permission Event Class](../../event-classes/audit-object-derived-permission-event-class.md). Также эквивалентно [Audit Statement Permission Event Class](../../event-classes/audit-statement-permission-event-class.md).|  
|SCHEMA_OBJECT_OWNERSHIP_CHANGE_GROUP|Это событие возникает при проверке разрешений на смену владельца объекта схемы (таблицы, процедуры, функции и т. д.). Возникает, когда объекту назначается владелец при помощи инструкции ALTER AUTHORIZATION. Эквивалентно [Audit Schema Object Take Ownership Event Class](../../event-classes/audit-schema-object-take-ownership-event-class.md).|  
|SCHEMA_OBJECT_PERMISSION_CHANGE_GROUP|Это событие возникает при вызове инструкции GRANT, REVOKE или DENY для объекта схемы. Эквивалентно [Audit Schema Object GDR Event Class](../../event-classes/audit-schema-object-gdr-event-class.md).|  
|SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP|Указывает, что участник успешно выполнил вход в автономную базу данных. Эквивалентно классу событий Audit Successful Database Authentication.|  
|USER_CHANGE_PASSWORD_GROUP|Это событие возникает при изменении пароля пользователя автономной базы данных с помощью инструкции ALTER USER.|  
|USER_DEFINED_AUDIT_GROUP|Эта группа наблюдает за событиями, вызываемыми с помощью процедуры [sp_audit_write (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-audit-write-transact-sql).|  
  
## <a name="database-level-audit-actions"></a>Действия аудита уровня базы данных  
 Действия аудита уровня базы данных поддерживают аудит напрямую в базе данных, схеме или в объектах схемы, например в таблицах, представлениях, хранимых процедурах, функциях, расширенных хранимых процедурах, очередях, синонимах. Не подлежат аудиту типы, коллекции схем XML, база данных и схема. Аудит объектов схемы можно настроить для схемы и базы данных. Это означает, что будет выполнен аудит событий всех объектов схемы, содержащихся в указанной схеме или базе данных. В следующей таблице описываются действия аудита уровня базы данных.  
  
|Действие|Описание|  
|------------|-----------------|  
|SELECT|Это событие возникает при вызове инструкции SELECT.|  
|UPDATE|Это событие возникает при вызове инструкции UPDATE.|  
|INSERT|Это событие возникает при вызове инструкции INSERT.|  
|DELETE|Это событие возникает при вызове инструкции DELETE.|  
|EXECUTE|Это событие возникает при вызове инструкции EXECUTE.|  
|RECEIVE|Это событие возникает при вызове инструкции RECEIVE.|  
|REFERENCES|Это событие возникает при проверке разрешения REFERENCES.|  
  
### <a name="considerations"></a>Замечания  
*  Действия аудита уровня базы данных не применяются к столбцам.  
  
*  Если обработчик запросов параметризует запрос, параметр может отображаться в журнале событий аудита вместо значений столбца запроса. 
 
*  Инструкции RPC не регистрируются.   
  
## <a name="audit-level-audit-action-groups"></a>Группы действий аудита уровня аудита  
 Также можно производить аудит действий, происходящих во время аудита. Это можно осуществлять как в области сервера, так и в области базы данных. В области базы данных это справедливо только для спецификаций аудита базы данных. В следующей таблице описываются группы действий аудита уровня аудита.  
  
|Имя группы действий|Описание|  
|-----------------------|-----------------|  
|AUDIT_ CHANGE_GROUP|Это событие возникает при вызове одной из следующих команд:<br /><br /> -СОЗДАНИЕ АУДИТА СЕРВЕРА<br />-ИНСТРУКЦИИ ALTER SERVER AUDIT<br />-DROP SERVER AUDIT<br />-СОЗДАТЬ СПЕЦИФИКАЦИЮ АУДИТА СЕРВЕРА<br />-ALTER SERVER AUDIT SPECIFICATION<br />-УДАЛИТЬ СПЕЦИФИКАЦИЮ АУДИТА СЕРВЕРА<br />-СОЗДАТЬ СПЕЦИФИКАЦИЮ АУДИТА БАЗЫ ДАННЫХ<br />-СПЕЦИФИКАЦИИ АУДИТА БАЗЫ ДАННЫХ ALTER<br />-УДАЛИТЬ СПЕЦИФИКАЦИЮ АУДИТА БАЗЫ ДАННЫХ|  
  
## <a name="related-content"></a>См. также  
 [Создание аудита сервера и спецификации аудита сервера](create-a-server-audit-and-server-audit-specification.md)  
  
 [Создание спецификация аудита для сервера и базы данных](create-a-server-audit-and-database-audit-specification.md)  
  
 [CREATE SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/create-server-audit-transact-sql)  
  
 [ALTER SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)  
  
 [DROP SERVER AUDIT (Transact-SQL)](/sql/t-sql/statements/drop-server-audit-transact-sql)  
  
 [CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/create-server-audit-specification-transact-sql)  
  
 [ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/alter-server-audit-transact-sql)  
  
 [DROP SERVER AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)  
  
 [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/create-database-audit-specification-transact-sql)  
  
 [ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)  
  
 [DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)  
  
 [ALTER AUTHORIZATION (Transact-SQL)](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
 [sys.fn_get_audit_file (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)  
  
 [sys.server_audits (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)  
  
 [sys.server_file_audits (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)  
  
 [sys.server_audit_specifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)  
  
 [sys.server_audit_specification_details (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)  
  
 [sys.database_audit_specifications (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)  
  
 [sys.database_audit_specification_details (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)  
  
 [sys.dm_server_audit_status (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)  
  
 [sys.dm_audit_actions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)  
  
 [sys.dm_audit_class_type_map (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)  
  
  
