---
title: "dbo.sysjobstepslogs (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- dbo.sysjobstepslogs_TSQL
- sysjobstepslogs_TSQL
- sysjobstepslogs
- dbo.sysjobstepslogs
dev_langs: TSQL
helpviewer_keywords: sysjobstepslogs system table
ms.assetid: 128c25db-0b71-449d-bfb2-38b8abcf24a0
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 050feecde1f82ca8962552744e2fc2d43d28bd4c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobstepslogs-transact-sql"></a>dbo.sysjobstepslogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит журнал шагов задания для всех шагов задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые настроены для записи выхода шага задания в таблицу. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**log_id**|**int**|Идентификатор журнала шагов задания.|  
|**журнал**|**nvarchar(max)**|Содержимое журнала шагов задания.|  
|**date_created**|**datetime**|Дата и время создания журнала шагов задания.|  
|**date_modified**|**datetime**|Дата и время последнего изменения журнала шагов задания.|  
|**log_size**|**int**|Размер журнала шагов задания в байтах.|  
|**step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания.|  
  
## <a name="see-also"></a>См. также:  
 [sp_help_jobsteplog &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [sp_delete_jobsteplog &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)  
  
  
