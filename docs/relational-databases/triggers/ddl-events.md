---
description: DDL-события
title: DDL-события | Документация Майкрософт
ms.custom: ''
ms.date: 11/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL events
- DDL triggers, events
- events [SQL Server], DDL
ms.assetid: 62ef24b4-3553-4aed-b62a-670980bae501
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 25cdef293ced7b58ea41f71f78a1046c6b5dd0ba
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96128636"
---
# <a name="ddl-events"></a>DDL-события
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  В следующих таблицах перечислены DDL-события, которые могут быть использованы для срабатывания триггера DDL или уведомления о событиях. Обратите внимание, что каждое событие соответствует инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] или хранимой процедуре, причем синтаксис инструкции при этом включает в себя символ подчеркивания (_) между ключевыми словами.  
  
> [!IMPORTANT]  
>  Системные хранимые процедуры, выполняющие операции, подобные операциям DDL, также запускают триггеры DDL и уведомления о событиях. Проверьте имеющиеся триггеры DDL и уведомления о событии, чтобы определить их ответы на выполняемые системные хранимые процедуры. Например, как инструкция CREATE TYPE, так и хранимая процедура **sp_addtype** приведут к инициации триггера DDL или уведомления о событии, создаваемом при наступлении события CREATE_TYPE.  
  
## <a name="ddl-statements-that-have-server-or-database-scope"></a>Инструкции DLL области сервера или базы данных  
 Можно создать триггеры DDL или уведомления о событиях, запускаемые в ответ на следующие события, возникающие в базе данных, в которой создан триггер или уведомление о событии, или в экземпляре сервера.  
  
