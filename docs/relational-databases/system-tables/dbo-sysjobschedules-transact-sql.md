---
title: dbo.sysжобсчедулес (Transact-SQL) | Документация Майкрософт
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1404af2beddd9cd3c5e5c65420cbe248396dd09c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890484"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит данные расписания для заданий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в базе данных **msdb** .  
  
> **Примечание.** Таблица **sysjobschedules** обновляется каждые 20 минут, что может повлиять на значения, возвращаемые хранимой процедурой **sp_help_jobschedule** .  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|Идентификатор расписания.|  
|**job_id**|**uniqueidentifier**|Идентификатор задания.|  
|**next_run_date**|**int**|Следующая дата выполнения задания по расписанию. Формат даты установлен как: ГГГГMMДД.|  
|**next_run_time**|**int**|Время выполнения задания по расписанию. Формат времени ЧЧMMСС с использованием интервала отсчета времени 24 часа.|  
  
## <a name="see-also"></a>См. также  
 [dbo.sysрасписания &#40;&#41;Transact-SQL](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
