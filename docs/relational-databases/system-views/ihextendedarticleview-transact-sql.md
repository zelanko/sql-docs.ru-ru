---
title: "IHextendedArticleView (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- IHextendedArticleView_TSQL
- IHextendedArticleView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedArticleView view
ms.assetid: 19ef0a12-3214-4bb0-9c25-a665897e65a2
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 413a95e5d39b5a335381f25a8214df9a0b3be779
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="ihextendedarticleview-transact-sql"></a>IHextendedArticleView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHextendedArticleView** отображает сведения о статьи в публикации, отличные от SQL Server. Это представление хранится в **распространения** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Уникальный идентификатор издателя.|  
|**publication_id**|**int**|Уникальный идентификатор публикации.|  
|**в статье**|**sysname**|Имя статьи.|  
|**destination_object**|**sysname**|Имя объекта, опубликованного на стороне подписчика.|  
|**source_owner**|**sysname**|Владелец объекта, опубликованного на стороне издателя.|  
|**source_object**|**sysname**|Имя объекта, опубликованного на стороне издателя.|  
|**Описание**|**nvarchar(255)**|Описание статьи.|  
|**creation_script**|**nvarchar(255)**|Скрипт создания схемы для статьи.|  
|**del_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции DELETE.|  
|**фильтр**|**int**|Идентификатор хранимой процедуры, с помощью которого определяется горизонтальная секция.|  
|**filter_clause**|**ntext**|Предложение WHERE, которое применяется для горизонтальной фильтрации статьи.|  
|**ins_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции INSERT.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE или TRUNCATE:<br /><br /> **0** = none.<br /><br /> **1** = DROP.<br /><br /> **2** = УДАЛЕНИЕ.<br /><br /> **3** = TRUNCATE.|  
|**status**|**tinyint**|Битовая маска параметров и состояния статьи, которая может быть результатом операции логического ИЛИ, проведенной над одним или несколькими из этих значений:<br /><br /> **1** = статья активна.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> **24** = оба включить имя столбца в операторы INSERT и использовать параметризованные инструкции.<br /><br /> Например, активной статье используются параметризованные инструкции будет иметь значение **17** в этом столбце. Значение **0** означает, что статья неактивна и никакие дополнительные свойства определяются.|  
|**type**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.<br /><br /> **3** = на основе журнала статья с фильтрацией вручную.<br /><br /> **5** = на основе журнала статья с представлением вручную.<br /><br /> **7** = на основе журнала статья с фильтрацией вручную и представлением вручную.|  
|**upd_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции UPDATE.|  
|**schema_option**|**binary**|Указывает, что будет выписано. В разделе [sp_addarticle &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) список поддерживаемых параметров схемы.|  
|**dest_owner**|**sysname**|Владелец объекта, опубликованного в целевой базе данных.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