:::row:::
    :::column:::
        CREATE_APPLICATION_ROLE (Применяется в инструкции CREATE APPLICATION ROLE и процедуре **sp_addapprole**. Если создается новая схема, это событие также запускает событие CREATE_SCHEMA.)
    :::column-end:::
    :::column:::
        ALTER_APPLICATION_ROLE (Применяется в инструкции ALTER_APPLICATION_ROLE и процедуре **sp_approlepassword**.)
    :::column-end:::
    :::column:::
        DROP_APPLICATION_ROLE (Применяется в инструкции DROP_APPLICATION_ROLE и процедуре **sp_dropapprole**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ASSEMBLY
    :::column-end:::
    :::column:::
        ALTER_ASSEMBLY
    :::column-end:::
    :::column:::
        DROP_ASSEMBLY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ASYMMETRIC_KEY
    :::column-end:::
    :::column:::
        ALTER_ASYMMETRIC_KEY
    :::column-end:::
    :::column:::
        DROP_ASYMMETRIC_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ALTER_AUTHORIZATION
    :::column-end:::
    :::column:::
        ALTER_AUTHORIZATION_DATABASE (Применяется в инструкции ALTER AUTHORIZATION, если указано предложение ON DATABASE, и процедуре **sp_changedbowner**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CERTIFICATE
    :::column-end:::
    :::column:::
        ALTER_CERTIFICATE
    :::column-end:::
    :::column:::
        DROP_CERTIFICATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CONTRACT
    :::column-end:::
    :::column:::
        DROP_CONTRACT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CREDENTIAL
    :::column-end:::
    :::column:::
        ALTER_CREDENTIAL
    :::column-end:::
    :::column:::
        DROP_CREDENTIAL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        GRANT_DATABASE
    :::column-end:::
    :::column:::
        DENY_DATABASE
    :::column-end:::
    :::column:::
        REVOKE_DATABASE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
    :::column:::
        ALTER_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
    :::column:::
        DENY_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE_ENCRYPTION_KEY
    :::column-end:::
    :::column:::
        ALTER_DATABASE_ENCRYPTION_KEY
    :::column-end:::
    :::column:::
        DROP_DATABASE_ENCRYPTION_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DEFAULT
    :::column-end:::
    :::column:::
        DROP_DEFAULT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        BIND_DEFAULT (Применяется в процедуре **sp_bindefault**.)
    :::column-end:::
    :::column:::
        UNBIND_DEFAULT (Применяется в процедуре **sp_unbindefault**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EVENT_NOTIFICATION
    :::column-end:::
    :::column:::
        DROP_EVENT_NOTIFICATION
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EXTENDED_PROPERTY (Применяется в процедуре **sp_addextendedproperty**.)
    :::column-end:::
    :::column:::
        ALTER_EXTENDED_PROPERTY (Применяется в процедуре **sp_updateextendedproperty**.)
    :::column-end:::
    :::column:::
        DROP_EXTENDED_PROPERTY (Применяется в процедуре **sp_dropextendedproperty**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_CATALOG (Применяется в инструкции CREATE FULLTEXT CATALOG и процедуре **sp_fulltextcatalog** , если указан аргумент *create* .)
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_CATALOG (Применяется в инструкции ALTER FULLTEXT CATALOG и процедуре **sp_fulltextcatalog** , если указаны аргументы *start_incremental*, *start_full*, *Stop* или *Rebuild* , и процедуре **sp_fulltext_database** , если указан аргумент *enable* .)
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_CATALOG (Применяется в инструкции DROP FULLTEXT CATALOG и процедуре **sp_fulltextcatalog** , если указан аргумент *drop* .)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_INDEX (Применяется в инструкции CREATE FULLTEXT INDEX и процедуре **sp_fulltexttable** , если указан аргумент *create* .)
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_INDEX (Применяется в инструкции ALTER FULLTEXT INDEX, процедуре **sp_fulltextcatalog** , если указаны аргументы *start_full*, *start_incremental* или *stop* , процедуре **sp_fulltext_column** и процедуре **sp_fulltext_table** , если определено любое действие, отличное от *create* или *drop* .)
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_INDEX (Применяется в инструкции DROP FULLTEXT INDEX и процедуре **sp_fulltexttable** , если указан аргумент *drop* .)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_STOPLIST
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_STOPLIST
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_STOPLIST
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FUNCTION
    :::column-end:::
    :::column:::
        ALTER_FUNCTION
    :::column-end:::
    :::column:::
        DROP_FUNCTION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX (Применяется в инструкции ALTER INDEX и процедуре **sp_indexoption**.)
    :::column-end:::
    :::column:::
        DROP_INDEX
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MASTER_KEY
    :::column-end:::
    :::column:::
        ALTER_MASTER_KEY
    :::column-end:::
    :::column:::
        DROP_MASTER_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MESSAGE_TYPE
    :::column-end:::
    :::column:::
        ALTER_MESSAGE_TYPE
    :::column-end:::
    :::column:::
        DROP_MESSAGE_TYPE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PARTITION_FUNCTION
    :::column-end:::
    :::column:::
        ALTER_PARTITION_FUNCTION
    :::column-end:::
    :::column:::
        DROP_PARTITION_FUNCTION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PARTITION_SCHEME
    :::column-end:::
    :::column:::
        ALTER_PARTITION_SCHEME
    :::column-end:::
    :::column:::
        DROP_PARTITION_SCHEME
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PLAN_GUIDE (Применяется в процедуре **sp_create_plan_guide**.)
    :::column-end:::
    :::column:::
        ALTER_PLAN_GUIDE (Применяется в процедуре **sp_control_plan_guide** , если указаны ключевые слова ENABLE, ENABLE ALL, DISABLE или DISABLE ALL.)
    :::column-end:::
    :::column:::
        DROP_PLAN_GUIDE (Применяется в процедуре **sp_control_plan_guide** , если указаны ключевые слова DROP или DROP ALL.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PROCEDURE
    :::column-end:::
    :::column:::
        ALTER_PROCEDURE (Применяется в инструкции ALTER PROCEDURE и процедуре **sp_procoption**.)
    :::column-end:::
    :::column:::
        DROP_PROCEDURE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_QUEUE
    :::column-end:::
    :::column:::
        ALTER_QUEUE
    :::column-end:::
    :::column:::
        DROP_QUEUE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_REMOTE_SERVICE_BINDING
    :::column-end:::
    :::column:::
        ALTER_REMOTE_SERVICE_BINDING
    :::column-end:::
    :::column:::
        DROP_REMOTE_SERVICE_BINDING
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SPATIAL_INDEX
    :::column-end:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        RENAME (Применяется в процедуре **sp_rename**.)
    :::column-end:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ROLE (Применяется в инструкции CREATE ROLE, процедурах **sp_addrole** и **sp_addgroup**.)
    :::column-end:::
    :::column:::
        ALTER_ROLE
    :::column-end:::
    :::column:::
        DROP_ROLE (Применяется в инструкции DROP ROLE, процедурах **sp_droprole** и **sp_dropgroup**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_ROLE_MEMBER
    :::column-end:::
    :::column:::
        DROP_ROLE_MEMBER
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ROUTE
    :::column-end:::
    :::column:::
        ALTER_ROUTE
    :::column-end:::
    :::column:::
        DROP_ROUTE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_RULE
    :::column-end:::
    :::column:::
        DROP_RULE
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        BIND_RULE (Применяется в процедуре **sp_bindrule**.)
    :::column-end:::
    :::column:::
        UNBIND_RULE (Применяется в процедуре **sp_unbindrule**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SCHEMA (Применяется в инструкции CREATE SCHEMA, процедурах **sp_addrole**, **sp_adduser**, **sp_addgroup** и **sp_grantdbaccess**.)
    :::column-end:::
    :::column:::
        ALTER_SCHEMA (Применяется в инструкции ALTER SCHEMA и процедуре **sp_changeobjectowner**.)
    :::column-end:::
    :::column:::
        DROP_SCHEMA
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SEARCH_PROPERTY_LIST
    :::column-end:::
    :::column:::
        ALTER_SEARCH_PROPERTY_LIST
    :::column-end:::
    :::column:::
        DROP_SEARCH_PROPERTY_LIST
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_ROLE
    :::column-end:::
    :::column:::
        ALTER_SERVER_ROLE
    :::column-end:::
    :::column:::
        DROP_SERVER_ROLE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVICE
    :::column-end:::
    :::column:::
        ALTER_SERVICE
    :::column-end:::
    :::column:::
        DROP_SERVICE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ALTER_SERVICE_MASTER_KEY
    :::column-end:::
    :::column:::
        BACKUP_SERVICE_MASTER_KEY
    :::column-end:::
    :::column:::
        RESTORE_SERVICE_MASTER_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SIGNATURE (для операций с подписями при работе с объектами, не содержащимися в области схемы, а также с базами данных, сборками и триггерами)
    :::column-end:::
    :::column:::
        DROP_SIGNATURE
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SIGNATURE_SCHEMA_OBJECT (для объектов с областью схемы, хранимых процедур, функций)
    :::column-end:::
    :::column:::
        DROP_SIGNATURE_SCHEMA_OBJECT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SPATIAL_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX может использоваться для пространственных индексов.
    :::column-end:::
    :::column:::
        DROP_INDEX может использоваться для пространственных индексов.
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_STATISTICS
    :::column-end:::
    :::column:::
        DROP_STATISTICS
    :::column-end:::
    :::column:::
        UPDATE_STATISTICS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SYMMETRIC_KEY
    :::column-end:::
    :::column:::
        ALTER_SYMMETRIC_KEY
    :::column-end:::
    :::column:::
        DROP_SYMMETRIC_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SYNONYM
    :::column-end:::
    :::column:::
        DROP_SYNONYM
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TABLE
    :::column-end:::
    :::column:::
        ALTER_TABLE (Применяется в инструкции ALTER TABLE и процедуре **sp_tableoption**.)
    :::column-end:::
    :::column:::
        DROP_TABLE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TRIGGER
    :::column-end:::
    :::column:::
        ALTER_TRIGGER (Применяется в инструкции ALTER TRIGGER и процедуре **sp_settriggerorder**.)
    :::column-end:::
    :::column:::
        DROP_TRIGGER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TYPE (Применяется в инструкции CREATE TYPE и процедуре **sp_addtype**.)
    :::column-end:::
    :::column:::
        DROP_TYPE (Применяется в инструкции DROP TYPE и процедуре **sp_droptype**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_USER (Применяется в инструкции CREATE USER, процедурах **sp_adduser** и **sp_grantdbaccess**.)
    :::column-end:::
    :::column:::
        ALTER_USER (Применяется в инструкции ALTER USER и процедуре **sp_change_users_login**.)
    :::column-end:::
    :::column:::
        DROP_USER (Применяется в инструкции DROP USER, процедурах **sp_dropuser** и **sp_revokedbaccess**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_VIEW
    :::column-end:::
    :::column:::
        ALTER_VIEW
    :::column-end:::
    :::column:::
        DROP_VIEW
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_XML_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX может использоваться для XML-индексов.
    :::column-end:::
    :::column:::
        DROP_INDEX может использоваться для XML-индексов.
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_XML_SCHEMA_COLLECTION
    :::column-end:::
    :::column:::
        ALTER_XML_SCHEMA_COLLECTION
    :::column-end:::
    :::column:::
        DROP_XML_SCHEMA_COLLECTION
    :::column-end:::
:::row-end:::
 
## <a name="ddl-statements-that-have-server-scope"></a>Инструкции DDL области сервера  
 Триггеры DDL или уведомления о событиях могут быть созданы, чтобы срабатывать в ответ на следующие события, происходящие в экземпляре сервера.  
  
:::row:::
    :::column:::
        ALTER_AUTHORIZATION_SERVER
    :::column-end:::
    :::column:::
        ALTER_SERVER_CONFIGURATION
    :::column-end:::
    :::column:::
        ALTER_INSTANCE (Применяется в процедурах **sp_configure** и **sp_addserver** , если указан локальный экземпляр сервера.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_AVAILABILITY_GROUP
    :::column-end:::
    :::column:::
        ALTER_AVAILABILITY_GROUP
    :::column-end:::
    :::column:::
        DROP_AVAILABILITY_GROUP
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CREDENTIAL
    :::column-end:::
    :::column:::
        ALTER_CREDENTIAL
    :::column-end:::
    :::column:::
        DROP_CREDENTIAL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
    :::column:::
        ALTER_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
    :::column:::
        DROP_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE
    :::column-end:::
    :::column:::
        ALTER_DATABASE (Применяется в инструкции ALTER DATABASE и процедуре **sp_fulltext_database**.)
    :::column-end:::
    :::column:::
        DROP_DATABASE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ENDPOINT
    :::column-end:::
    :::column:::
        ALTER_ENDPOINT
    :::column-end:::
    :::column:::
        DROP_ENDPOINT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EVENT_SESSION
    :::column-end:::
    :::column:::
        ALTER_EVENT_SESSION
    :::column-end:::
    :::column:::
        DROP_EVENT_SESSION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EXTENDED_PROCEDURE (Применяется в процедуре **sp_addextendedproc**.)
    :::column-end:::
    :::column:::
        DROP_EXTENDED_PROCEDURE (Применяется в процедуре **sp_dropextendedproc**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LINKED_SERVER (Применяется в процедуре **sp_addlinkedserver**.)
    :::column-end:::
    :::column:::
        ALTER_LINKED_SERVER (Применяется в процедуре **sp_serveroption**.)
    :::column-end:::
    :::column:::
        DROP_LINKED_SERVER (Применяется в процедуре **sp_dropserver** , если определен связанный сервер.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LINKED_SERVER_LOGIN (Применяется в процедуре **sp_addlinkedsrvlogin**.)
    :::column-end:::
    :::column:::
        DROP_LINKED_SERVER_LOGIN (Применяется в процедуре **sp_droplinkedsrvlogin**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LOGIN (Применяется в инструкции CREATE LOGIN, процедурах **sp_addlogin**, **sp_grantlogin**, **xp_grantlogin** и **sp_denylogin** при использовании несуществующего имени входа, который должен быть неявно создан.)
    :::column-end:::
    :::column:::
        ALTER_LOGIN (Применяется в инструкции ALTER LOGIN, процедурах **sp_defaultdb**, **sp_defaultlanguage**, **sp_password** и **sp_change_users_login** , если указан параметр *Auto_Fix* .)
    :::column-end:::
    :::column:::
        DROP_LOGIN (Применяется в инструкции DROP LOGIN, процедурах **sp_droplogin**, **sp_revokelogin** и **xp_revokelogin**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MESSAGE (Применяется в процедуре **sp_addmessage**.)
    :::column-end:::
    :::column:::
        ALTER_MESSAGE (Применяется в процедуре **sp_altermessage**.)
    :::column-end:::
    :::column:::
        DROP_MESSAGE (Применяется в процедуре **sp_dropmessage**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_REMOTE_SERVER (Применяется в процедуре **sp_addserver**.)
    :::column-end:::
    :::column:::
        ALTER_REMOTE_SERVER (Применяется в процедуре **sp_setnetname**.)
    :::column-end:::
    :::column:::
        DROP_REMOTE_SERVER (Применяется в процедуре **sp_dropserver** , если указан удаленный сервер.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_RESOURCE_POOL
    :::column-end:::
    :::column:::
        ALTER_RESOURCE_POOL
    :::column-end:::
    :::column:::
        DROP_RESOURCE_POOL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        GRANT_SERVER
    :::column-end:::
    :::column:::
        DENY_SERVER
    :::column-end:::
    :::column:::
        REVOKE_SERVER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SERVER_ROLE_MEMBER
    :::column-end:::
    :::column:::
        DROP_SERVER_ROLE_MEMBER
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_AUDIT
    :::column-end:::
    :::column:::
        ALTER_SERVER_AUDIT
    :::column-end:::
    :::column:::
        DROP_SERVER_AUDIT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
    :::column:::
        ALTER_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
    :::column:::
        DROP_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_WORKLOAD_GROUP
    :::column-end:::
    :::column:::
        ALTER_WORKLOAD_GROUP
    :::column-end:::
    :::column:::
        DROP_WORKLOAD_GROUP
    :::column-end:::
:::row-end:::
 
## <a name="see-also"></a>См. также  
 [Триггеры DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [Уведомления о событиях](../../relational-databases/service-broker/event-notifications.md)   
 [Группы DDL-событий](../../relational-databases/triggers/ddl-event-groups.md)  
  
  
