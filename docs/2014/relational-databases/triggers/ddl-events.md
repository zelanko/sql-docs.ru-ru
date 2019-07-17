---
title: DDL-события | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: c9c90dbb072ace600258edfb4ff13f99ecadf188
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68196518"
---
# <a name="ddl-events"></a>DDL-события
  В следующих таблицах перечислены DDL-события, которые могут быть использованы для срабатывания триггера DDL или уведомления о событиях. Обратите внимание, что каждое событие соответствует инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] или хранимой процедуре, причем синтаксис инструкции при этом включает в себя символ подчеркивания (_) между ключевыми словами.  
  
> [!IMPORTANT]  
>  Системные хранимые процедуры, выполняющие операции, подобные операциям DDL, также запускают триггеры DDL и уведомления о событиях. Проверьте имеющиеся триггеры DDL и уведомления о событии, чтобы определить их ответы на выполняемые системные хранимые процедуры. Например, как инструкция CREATE TYPE, так и хранимая процедура **sp_addtype** приведут к инициации триггера DDL или уведомления о событии, создаваемом при наступлении события CREATE_TYPE.  
  
## <a name="ddl-statements-that-have-server-or-database-scope"></a>Инструкции DLL области сервера или базы данных  
 Можно создать триггеры DDL или уведомления о событиях, запускаемые в ответ на следующие события, возникающие в базе данных, в которой создан триггер или уведомление о событии, или в экземпляре сервера.  
  
