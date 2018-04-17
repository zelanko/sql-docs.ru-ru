---
title: процедура sp_helppublication (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helppublication_TSQL
- sp_helppublication
helpviewer_keywords:
- sp_helppublication
ms.assetid: e801c3f0-dcbd-4b4a-b254-949a05f63518
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7160c358f0969c967cb0995e410f7e75427285bc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sphelppublication-transact-sql"></a>sp_helppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о публикации. Для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] публикации, эта хранимая процедура выполняется на издателе в базе данных публикации. В публикации Oracle эта хранимая процедура выполняется в распространителе для любой базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppublication [ [ @publication = ] 'publication' ]  
    [ , [ @found=] found OUTPUT]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication =** ] **"***публикации***"**  
 Имя просматриваемой публикации. *Публикация* имеет тип sysname и значение по умолчанию **%**, которая возвращает сведения обо всех публикациях.  
  
 [  **@found =** ] **"***найти***"** выходных данных  
 Флаг для указания возвращаемых строк. *найти*— **int** и является ВЫХОДНЫМ параметром, значение по умолчанию **23456**. **1** указывает, что публикация найдена. **0** указывает, что публикация не найдена.  
  
 [ **@publisher** =] **"***издатель***"**  
 Задает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *издатель* имеет тип sysname и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует указывать при запросе сведений о публикации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pubid|**int**|Идентификатор публикации.|  
