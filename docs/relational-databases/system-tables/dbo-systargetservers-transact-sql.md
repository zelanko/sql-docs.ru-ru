---
title: dbo.systargetservers (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c8297c02d66671ea41b8a2dae4462514d4ef2fe4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783522"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Записи, занесенные целевыми серверами в этот многосерверный операционный домен.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор сервера.|  
|**server_name**|**sysname**|Имя сервера.|  
|**расположение**|**Nvarchar(200)**|Расположение указанного целевого сервера.|  
|**time_zone_adjustment**|**int**|Интервал смещения времени, в часах, от среднего времени по Гринвичу (GMT).|  
|**enlist_date**|**datetime**|Дата и время, когда указанный сервер был занесен в список.|  
|**last_poll_date**|**datetime**|Дата и время, что указанный целевой сервер последний опрос к многосерверной **sysdownloadlist** системная таблица, для запуска заданий.|  
|**status**|**int**|Состояние целевого сервера:<br /><br /> **1** = норм.<br /><br /> **2** = ожидание повторной синхронизации<br /><br /> **4** = возможен режим вне сети|  
|**local_time_at_last_poll**|**datetime**|Дата и время последнего обращения к целевому серверу за операциями заданий.|  
|**enlisted_by_nt_user**|**Nvarchar(100)**|Имя пользователя, выполняющего **sp_msx_enlist** на целевом сервере.|  
|**poll_internal**|**int**|Количество секунд, которое должно пройти, прежде чем целевой сервер обратится к главному серверу за новыми инструкциями по загрузке.|  
  
  
