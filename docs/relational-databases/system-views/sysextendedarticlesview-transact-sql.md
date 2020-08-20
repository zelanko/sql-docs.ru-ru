---
description: sysextendedarticlesview (Transact-SQL)
title: сисекстендедартиклесвиев (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysextendedarticlesview_TSQL
- sysextendedarticlesview
dev_langs:
- TSQL
helpviewer_keywords:
- sysextendedarticlesview view
ms.assetid: 8bdd22f7-c268-49b6-820c-3fe603feb128
author: stevestein
ms.author: sstein
ms.openlocfilehash: 347d05c4ca4d5c29c04af853581ad02efb287d10
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463863"
---
# <a name="sysextendedarticlesview-transact-sql"></a>sysextendedarticlesview (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Представление **сисекстендедартиклесвиев** содержит сведения о опубликованных статьях. Это представление хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Столбец идентификаторов, в котором хранится уникальный идентификатор статьи.|  
|**creation_script**|**nvarchar(255)**|Скрипт создания схемы для статьи.|  
|**del_cmd**|**nvarchar(255)**|Команда для выполнения после инструкции DELETE; в ином случае строится на основе журнала.|  
|**description**|**nvarchar(255)**|Описание статьи.|  
|**dest_table**|**nvarchar(128)**|Имя целевой таблицы.|  
|**Фильтрация**|**int**|Идентификатор объекта хранимой процедуры, используемой для горизонтального секционирования.|  
|**filter_clause**|**ntext**|Предложение WHERE для статьи, используемое при горизонтальной фильтрации.|  
|**ins_cmd**|**nvarchar(255)**|Команда, которая должна быть выполнена после инструкции INSERT.|  
|**name**|**nvarchar(128)**|Имя, ассоциированное со статьей, уникальное внутри публикации.|  
|**objid**|**int**|Идентификатор объекта опубликованной таблицы.|  
|**pubid**|**int**|Идентификатор публикации, к которой принадлежит статья.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE или TRUNCATE:<br /><br /> **0** = нет.<br /><br /> **1** = удалить.<br /><br /> **2** = удалить.<br /><br /> **3** = усечение.|  
|**status**|**int**|Битовая маска параметров и состояния статьи, которая может быть результатом операции побитового логического ИЛИ над одним или несколькими из следующих значений:<br /><br /> **1** = статья активна.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> **24** = оба значения включают имя столбца в инструкции INSERT и используют параметризованные инструкции.<br /><br /> Например, для активной статьи, в которой используются параметризованные инструкции, значение данного столбца должно быть равно 17. Значение 0 указывает, что статья неактивна и никакие дополнительные свойства не определены.|  
|**sync_objid**|**int**|Идентификатор таблицы или представления, которое является определением статьи.|  
|**type**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.<br /><br /> **3** = статья на основе журнала с ручным фильтром.<br /><br /> **5** = статья на основе журнала с ручным просмотром.<br /><br /> **7** = статья на основе журнала с ручным фильтром и ручным просмотром.|  
|**upd_cmd**|**nvarchar(255)**|Команда, которая должна быть выполнена после инструкции UPDATE; в ином случае она строится на основе журнала.|  
|**schema_option**|**binary**|Указывает, какие свойства опубликованного объекта вносятся в сценарий моментального снимка. Список поддерживаемых параметров схемы см. в разделе [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).|  
|**dest_owner**|**nvarchar(128)**|Владелец таблицы в целевой базе данных.|  
|**ins_scripting_proc**|**int**|Идентификатор объекта пользовательской хранимой процедуры или скрипта, выполняемых при репликации инструкции INSERT.|  
|**del_scripting_proc**|**int**|Идентификатор объекта пользовательской хранимой процедуры или скрипта, выполняемых при репликации инструкции DELETE.|  
|**upd_scripting_proc**|**int**|Идентификатор объекта пользовательской хранимой процедуры или скрипта, выполняемых при репликации инструкции UPDATE.|  
|**custom_script**|**int**|Идентификатор объекта пользовательского скрипта или процедуры, выполняемых после выполнения триггера DDL.|  
|**fire_triggers_on_snapshot**|**int**|Показывает, выполняются ли реплицированные триггеры в момент, когда делается моментальный снимок. Может принимать следующие значения:<br /><br /> **0** = триггеры не выполняются.<br /><br /> **1** = триггеры выполняются.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
