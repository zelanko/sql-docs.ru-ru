---
description: MSqreader_agents (Transact-SQL)
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
ms.openlocfilehash: 10ed60edbbbe2e94e09a9205d34f856cee42c687
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492780"
---
# <a name="msqreader_agents-transact-sql"></a>MSqreader_agents (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSqreader_agents** содержит по одной строке для каждого агент чтения очереди, выполняемого на локальном распространителе. Эта таблица хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента чтения очереди.|  
|**name**|**nvarchar (100)**|Имя агента чтения очереди.|  
|**job_id**|**двоичный (16)**|Уникальный ИДЕНТИФИКАЦИОНный номер задания из таблицы **sysjobs** .|  
|**profile_id**|**int**|Идентификатор профиля из таблицы **MSagent_profiles** .|  
|**job_step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором запущен агент.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
