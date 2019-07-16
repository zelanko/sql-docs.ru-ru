---
title: MSsnapshot_agents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshot_agents
- MSsnapshot_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshot_agents system table
ms.assetid: aeae0a2e-4c21-4c45-be65-1e426fa52bdd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d57700abecccf3dae55289b49d4fd6c1af3e537
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079957"
---
# <a name="mssnapshotagents-transact-sql"></a>MSsnapshot_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshot_agents** таблица содержит по одной строке для каждого агента моментальных снимков, связанных с локальным распространителем. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента моментальных снимков.|  
|**name**|**Nvarchar(100)**|Имя агента моментальных снимков.|  
|**publisher_id**|**smallint**|Идентификатор издателя.|  
|**publisher_db**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**publication_type**|**int**|Тип публикации:<br /><br /> **0** = публикация транзакций.<br /><br /> **1** = моментальный снимок.<br /><br /> **2** = публикация слиянием.|  
|**local_job**|**bit**|Показывает, есть ли задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальном распространителе.|  
|**job_id**|**binary(16)**|Идентификационный номер задания.|  
|**profile_id**|**int**|Идентификатор конфигурации из [MSagent_profiles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md) таблицы.|  
|**dynamic_filter_login**|**sysname**|Значение, используемое для вычисления [SUSER_SNAME &#40;Transact-SQL&#41; ](../../t-sql/functions/suser-sname-transact-sql.md) функции в параметризованных фильтров, которые определяют секцию. Столбец используется для секционированного моментального снимка.|  
|**dynamic_filter_hostname**|**sysname**|Значение, используемое для вычисления [HOST_NAME &#40;Transact-SQL&#41; ](../../t-sql/functions/host-name-transact-sql.md) функции в параметризованных фильтров, которые определяют секцию. Столбец используется для секционированного моментального снимка.|  
|**publisher_security_mode**|**smallint**|Режим безопасности, используемый агентом при подключении к издателю, может принимать одно из следующих значений:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности Windows.|  
|**publisher_login**|**sysname**|Имя входа, используемое для соединения с издателем.|  
|**publisher_password**|**nvarchar(524)**|Зашифрованное значение пароля, используемое для соединения с издателем.|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором запущен агент.|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar(524)**||  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
