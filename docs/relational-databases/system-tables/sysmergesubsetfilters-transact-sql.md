---
title: "sysmergesubsetfilters (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmergesubsetfilters
- sysmergesubsetfilters_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmergesubsetfilters system table
ms.assetid: f91d1c6c-3132-47f6-926c-88f56848cafe
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 66ef85eacefa716b50e3af7e125e877116185a64
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysmergesubsetfilters-transact-sql"></a>sysmergesubsetfilters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о фильтрах соединения для секционированных статей. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**FilterName**|**sysname**|Имя фильтра, используемого для создания новых статей.|  
|**join_filterid**|**int**|Идентификатор объекта, представляющего фильтр соединения.|  
|**pubid**|**uniqueidentifier**|Идентификатор публикации.|  
|**artid**|**uniqueidentifier**|Идентификатор статьи.|  
|**art_nickname**|**int**|Псевдоним статьи.|  
|**join_articlename**|**sysname**|Имя таблицы, с которой необходимо выполнить соединение для определения принадлежности строк.|  
|**join_nickname**|**int**|Псевдоним таблицы, с которой необходимо выполнить соединение для определения принадлежности строк.|  
|**join_unique_key**|**int**|Указывает соединение по уникальному ключу из **join_tablename**:<br /><br /> 0 = Не уникальный ключ.<br /><br /> 1 = Уникальный ключ.|  
|**expand_proc**|**sysname**|Имя хранимой процедуры, используемой агентом слияния для выявления строк, которые необходимо отправить или удалить на подписчике.|  
|**join_filterclause**|**nvarchar(1000)**|Предложение фильтра, используемое для соединения.|  
|**filter_type**|**tinyint**|Показывает тип фильтра, который может быть одним из следующих:<br /><br /> 1 = Фильтр соединения.<br /><br /> 2 = Связь логических записей.<br /><br /> 3 = Одновременно фильтр соединения и связь логических записей.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
