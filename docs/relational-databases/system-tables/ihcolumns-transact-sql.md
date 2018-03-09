---
title: "IHcolumns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- IHcolumns_TSQL
- IHcolumns
dev_langs: TSQL
helpviewer_keywords: IHcolumns system table
ms.assetid: 5bb027e5-5279-487b-9c33-5f402987253c
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 857380d30397d02b2fe1ba9adfd11ca9382b9eee
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihcolumns-transact-sql"></a>IHcolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHcolumns** системная таблица содержит по одной строке для каждого опубликованного столбца. Эта таблица используется для определения того, как представлены типы данных столбцов из SQL Server издателем при публикации, который фактически сопоставление типов данных между систем управления базами данных (СУБД) SQL Server и SQL Server. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Идентификатор column_id**|**int**|Идентифицирует опубликованный столбец.|  
|**publishercolumn_id**|**int**|Связывает опубликованный столбец с метаданными столбца, хранящимися в [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) системной таблицы.|  
|**name**|**sysname**|Указывает имя столбца.|  
|**article_id**|**int**|Идентифицирует статью, к которой относится столбец.|  
|**column_ordinal**|**int**|Определяет порядковый номер столбца.|  
|**mapped_type**|**tinyint**|Тип данных целевого столбца на подписчике.|  
|**mapped_length**|**bigint**|Длина столбца на подписчике.|  
|**mapped_prec**|**int**|Точность столбца на подписчике.|  
|**mapped_scale**|**int**|Масштаб столбца на подписчике.|  
|**mapped_nullable**|**bit**|Указывает, допускает ли столбец на подписчике значения NULL, где **1** означает, что значения NULL допустимы.|  
  
## <a name="see-also"></a>См. также:  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40; Системное представление &#41; &#40; Transact-SQL &#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40; Transact-SQL &#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
