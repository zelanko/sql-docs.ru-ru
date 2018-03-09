---
title: "MSdistribution_agents (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/28/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistribution_agents_TSQL
- MSdistribution_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_agents system table
ms.assetid: 0e8f0653-1351-41d1-95d2-40f6d5a050ca
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f71cc1c79f36dcc14980ce4a04b1079fba6a8ee9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="msdistributionagents-transact-sql"></a>MSdistribution_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_agents** содержит по одной строке для каждого агента распространителя, запущенного на локальном распространителе. Эта таблица хранится в базе данных распространителя.  
  
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
|**local_job**|**bit**|Указывает, существует ли задание агента SQL Server на локальном распространителе.|  
|**Аргумент job_id**|**binary(16)**|Идентификационный номер задания.|  
|**subscription_guid**|**binary(16)**|Идентификатор подписок данного агента.|  
|**profile_id**|**int**|Идентификатор конфигурации из [MSagent_profiles &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) таблицы.|  
|**anonymous_subid**|**uniqueidentifier**|Идентификатор анонимного агента.|  
|**subscriber_name**|**sysname**|Имя подписчика, указывается только для анонимных агентов.|  
|**virtual_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**anonymous_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**creation_date**|**datetime**|Дата и время, когда был создан агент распространителя или агент слияния.|  
|**queue_id**|**sysname**|Идентификатор для поиска очереди для очереди обновляемых подписок. Для подписок, не использующих очереди, значение равно NULL. Для публикаций на основе очереди сообщений [!INCLUDE[msCoName](../../includes/msconame-md.md)] значением является идентификатор GUID, который однозначно идентифицирует очередь, используемую подпиской. Для публикаций в очереди на основе SQL Server, столбец содержит значение **SQL**.<br /><br /> Примечание: С помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] очереди сообщений рекомендуется к использованию и больше не поддерживается.|  
|**queue_status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offload_enabled**|**bit**|Указывает, может ли агент быть активизирован удаленно.<br /><br /> **0** указывает, что агент не может быть активирован удаленно.<br /><br /> **1** указывает, что агент может быть активизирован удаленно и на удаленном компьютере, указанном в *offload_server* свойство.|  
|**offload_server**|**sysname**|Сетевое имя сервера для удаленной активации.|  
|**dts_package_name**|**sysname**|Имя пакета служб DTS. Например, пакет с именем **DTSPub_Package**, укажите `@dts_package_name = N'DTSPub_Package'`.|  
|**dts_package_password**|**nvarchar(524)**|Пароль пакета.|  
|**dts_package_location**|**int**|Местонахождение пакета. Расположение пакета может быть **распространителя** или **подписчика**.|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор безопасности (SID) агента распространителя или агента слияния при первом выполнении.|  
|**queue_server**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**subscriber_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к подписчику. Предусмотрены следующие режимы:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности SQL Server<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверку подлинности Windows.|  
|**subscriber_login**|**sysname**|Имя входа для подключения к подписчику.|  
|**subscriber_password**|**nvarchar(524)**|Зашифрованное значение пароля, используемое для подключения к подписчику.|  
|**reset_partial_snapshot_progress**|**bit**|Установлен, если частично загруженный моментальный снимок будет отменен, затем загружен с самого начала.|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор задания агента SQL Server выполните шаг, на котором запущен агент.|  
|**потоки подписки**|**tinyint**|Устанавливает максимальное число соединений, разрешенных каждому из агентов распространителя для параллельного применения пакетов изменений на подписчике. Поддерживаются значения в диапазоне от 1 до 64.|  
|**оптимизированные для памяти**|**bit**|1 указывает, что подписчик может использоваться для таблиц, оптимизированных для памяти.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
