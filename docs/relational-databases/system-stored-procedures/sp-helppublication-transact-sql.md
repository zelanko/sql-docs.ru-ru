---
title: sp_helppublication (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppublication_TSQL
- sp_helppublication
helpviewer_keywords:
- sp_helppublication
ms.assetid: e801c3f0-dcbd-4b4a-b254-949a05f63518
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b4c5d3157c6683a793f30eccd878aa9e691c7023
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729223"
---
# <a name="sp_helppublication-transact-sql"></a>sp_helppublication (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает сведения о публикации. Для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] публикации эта хранимая процедура выполняется на издателе в базе данных публикации. В публикации Oracle эта хранимая процедура выполняется в распространителе для любой базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppublication [ [ @publication = ] 'publication' ]  
    [ , [ @found=] found OUTPUT]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя просматриваемой публикации. Аргумент *publication* имеет тип sysname и значение по умолчанию **%** , которое возвращает сведения обо всех публикациях.  
  
`[ @found = ] 'found' OUTPUT`Флаг, указывающий возвращаемые строки. Аргумент *Found*имеет **тип int** и выходной параметр и значение по умолчанию **23456**. **1** указывает, что публикация найдена. значение **0** указывает, что публикация не найдена.  
  
`[ @publisher = ] 'publisher'`Указывает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип sysname и значение по умолчанию NULL.  
  
> [!NOTE]  
>  не следует указывать *Издатель* при запросе сведений о публикации от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|pubid|**int**|Идентификатор публикации.|  
|name|**sysname**|Имя публикации.|  
|restricted|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**tinyint**|Текущее состояние публикации.<br /><br /> **0** = неактивно.<br /><br /> **1** = активно.|  
|задача||Используется для обратной совместимости.|  
|replication frequency|**tinyint**|Тип частоты репликации:<br /><br /> **0** = транзакционное<br /><br /> **1** = моментальный снимок|  
|synchronization method|**tinyint**|Режим синхронизации:<br /><br /> **0** = собственная программа для выполнения операций копирования (программа**bcp** )<br /><br /> **1** = символьное групповое копирование<br /><br /> **3** = одновременные. Это означает, что используется собственная операция копирования (программа**bcp**), но таблицы не блокируются во время создания моментального снимка.<br /><br /> **4** = Concurrent_c. Это означает, что используется символьное групповое копирование, но таблицы не блокируются во время создания моментального снимка.|  
|description|**nvarchar(255)**|Дополнительное описание публикации.|  
|immediate_sync|**bit**|Указывает, выполняется ли создание (повторное создание) файлов синхронизации при каждом запуске агента моментальных снимков.|  
|enabled_for_internet|**bit**|Указывает доступность файлов синхронизации для публикации через Интернет по протоколу FTP, а также их доступность для других служб.|  
|allow_push|**bit**|Указывает, разрешена ли для данной публикации принудительная подписка.|  
|allow_pull|**bit**|Указывает, разрешена ли для данной публикации подписка по запросу.|  
|allow_anonymous|**bit**|Указывает, разрешена ли для данной публикации анонимная подписка.|  
|independent_agent|**bit**|Указывает, есть ли у данной публикации изолированный агент распространителя.|  
|immediate_sync_ready|**bit**|Указывает готовность агента моментальных снимков к работе с новыми подписками. Этот аргумент задается только в том случае, если в данной публикации моментальный снимок всегда доступен для новых или повторно инициализированных подписок.|  
|allow_sync_tran|**bit**|Определяет, разрешены ли в публикации немедленно обновляемые подписки.|  
|autogen_sync_procs|**bit**|Указывает, будут ли автоматически создаваться хранимые процедуры для поддержки немедленно обновляемых подписок.|  
|snapshot_jobid|**двоичный (16)**|Идентификатор запланированной задачи.|  
|retention|**int**|Сохраняемый объем изменений данной публикации в часах.|  
|has subscription|**bit**|Указывает, есть ли у публикации активные подписки. **1** означает, что публикация имеет активные подписки, а значение **0** означает, что у публикации нет подписок.|  
|allow_queued_tran|**bit**|Указывает, разрешено ли накопление изменений в подписчике в очереди до тех пор, пока их можно применить к издателю. Если значение **равно 0**, изменения на подписчике не помещаются в очередь.|  
|snapshot_in_defaultfolder|**bit**|Указывает, хранятся ли файлы моментальных снимков в папке по умолчанию. Если значение **равно 0**, файлы моментальных снимков хранились в альтернативном расположении, указанном *alternate_snapshot_folder*. Если значение равно **1**, файлы моментальных снимков можно найти в папке по умолчанию.|  
|alt_snapshot_folder|**nvarchar(255)**|Указывает местоположение альтернативной папки для моментального снимка.|  
|pre_snapshot_script|**nvarchar(255)**|Задает указатель на расположение файла **SQL** . Если моментальный снимок применяется на подписчике, то агент распространителя запускает предварительный скрипт моментального снимка до выполнения скриптов реплицируемых объектов.|  
|post_snapshot_script|**nvarchar(255)**|Задает указатель на расположение файла **SQL** . Агент распространителя запускает заключительный скрипт после применения скриптов и данных всех реплицируемых объектов во время первоначальной синхронизации.|  
|compress_snapshot|**bit**|Указывает, что моментальный снимок, записываемый в *alt_snapshot_folder* расположение, должен быть сжат в [!INCLUDE[msCoName](../../includes/msconame-md.md)] формате CAB. значение **0** указывает, что моментальный снимок не будет сжиматься.|  
|ftp_address|**sysname**|Сетевой адрес службы FTP для распространителя. Указывает расположение файлов моментальных снимков публикаций для агента распространителя или агента слияния подписчика.|  
|ftp_port|**int**|Номер порта службы FTP для распространителя.|  
|ftp_subdirectory|**nvarchar(255)**|Указывает расположение файлов моментальных снимков для агента распространителя или агента слияния данного подписчика, если публикация поддерживает распространение моментальных снимков с помощью FTP.|  
|ftp_login|**sysname**|Имя пользователя для подключения к службе FTP.|  
|allow_dts|**bit**|Указывает, что в публикации разрешены преобразования данных. **0** указывает, что преобразование DTS не разрешено.|  
|allow_subscription_copy|**bit**|Указывает, разрешено ли копирование баз данных подписки, подписанных на данную публикацию. **0** означает, что копирование запрещено.|  
|centralized_conflicts|**bit**|Определяет, хранятся ли на издателе конфликтные записи.<br /><br /> **0** = конфликтные записи хранятся как на издателе, так и на подписчике, вызвавшем конфликт.<br /><br /> **1** = конфликтующие записи хранятся на издателе.|  
|conflict_retention|**int**|Задает срок хранения конфликтных записей в днях.|  
|conflict_policy|**int**|Задает политику устранения конфликтов при обновлении подписчика посредством очередей. Может принимать одно из следующих значений:<br /><br /> **1** = побеждает конфликт с издателем.<br /><br /> **2** = конфликт побеждает подписчиком.<br /><br /> **3** = подписка повторно инициализирована.|  
|queue_type||Задает используемый тип очереди. Может принимать одно из следующих значений:<br /><br /> **MSMQ** = использовать [!INCLUDE[msCoName](../../includes/msconame-md.md)] очередь сообщений для хранения транзакций.<br /><br /> **SQL** = используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения транзакций.<br /><br /> Примечание. Поддержка очереди сообщений была прекращена.|  
|backward_comp_level||Уровень совместимости базы данных. Может иметь одно из следующих значений:<br /><br /> **90**  =  90 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100**  =  100 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|publish_to_AD|**bit**|Указывает, опубликована ли публикация в каталоге [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory. Значение **1** указывает на то, что оно опубликовано, а значение **0** указывает на то, что оно не опубликовано.|  
|allow_initialize_from_backup|**bit**|Показывает, может ли подписчик инициализировать подписку на эту публикацию из резервной копии, а не из исходного моментального снимка. **1** означает, что подписки можно инициализировать из резервной копии, а **0** — нет. Дополнительные сведения см. в разделе [Инициализация транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md) подписчика транзакций без моментального снимка.|  
|replicate_ddl|**int**|Указывает, поддерживается ли для публикации репликация схемы. **1** указывает, что инструкции языка описания данных DDL, выполняемые на издателе, реплицируются, а **0** означает, что инструкции DDL не реплицируются. Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).|  
|enabled_for_p2p|**int**|Указывает, может ли публикация использоваться в одноранговой топологии репликации. значение **1** указывает, что публикация поддерживает одноранговую репликацию. Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
|publish_local_changes_only|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|enabled_for_het_sub|**int**|Указывает, поддерживает ли публикация подписчиков, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение **1** означает, что подписчики, отличные от, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются. Значение **0** означает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются только подписчики. Дополнительные сведения см. в статье [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).|  
|enabled_for_p2p_conflictdetection|**int**|Определяет, будет ли агент распространителя обнаруживать конфликты публикации, разрешенной для одноранговой репликации. Значение **1** означает, что конфликты обнаруживаются. Дополнительные сведения см. в разделе [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|originator_id|**int**|Указывает идентификатор в одноранговой топологии. Этот идентификатор используется для обнаружения конфликтов, если **enabled_for_p2p_conflictdetection** имеет значение **1**. Список использованных идентификаторов запросите в системной таблице [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) .|  
|p2p_continue_onconflict|**int**|Указывает, продолжает ли агент распространителя обрабатывать изменения при обнаружении конфликта. Значение **1** означает, что агент продолжит обрабатывать изменения.<br /><br /> ** \* \* Внимание \* ! \* ** рекомендуется использовать значение по умолчанию **0**. Если этот параметр имеет значение **1**, агент распространения пытается выполнить согласование данных в топологии, применяя конфликтующую строку из узла с НАИБОЛЬШим идентификатором инициатора. Этот метод не гарантирует конвергенции. После обнаружения конфликта следует убедиться, что топология остается согласованной. Дополнительные сведения см. в подразделе «Обработка конфликтов» раздела [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|allow_partition_switch|**int**|Указывает, будет ли ALTER TABLE... Операторы SWITCH можно выполнять в опубликованной базе данных. Дополнительные сведения см. в статье [Replicate Partitioned Tables and Indexes](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md) (Репликация секционированных таблиц и индексов).|  
|replicate_partition_switch|**int**|Указывает, будет ли ALTER TABLE... Инструкции SWITCH, которые выполняются в опубликованной базе данных, должны реплицироваться на подписчики. Этот параметр допустим, только если *allow_partition_switch* имеет значение **1**.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_helppublication используется при репликации моментальных снимков и транзакций.  
  
 Процедура sp_helppublication возвращает сведения обо всех публикациях, которые принадлежат пользователю, выполняющему эту процедуру.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_helppublication](../../relational-databases/replication/codesnippet/tsql/sp-helppublication-trans_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Процедуру sp_helppublication могут выполнять только члены предопределенной роли сервера sysadmin на издателе, члены предопределенной роли базы данных db_owner в базе данных публикации, а также пользователи из списка доступа к публикации (PAL).  
  
 Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, не являющегося издателем, только члены предопределенной роли сервера sysadmin на распространителе или члены предопределенной роли базы данных db_owner в базе данных распространителя или пользователи в списке доступа к публикации могут выполнять sp_helppublication.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
