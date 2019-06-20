---
title: IHcolumns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHcolumns_TSQL
- IHcolumns
dev_langs:
- TSQL
helpviewer_keywords:
- IHcolumns system table
ms.assetid: 5bb027e5-5279-487b-9c33-5f402987253c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c5d05f2667b6f7196338b182f2b9cca1a84e7b6e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62744171"
---
# <a name="ihcolumns-transact-sql"></a>IHcolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHcolumns** системная таблица содержит по одной строке для каждого опубликованного столбца. Эта таблица используется для определения типов данных столбцов из SQL Server издателем представления при публикации, по сути, который сопоставляет типы данных между системами управления базы данных SQL Server (СУБД) и SQL Server. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**column_id**|**int**|Идентифицирует опубликованный столбец.|  
|**publishercolumn_id**|**int**|Связывает опубликованный столбец с метаданными столбца, хранящимися в [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) системная таблица.|  
|**name**|**sysname**|Указывает имя столбца.|  
|**article_id**|**int**|Идентифицирует статью, к которой относится столбец.|  
|**column_ordinal**|**int**|Определяет порядковый номер столбца.|  
|**mapped_type**|**tinyint**|Тип данных целевого столбца на подписчике.|  
|**mapped_length**|**bigint**|Длина столбца на подписчике.|  
|**mapped_prec**|**int**|Точность столбца на подписчике.|  
|**mapped_scale**|**int**|Масштаб столбца на подписчике.|  
|**mapped_nullable**|**bit**|Указывает, допускает ли столбец на подписчике значения NULL, где **1** означает, что значения NULL допускаются.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;системное представление&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
