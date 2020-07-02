---
title: MSqreader_agents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSqreader_agents_TSQL
- MSqreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_agents system table
ms.assetid: dfa1f45e-c531-4385-a097-0a9edd1d7eab
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c3919d40f7c1d52125f071f96844f6881fac955f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751589"
---
# <a name="msqreader_agents-transact-sql"></a>MSqreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSqreader_agents** содержит по одной строке для каждого агент чтения очереди, выполняемого на локальном распространителе. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента чтения очереди.|  
|**name**|**nvarchar (100)**|Имя агента чтения очереди.|  
|**job_id**|**двоичный (16)**|Уникальный ИДЕНТИФИКАЦИОНный номер задания из таблицы **sysjobs** .|  
|**profile_id**|**int**|Идентификатор профиля из таблицы **MSagent_profiles** .|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором запущен агент.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
