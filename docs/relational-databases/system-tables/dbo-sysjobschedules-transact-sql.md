---
title: dbo. sysjobschedules (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: a7f2dfc6196bfba6c274eb45a45745159447cc39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061183"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит данные расписания для заданий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в базе данных **msdb** .  
  
> **Примечание.** Таблица **sysjobschedules** обновляется каждые 20 минут, что может повлиять на значения, возвращаемые хранимой процедурой **sp_help_jobschedule** .  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификатор расписания.|  
|**job_id**|**UNIQUEIDENTIFIER**|Идентификатор задания.|  
|**next_run_date**|**int**|Следующая дата выполнения задания по расписанию. Формат даты установлен как: ГГГГMMДД.|  
|**next_run_time**|**int**|Время выполнения задания по расписанию. Формат времени ЧЧMMСС с использованием интервала отсчета времени 24 часа.|  
  
## <a name="see-also"></a>См. также:  
 [dbo. sysschedules &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
