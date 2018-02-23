---
title: "sys.dm_tran_locks (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_tran_locks
- sys.dm_tran_locks
- sys.dm_tran_locks_TSQL
- dm_tran_locks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_locks dynamic management view
ms.assetid: f0d3b95a-8a00-471b-9da4-14cb8f5b045f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c54a97a7b84dcb4d9873ee2537e31714b6f62172
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2018
---
# <a name="sysdmtranlocks-transact-sql"></a>sys.dm_tran_locks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения об активных в данный момент в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ресурсах диспетчера блокировок. Каждая строка представляет текущий активный запрос диспетчеру блокировок о блокировке, которая была получена или находится в ожидании получения.  
  
 Столбцы в результирующем наборе разделяются на две группы: ресурсы и запросы. Группа ресурсов описывает ресурсы, на которые был выполнен запрос блокировки, а группа запросов описывает запрос блокировки.  
  
> [!NOTE]  
> Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_tran_locks**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**resource_type**|**nvarchar(60)**|Представляет тип ресурса. Значение может быть одним из следующих: базы данных, файла, ОБЪЕКТА, страницы, ключ, ЭКСТЕНТ, RID, приложения, МЕТАДАННЫЕ, HOBT или ALLOCATION_UNIT.|  
|**resource_subtype**|**nvarchar(60)**|Представляет подтип типа **resource_type**. Технически возможно получить блокировку подтипа без удерживания блокировки родительского типа, не разбитого на подтипы. Различные подтипы не конфликтуют между собой или с родительским типом, не разбитым на подтипы. Не у всех типов ресурсов имеются подтипы.|  
|**resource_database_id**|**int**|Идентификатор базы данных, в рамках которой находится ресурс. Все ресурсы, обрабатываемые диспетчером блокировок, находятся в рамках идентификатора базы данных.|  
|**resource_description**|**nvarchar(256)**|Описание ресурса, содержащее только те данные, которые недоступны из других столбцов источника.|  
|**resource_associated_entity_id**|**bigint**|Идентификатор сущности в базе данных, с которой связан ресурс. Это может быть идентификатор объекта, идентификатор Hobt или идентификатор единицы распределения в зависимости от типа ресурса.|  
|**resource_lock_partition**|**Int**|Идентификатор секционирования блокировки для ресурса с секционированными блокировками. Это значение для ресурса с несекционированными блокировками равно 0.|  
|**request_mode**|**nvarchar(60)**|Режим запроса. Режимом для предоставленных запросов является режим предоставления, для запросов в ожидании — запрашиваемый режим.|  
|**request_type**|**nvarchar(60)**|Тип запроса. Значение LOCK.|  
|**request_status**|**nvarchar(60)**|Текущее состояние запроса. Возможные значения: GRANTED, CONVERT, WAIT, LOW_PRIORITY_CONVERT, LOW_PRIORITY_WAIT или ABORT_BLOCKERS. Дополнительные сведения об ожиданиях с низким приоритетом и блокираторах отмены см. в разделе *low_priority_lock_wait* раздел [ALTER INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-index-transact-sql.md).|  
|**request_reference_count**|**smallint**|Возвращает приблизительное количество случаев, когда этот ресурс был запрошен одним и тем же объектом.|  
|**request_lifetime**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**request_session_id**|**int**|Идентификатор сеанса, которому в данный момент принадлежит этот запрос. Для распределенных и связанных транзакций идентификатор владеющего сеанса может меняться. Значение -2 показывает, что запрос относится к потерянной распределенной транзакции. Значение -3 показывает, что запрос принадлежит отложенной транзакции восстановления, например транзакции, для которой откат во время восстановления был отложен из-за невозможности успешно завершить операцию.|  
|**request_exec_context_id**|**int**|Идентификатор контекста выполнения процесса, которому в данный момент принадлежит запрос.|  
|**request_request_id**|**int**|Идентификатор запроса (идентификатор пакета) в процессе, которому в данный момент принадлежит запрос. Это значение меняется каждый раз при изменении в соединении режима MARS для транзакций.|  
|**request_owner_type**|**nvarchar(60)**|Тип сущности, которой принадлежит запрос. Запрос диспетчера блокировок может принадлежать нескольким разным объектам. Возможны следующие значения:<br /><br /> TRANSACTION = Запрос принадлежит транзакции.<br /><br /> CURSOR = Запрос принадлежит курсору.<br /><br /> SESSION = Запрос принадлежит сеансу пользователя.<br /><br /> SHARED_TRANSACTION_WORKSPACE = Запрос принадлежит общей части рабочего пространства транзакции.<br /><br /> EXCLUSIVE_TRANSACTION_WORKSPACE = Запрос принадлежит монопольной части рабочей области транзакции.<br /><br /> NOTIFICATION_OBJECT = запрос принадлежит внутреннему компоненту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот компонент попросил диспетчера блокировок уведомлять его в случае, если другой компонент ожидает получения блокировки. Функция FileTable — это компонент, который использует это значение.<br /><br /> **Примечание:** рабочие пространства предназначены внутренне хранят блокировки для прикрепленных сеансов.|  
|**request_owner_id**|**bigint**|Идентификатор определенного владельца запроса.<br /><br /> Если владельцем запроса является транзакция, это значение содержит идентификатор транзакции.<br /><br /> Если владельцем запроса, является таблица FileTable **request_owner_id** имеет одно из следующих значений.<br /><br /> <br /><br /> -4: таблица FileTable получила блокировку базы данных.<br /><br /> -3: таблица FileTable получила блокировку таблицы.<br /><br /> Другое значение: значение представляет дескриптор файла. Это значение также отображается как **fcb_id** в динамическом административном представлении [sys.dm_filestream_non_transacted_handles &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).|  
|**request_owner_guid**|**uniqueidentifier**|Идентификатор GUID определенного владельца запроса. Это значение используется только распределенной транзакцией, для которой оно является идентификатором GUID координатора MS DTC.|  
|**request_owner_lockspace_id**|**nvarchar(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Это значение представляет идентификатор заблокированного пространства запрашивающего объекта. Идентификатор заблокированного пространства определяет, совместимы ли друг с другом два запрашивающих объекта и можно ли им предоставить блокировки в режимах, которые в противном случае привели бы к конфликту.|  
|**lock_owner_address**|**varbinary(8)**|Адрес внутренней структуры данных в памяти, используемый для отслеживания этого запроса. Этот столбец может быть соединен с **resource_address** столбца в **sys.dm_os_waiting_tasks**.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> <br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
 
## <a name="remarks"></a>Remarks  
 Состояние предоставленного запроса показывает, что блокировка ресурса была предоставлена запрашивающему объекту. Ожидающий запрос обозначает, что запрос еще не был предоставлен. Возвращаются следующие типы ожидающих запросов **request_status** столбца:  
  
-   Состояние преобразованного запроса означает, что запрашивающий объект получил запрос ресурса и в настоящий момент ожидает, пока будет предоставлено обновление исходного запроса.  
  
-   Состояние ожидающего запроса означает, что к настоящему моменту запрашивающему объекту не был предоставлен запрос ресурса.  
  
 Поскольку **sys.dm_tran_locks** заполняется из структурам данных диспетчера внутренних блокировок, обслуживание этих данных не добавляет дополнительной нагрузки к обычной обработке. Для материализации представлений требуется доступ к внутренним структурам данных диспетчера блокировок. Это может в незначительной степени повлиять на обычную обработку на сервере. Это влияние должно быть незаметным и проявляться только в отношении часто используемых ресурсов. Поскольку данные этого представления соответствуют активному состоянию диспетчера блокировок, они в любое время могут измениться, а строки добавляются и удаляются по мере выдачи и отмены блокировок. Для этого представления нет данных предыстории.  
  
 Два запроса выполняются на одном и том же ресурсе только в том случае, когда все столбцы группы ресурса совпадают.  
  
 Управлять блокировкой операций считывания можно с помощью следующих средств.  
  
-   SET TRANSACTION ISOLATION LEVEL для определения уровня блокировки сеанса. Дополнительные сведения см. в разделе [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
-   Табличные подсказки блокировки для указания уровня блокировки для отдельной ссылки таблицы в предложении FROM. Синтаксис и ограничения см. в разделе [табличные подсказки &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-table.md).  
  
 В пределах одного сеанса ресурсу может быть предоставлено более одной блокировки. Другой сущности, которые выполняются в одном сеансе можно друг является владельцем блокировки на тот же ресурс и информация отображается в **request_owner_type** и **request_owner_id** столбцы, которые являются возвращенный **sys.dm_tran_locks**. Если несколько экземпляров одной и той же **request_owner_type** существует, **request_owner_id** столбец используется для различия экземпляров. Для распределенных транзакций **request_owner_type** и **request_owner_guid** столбцы будут показаны различные сведения о сущности.  
  
 Например, сеанс S1 владеет совмещаемой блокировкой на **Table1**; а транзакция Т1, запущенная в сеансе S1, также владеет совмещаемой блокировкой на **Table1**. В этом случае **resource_description** столбец, который возвращается методом **sys.dm_tran_locks** , отображает два экземпляра одного ресурса. **Request_owner_type** столбца один экземпляр отображается как сеанс, второй — как транзакция. Кроме того **resource_owner_id** столбец будет содержать разные значения.  
  
 Несколько курсоров, существующих в одном сеансе, неразличимы и обрабатываются как одна сущность.  
  
 Распределенные транзакции, не связанные со значением идентификатора сеанса, являются потерянными, и им назначается значение идентификатора сеанса, равное -2. Дополнительные сведения см. в разделе [KILL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/kill-transact-sql.md).  
  
## <a name="resource-details"></a>Подробности ресурса  
 В следующей таблице перечислены ресурсы, которые представлены в **resource_associated_entity_id** столбца.  
  
|Тип ресурса|Описание ресурса|Resource_associated_entity_id|  
|-------------------|--------------------------|--------------------------------------|  
|DATABASE|Представляет базу данных.|Неприменимо|  
|FILE|Представляет файл базы данных. Может быть файлом данных или журнала.|Неприменимо|  
|OBJECT|Представляет объект базы данных. Может быть таблицей данных, представлением, хранимой процедурой, расширенной хранимой процедурой или любым другим объектом, имеющим идентификатор объекта.|Идентификатор объекта.|  
|PAGE|Представляет отдельную страницу в файле данных.|Идентификатор HoBt. Это значение соответствует **sys.partitions.hobt_id**. Идентификатор HoBt не всегда доступен для ресурсов PAGE, так как Идентификатор HoBt — дополнительные данные, предоставляемые вызывающим участником, и не все вызывающие объекты способны предоставить эти данные.|  
|KEY|Представляет строку в указателе.|Идентификатор HoBt. Это значение соответствует **sys.partitions.hobt_id**.|  
|EXTENT|Представляет экстент файла данных. Экстент — это группа из восьми последовательных страниц.|Неприменимо|  
|RID|Представляет физическую строку в куче.|Идентификатор HoBt. Это значение соответствует **sys.partitions.hobt_id**. Идентификатор HoBt не всегда доступен для ресурсов RID, поскольку в нем содержатся дополнительные данные, предоставляемые вызывающим участником, но не все вызывающие объекты способны предоставить эти данные.|  
|APPLICATION|Представляет определенный ресурс приложения.|Неприменимо|  
|METADATA|Представляет метаданные.|Неприменимо|  
|HOBT|Представляет кучу или сбалансированное дерево. Это основные структуры путей доступа.|Идентификатор HoBt. Это значение соответствует **sys.partitions.hobt_id**.|  
|ALLOCATION_UNIT|Представляет набор связанных страниц, таких как секция индекса. Каждая единица распределения покрывает отдельную цепочку карты распределения индекса (IAM).|Идентификатор единицы распределения. Это значение соответствует **sys.allocation_units.allocation_unit_id**.|  
  
 В следующей таблице перечислены подтипы, связанные с типом каждого ресурса.  
  
|ResourceSubType|Действия синхронизации|  
|---------------------|------------------|  
|ALLOCATION_UNIT.BULK_OPERATION_PAGE|Предварительно выделенные страницы, используемые для массовых операций.|  
|ALLOCATION_UNIT.PAGE_COUNT|Статистика счетчика страниц для единиц распределения во время отложенных операций удаления.|  
|DATABASE.BULKOP_BACKUP_DB|Создание резервных копий базы данных с помощью массовых операций.|  
|DATABASE.BULKOP_BACKUP_LOG|Создание резервных копий журнала базы данных с помощью массовых операций.|  
|DATABASE.CHANGE_TRACKING_CLEANUP|Задачи очистки отслеживания изменений.|  
|DATABASE.CT_DDL|Операции DDL над отслеживанием изменений на уровне таблиц и базы данных.|  
|DATABASE.CONVERSATION_PRIORITY|Операции приоритета диалогов компонента Service Broker, например CREATE BROKER PRIORITY.|  
|DATABASE.DDL|Операции языка DDL, связанные с операциями над файловой группой, такими как удаление.|  
|DATABASE.ENCRYPTION_SCAN|Синхронизация шифрования TDE.|  
|DATABASE.PLANGUIDE|Синхронизация структуры плана.|  
|DATABASE.RESOURCE_GOVERNOR_DDL|Операции языка DDL, относящиеся к операциям регулятора ресурсов, такие как ALTER RESOURCE POOL.|  
|DATABASE.SHRINK|Операции сжатия базы данных.|  
|DATABASE.STARTUP|Синхронизация базы данных при запуске.|  
|FILE.SHRINK|Операции сжатия файлов.|  
|HOBT.BULK_OPERATION|Операции массовой загрузки, оптимизированные для кучи, с одновременным просмотром на следующих уровнях изоляции: моментальные снимки, незафиксированная операция чтения и зафиксированная операция чтения с использованием управления версиями строк.|  
|HOBT.INDEX_REORGANIZE|Операции реорганизации кучи или индекса.|  
|OBJECT.COMPILE|Компиляция хранимой процедуры.|  
|OBJECT.INDEX_OPERATION|Операции с индексами.|  
|OBJECT.UPDSTATS|Обновление статистики для таблицы.|  
|METADATA.ASSEMBLY|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ASSEMBLY_CLR_NAME|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ASSEMBLY_TOKEN|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ASYMMETRIC_KEY|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AUDIT|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AUDIT_ACTIONS|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AUDIT_SPECIFICATION|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AVAILABILITY_GROUP|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CERTIFICATE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CHILD_INSTANCE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.COMPRESSED_FRAGMENT|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.COMPRESSED_ROWSET|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSTATION_ENDPOINT_RECV|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSTATION_ENDPOINT_SEND|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSATION_GROUP|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSATION_PRIORITY|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CREDENTIAL|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CRYPTOGRAPHIC_PROVIDER|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DATA_SPACE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DATABASE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DATABASE_PRINCIPAL|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DB_MIRRORING_SESSION|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DB_MIRRORING_WITNESS|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DB_PRINCIPAL_SID|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ENDPOINT|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ENDPOINT_WEBMETHOD|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.EXPR_COLUMN|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.EXPR_HASH|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_CATALOG|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_INDEX|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_STOPLIST|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.INDEX_EXTENSION_SCHEME|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.INDEXSTATS|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.INSTANTIATED_TYPE_HASH|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.MESSAGE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.METADATA_CACHE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PARTITION_FUNCTION|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PASSWORD_POLICY|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PERMISSIONS|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PLAN_GUIDE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PLAN_GUIDE_HASH|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PLAN_GUIDE_SCOPE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.QNAME|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.QNAME_HASH|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.REMOTE_SERVICE_BINDING|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ROUTE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SCHEMA|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SECURITY_CACHE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SECURITY_DESCRIPTOR|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SEQUENCE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVER_EVENT_SESSIONS|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVER_PRINCIPAL|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE_BROKER_GUID|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE_CONTRACT|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE_MESSAGE_TYPE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.STATS|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SYMMETRIC_KEY|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.USER_TYPE|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.XML_COLLECTION|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.XML_COMPONENT|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.XML_INDEX_QNAME|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 В следующей таблице приведены формат **resource_description** столбец для каждого типа ресурсов.  
  
|Ресурс|Формат|Описание|  
|--------------|------------|-----------------|  
|DATABASE|Неприменимо|Идентификатор базы данных уже доступен в **resource_database_id** столбца.|  
|FILE|<file_id>|Идентификатор файла, представляемого данным ресурсом.|  
|OBJECT|< object_id >|Идентификатор объекта, представляемого данным ресурсом. Этот объект может быть любой объект из списка **sys.objects**, не только таблица.|  
|PAGE|<file_id>:<page_in_file>|Представляет файл и идентификатор страницы, представляемые данным ресурсом.|  
|KEY|<hash_value>|Представляет хэш ключевых столбцов из строки, представляемой данным ресурсом.|  
|EXTENT|<file_id>:<page_in_files>|Представляет файл и идентификатор экстента, представляемые данным ресурсом. Идентификатор экстента совпадает с идентификатором первой страницы этого экстента.|  
|RID|<file_id>:<page_in_file>:<row_on_page>|Представляет идентификатор страницы и идентификатор строки, представленной данным ресурсом. Обратите внимание на то, что, если идентификатор связанного объекта имеет значение 99, этот ресурс представляет одну из восьми областей памяти смешанных страниц первой IAM-страницы в цепочке IAM.|  
|APPLICATION|\<DbPrincipalId >:\<до 32 символов > :(< hash_value >)|Представляет идентификатор участника базы данных, используемого для определения области действия ресурса блокировки этого приложения. Также включает до 32 символов из строки ресурса, соответствующего ресурсу блокировок для этого приложения. В некоторых случаях из полной строки, больше не являющейся доступной, могут отображаться только 2 символа. Это происходит только во время восстановления базы данных для блокировок приложений, которые вызываются заново как часть процесса восстановления. Это хэш-значение представляет собой хэш-код полной строки ресурса, соответствующего ресурсу блокировки данного приложения.|  
|HOBT|Неприменимо|Идентификатор HoBt включается в качестве **resource_associated_entity_id**.|  
|ALLOCATION_UNIT|Неприменимо|Идентификатор единицы размещения включается в качестве **resource_associated_entity_id**.|  
|METADATA.ASSEMBLY|assembly_id = A|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ASSEMBLY_CLR_NAME|$qname_id = Q|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ASSEMBLY_TOKEN|assembly_id = A, $token_id|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ASSYMMETRIC_KEY|asymmetric_key_id = A|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AUDIT|audit_id = A|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AUDIT_ACTIONS|device_id = D, major_id = M|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AUDIT_SPECIFICATION|audit_specification_id = A|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.AVAILABILITY_GROUP|availability_group_id = A|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CERTIFICATE|certificate_id = C|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CHILD_INSTANCE|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.COMPRESSED_FRAGMENT|object_id = O , compressed_fragment_id = C|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.COMPRESSED_ROW|object_id = O|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSTATION_ENDPOINT_RECV|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSTATION_ENDPOINT_SEND|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSATION_GROUP|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CONVERSATION_PRIORITY|conversation_priority_id = C|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CREDENTIAL|credential_id = C|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.CRYPTOGRAPHIC_PROVIDER|provider_id = P|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DATA_SPACE|data_space_id = D|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DATABASE|database_id = D|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DATABASE_PRINCIPAL|principal_id = P|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DB_MIRRORING_SESSION|database_id = D|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DB_MIRRORING_WITNESS|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.DB_PRINCIPAL_SID|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ENDPOINT|endpoint_id = E|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ENDPOINT_WEBMETHOD|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_CATALOG|fulltext_catalog_id = F|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_INDEX|object_id = O|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.EXPR_COLUMN|object_id = O, column_id = C|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.EXPR_HASH|object_id = O, $hash = H|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_CATALOG|fulltext_catalog_id = F|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_INDEX|object_id = O|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.FULLTEXT_STOPLIST|fulltext_stoplist_id = F|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.INDEX_EXTENSION_SCHEME|index_extension_id = I|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.INDEXSTATS|object_id = O, index_id or stats_id = I|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.INSTANTIATED_TYPE_HASH|user_type_id = U, hash = H|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.MESSAGE|message_id = M|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.METADATA_CACHE|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PARTITION_FUNCTION|function_id = F|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PASSWORD_POLICY|principal_id = P|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PERMISSIONS|class = C|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.PLAN_GUIDE|plan_guide_id = P|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA. PLAN_GUIDE_HASH|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA. PLAN_GUIDE_SCOPE|scope_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.QNAME|$qname_id = Q|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.QNAME_HASH|$qname_scope_id = Q, $qname_hash = H|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.REMOTE_SERVICE_BINDING|remote_service_binding_id = R|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.ROUTE|route_id = R|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SCHEMA|schema_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SECURITY_CACHE|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SECURITY_DESCRIPTOR|sd_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SEQUENCE|$seq_type = S, object_id = O|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVER|server_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVER_EVENT_SESSIONS|event_session_id = E|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVER_PRINCIPAL|principal_id = P|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE|service_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE_BROKER_GUID|$hash = H1:H2:H3|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE_CONTRACT|service_contract_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SERVICE_MESSAGE_TYPE|message_type_id = M|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.STATS|object_id = O, stats_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.SYMMETRIC_KEY|symmetric_key_id = S|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.USER_TYPE|user_type_id = U|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.XML_COLLECTION|xml_collection_id = X|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.XML_COMPONENT|xml_component_id = X|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|METADATA.XML_INDEX_QNAME|object_id = O, $qname_id = Q|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 Следующие события XEvents относятся к секции **КОММУТАТОР** и перестроение индекса в сети. Сведения о синтаксисе см. в разделе [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md) и [ALTER INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-index-transact-sql.md).  
  
-   lock_request_priority_state  
  
-   process_killed_by_abort_blockers  
  
-   ddl_with_wait_at_low_priority  
  
 Существующее событие XEvent **progress_report_online_index_operation** для индексами операции было расширено путем добавления **partition_number** и **partition_id**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-sysdmtranlocks-with-other-tools"></a>A. Использование sys.dm_tran_locks с другими средствами  
 В следующем примере выполняется работа со сценарием, в котором операция обновления блокируется другой транзакцией. С помощью **sys.dm_tran_locks** и других средств можно получить сведения об источниках блокировки.  
  
```sql  
USE tempdb;  
GO  
  
-- Create test table and index.  
CREATE TABLE t_lock  
    (  
    c1 int, c2 int  
    );  
GO  
  
CREATE INDEX t_lock_ci on t_lock(c1);  
GO  
  
-- Insert values into test table  
INSERT INTO t_lock VALUES (1, 1);  
INSERT INTO t_lock VALUES (2,2);  
INSERT INTO t_lock VALUES (3,3);  
INSERT INTO t_lock VALUES (4,4);  
INSERT INTO t_lock VALUES (5,5);  
INSERT INTO t_lock VALUES (6,6);  
GO  
  
-- Session 1  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
  
BEGIN TRAN  
    SELECT c1  
        FROM t_lock  
        WITH(holdlock, rowlock);  
  
-- Session 2  
BEGIN TRAN  
    UPDATE t_lock SET c1 = 10  
```  
  
 Следующий запрос отображает сведения о блокировке. Значение для `<dbid>` необходимо заменить **database_id** из **sys.databases**.  
  
```sql  
SELECT resource_type, resource_associated_entity_id,  
    request_status, request_mode,request_session_id,  
    resource_description   
    FROM sys.dm_tran_locks  
    WHERE resource_database_id = <dbid>  
```  
  
 Следующий запрос возвращает сведения об объекте с помощью значения `resource_associated_entity_id` из предыдущего запроса. Этот запрос должен быть выполнен, пока существует соединение с базой данных, содержащей объект.  
  
```  
SELECT object_name(object_id), *  
    FROM sys.partitions  
    WHERE hobt_id=<resource_associated_entity_id>  
```  
  
 Следующий запрос отображает сведения о блокировках.  
  
```sql  
SELECT   
        t1.resource_type,  
        t1.resource_database_id,  
        t1.resource_associated_entity_id,  
        t1.request_mode,  
        t1.request_session_id,  
        t2.blocking_session_id  
    FROM sys.dm_tran_locks as t1  
    INNER JOIN sys.dm_os_waiting_tasks as t2  
        ON t1.lock_owner_address = t2.resource_address;  
```  
  
 Освобождение ресурсов с помощью отката транзакций.  
  
```sql  
-- Session 1  
ROLLBACK;  
GO  
  
-- Session 2  
ROLLBACK;  
GO  
```  
  
### <a name="b-linking-session-information-to-operating-system-threads"></a>Б. Связывание данных о сеансе с потоками операционной системы  
 Следующий пример возвращает информацию, связывающую идентификатор сеанса с идентификатором потока Windows. За производительностью потока можно наблюдать в системном мониторе Windows. Запрос не возвращает идентификаторы сеансов, которые в настоящий момент находятся в ждущем режиме.  
  
```sql  
SELECT STasks.session_id, SThreads.os_thread_id  
    FROM sys.dm_os_tasks AS STasks  
    INNER JOIN sys.dm_os_threads AS SThreads  
        ON STasks.worker_address = SThreads.worker_address  
    WHERE STasks.session_id IS NOT NULL  
    ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sys.dm_tran_database_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-database-transactions-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с транзакциями (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
