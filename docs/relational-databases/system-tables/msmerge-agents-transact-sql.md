---
title: "\"MSmerge_agents\" (Transact-SQL) | Документация Майкрософт"
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_agents
- MSmerge_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_agents system table
ms.assetid: 639d2ebb-2c37-4fe0-b14b-1637bc5fc221
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a8df66853b124d8f6965e9fe46e4e19ec9ff5584
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677812"
---
# <a name="msmergeagents-transact-sql"></a>MSmerge_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_agents** таблица содержит по одной строке для каждого агента слияния на подписчике. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента слияния.|  
|**name**|**Nvarchar(100)**|Имя агента слияния.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**local_job**|**bit**|Показывает, есть ли задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальном распространителе.|  
|**job_id**|**binary(16)**|Идентификационный номер задания.|  
|**profile_id**|**int**|Идентификатор конфигурации из **MSagent_profiles** таблицы.|  
|**anonymous_subid**|**uniqueidentifier**|Идентификатор анонимного агента.|  
|**subscriber_name**|**sysname**|Имя подписчика.|  
|**creation_date**|**datetime**|Дата и время, когда был создан агент распространителя или агент слияния.|  
|**offload_enabled**|**bit**|Указывает на то, что агент может быть активирован удаленно.<br /><br /> **0** указывает агент не может быть активирован удаленно.<br /><br /> **1** указывает, что агент будет активирован удаленно и на удаленном компьютере, указанном в свойстве offload_server.|  
|**offload_server**|**sysname**|Указывает сетевое имя сервера, используемого для удаленной активации агента.|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор безопасности (SID) агента распространителя или агента слияния при первом выполнении.|  
|**subscriber_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к подписчику. Предусмотрены следующие режимы:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности Windows.|  
|**subscriber_login**|**sysname**|Имя входа для подключения к подписчику.|  
|**subscriber_password**|**nvarchar(524)**|Зашифрованное значение пароля, используемого для подключения к подписчику.|  
|**publisher_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к издателю, может принимать одно из следующих значений:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности Windows.|  
|**publisher_login**|**sysname**|Имя входа, используемое для соединения с издателем.|  
|**publisher_password**|**nvarchar(524)**|Зашифрованное значение пароля, используемое для соединения с издателем.|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором запущен агент.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
