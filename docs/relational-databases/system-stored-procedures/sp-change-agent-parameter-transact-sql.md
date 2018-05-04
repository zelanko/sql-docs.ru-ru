---
title: Хранимая процедура sp_change_agent_parameter (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 57a983075bd83d60269cb293be7d2d7f200a2b95
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spchangeagentparameter-transact-sql"></a>Хранимая процедура sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменения параметра профиля агента репликации хранятся в [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) системной таблицы. Эта хранимая процедура выполняется на распространителе в любой базе данных с запущенным агентом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@profile_id=**] *profile_id*,  
 Идентификатор профиля. *profile_id* — **int**, не имеет значения по умолчанию.  
  
 [  **@parameter_name=**] **"***parameter_name***"**  
 Имя параметра. *имя_параметра* — **sysname**, не имеет значения по умолчанию. Для системных профилей параметры, которые могут быть изменены, зависят от типа агента. Чтобы узнать, какой тип агента, это *profile_id* представляет, найдите *profile_id* столбца в **Msagent_profiles** и посмотрите *agent_type*  значение.  
  
> [!NOTE]  
>  Если параметр поддерживается для данного *agent_type*, но не был определен в профиле агента, возвращается сообщение об ошибке. Чтобы добавить параметр к профилю агента, необходимо выполнить [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 Для агента моментальных снимков (*agent_type*=**1**), если определен в профиле, можно изменить следующие свойства:  
  
-   **70Subscribers**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxNetworkOptimization**  
  
-   **Выходные данные**  
  
-   **OutputVerboseLevel**  
  
-   **Размер_пакета**  
  
-   **queryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **UsePerArticleContentsView**  
  
 Для агента чтения журнала (*agent_type*=**2**), если определен в профиле, можно изменить следующие свойства:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MessageInterval**  
  
-   **Выходные данные**  
  
-   **OutputVerboseLevel**  
  
-   **Размер_пакета**  
  
-   **PollingInterval**  
  
-   **queryTimeout**  
  
-   **ReadBatchSize**  
  
-   **ReadBatchThreshold**  
  
 Для агента распространителя (*agent_type*=**3**), если определен в профиле, можно изменить следующие свойства:  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **CommitBatchThreshold**  
  
-   **FileTransferType**  
  
-   **HistoryVerboseLevel**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **MessageInterval**  
  
-   **Выходные данные**  
  
-   **OutputVerboseLevel**  
  
-   **Размер_пакета**  
  
-   **PollingInterval**  
  
-   **queryTimeout**  
  
-   **QuotedIdentifier**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory**  
  
 Для агента слияния (*agent_type*=**4**), если определен в профиле, можно изменить следующие свойства:  
  
-   **AltSnapshotFolder**  
  
-   **BcpBatchSize**  
  
-   **ChangesPerHistory**  
  
-   **DestThreads**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **DownloadReadChangesPerBatch**  
  
-   **DownloadWriteChangesPerBatch**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **FastRowCount**  
  
-   **FileTransferType**  
  
-   **GenerationChangeThreshold**  
  
-   **HistoryVerboseLevel**  
  
-   **InputMessageFile**  
  
-   **InteractiveResolution**  
  
-   **InterruptOnMessagePattern**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDownloadChanges**  
  
-   **MaxUploadChanges**  
  
-   **MetadataRetentionCleanup**  
  
-   **NumDeadlockRetries**  
  
-   **Выходные данные**  
  
-   **OutputMessageFile**  
  
-   **OutputVerboseLevel**  
  
-   **Размер_пакета**  
  
-   **ParallelUploadDownload**  
  
-   **PauseOnMessagePattern**  
  
-   **PauseTime**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **queryTimeout**  
  
-   **QueueSizeMultiplier**  
  
-   **SrcThreads**  
  
-   **StartQueueTimeout**  
  
-   **SyncToAlternate**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **UploadWriteChangesPerBatch**  
  
-   **UseInprocLoader**  
  
-   **Проверить**  
  
-   **ValidateInterval**  
  
 Для агента чтения очереди (*agent_type*=**9**), если определен в профиле, можно изменить следующие свойства:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **Выходные данные**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **queryTimeout**  
  
-   **ResolverState**  
  
-   **SQLQueueMode**  
  
 Чтобы просмотреть, какие параметры определены для данного профиля, запустите **sp_help_agent_profile** и обратите внимание, *profile_name* связанных с *profile_id*. С помощью соответствующих *profile_id*, затем запустите **sp_help_agent_parameters** , используя *profile_id* для просмотра параметров, связанных с профилем. Параметры могут добавляться к профилю путем выполнения [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 [  **@parameter_value=**] **"***parameter_value***"**  
 Новое значение параметра. *parameter_value* — **nvarchar(255)**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_change_agent_parameter** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **хранимая процедура sp_change_agent_parameter**.  
  
## <a name="see-also"></a>См. также  
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Агент слияния репликации](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