||||  
|-|-|-|  
|CREATE_APPLICATION_ROLE (Применяется в инструкции CREATE APPLICATION ROLE и процедуре **sp_addapprole**. Если создается новая схема, это событие также запускает событие CREATE_SCHEMA.)|ALTER_APPLICATION_ROLE (Применяется в инструкции ALTER_APPLICATION_ROLE и процедуре **sp_approlepassword**.)|DROP_APPLICATION_ROLE (Применяется в инструкции DROP_APPLICATION_ROLE и процедуре **sp_dropapprole**.)|  
|CREATE_ASSEMBLY|ALTER_ASSEMBLY|DROP_ASSEMBLY|  
|CREATE_ASYMMETRIC_KEY|ALTER_ASYMMETRIC_KEY|DROP_ASYMMETRIC_KEY|  
|ALTER_AUTHORIZATION|ALTER_AUTHORIZATION_DATABASE (Применяется в инструкции ALTER AUTHORIZATION, если указано предложение ON DATABASE, и процедуре **sp_changedbowner**.)||  
|CREATE_BROKER_PRIORITY|CREATE_BROKER_PRIORITY|CREATE_BROKER_PRIORITY|  
|CREATE_CERTIFICATE|ALTER_CERTIFICATE|DROP_CERTIFICATE|  
|CREATE_CONTRACT|DROP_CONTRACT||  
|CREATE_CREDENTIAL|ALTER_CREDENTIAL|DROP_CREDENTIAL|  
|GRANT_DATABASE|DENY_DATABASE|REVOKE_DATABASE|  
|CREATE_DATABASE_AUDIT_SPEFICIATION|ALTER_DATABASE_AUDIT_SPEFICIATION|DENY_DATABASE_AUDIT_SPEFICIATION|  
|CREATE_DATABASE_ENCRYPTION_KEY|ALTER_DATABASE_ENCRYPTION_KEY|DROP_DATABASE_ENCRYPTION_KEY|  
|CREATE_DEFAULT|DROP_DEFAULT||  
|BIND_DEFAULT (Применяется в процедуре **sp_bindefault**.)|UNBIND_DEFAULT (Применяется в процедуре **sp_unbindefault**.)||  
|CREATE_EVENT_NOTIFICATION|DROP_EVENT_NOTIFICATION||  
|CREATE_EXTENDED_PROPERTY (Применяется в процедуре **sp_addextendedproperty**.)|ALTER_EXTENDED_PROPERTY (Применяется в процедуре **sp_updateextendedproperty**.)|DROP_EXTENDED_PROPERTY (Применяется в процедуре **sp_dropextendedproperty**.)|  
|CREATE_FULLTEXT_CATALOG (Применяется в инструкции CREATE FULLTEXT CATALOG и процедуре **sp_fulltextcatalog** , если указан аргумент *create* .)|ALTER_FULLTEXT_CATALOG (Применяется в инструкции ALTER FULLTEXT CATALOG и процедуре **sp_fulltextcatalog** , если указаны аргументы *start_incremental*, *start_full*, *Stop*или *Rebuild* , и процедуре **sp_fulltext_database** , если указан аргумент *enable* .)|DROP_FULLTEXT_CATALOG (Применяется в инструкции DROP FULLTEXT CATALOG и процедуре **sp_fulltextcatalog** , если указан аргумент *drop* .)|  
|CREATE_FULLTEXT_INDEX (Применяется в инструкции CREATE FULLTEXT INDEX и процедуре **sp_fulltexttable** , если указан аргумент *create* .)|ALTER_FULLTEXT_INDEX (Применяется в инструкции ALTER FULLTEXT INDEX, процедуре **sp_fulltextcatalog** , если указаны аргументы *start_full*, *start_incremental*или *stop* , процедуре **sp_fulltext_column**и процедуре **sp_fulltext_table** , если определено любое действие, отличное от *create* или *drop* .)|DROP_FULLTEXT_INDEX (Применяется в инструкции DROP FULLTEXT INDEX и процедуре **sp_fulltexttable** , если указан аргумент *drop* .)|  
|CREATE_FULLTEXT_STOPLIST|ALTER_FULLTEXT_STOPLIST|DROP_FULLTEXT_STOPLIST|  
|CREATE_FUNCTION|ALTER_FUNCTION|DROP_FUNCTION|  
|CREATE_INDEX|ALTER_INDEX (Применяется в инструкции ALTER INDEX и процедуре **sp_indexoption**.)|DROP_INDEX|  
|CREATE_MASTER_KEY|ALTER_MASTER_KEY|DROP_MASTER_KEY|  
|CREATE_MESSAGE_TYPE|ALTER_MESSAGE_TYPE|DROP_MESSAGE_TYPE|  
|CREATE_PARTITION_FUNCTION|ALTER_PARTITION_FUNCTION|DROP_PARTITION_FUNCTION|  
|CREATE_PARTITION_SCHEME|ALTER_PARTITION_SCHEME|DROP_PARTITION_SCHEME|  
|CREATE_PLAN_GUIDE (Применяется в процедуре **sp_create_plan_guide**.)|ALTER_PLAN_GUIDE (Применяется в процедуре **sp_control_plan_guide** , если указаны ключевые слова ENABLE, ENABLE ALL, DISABLE или DISABLE ALL.)|DROP_PLAN_GUIDE (Применяется в процедуре **sp_control_plan_guide** , если указаны ключевые слова DROP или DROP ALL.)|  
|CREATE_PROCEDURE|ALTER_PROCEDURE (Применяется в инструкции ALTER PROCEDURE и процедуре **sp_procoption**.)|DROP_PROCEDURE|  
|CREATE_QUEUE|ALTER_QUEUE|DROP_QUEUE|  
|CREATE_REMOTE_SERVICE_BINDING|ALTER_REMOTE_SERVICE_BINDING|DROP_REMOTE_SERVICE_BINDING|  
|CREATE_SPATIAL_INDEX|||  
|RENAME (Применяется в процедуре **sp_rename**.)|||  
|CREATE_ROLE (Применяется в инструкции CREATE ROLE, процедурах **sp_addrole**и **sp_addgroup**.)|ALTER_ROLE|DROP_ROLE (Применяется в инструкции DROP ROLE, процедурах **sp_droprole**и **sp_dropgroup**.)|  
|ADD_ROLE_MEMBER|DROP_ROLE_MEMBER||  
|CREATE_ROUTE|ALTER_ROUTE|DROP_ROUTE|  
|CREATE_RULE|DROP_RULE||  
|BIND_RULE (Применяется в процедуре **sp_bindrule**.)|UNBIND_RULE (Применяется в процедуре **sp_unbindrule**.)||  
|CREATE_SCHEMA (Применяется в инструкции CREATE SCHEMA, процедурах **sp_addrole**, **sp_adduser**, **sp_addgroup**и **sp_grantdbaccess**.)|ALTER_SCHEMA (Применяется в инструкции ALTER SCHEMA и процедуре **sp_changeobjectowner**.)|DROP_SCHEMA|  
|CREATE_SEARCH_PROPERTY_LIST|ALTER_SEARCH_PROPERTY_LIST|DROP_SEARCH_PROPERTY_LIST|  
|CREATE_SEQUENCE_EVENTS|CREATE_SEQUENCE_EVENTS|CREATE_SEQUENCE_EVENTS|  
|CREATE_SERVER_ROLE|ALTER_SERVER_ROLE|DROP_SERVER_ROLE|  
|CREATE_SERVICE|ALTER_SERVICE|DROP_SERVICE|  
|ALTER_SERVICE_MASTER_KEY|BACKUP_SERVICE_MASTER_KEY|RESTORE_SERVICE_MASTER_KEY|  
|ADD_SIGNATURE (для операций с подписями при работе с объектами, не содержащимися в области схемы, а также с базами данных, сборками и триггерами)|DROP_SIGNATURE||  
|ADD_SIGNATURE_SCHEMA_OBJECT (для объектов с областью схемы, хранимых процедур, функций)|DROP_SIGNATURE_SCHEMA_OBJECT||  
|CREATE_SPATIAL_INDEX|ALTER_INDEX может использоваться для пространственных индексов.|DROP_INDEX может использоваться для пространственных индексов.|  
|CREATE_STATISTICS|DROP_STATISTICS|UPDATE_STATISTICS|  
|CREATE_SYMMETRIC_KEY|ALTER_SYMMETRIC_KEY|DROP_SYMMETRIC_KEY|  
|CREATE_SYNONYM|DROP_SYNONYM||  
|CREATE_TABLE|ALTER_TABLE (Применяется в инструкции ALTER TABLE и процедуре **sp_tableoption**.)|DROP_TABLE|  
|CREATE_TRIGGER|ALTER_TRIGGER (Применяется в инструкции ALTER TRIGGER и процедуре **sp_settriggerorder**.)|DROP_TRIGGER|  
|CREATE_TYPE (Применяется в инструкции CREATE TYPE и процедуре **sp_addtype**.)|DROP_TYPE (Применяется в инструкции DROP TYPE и процедуре **sp_droptype**.)||  
|CREATE_USER (Применяется в инструкции CREATE USER, процедурах **sp_adduser**и **sp_grantdbaccess**.)|ALTER_USER (Применяется в инструкции ALTER USER и процедуре **sp_change_users_login**.)|DROP_USER (Применяется в инструкции DROP USER, процедурах **sp_dropuser**и **sp_revokedbaccess**.)|  
|CREATE_VIEW|ALTER_VIEW|DROP_VIEW|  
|CREATE_XML_INDEX|ALTER_INDEX может использоваться для XML-индексов.|DROP_INDEX может использоваться для XML-индексов.|  
|CREATE_XML_SCHEMA_COLLECTION|ALTER_XML_SCHEMA_COLLECTION|DROP_XML_SCHEMA_COLLECTION|  
  
