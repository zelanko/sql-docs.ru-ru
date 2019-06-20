---
title: dbo.sysjobschedules (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d055e9b76d248319bddb37241b1b79428ee5f3b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470812"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит данные расписания для заданий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
> **ПРИМЕЧАНИЕ.** **Sysjobschedules** таблица обновляется каждые 20 минут, которые могут влиять на значения, возвращаемые методом **sp_help_jobschedule** хранимой процедуры.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификатор расписания.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**next_run_date**|**int**|Следующая дата выполнения задания по расписанию. Формат даты установлен как: ГГГГMMДД.|  
|**next_run_time**|**int**|Время выполнения задания по расписанию. Формат времени ЧЧMMСС с использованием интервала отсчета времени 24 часа.|  
  
## <a name="see-also"></a>См. также  
 [dbo.sysschedules &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
