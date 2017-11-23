---
title: "sysdbmaintplan_jobs (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_jobs
- sysdbmaintplan_jobs_TSQL
dev_langs: TSQL
helpviewer_keywords: sysdbmaintplan_jobs system table
ms.assetid: bc65cd70-6ef2-4c17-be11-877ecf4efe50
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a10398311460d0e002c8adf059a1887c7d0d81af
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdbmaintplanjobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Эта таблица включена в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы сохранить существующие сведения по экземплярам, обновленным с предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет содержимое этой таблицы. Эта таблица хранится в **msdb** базы данных.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|Идентификатор плана обслуживания базы данных.|  
|**Аргумент job_id**|**uniqueidentifier**|Идентификатор задания, связанного с планом обслуживания базы данных.|  
  
  
