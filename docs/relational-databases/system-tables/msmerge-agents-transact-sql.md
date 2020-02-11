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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 980ecd00a07e1119a64552a3f4c903434fd09029
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106446"
---
# <a name="msmerge_agents-transact-sql"></a>MSmerge_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSmerge_agents** содержит по одной строке для каждой агент слияния, выполняемой на подписчике. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**удостоверения**|**int**|Идентификатор агента слияния.|  
|**name**|**nvarchar (100)**|Имя агента слияния.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**имеет sysname**|Имя базы данных издателя.|  
|**публикации**|**имеет sysname**|Имя публикации.|  
|**subscriber_id**|**smallint**|Идентификатор подписчика.|  
|**subscriber_db**|**имеет sysname**|Имя базы данных подписки.|  
|**local_job**|**bit**|Показывает, есть ли задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальном распространителе.|  
|**job_id**|**двоичный (16)**|Идентификационный номер задания.|  
|**profile_id**|**int**|Идентификатор конфигурации из таблицы **MSagent_profiles** .|  
|**anonymous_subid**|**UNIQUEIDENTIFIER**|Идентификатор анонимного агента.|  
|**subscriber_name**|**имеет sysname**|Имя подписчика.|  
|**creation_date**|**datetime**|Дата и время, когда был создан агент распространителя или агент слияния.|  
|**offload_enabled**|**bit**|Указывает на то, что агент может быть активирован удаленно.<br /><br /> **0** указывает, что агент нельзя активировать удаленно.<br /><br /> **1** указывает, что агент будет активирован удаленно и на удаленном компьютере, указанном в свойстве offload_server.|  
|**offload_server**|**имеет sysname**|Указывает сетевое имя сервера, используемого для удаленной активации агента.|  
|**sid**|**varbinary (85)**|Идентификатор безопасности (SID) агента распространителя или агента слияния при первом выполнении.|  
|**subscriber_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к подписчику. Предусмотрены следующие режимы:<br /><br /> **** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)] Проверка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подлинности.<br /><br /> **** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] проверка подлинности Windows.|  
|**subscriber_login**|**имеет sysname**|Имя входа для подключения к подписчику.|  
|**subscriber_password**|**nvarchar (524)**|Зашифрованное значение пароля, используемого для подключения к подписчику.|  
|**publisher_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к издателю, может принимать одно из следующих значений:<br /><br /> **** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)] Проверка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подлинности.<br /><br /> **** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] проверка подлинности Windows.|  
|**publisher_login**|**имеет sysname**|Имя входа, используемое для соединения с издателем.|  
|**publisher_password**|**nvarchar (524)**|Зашифрованное значение пароля, используемое для соединения с издателем.|  
|**job_step_uid**|**UNIQUEIDENTIFIER**|Уникальный идентификатор шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором запущен агент.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
