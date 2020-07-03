---
title: MSmerge_agents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_agents
- MSmerge_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_agents system table
ms.assetid: 639d2ebb-2c37-4fe0-b14b-1637bc5fc221
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8ffc2075f3994ec24339cc74e0d87085679e379c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889900"
---
# <a name="msmerge_agents-transact-sql"></a>MSmerge_agents (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSmerge_agents** содержит по одной строке для каждой агент слияния, выполняемой на подписчике. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента слияния.|  
|**name**|**nvarchar (100)**|Имя агента слияния.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика.|  
|**subscriber_db**|**sysname**|Имя базы данных подписки.|  
|**local_job**|**bit**|Показывает, есть ли задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальном распространителе.|  
|**job_id**|**двоичный (16)**|Идентификационный номер задания.|  
|**profile_id**|**int**|Идентификатор конфигурации из таблицы **MSagent_profiles** .|  
|**anonymous_subid**|**uniqueidentifier**|Идентификатор анонимного агента.|  
|**subscriber_name**|**sysname**|Имя подписчика.|  
|**creation_date**|**datetime**|Дата и время, когда был создан агент распространителя или агент слияния.|  
|**offload_enabled**|**bit**|Указывает на то, что агент может быть активирован удаленно.<br /><br /> **0** указывает, что агент нельзя активировать удаленно.<br /><br /> **1** указывает, что агент будет активирован удаленно и на удаленном компьютере, указанном в свойстве offload_server.|  
|**offload_server**|**sysname**|Указывает сетевое имя сервера, используемого для удаленной активации агента.|  
|**sid**|**varbinary(85)**|Идентификатор безопасности (SID) агента распространителя или агента слияния при первом выполнении.|  
|**subscriber_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к подписчику. Предусмотрены следующие режимы:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Проверка подлинности Windows.|  
|**subscriber_login**|**sysname**|Имя входа для подключения к подписчику.|  
|**subscriber_password**|**nvarchar (524)**|Зашифрованное значение пароля, используемого для подключения к подписчику.|  
|**publisher_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к издателю, может принимать одно из следующих значений:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Проверка подлинности Windows.|  
|**publisher_login**|**sysname**|Имя входа, используемое для соединения с издателем.|  
|**publisher_password**|**nvarchar (524)**|Зашифрованное значение пароля, используемое для соединения с издателем.|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором запущен агент.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