## <a name="ddl-statements-that-have-server-scope"></a>Инструкции DDL области сервера  
 Триггеры DDL или уведомления о событиях могут быть созданы, чтобы срабатывать в ответ на следующие события, происходящие в экземпляре сервера.  
  
||||  
|-|-|-|  
|ALTER_AUTHORIZATION_SERVER|ALTER_SERVER_CONFIGURATION|ALTER_INSTANCE (Применяется в процедурах **sp_configure** и **sp_addserver** , если указан локальный экземпляр сервера.)|  
|CREATE_AVAILABILITY_GROUP|ALTER_AVAILABILITY_GROUP|DROP_AVAILABILITY_GROUP|  
|CREATE_CREDENTIAL|ALTER_CREDENTIAL|DROP_CREDENTIAL|  
|CREATE_CRYPTOGRAPHIC_PROVIDER|ALTER_CRYPTOGRAPHIC_PROVIDER|DROP_CRYPTOGRAPHIC_PROVIDER|  
|CREATE_DATABASE|ALTER_DATABASE (Применяется в инструкции ALTER DATABASE и процедуре **sp_fulltext_database**.)|DROP_DATABASE|  
|CREATE_ENDPOINT|ALTER_ENDPOINT|DROP_ENDPOINT|  
|CREATE_EVENT_SESSION|ALTER_EVENT_SESSION|DROP_EVENT_SESSION|  
|CREATE_EXTENDED_PROCEDURE (Применяется в процедуре **sp_addextendedproc**.)|DROP_EXTENDED_PROCEDURE (Применяется в процедуре **sp_dropextendedproc**.)||  
|CREATE_LINKED_SERVER (Применяется в процедуре **sp_addlinkedserver**.)|ALTER_LINKED_SERVER (Применяется в процедуре **sp_serveroption**.)|DROP_LINKED_SERVER (Применяется в процедуре **sp_dropserver** , если определен связанный сервер.)|  
|CREATE_LINKED_SERVER_LOGIN (Применяется в процедуре **sp_addlinkedsrvlogin**.)|DROP_LINKED_SERVER_LOGIN (Применяется в процедуре **sp_droplinkedsrvlogin**.)||  
|CREATE_LOGIN (Применяется в инструкции CREATE LOGIN, процедурах **sp_addlogin**, **sp_grantlogin**, **xp_grantlogin**и **sp_denylogin** при использовании несуществующего имени входа, который должен быть неявно создан.)|ALTER_LOGIN (Применяется в инструкции ALTER LOGIN, процедурах **sp_defaultdb**, **sp_defaultlanguage**, **sp_password**и **sp_change_users_login** , если указан параметр *Auto_Fix* .)|DROP_LOGIN (Применяется в инструкции DROP LOGIN, процедурах **sp_droplogin**, **sp_revokelogin**и **xp_revokelogin**.)|  
|CREATE_MESSAGE (Применяется в процедуре **sp_addmessage**.)|ALTER_MESSAGE (Применяется в процедуре **sp_altermessage**.)|DROP_MESSAGE (Применяется в процедуре **sp_dropmessage**.)|  
|CREATE_REMOTE_SERVER (Применяется в процедуре **sp_addserver**.)|ALTER_REMOTE_SERVER (Применяется в процедуре **sp_setnetname**.)|DROP_REMOTE_SERVER (Применяется в процедуре **sp_dropserver** , если указан удаленный сервер.)|  
|CREATE_RESOURCE_POOL|ALTER_RESOURCE_POOL|DROP_RESOURCE_POOL|  
|GRANT_SERVER|DENY_SERVER|REVOKE_SERVER|  
|ADD_SERVER_ROLE_MEMBER|DROP_SERVER_ROLE_MEMBER||  
|CREATE_SERVER_AUDIT|ALTER_SERVER_AUDIT|DROP_SERVER_AUDIT|  
|CREATE_SERVER_AUDIT_SPECIFICATION|ALTER_SERVER_AUDIT_SPECIFICATION|DROP_SERVER_AUDIT_SPECIFICATION|  
|CREATE_WORKLOAD_GROUP|CREATE_WORKLOAD_GROUP|CREATE_WORKLOAD_GROUP|  
  
## <a name="see-also"></a>См. также  
 [Триггеры DDL](ddl-triggers.md)   
 [Уведомления о событиях](../service-broker/event-notifications.md)   
 [Группы DDL-событий](ddl-event-groups.md)  
  
  
