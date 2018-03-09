---
title: "sys.databases (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- databases
- databases_TSQL
- sys.databases
- sys.databases_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.databases catalog view
ms.assetid: 46c288c1-3410-4d68-a027-3bbf33239289
caps.latest.revision: "152"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: cccac1ba1615e6a825230c3735488e182aeed1e5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sysdatabases-transact-sql"></a>sys.databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит одну строку для каждой базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если база данных не `ONLINE`, или `AUTO_CLOSE` равно `ON` и база данных закрыта, значения некоторых столбцов могут быть `NULL`. Если база данных находится в `OFFLINE`, соответствующая строка не отображается для пользователей с ограниченными правами доступа. Чтобы увидеть соответствующую строку, если база данных `OFFLINE`, пользователь должен иметь по крайней мере `ALTER ANY DATABASE` разрешение уровня сервера или `CREATE DATABASE` разрешение в `master` базы данных.  
  

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных, уникальное внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или на сервере [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**database_id**|**int**|Идентификатор базы данных, уникальный внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или на сервере [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**source_database_id**|**int**|Не NULL = идентификатор базы данных-источника данного моментального снимка базы данных.<br /> NULL = моментальный снимок не базы данных.|  
|**owner_sid**|**varbinary(85)**|SID (идентификатор безопасности) внешнего владельца базы данных, зарегистрированного на сервере. Сведения о владеющих базы данных см. в разделе **ALTER AUTHORIZATION для баз данных** раздел [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).|  
|**create_date**|**datetime**|Дата создания или переименования базы данных. Для **tempdb**, это значение изменяется каждый раз при перезапуске сервера.|  
|**compatibility_level**|**tinyint**|Целое число, соответствующее версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которой поведение совместимо:<br /> **Значение** : **применяется к**<br /> 70: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 80: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 90: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /> 100: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 110: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 120: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 130: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] |  
|**collation_name**|**sysname**|Параметры сортировки для базы данных. Действует как параметры сортировки по умолчанию для базы данных.<br /> NULL — база данных не находится в режиме «в сети», либо параметр AUTO_CLOSE установлен в ON, и база данных закрыта.|  
|**user_access**|**tinyint**|Установка доступа пользователя:<br /> 0 = указано MULTI_USER.<br /> 1 = указано SINGLE_USER;<br /> 2 = указан RESTRICTED_USER.|  
|**user_access_desc**|**nvarchar(60)**|Описание задания доступа пользователя.|  
|**is_read_only**|**bit**|1 = база данных находится в режиме READ_ONLY<br /> 0 = база данных находится в режиме READ_WRITE|  
|**is_auto_close_on**|**bit**|1 = параметр AUTO_CLOSE находится в состоянии ON<br /> 0 = параметр AUTO_CLOSE находится в состоянии OFF|  
|**is_auto_shrink_on**|**bit**|1 = параметр AUTO_SHRINK находится в состоянии ON<br /> 0 = параметр AUTO_SHRINK находится в состоянии OFF|  
|**state**|**tinyint**|**Значение &#124; Применяется к**<br /> 0 = ONLINE <br /> 1 = RESTORING <br /> 2 = RECOVERING: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 3 = RECOVERY_PENDING: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 4 = SUSPECT <br /> 5 = АВАРИЙНОГО: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 6 = вне сети: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 7 = COPYING: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)][!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /> 10 = OFFLINE_SECONDARY: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)][!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /><br /> **Примечание:** базы данных Always On, запрос `database_state` или `database_state_desc` столбцы [sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md).|  
|**state_desc**|**nvarchar(60)**|Описание состояния базы данных. Для проверки состояния.|  
|**is_in_standby**|**bit**|База данных доступна только для чтения для журнала восстановления.|  
|**is_cleanly_shutdown**|**bit**|1 = база данных закрыта верно; восстановление при запуске не требуется<br /> 0 = база данных закрыта неверно; требуется восстановление при запуске|  
|**is_supplemental_logging_enabled**|**bit**|1 = SUPPLEMENTAL_LOGGING в состоянии ON<br /> 0 = SUPPLEMENTAL_LOGGING в состоянии OFF|  
|**snapshot_isolation_state**|**tinyint**|Состояние транзакций изоляции моментальных снимков, задаваемое при помощи параметра ALLOW_SNAPSHOT_ISOLATION.<br /> 0 = изоляция моментальных снимков в состоянии OFF (по умолчанию). Изоляция моментальных снимков запрещена.<br /> 1 = изоляция моментальных снимков в состоянии ON. Изоляция моментальных снимков разрешена.<br /> 2 = изоляция моментальных снимков в состоянии перехода в состояние OFF. Для всех транзакций записываются изменения. Нельзя запустить новые транзакции, использующие изоляцию моментальных снимков. База данных находится в состоянии перехода в состояние OFF до тех пор, пока все транзакции, активные при выполнении инструкции ALTER DATABASE, не будут завершены.<br /> 3 = изоляция моментальных снимков в состоянии перехода в состояние ON. Для новых транзакций записываются изменения. Транзакции не могут использовать изоляцию моментальных снимков до тех пор, пока состояние изоляции моментальных снимков не перейдет в 1 (ON). База данных находится в состоянии перехода в состояние ON до тех пор, пока все транзакции, активные при выполнении инструкции ALTER DATABASE, не будут завершены.|  
|**snapshot_isolation_state_desc**|**nvarchar(60)**|Описание состояния транзакций изоляции моментальных снимков, задаваемое при помощи параметра ALLOW_SNAPSHOT_ISOLATION.|  
|**is_read_committed_snapshot_on**|**bit**|1 = параметр READ_COMMITTED_SNAPSHOT установлен в значение ON. Операции чтения с уровнем изоляции read-committed основаны на просмотре моментальных снимков и не запрашивают блокировок.<br /> 0 = параметр READ_COMMITTED_SNAPSHOT установлен в значение OFF (по умолчанию). Операции чтения с уровнем изоляции read-committed используют разделяемые блокировки.|  
|**recovery_model**|**tinyint**|Выбранная модель восстановления:<br /> 1 = FULL<br /> 2 = BULK_LOGGED<br /> 3 = SIMPLE|  
|**recovery_model_desc**|**nvarchar(60)**|Описание выбранной модели восстановления.|  
|**page_verify_option**|**tinyint**|Значение параметра PAGE_VERIFY:<br /> 0 = нет<br /> 1 = TORN_PAGE_DETECTION<br /> 2 = CHECKSUM|  
|**page_verify_option_desc**|**nvarchar(60)**|Описание значения параметра PAGE_VERIFY.|  
|**is_auto_create_stats_on**|**bit**|1 = AUTO_CREATE_STATISTICS в состоянии ON<br /> 0 = AUTO_CREATE_STATISTICS в состоянии OFF|  
|**is_auto_create_stats_incremental_on**|**bit**|Указывает параметр по умолчанию для добавочной обработки автоматической статистики.<br /> 0 = автоматическое создание статистики не добавочно<br /> 1 = автоматическое создание статистики по возможности добавочно<br /> **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**is_auto_update_stats_on**|**bit**|1 = AUTO_UPDATE_STATISTICS в состоянии ON<br /> 0 = AUTO_UPDATE_STATISTICS в состоянии OFF|  
|**is_auto_update_stats_async_on**|**bit**|1 = AUTO_UPDATE_STATISTICS_ASYNC в состоянии ON<br /> 0 = AUTO_CREATE_STATISTICS_ASYNC в состоянии OFF|  
|**is_ansi_null_default_on**|**bit**|1 = ANSI_NULL_DEFAULT в состоянии ON<br /> 0 = ANSI_NULL_DEFAULT в состоянии OFF|  
|**is_ansi_nulls_on**|**bit**|1 = ANSI_NULLS в состоянии ON<br /> 0 = ANSI_NULLS в состоянии OFF|  
|**is_ansi_padding_on**|**bit**|1 = ANSI_PADDING в состоянии ON<br /> 0 = ANSI_PADDING в состоянии OFF|  
|**is_ansi_warnings_on**|**bit**|1 = ANSI_WARNINGS в состоянии ON<br /> 0 = ANSI_WARNINGS в состоянии OFF|  
|**is_arithabort_on**|**bit**|1 = ARITHABORT в состоянии ON<br /> 0 = ARITHABORT в состоянии OFF|  
|**is_concat_null_yields_null_on**|**bit**|1 = CONCAT_NULL_YIELDS_NULL в состоянии ON<br /> 0 = CONCAT_NULL_YIELDS_NULL в состоянии OFF|  
|**is_numeric_roundabort_on**|**bit**|1 = NUMERIC_ROUNDABORT в состоянии ON<br /> 0 = NUMERIC_ROUNDABORT в состоянии OFF|  
|**is_quoted_identifier_on**|**bit**|1 = QUOTED_IDENTIFIER в состоянии ON<br /> 0 = QUOTED_IDENTIFIER в состоянии OFF|  
|**is_recursive_triggers_on**|**bit**|1 = RECURSIVE_TRIGGERS в состоянии ON<br /> 0 = RECURSIVE_TRIGGERS в состоянии OFF|  
|**is_cursor_close_on_commit_on**|**bit**|1 = CURSOR_CLOSE_ON_COMMIT в состоянии ON<br /> 0 = CURSOR_CLOSE_ON_COMMIT в состоянии OFF|  
|**is_local_cursor_default**|**bit**|1 = CURSOR_DEFAULT соответствует локальному курсору<br /> 0 = CURSOR_DEFAULT соответствует глобальному курсору|  
|**is_fulltext_enabled**|**bit**|1 = полнотекстовый режим включен для данной базы данных<br /> 0 = полнотекстовый режим отключен для данной базы данных|  
|**is_trustworthy_on**|**bit**|1 = база данных помечена как надежная<br /> 0 = база данных не помечена как надежная|  
|**is_db_chaining_on**|**bit**|1 = межбазовые цепочки владения в состоянии ON<br /> 0 = межбазовые цепочки владения в состоянии OFF|  
|**is_parameterization_forced**|**bit**|1 = параметризация в состоянии FORCED<br /> 0 = параметризация в состоянии SIMPLE|  
|**is_master_key_encrypted_by_server**|**bit**|1 = база данных имеет главный ключ шифрования<br /> 0 = база данных не имеет главного ключа шифрования|  
|**is_query_store_on**|**bit**|1 = запрос хранилища включена для этой базы данных. Проверьте [sys.database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md) для просмотра состояния хранилища запросов.<br /> 0 = запрос хранилища не включена.<br /> **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
|**is_published**|**bit**|1 = база данных является базой данных публикации в топологии репликации транзакций или моментальных снимков<br /> 0 = не является базой данных публикации|  
|**is_subscribed**|**bit**|Данный столбец не используется. Он всегда возвращает 0, независимо от состояния подписчика базы данных.|  
|**is_merge_published**|**bit**|1 = база данных является базой данных публикации в топологии репликации слиянием<br /> 0 = база данных не является базой данных публикации в топологии репликации слиянием|  
|**is_distributor**|**bit**|1 = база данных является базой данных распространителя в топологии репликации<br /> 0 = база данных не является базой данных распространителя в топологии репликации|  
|**is_sync_with_backup**|**bit**|1 = база данных помечена для синхронизации с резервной копией при помощи репликации<br /> 0 = база данных не помечена для синхронизации с резервной копией при помощи репликации|  
|**service_broker_guid**|**uniqueidentifier**|Идентификатор компонента Service Broker для данной базы данных. Используется в качестве **broker_instance** целевого объекта в таблице маршрутизации.|  
|**is_broker_enabled**|**bit**|1 = брокер в этой базе данных в данный момент отправляет и принимает сообщения.<br /> 0 = все отправленные сообщения останутся в очереди передачи, а полученные сообщения не будут помещены в очередь в этой базе данных.<br /> По умолчанию в восстановленных или прикрепленных базах данных брокер отключен. Исключением является зеркальное отображение базы данных, при котором брокер включается после отработки отказа.|  
|**log_reuse_wait**|**tinyint**|Повторное использование места журнала транзакций в данный момент ожидает один из следующих на момент последней контрольной точки. (Более подробные объяснения этих значений см. в разделе [резервная копия журнала транзакций](../../relational-databases/logs/the-transaction-log-sql-server.md).)<br /> 0 = ничего<br />   1 = контрольная точка (Если база данных использует модель восстановления и содержит оптимизированную для памяти файловую группу данных, следует ожидать, что в столбце log_reuse_wait будет указано checkpoint или xtp_checkpoint.) **Применяется к** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  2 = резервная копия журнала **применяется к** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  3 = активное резервное копирование или восстановление **применяется к** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  4 = активная транзакция **применяется к** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  5 = зеркальное отображение базы данных **применяется к** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  6 = репликация **применяется к** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  7 = создание моментального снимка базы данных **применяется к** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  8 = Просмотр журнала **применяется к**<br />  9 = группы доступности AlwaysOn для соответствующей базы данных-получателя вторичная реплика применяет записи журнала транзакций этой базы данных. **Применяется к** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В более ранних версиях SQL Server 9 = прочее (нерегулярное).<br />  10 = только для внутреннего использования **применяется к** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  11 = только для внутреннего использования **применяется к** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 12 = только для внутреннего использования **применяется к** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />13 = самая старая страница **применяется к** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 14 = other **применяется к** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  16 = XTP_CHECKPOINT (Если база данных использует модель восстановления и содержит оптимизированную для памяти файловую группу данных, следует ожидать, что в столбце log_reuse_wait будет указано checkpoint или xtp_checkpoint.) **Применяется к** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**log_reuse_wait_desc**|**nvarchar(60)**|Описание повторного использования места в журнале транзакций, ожидаемого в настоящее время по состоянию на последнюю контрольную точку.|  
|**is_date_correlation_on**|**bit**|1 = DATE_CORRELATION_OPTIMIZATION в состоянии ON<br /> 0 = DATE_CORRELATION_OPTIMIZATION в состоянии OFF|  
|**is_cdc_enabled**|**bit**|1 = в базе данных включена система отслеживания измененных данных. Дополнительные сведения см. в разделе [sys.sp_cdc_enable_db &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md).|  
|**is_encrypted**|**bit**|Указывает, зашифрована ли база данных (отражает последнее состояние, установленное с помощью предложения ALTER DATABASE SET ENCRYPTION). Может использоваться одно из следующих значений:<br /> 1 = зашифрована<br /> 0 = не зашифрована.<br /> Дополнительные сведения о шифровании баз данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).<br /> Если база данных находится в процессе расшифровки, **is_encrypted** указано значение 0. Можно просмотреть состояние процесса шифрования с помощью [sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) динамическое административное представление.|  
|**is_honor_broker_priority_on**|**bit**|Указывает, учитываются ли в базе данных приоритеты диалогов (отражает последнее состояние, установленное предложением ALTER DATABASE SET HONOR_BROKER_PRIORITY). Может использоваться одно из следующих значений:<br /> 1 = HONOR_BROKER_PRIORITY имеет значение ON;<br /> 0 = HONOR_BROKER_PRIORITY имеет значение OFF.|  
|**replica_id**|**uniqueidentifier**|Уникальный идентификатор локальной реплики доступности [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] группы доступности, если таковая имеется, частью которой является база данных.<br /> NULL = база данных не является частью реплики доступности в группе доступности.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**group_database_id**|**uniqueidentifier**|Уникальный идентификатор базы данных в пределах доступности группы AlwaysOn, если таковая имеется, в которой участвует база данных. **group_database_id** одинаково для этой базы данных на первичной реплике и на каждой вторичной реплике, на котором базы данных была присоединена к группе доступности.<br /> NULL = база данных не является частью реплики доступности в любой группе доступности.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**resource_pool_id**|**int**|Идентификатор пула ресурсов, сопоставленного с этой базой данных. Этот пул ресурсов управляет общим объемом памяти, доступным оптимизированным для памяти таблицам из этой базы данных.<br /> **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**default_language_lcid**|**smallint**|Указывает идентификатор локали (lcid) языка по умолчанию автономной базы данных.<br /> **Примечание** функционирует как [Настройка параметра конфигурации сервера язык по умолчанию](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) из **sp_configure**. Это значение является **null** для неавтономной базы данных.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_language_name**|**nvarchar(128)**|Указывает язык по умолчанию автономной базы данных.<br /> Это значение является **null** для неавтономной базы данных.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_lcid**|**int**|Указывает идентификатор локали (lcid) языка полнотекстового поиска по умолчанию автономной базы данных.<br /> **Примечание** функционирует как значение по умолчанию [Настройка параметра default full-text language параметр конфигурации сервера](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) из **sp_configure**. Это значение является **null** для неавтономной базы данных.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_name**|**nvarchar(128)**|Указывает язык полнотекстового поиска по умолчанию автономной базы данных.<br /> Это значение является **null** для неавтономной базы данных.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_nested_triggers_on**|**bit**|Указывает, разрешены ли вложенные триггеры в автономной базе данных.<br /> 0 = вложенные триггеры не разрешены<br /> 1 = вложенные триггеры разрешены<br /> **Примечание** функционирует как [Настройка параметра конфигурации сервера nested triggers](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) из **sp_configure**. Это значение является **null** для неавтономной базы данных. В разделе [sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) для получения дополнительных сведений.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_transform_noise_words_on**|**bit**|Указывает, должны ли преобразовываться пропускаемые слова в автономной базе данных.<br /> 0 = пропускаемые слова не должны преобразовываться.<br /> 1 = пропускаемые слова должны преобразовываться.<br /> **Примечание** функционирует как [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md) из **sp_configure**. Это значение является **null** для неавтономной базы данных. В разделе [sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) для получения дополнительных сведений.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**two_digit_year_cutoff**|**smallint**|Указывает числовое значение в диапазоне от 1753 до 9999, представляющее пороговый год для интерпретации года, обозначенного двумя цифрами, в виде года, обозначенного четырьмя цифрами.<br /> **Примечание** функционирует как [Настройка two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) из **sp_configure**. Это значение является **null** для неавтономной базы данных. В разделе [sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) для получения дополнительных сведений.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**вложения**|**tinyint не null**|Указывает состояние включения базы данных.<br />  0 = автономная работа базы данных отключена. **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 1 = база данных находится в состоянии частичного включения **применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**containment_desc**|**nvarchar(60) не null**|Указывает состояние включения базы данных.<br /> NONE = прежняя версия базы данных (нулевое включение)<br /> PARTIAL = частично автономная база данных<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**target_recovery_time_in_seconds**|**int**|Предполагаемое время восстановления базы данных в секундах. Допускает значение NULL.<br /> **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)],[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**delayed_durability**|**int**|Параметр отложенной длительности:<br /> 0 = ОТКЛЮЧЕНО<br /> 1 = РАЗРЕШЕНО<br /> 2 = ПРИНУДИТЕЛЬНЫЙ<br /> Дополнительные сведения см. в разделе [управление устойчивостью транзакций](../../relational-databases/logs/control-transaction-durability.md).<br /> **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**delayed_durability_desc**|**nvarchar(60)**|Параметр отложенной длительности:<br /> DISABLED<br /> ALLOWED<br /> FORCED<br /> **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /> **Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**is_memory_optimized_elevate_to_snapshot_on**|**bit**|К таблицам с оптимизацией для памяти доступ производится с использованием изоляции SNAPSHOT, когда в TRANSACTION ISOLATION LEVEL установлен более низкий уровень изоляции — READ COMMITTED или READ UNCOMMITTED.<br /> 1 = минимальный уровень изоляции — SNAPSHOT.<br /> 0 = уровень изоляции не повышается.|  
|**is_federation_member**|**bit**|Указывает, является ли база данных членом федерации.<br /> **Область применения**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_remote_data_archive_enabled**|**bit**|Указывает, растягивается ли базы данных.<br /> 0 = база данных не включена.<br /> 1 = база данных находится, совместимую со Stretch.<br /> **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> Дополнительные сведения см. в разделе [базы данных Stretch](../../sql-server/stretch-database/stretch-database.md).|  
|**is_mixed_page_allocation_on**|**bit**|Указывает, является ли таблицы и индексы в базе данных можно выделить начальной страницы из смешанных экстентов.<br /> 0 = таблиц и индексов в базе данных всегда выделяет начальной страницы из однородных экстентов.<br /> 1 = таблиц и индексов в базе данных можно выделить начальной страницы из смешанных экстентов.<br /> **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> Дополнительные сведения см. в разделе ЗАДАТЬ инструкции mixed_page_allocation [параметры ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md).|  
|**is_temporal_retention_enabled**|**bit**|Указывает, включен ли задача очистки политики временного хранения.<br /> **Применяется к**: база данных Azure SQL|
|**catalog_collation_type**|**int**|Настройка параметров сортировки каталога:<br />0 = DATABASE_DEFAULT<br />2 = SQL_Latin_1_General_CP1_CI_AS<br /> **Применяется к**: база данных Azure SQL|
|**catalog_collation_type_desc**|**nvarchar(60)**|Настройка параметров сортировки каталога:<br />DATABASE_DEFAULT<br />SQL_Latin_1_General_CP1_CI_AS<br /> **Применяется к**: база данных Azure SQL|
  
## <a name="permissions"></a>Разрешения  
 Если код, вызывающий `sys.databases` не является владельцем базы данных и база данных не `master` или `tempdb`, минимальные разрешения, необходимые для просмотра соответствующей строки являются `ALTER ANY DATABASE` или `VIEW ANY DATABASE` разрешение уровня сервера или `CREATE DATABASE` разрешение в `master` базы данных. Всегда можно просматривать базы данных, к которой подключен участник в `sys.databases`.  
  
> [!IMPORTANT]  
>  По умолчанию имеет роли public `VIEW ANY DATABASE` разрешений, что все имена входа просмотреть сведения о базе данных. Чтобы заблокировать вход с возможность обнаружения базы данных, `REVOKE` `VIEW ANY DATABASE` разрешений у `public`, или `DENY` "разрешение VIEW ANY DATABASE для отдельных имен входа.  
  
## <a name="includesssdsincludessssds-mdmd-remarks"></a>[!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Замечания  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)], это представление доступно в `master` базы данных и в пользовательской базе данных. В `master` базы данных, это представление возвращает сведения о `master` базы данных и все пользовательские базы данных на сервере. В пользовательской базе данных это представление возвращает сведения только по текущей базе данных и базе данных master.  
  
 Воспользуйтесь представлением `sys.databases` в базе данных `master` на сервере [!INCLUDE[ssSDS](../../includes/sssds-md.md)], где создается новая база данных. После начала копирования базы данных, можно выполнять запросы `sys.databases` и `sys.dm_database_copies` представлений из `master` базы данных на сервере назначения для получения дополнительных сведений о ходе копирования.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-query-the-sysdatabases-view"></a>A. Запрос к представлению sys.databases  
 Следующий пример возвращает несколько столбцов, доступных в `sys.databases` представления.  
  
```  
SELECT name, user_access_desc, is_read_only, state_desc, recovery_model_desc  
FROM sys.databases;  
```  
  
### <a name="b-check-the-copying-status-in-includesssdsincludessssds-mdmd"></a>Б. Проверка состояния копирования в продукте [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 В следующем примере запрос `sys.databases` и `sys.dm_database_copies` операции копирования представления для возврата сведений о базе данных.  
  
**Применяется к**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
  
```  
-- Execute from the master database.  
SELECT a.name, a.state_desc, b.start_date, b.modify_date, b.percentage_complete  
FROM sys.databases AS a  
INNER JOIN sys.dm_database_copies AS b ON a.database_id = b.database_id  
WHERE a.state = 7;  
```  
### <a name="c-check-the-temporal-retention-policy-status-in-includesssdsincludessssds-mdmd"></a>В. Проверка состояния политики временного хранения[!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 В следующем примере запрос `sys.databases` для возврата сведений о ли задача очистки временного хранения включена. Имейте в виду, что после операции восстановления временного хранения по умолчанию отключены. Используйте `ALTER DATABASE` чтобы явно включить.
  
**Область применения**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```  
-- Execute from the master database.  
SELECT a.name, a.is_temporal_history_retention_enabled 
FROM sys.databases AS a;
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.database_recovery_status &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-recovery-status-transact-sql.md)   
 [Представления каталогов баз данных и файлов (Transact-SQL)](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.dm_database_copies &#40; База данных Azure SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)  
  
  
