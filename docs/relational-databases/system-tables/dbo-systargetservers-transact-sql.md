---
title: "dbo.systargetservers (Transact-SQL) | Документы Microsoft"
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
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs: TSQL
helpviewer_keywords: systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c46f7d8861376b5bc8a25f4befc3c46dad31342
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Записи, занесенные целевыми серверами в этот многосерверный операционный домен.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор сервера.|  
|**имя_сервера**|**sysname**|Имя сервера.|  
|**расположение**|**nvarchar(200)**|Расположение указанного целевого сервера.|  
|**time_zone_adjustment**|**int**|Интервал смещения времени, в часах, от среднего времени по Гринвичу (GMT).|  
|**enlist_date**|**datetime**|Дата и время, когда указанный сервер был занесен в список.|  
|**last_poll_date**|**datetime**|Даты и времени последнего опроса указанный целевой сервер к многосерверной **sysdownloadlist** системной таблицы, для запуска заданий.|  
|**status**|**int**|Состояние целевого сервера:<br /><br /> **1** = обычный<br /><br /> **2** = ожидание повторной синхронизации<br /><br /> **4** = возможен режим вне сети|  
|**local_time_at_last_poll**|**datetime**|Дата и время последнего обращения к целевому серверу за операциями заданий.|  
|**enlisted_by_nt_user**|**nvarchar(100)**|Имя пользователя, выполняющего **sp_msx_enlist** на целевом сервере.|  
|**poll_internal**|**int**|Количество секунд, которое должно пройти, прежде чем целевой сервер обратится к главному серверу за новыми инструкциями по загрузке.|  
  
  
