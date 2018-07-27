---
title: IHpublishercolumns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHpublishercolumns
- IHpublishercolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumns system table
ms.assetid: a5347750-224c-40d9-ae12-57e7213b7db9
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1032578837699182d4c1ba73a118d03ece01b5f6
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103879"
---
# <a name="ihpublishercolumns-transact-sql"></a>Таблица IHpublishercolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumns** системная таблица представляет метаданные, хранящиеся на издателе. Эта таблица содержит по одной строке для каждого столбца, реплицируемого из отличных от издателей SQL Server с помощью текущего распространителя. Сведения о в типе данных **IHpublishercolumns** относится только к базе данных системы управления SQL Server (СУБД), который откуда данные публикуются. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Идентифицирует опубликованный столбец.|  
|**table_id**|**int**|Идентифицирует исходную таблицу из [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , которой принадлежит столбец.|  
|**publisher_id**|**smallint**|Определяет, отличном от издателя SQL Server откуда выполняется публикация столбца.|  
|**name**|**sysname**|Имя публикуемого столбца.|  
|**column_ordinal**|**int**|Определяет порядковый номер столбца.|  
|**type**|**varchar(255)**|Тип данных исходного столбца издателя.|  
|**Длина**|**bigint**|Длина данных исходного столбца издателя.|  
|**prec**|**int**|Точность числовых данных исходного столбца издателя.|  
|**Масштаб**|**int**|Масштаб данных исходного столбца издателя.|  
|**IsNullable**|**bit**|Указывает, допускает ли столбец значения NULL, где **1** означает, что значения NULL допускаются.|  
|**iscaptured**|**bit**|Указывает, существует ли триггер, связанный со столбцом; триггер может существовать, даже если столбец не публикуется в статье. Значение **1** означает, что для данного столбца существует триггера.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sysarticlecolumns &#40;системное представление&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
