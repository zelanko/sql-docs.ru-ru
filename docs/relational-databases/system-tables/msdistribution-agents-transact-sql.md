---
title: MSdistribution_agents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_agents_TSQL
- MSdistribution_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_agents system table
ms.assetid: 0e8f0653-1351-41d1-95d2-40f6d5a050ca
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 357d0cf774d3e95d700c840f88bb0165bdb9a12f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817165"
---
# <a name="msdistributionagents-transact-sql"></a>MSdistribution_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_agents** таблица содержит по одной строке для каждого агента распространителя, запущенного на локальном распространителе. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента распространителя.|  
|**name**|**nvarchar(100)**|Имя агента распространителя.|  
|**publisher_database_id**|**int**|Идентификатор базы данных издателя.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика, указан только для общеизвестных агентов. Для анонимных агентов этот столбец зарезервирован.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**subscription_type**|**int**|Тип подписки.<br /><br /> **0** = принудительно отправить.<br /><br /> **1** = по запросу.<br /><br /> **2** = анонимная.|  
|**local_job**|**bit**|Указывает, есть ли задание агента SQL Server на локальном распространителе.|  
|**job_id**|**binary(16)**|Идентификационный номер задания.|  
|**subscription_guid**|**binary(16)**|Идентификатор подписок данного агента.|  
|**profile_id**|**int**|Идентификатор конфигурации из [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) таблицы.|  
|**anonymous_subid**|**uniqueidentifier**|Идентификатор анонимного агента.|  
|**subscriber_name**|**sysname**|Имя подписчика, указывается только для анонимных агентов.|  
|**virtual_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**anonymous_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**creation_date**|**datetime**|Дата и время, когда был создан агент распространителя или агент слияния.|  
|**queue_id**|**sysname**|Идентификатор для поиска очереди для очереди обновляемых подписок. Для подписок, не использующих очереди, значение равно NULL. Для публикаций на основе очереди сообщений [!INCLUDE[msCoName](../../includes/msconame-md.md)] значением является идентификатор GUID, который однозначно идентифицирует очередь, используемую подпиской. Для публикаций в очереди на основе SQL Server, столбец содержит значение **SQL**.<br /><br /> Примечание. С помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing устарел и больше не поддерживается.|  
|**queue_status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offload_enabled**|**bit**|Указывает, может ли агент быть активизирован удаленно.<br /><br /> **0** указывает, что агент не может быть активирован удаленно.<br /><br /> **1** указывает, что агент может быть активизирован удаленно и на удаленном компьютере, указанном в *offload_server* свойство.|  
|**offload_server**|**sysname**|Сетевое имя сервера для удаленной активации.|  
|**dts_package_name**|**sysname**|Имя пакета служб DTS. Например, пакет с именем **DTSPub_Package**, укажите `@dts_package_name = N'DTSPub_Package'`.|  
|**dts_package_password**|**nvarchar(524)**|Пароль пакета.|  
|**dts_package_location**|**int**|Местонахождение пакета. Расположение пакета может быть **распространителя** или **подписчика**.|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор безопасности (SID) агента распространителя или агента слияния при первом выполнении.|  
|**queue_server**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**subscriber_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к подписчику. Предусмотрены следующие режимы:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности SQL Server<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности Windows.|  
|**subscriber_login**|**sysname**|Имя входа для подключения к подписчику.|  
|**subscriber_password**|**nvarchar(524)**|Зашифрованное значение пароля, используемое для подключения к подписчику.|  
|**reset_partial_snapshot_progress**|**bit**|Установлен, если частично загруженный моментальный снимок будет отменен, затем загружен с самого начала.|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор задания агента SQL Server шаг, на котором запущен агент.|  
|**SubscriptionStreams**|**tinyint**|Устанавливает максимальное число соединений, разрешенных каждому из агентов распространителя для параллельного применения пакетов изменений на подписчике. Поддерживаются значения в диапазоне от 1 до 64.|  
|**memory_optimized**|**bit**|1 указывает, что подписчик может использоваться для оптимизированных для памяти таблицах.|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar(524)**||  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
