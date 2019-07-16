---
title: dbo.sysjobstepslogs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobstepslogs_TSQL
- sysjobstepslogs_TSQL
- sysjobstepslogs
- dbo.sysjobstepslogs
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobstepslogs system table
ms.assetid: 128c25db-0b71-449d-bfb2-38b8abcf24a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: fec1b43f3e129a752e79024f3800d6f4fb3fb60a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984925"
---
# <a name="dbosysjobstepslogs-transact-sql"></a>dbo.sysjobstepslogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит журнал шагов задания для всех шагов задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые настроены для записи выхода шага задания в таблицу. Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**log_id**|**int**|Идентификатор журнала шагов задания.|  
|**log**|**nvarchar(max)**|Содержимое журнала шагов задания.|  
|**date_created**|**datetime**|Дата и время создания журнала шагов задания.|  
|**date_modified**|**datetime**|Дата и время последнего изменения журнала шагов задания.|  
|**log_size**|**int**|Размер журнала шагов задания в байтах.|  
|**step_uid**|**uniqueidentifier**|Уникальный идентификатор шага задания.|  
  
## <a name="see-also"></a>См. также  
 [sp_help_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)  
  
  
