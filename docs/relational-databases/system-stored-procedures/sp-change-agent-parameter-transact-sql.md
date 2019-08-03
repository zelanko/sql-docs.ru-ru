---
title: sp_change_agent_parameter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd737be5a1e71e46750f6c80fd68ad254cb6436f
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768941"
---
# <a name="spchangeagentparameter-transact-sql"></a>Хранимая процедура sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Изменяет параметр профиля агента репликации, хранящегося в системной таблице [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) . Эта хранимая процедура выполняется на распространителе в любой базе данных с запущенным агентом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_id = ] profile_id,`Идентификатор профиля. *profile_id* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @parameter_name = ] 'parameter_name'`Имя параметра. *parameter_name* имеет тип **sysname**и не имеет значения по умолчанию. Для системных профилей параметры, которые могут быть изменены, зависят от типа агента. Чтобы узнать, какой тип агента представляет этот *profile_id* , найдите столбец *Profile_id* в таблице **Msagent_profiles** и запишите значение *agent_type* .  
  
> [!NOTE]  
>  Если параметр поддерживается для данного *agent_type*, но он не был определен в профиле агента, возвращается ошибка. Чтобы добавить параметр в профиль агента, необходимо выполнить [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 Для агент моментальных снимков (*agent_type*=**1**), если он определен в профиле, можно изменить следующие свойства:  
  
-   **70Subscribers**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxNetworkOptimization значение**  
  
-   **Проверки**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **QueryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **усеперартиклеконтентсвиев**  
  
 Для агент чтения журнала (*agent_type*=**2**), если он определен в профиле, можно изменить следующие свойства:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MessageInterval**  
  
-   **Проверки**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ReadBatchSize**  
  
-   **реадбатчсрешолд**  
  
 Для агент распространения (*agent_type*=**3**), если он определен в профиле, можно изменить следующие свойства:  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **коммитбатчсрешолд**  
  
-   **филетрансфертипе**  
  
-   **HistoryVerboseLevel**  
  
-   **кипаливемессажеинтервал**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **MessageInterval**  
  
-   **Проверки**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **QuotedIdentifier**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory**  
  
 Для агент слияния (*agent_type*=**4**), если он определен в профиле, можно изменить следующие свойства:  
  
-   **AltSnapshotFolder**  
  
-   **BcpBatchSize**  
  
-   **чанжесперхистори**  
  
-   **дестсреадс**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **довнлоадреадчанжеспербатч**  
  
-   **довнлоадвритечанжеспербатч**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **фастровкаунт**  
  
-   **филетрансфертипе**  
  
-   **женератиончанжесрешолд**  
  
-   **HistoryVerboseLevel**  
  
-   **инпутмессажефиле**  
  
-   **интерактивересолутион**  
  
-   **InterruptOnMessagePattern**  
  
-   **кипаливемессажеинтервал**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **максдовнлоадчанжес**  
  
-   **максуплоадчанжес**  
  
-   **метадатаретентионклеануп**  
  
-   **нумдеадлоккретриес**  
  
-   **Проверки**  
  
-   **аутпутмессажефиле**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **ParallelUploadDownload**  
  
-   **паусеонмессажепаттерн**  
  
-   **паусетиме**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **QueryTimeout**  
  
-   **куеуесиземултиплиер**  
  
-   **срксреадс**  
  
-   **StartQueueTimeout**  
  
-   **синктоалтернате**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **уплоадвритечанжеспербатч**  
  
-   **UseInprocLoader**  
  
-   **Проверить**  
  
-   **валидатеинтервал**  
  
 Для агент чтения очереди (*agent_type*=**9**), если он определен в профиле, можно изменить следующие свойства:  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **Проверки**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ресолверстате**  
  
-   **склкуеуемоде**  
  
 Чтобы узнать, какие параметры были определены для данного профиля, выполните **sp_help_agent_profile** и обратите внимание на *profile_name* , связанный с *profile_id*. Используя соответствующий *profile_id*, выполните следующую команду, **sp_help_agent_parameters** с помощью *profile_id* , чтобы просмотреть параметры, связанные с профилем. Параметры можно добавить в профиль, выполнив [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
`[ @parameter_value = ] 'parameter_value'`Новое значение параметра. *parameter_value* имеет тип **nvarchar (255)** и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_change_agent_parameter** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_change_agent_parameter**.  
  
## <a name="see-also"></a>См. также  
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Агент слияния репликации](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [sp_add_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
