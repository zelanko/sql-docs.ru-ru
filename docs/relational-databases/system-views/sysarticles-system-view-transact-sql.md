---
title: sysarticles (Системное представление) (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysarticles
- sysarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticles view
ms.assetid: 18f8c9b3-cab7-4e8f-8754-11ac38c3f789
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2165a1e6909e8c02468a89bf18a0fe9cdb280c56
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysarticles-system-view-transact-sql"></a>sysarticles (системное представление) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticles** представления отображаются свойства статьи. Это представление хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Столбец идентификаторов, в котором хранится уникальный идентификатор статьи.|  
|**creation_script**|**nvarchar(255)**|Скрипт схемы для статьи.|  
|**del_cmd**|**nvarchar(255)**|Команда для выполнения после инструкции DELETE; в ином случае строится на основе журнала.|  
|**Описание**|**nvarchar(255)**|Описание статьи.|  
|**dest_table**|**sysname**|Имя целевой таблицы.|  
|**фильтр**|**int**|Идентификатор хранимой процедуры, используемый для горизонтального секционирования.|  
|**filter_clause**|**ntext**|Предложение WHERE для статьи, используемое при горизонтальной фильтрации.|  
|**ins_cmd**|**nvarchar(255)**|Команда для выполнения после инструкции INSERT; иначе строится на основе журнала.|  
|**name**|**sysname**|Имя, ассоциированное со статьей, уникальное внутри публикации.|  
|**objID**|**int**|Идентификатор объекта опубликованной таблицы.|  
|**pubid**|**int**|Идентификатор публикации, к которой принадлежит статья.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE или TRUNCATE:<br /><br /> **0** = none.<br /><br /> **1** = DROP.<br /><br /> **2** = УДАЛЕНИЕ.<br /><br /> **3** = TRUNCATE.|  
|**status**|**tinyint**|Битовая маска параметров и состояния статьи, которая может быть результатом операции логического ИЛИ, проведенной над одним или несколькими из этих значений:<br /><br /> **1** = статья активна.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> **24** = оба включить имя столбца в операторы INSERT и использовать параметризованные инструкции.<br /><br /> **64** = горизонтальная секция статьи, определенных трансформируемой подпиской.<br /><br /> Например, активной статье используются параметризованные инструкции будет иметь значение **17** в этом столбце. Значение **0** означает, что статья неактивна и никакие дополнительные свойства определяются.|  
|**sync_objid**|**int**|Идентификатор таблицы или представления, которое является определением статьи.|  
|**type**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.<br /><br /> **3** = на основе журнала статья с фильтрацией вручную.<br /><br /> **5** = на основе журнала статья с представлением вручную.<br /><br /> **7** = на основе журнала статья с фильтрацией вручную и представлением вручную.<br /><br /> **8** = выполнение хранимой процедуры.<br /><br /> **24** = Выполнение сериализуемой хранимой процедуры.<br /><br /> **32** = хранимая процедура (только схема).<br /><br /> **64** = представление (только схема).<br /><br /> **128** = функция (только схема).|  
|**upd_cmd**|**nvarchar(255)**|Команда, которая должна быть выполнена после инструкции UPDATE; в ином случае она строится на основе журнала.|  
|**schema_option**|**binary(8)**|Битовая маска параметров формирования схемы для статьи, указывающая, какие части схемы статьи назначены для доставки подписчику. Дополнительные сведения о параметрах схемы см. в статье [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).|  
|**dest_owner**|**sysname**|Владелец таблицы в целевой базе данных.|  
|**ins_scripting_proc**|**int**|Зарегистрированная пользовательская хранимая процедура или скрипт, выполняющиеся при репликации инструкции INSERT.|  
|**del_scripting_proc**|**int**|Зарегистрированная пользовательская хранимая процедура или скрипт, выполняющиеся при репликации инструкции DELETE.|  
|**upd_scripting_proc**|**int**|Зарегистрированная пользовательская хранимая процедура или скрипт, выполняющиеся при репликации инструкции UPDATE.|  
|**custom_script**|**nvarchar(2048)**|Зарегистрированная пользовательская хранимая процедура или скрипт, выполняющиеся в конце триггера DDL.|  
|**fire_triggers_on_snapshot**|**бит**|Показывает, выполняются ли реплицированные триггеры в момент, когда делается моментальный снимок. Может принимать следующие значения:<br /><br /> **0** = триггеры не выполняются.<br /><br /> **1** = триггеры выполняются.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
