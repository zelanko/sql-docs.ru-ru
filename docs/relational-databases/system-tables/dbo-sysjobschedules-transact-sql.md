---
title: "dbo.sysjobschedules (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
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
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 745f3e858a195e2004c3b67e0b3ec973df58a3fb
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит данные расписания для заданий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
> **Примечание:** **sysjobschedules** таблица обновляется каждые 20 минут, что может повлиять на значения, возвращаемые методом **sp_help_jobschedule** хранимой процедуры.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификатор расписания.|  
|**Аргумент job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**next_run_date**|**int**|Следующая дата выполнения задания по расписанию. Формат даты установлен как: ГГГГMMДД.|  
|**next_run_time**|**int**|Время выполнения задания по расписанию. Формат времени ЧЧMMСС с использованием интервала отсчета времени 24 часа.|  
  
## <a name="see-also"></a>См. также:  
 [dbo.sysschedules &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
