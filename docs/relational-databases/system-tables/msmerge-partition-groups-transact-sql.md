---
title: MSmerge_partition_groups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_partition_groups_TSQL
- MSmerge_partition_groups
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_partition_groups system table
ms.assetid: 5d56d780-ee40-4afc-9c2a-d1723d86e430
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6b0b9f18377de89f6cf607f9aaab6c294f4a716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846572"
---
# <a name="msmergepartitiongroups-transact-sql"></a>MSmerge_partition_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_partition_groups** таблица хранит по одной строке для каждой предварительно вычисляемой секции в данной базе данных. Наряду с указанными столбцами, в эту таблицу добавляется еще один столбец для каждой функции, используемой в параметризованном фильтре строк. Например, столбец с именем **HOST_NAME_FN** добавляется в таблицу, если фильтр использует [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) функции. Хранится по одной строке для каждого уникального набора значений функции, синхронизированного с издателем. Два или более подписчика, синхронизирующиеся точно с таким же значением для всех этих функций, будут иметь общую строку в этой таблице, поэтому все они будут иметь один и тот же идентификатор секции. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Столбец идентификаторов, который предоставляет уникальный идентификационный номер для предварительно вычисляемой секции.|  
|**publication_number**|**smallint**|Номер публикации, который хранится в **sysmergepublications**.|  
|**maxgen_whenadded**|**bigint**|Последнее поколение, известное на издателе во время вставки строки в эту таблицу.|  
|**using_partition_groups**|**bit**|Указывает, принадлежит ли секция публикации, использующей предварительно вычисляемые секции. Этот параметр может иметь одно из следующих значений.<br /><br /> **0** = публикация использует предварительно вычисляемые секции.<br /><br /> **1** = публикация использует предварительно вычисляемые секции<br /><br /> Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|**HOST_NAME_FN**|**nvarchar(128)**|Значение, предоставляемое при использовании параметризованных фильтров строк для формирования секций. Дополнительные сведения см. в статье [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
