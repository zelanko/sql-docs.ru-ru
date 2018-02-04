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
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 272a950b77f541172b3c76ce4b5d597b9e908dee
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит данные расписания для заданий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
> **Примечание:** **sysjobschedules** таблица обновляется каждые 20 минут, что может повлиять на значения, возвращаемые методом **sp_help_jobschedule** хранимой процедуры.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификатор расписания.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**next_run_date**|**int**|Следующая дата выполнения задания по расписанию. Формат даты установлен как: ГГГГMMДД.|  
|**next_run_time**|**int**|Время выполнения задания по расписанию. Формат времени ЧЧMMСС с использованием интервала отсчета времени 24 часа.|  
  
## <a name="see-also"></a>См. также  
 [dbo.sysschedules &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
