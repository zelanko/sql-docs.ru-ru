---
title: dbo.cdc_jobs (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1ea10a7d9959fa29367e69cfc2d5831ae44dd292
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258901"
---
# <a name="dbocdcjobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Хранит параметры конфигурации системы отслеживания измененных данных для заданий отслеживания и очистки. Эта таблица хранится в **msdb**.  
  
 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных, в которой выполняется задание.|  
|**job_type**|**nvarchar(20)**|Тип задания — «capture» или «cleanup».|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания.|  
|**maxtrans**|**int**|Максимальное количество транзакций, обрабатываемое в каждом цикле просмотра.<br /><br /> **maxtrans** допустим только для заданий записи.|  
|**maxscans**|**int**|Максимальное количество циклов просмотра, выполняемых для извлечения всех строк из журнала.<br /><br /> **maxscans** допустим только для заданий записи.|  
|**Непрерывные**|**бит**|Флаг, указывающий, следует ли выполнять задание записи непрерывно (1) или запускать однократно (0). Дополнительные сведения см. в разделе [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **непрерывные** допустим только для заданий записи.|  
|**pollingInterval**|**bigint**|Число секунд между циклами просмотра журнала.<br /><br /> **pollingInterval** допустим только для заданий записи.|  
|**Хранения**|**bigint**|Число минут, в течение которого строки изменений нужно хранить в таблицах изменений.<br /><br /> **хранения** допустим только для заданий очистки.|  
|**Пороговое значение**|**bigint**|Максимальное число записей, подлежащих удалению, которые могут быть удалены с помощью одной инструкции при очистке.|  
  
## <a name="see-also"></a>См. также  
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sys.sp_cdc_change_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sys.sp_cdc_help_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sys.sp_cdc_drop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
