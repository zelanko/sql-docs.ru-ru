---
title: "sysextendedarticlesview (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysextendedarticlesview_TSQL
- sysextendedarticlesview
dev_langs:
- TSQL
helpviewer_keywords:
- sysextendedarticlesview view
ms.assetid: 8bdd22f7-c268-49b6-820c-3fe603feb128
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5bb71fcae44867e24b022e187cacfbcddac2ee0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysextendedarticlesview-transact-sql"></a>sysextendedarticlesview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysextendedarticlesview** представление предоставляет сведения об опубликованных статьях. Это представление хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Столбец идентификаторов, в котором хранится уникальный идентификатор статьи.|  
|**creation_script**|**nvarchar(255)**|Скрипт создания схемы для статьи.|  
|**del_cmd**|**nvarchar(255)**|Команда для выполнения после инструкции DELETE; в ином случае строится на основе журнала.|  
|**Описание**|**nvarchar(255)**|Описание статьи.|  
|**dest_table**|**nvarchar(128)**|Имя целевой таблицы.|  
|**фильтр**|**int**|Идентификатор объекта хранимой процедуры, используемой для горизонтального секционирования.|  
|**filter_clause**|**ntext**|Предложение WHERE для статьи, используемое при горизонтальной фильтрации.|  
|**ins_cmd**|**nvarchar(255)**|Команда, которая должна быть выполнена после инструкции INSERT.|  
|**name**|**nvarchar(128)**|Имя, ассоциированное со статьей, уникальное внутри публикации.|  
|**objid**|**int**|Идентификатор объекта опубликованной таблицы.|  
|**pubid**|**int**|Идентификатор публикации, к которой принадлежит статья.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE или TRUNCATE:<br /><br /> **0** = none.<br /><br /> **1** = DROP.<br /><br /> **2** = УДАЛЕНИЕ.<br /><br /> **3** = TRUNCATE.|  
|**status**|**int**|Битовая маска параметров и состояния статьи, которая может быть результатом операции логического ИЛИ, проведенной над одним или несколькими из этих значений:<br /><br /> **1** = статья активна.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> **24** = оба включить имя столбца в операторы INSERT и использовать параметризованные инструкции.<br /><br /> Например, для активной статьи, в которой используются параметризованные инструкции, значение данного столбца должно быть равно 17. Значение 0 указывает, что статья неактивна и никакие дополнительные свойства не определены.|  
|**sync_objid**|**int**|Идентификатор таблицы или представления, которое является определением статьи.|  
|**type**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.<br /><br /> **3** = на основе журнала статья с фильтрацией вручную.<br /><br /> **5** = на основе журнала статья с представлением вручную.<br /><br /> **7** = на основе журнала статья с фильтрацией вручную и представлением вручную.|  
|**upd_cmd**|**nvarchar(255)**|Команда, которая должна быть выполнена после инструкции UPDATE; в ином случае она строится на основе журнала.|  
|**schema_option**|**binary**|Указывает, какие свойства опубликованного объекта вносятся в сценарий моментального снимка. Список поддерживаемых параметров схемы см. в разделе [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).|  
|**dest_owner**|**nvarchar(128)**|Владелец таблицы в целевой базе данных.|  
|**ins_scripting_proc**|**int**|Идентификатор объекта пользовательской хранимой процедуры или скрипта, выполняемых при репликации инструкции INSERT.|  
|**del_scripting_proc**|**int**|Идентификатор объекта пользовательской хранимой процедуры или скрипта, выполняемых при репликации инструкции DELETE.|  
|**upd_scripting_proc**|**int**|Идентификатор объекта пользовательской хранимой процедуры или скрипта, выполняемых при репликации инструкции UPDATE.|  
|**custom_script**|**int**|Идентификатор объекта пользовательского скрипта или процедуры, выполняемых после выполнения триггера DDL.|  
|**fire_triggers_on_snapshot**|**int**|Показывает, выполняются ли реплицированные триггеры в момент, когда делается моментальный снимок. Может принимать следующие значения:<br /><br /> **0** = триггеры не выполняются.<br /><br /> **1** = триггеры выполняются.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
