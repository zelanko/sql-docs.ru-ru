---
title: IHextendedArticleView (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHextendedArticleView_TSQL
- IHextendedArticleView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedArticleView view
ms.assetid: 19ef0a12-3214-4bb0-9c25-a665897e65a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0abca8ca826ec986a9cbf71f4fb577291e095e39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029544"
---
# <a name="ihextendedarticleview-transact-sql"></a>IHextendedArticleView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHextendedArticleView** представление отображает сведения о статьях в публикации SQL Server. Это представление хранится в **распространения** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Уникальный идентификатор издателя.|  
|**publication_id**|**int**|Уникальный идентификатор публикации.|  
|**Статья**|**sysname**|Имя статьи.|  
|**destination_object**|**sysname**|Имя объекта, опубликованного на стороне подписчика.|  
|**source_owner**|**sysname**|Владелец объекта, опубликованного на стороне издателя.|  
|**source_object**|**sysname**|Имя объекта, опубликованного на стороне издателя.|  
|**description**|**nvarchar(255)**|Описание статьи.|  
|**creation_script**|**nvarchar(255)**|Скрипт создания схемы для статьи.|  
|**del_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции DELETE.|  
|**фильтр**|**int**|Идентификатор хранимой процедуры, с помощью которого определяется горизонтальная секция.|  
|**filter_clause**|**ntext**|Предложение WHERE, которое применяется для горизонтальной фильтрации статьи.|  
|**ins_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции INSERT.|  
|**pre_creation_cmd**|**tinyint**|Команда, выполняемая перед инструкциями DROP TABLE, DELETE TABLE или TRUNCATE:<br /><br /> **0** = none.<br /><br /> **1** = DROP.<br /><br /> **2** = DELETE.<br /><br /> **3** = TRUNCATE.|  
|**status**|**tinyint**|Битовая маска параметров и состояния статьи, которая может быть результатом операции побитового логического ИЛИ над одним или несколькими из следующих значений:<br /><br /> **1** = статья активна.<br /><br /> **8** = включить имя столбца в инструкции INSERT.<br /><br /> **16** = использовать параметризованные инструкции.<br /><br /> **24** = включить имя столбца в инструкции INSERT и использовать параметризованные инструкции.<br /><br /> Например, активной статье используются параметризованные инструкции будет иметь значение **17** в этом столбце. Значение **0** означает, что статья неактивна и никакие дополнительные свойства определены.|  
|**type**|**tinyint**|Тип статьи:<br /><br /> **1** = статья на основе журнала.<br /><br /> **3** = на основе журнала статья с фильтрацией вручную.<br /><br /> **5** = на основе журнала статья с представлением вручную.<br /><br /> **7** = на основе журнала статья с фильтрацией вручную и представлением вручную.|  
|**upd_cmd**|**nvarchar(255)**|Команда, выполняемая для инструкции UPDATE.|  
|**schema_option**|**binary**|Указывает, что будет выписано. См. в разделе [sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) список поддерживаемых параметров схемы.|  
|**dest_owner**|**sysname**|Владелец объекта, опубликованного в целевой базе данных.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