|имя|**sysname**|Имя публикации.|  
|restricted|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**tinyint**|Текущее состояние публикации.<br /><br /> **0** = неактивно.<br /><br /> **1** = активно.|  
|задача||Используется для обратной совместимости.|  
|replication frequency|**tinyint**|Тип частоты репликации:<br /><br /> **0** = публикация транзакций<br /><br /> **1** = моментальный снимок|  
|synchronization method|**tinyint**|Режим синхронизации:<br /><br /> **0** = собственная программа массового копирования (**bcp** программы)<br /><br /> **1** = символьное массовое копирование<br /><br /> **3** = одновременный означает собственная программа массового копирования, (**bcp**программа) используется, но таблицы во время моментального снимка не блокируются<br /><br /> **4** = Concurrent_c, то используется символьное массовое копирование, но таблицы во время моментального снимка не блокируются|  
|description|**nvarchar(255)**|Дополнительное описание публикации.|  
|immediate_sync|**бит**|Указывает, выполняется ли создание (повторное создание) файлов синхронизации при каждом запуске агента моментальных снимков.|  
|enabled_for_internet|**бит**|Указывает доступность файлов синхронизации для публикации через Интернет по протоколу FTP, а также их доступность для других служб.|  
|allow_push|**бит**|Указывает, разрешена ли для данной публикации принудительная подписка.|  
|allow_pull|**бит**|Указывает, разрешена ли для данной публикации подписка по запросу.|  
|allow_anonymous|**бит**|Указывает, разрешена ли для данной публикации анонимная подписка.|  
|independent_agent|**бит**|Указывает, есть ли у данной публикации изолированный агент распространителя.|  
|immediate_sync_ready|**бит**|Указывает готовность агента моментальных снимков к работе с новыми подписками. Этот аргумент задается только в том случае, если в данной публикации моментальный снимок всегда доступен для новых или повторно инициализированных подписок.|  
|allow_sync_tran|**бит**|Определяет, разрешены ли в публикации немедленно обновляемые подписки.|  
|autogen_sync_procs|**бит**|Указывает, будут ли автоматически создаваться хранимые процедуры для поддержки немедленно обновляемых подписок.|  
|snapshot_jobid|**binary(16)**|Идентификатор запланированной задачи.|  
|retention|**int**|Сохраняемый объем изменений данной публикации в часах.|  
|has subscription|**бит**|Указывает, есть ли у публикации активные подписки. **1** означает, что публикация имеет активные подписки и **0** означает, что публикация не имеет подписок.|  
|allow_queued_tran|**бит**|Указывает, разрешено ли накопление изменений в подписчике в очереди до тех пор, пока их можно применить к издателю. Если **0**, изменения на подписчике не помещаются в очередь.|  
|snapshot_in_defaultfolder|**бит**|Указывает, хранятся ли файлы моментальных снимков в папке по умолчанию. Если **0**, файлы моментальных снимков хранятся в расположении, указанном в *alternate_snapshot_folder*. Если **1**, файлы моментальных снимков находятся в папке по умолчанию.|  
|alt_snapshot_folder|**nvarchar(255)**|Указывает местоположение альтернативной папки для моментального снимка.|  
|pre_snapshot_script|**nvarchar(255)**|Задает указатель **.sql** расположение файла. Если моментальный снимок применяется на подписчике, то агент распространителя запускает предварительный скрипт моментального снимка до выполнения скриптов реплицируемых объектов.|  
|post_snapshot_script|**nvarchar(255)**|Задает указатель **.sql** расположение файла. Агент распространителя запускает заключительный скрипт после применения скриптов и данных всех реплицируемых объектов во время первоначальной синхронизации.|  
|compress_snapshot|**бит**|Указывает, что моментальный снимок, записываемый *alt_snapshot_folder* сжатия в [!INCLUDE[msCoName](../../includes/msconame-md.md)] формате CAB. **0** указывает, что моментальный снимок не сжимается.|  
|ftp_address|**sysname**|Сетевой адрес службы FTP для распространителя. Указывает расположение файлов моментальных снимков публикаций для агента распространителя или агента слияния подписчика.|  
|ftp_port|**int**|Номер порта службы FTP для распространителя.|  
|ftp_subdirectory|**nvarchar(255)**|Указывает расположение файлов моментальных снимков для агента распространителя или агента слияния данного подписчика, если публикация поддерживает распространение моментальных снимков с помощью FTP.|  
|ftp_login|**sysname**|Имя пользователя для подключения к службе FTP.|  
|allow_dts|**бит**|Указывает, что в публикации разрешены преобразования данных. **0** указывает, что преобразование DTS запрещено.|  
|allow_subscription_copy|**бит**|Указывает, разрешено ли копирование баз данных подписки, подписанных на данную публикацию. **0** означает, что копирование запрещено.|  
|centralized_conflicts|**бит**|Определяет, хранятся ли на издателе конфликтные записи.<br /><br /> **0** = конфликтные записи хранятся как на издателе и на подписчике, вызвавшем конфликт.<br /><br /> **1** = конфликтные записи хранятся на издателе.|  
|conflict_retention|**int**|Задает срок хранения конфликтных записей в днях.|  
|conflict_policy|**int**|Задает политику устранения конфликтов при обновлении подписчика посредством очередей. Может принимать одно из следующих значений:<br /><br /> **1** = в конфликте Побеждает издатель.<br /><br /> **2** = в конфликте Побеждает подписчик.<br /><br /> **3** = повторной инициализации подписки.|  
|queue_type||Задает используемый тип очереди. Может принимать одно из следующих значений:<br /><br /> **MSMQ** = использовать [!INCLUDE[msCoName](../../includes/msconame-md.md)] очереди сообщений для хранения транзакций.<br /><br /> **SQL** = использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения транзакций.<br /><br /> Примечание: Служба очереди сообщений не поддерживается.|  
|backward_comp_level||Уровень совместимости базы данных. Может иметь одно из следующих значений:<br /><br /> **90** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|publish_to_AD|**бит**|Указывает, опубликована ли публикация в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory™. Значение **1** указывает, что она опубликована и значение **0** указывает, что он не опубликован.|  
|allow_initialize_from_backup|**бит**|Показывает, может ли подписчик инициализировать подписку на эту публикацию из резервной копии, а не из исходного моментального снимка. **1** означает, что подписки можно инициализировать из резервной копии, и **0** означает, что это невозможно. Дополнительные сведения см. в разделе [инициализировать транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) подписчика на публикацию транзакций без моментального снимка.|  
|replicate_ddl|**int**|Указывает, поддерживается ли для публикации репликация схемы. **1** указывает, что инструкции языка DDL для определения данных, выполняемые на издателе, реплицируются, а **0** указывает, что инструкции DDL не реплицируются. Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).|  
|enabled_for_p2p|**int**|Указывает, может ли публикация использоваться в одноранговой топологии репликации. **1** указывает, что публикация поддерживает — одноранговая репликация. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
|publish_local_changes_only|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|enabled_for_het_sub|**int**|Указывает, поддерживает ли публикация подписчиков, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение **1** означает, отличные от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются подписчики. Значение **0** означает, что только [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются подписчики. Дополнительные сведения см. в разделе [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).|  
|enabled_for_p2p_conflictdetection|**int**|Определяет, будет ли агент распространителя обнаруживать конфликты публикации, разрешенной для одноранговой репликации. Значение **1** означает, что конфликты обнаруживаются. Дополнительные сведения см. в разделе [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|originator_id|**int**|Указывает идентификатор в одноранговой топологии. Этот идентификатор используется для обнаружения конфликтов, если **enabled_for_p2p_conflictdetection** равно **1**. Список использованных идентификаторов запросите в системной таблице [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) .|  
|p2p_continue_onconflict|**int**|Указывает, продолжает ли агент распространителя обрабатывать изменения при обнаружении конфликта. Значение **1** означает, что агент продолжает обрабатывать изменения.<br /><br /> **\*\* Внимание \* \***  рекомендуется использовать значение по умолчанию **0**. Если значение этого параметра **1**, агент распространителя будет пытаться обеспечить конвергентность данных в топологии, применяя конфликтующую строку из узла с наибольшим значением идентификатора инициатора. Этот метод не гарантирует конвергенции. После обнаружения конфликта следует убедиться, что топология остается согласованной. Дополнительные сведения см. в подразделе «Обработка конфликтов» раздела [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|alllow_partition_switch|**int**|Указывает, могут ли инструкции ALTER TABLE…SWITCH выполняться по отношению к опубликованной базе данных. Дополнительные сведения см. в статье [Replicate Partitioned Tables and Indexes](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md) (Репликация секционированных таблиц и индексов).|  
|replicate_partition_switch|**int**|Указывает, должны ли инструкции ALTER TABLE…SWITCH, которые выполняются по отношению к опубликованной базе данных, реплицироваться на подписчики. Этот параметр действителен, только если *allow_partition_switch* равно **1**.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_helppublication используется при репликации моментальных снимков и транзакций.  
  
 Процедура sp_helppublication возвращает сведения обо всех публикациях, которые принадлежат пользователю, выполняющему эту процедуру.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_helppublication](../../relational-databases/replication/codesnippet/tsql/sp-helppublication-trans_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Процедуру sp_helppublication могут выполнять только члены предопределенной роли сервера sysadmin на издателе, члены предопределенной роли базы данных db_owner в базе данных публикации, а также пользователи из списка доступа к публикации (PAL).  
  
 Если издатель отличается от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то процедуру sp_helppublication могут выполнять только члены предопределенной роли сервера sysadmin на распространителе или предопределенной роли базы данных db_owner в базе данных распространителя, а также пользователи из списка доступа к публикации.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
