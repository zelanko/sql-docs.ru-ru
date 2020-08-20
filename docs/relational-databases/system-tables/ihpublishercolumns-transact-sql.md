---
description: Таблица IHpublishercolumns (Transact-SQL)
title: Ихпублишерколумнс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumns
- IHpublishercolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumns system table
ms.assetid: a5347750-224c-40d9-ae12-57e7213b7db9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b5d3f4b833d6d5183c888dba9a4a3a39ac42598d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492785"
---
# <a name="ihpublishercolumns-transact-sql"></a>Таблица IHpublishercolumns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Системная таблица **ихпублишерколумнс** представляет метаданные, хранящиеся на издателе. Эта таблица содержит по одной строке для каждого столбца, реплицируемого из издателей, отличных от SQL Server, с помощью текущего распространителя. Сведения о типах данных в **ихпублишерколумнс** относятся только к неSQL Serverной системе управления базами данных (СУБД), из которой публикуются данные. Эта таблица хранится в базе данных распространителя.  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Идентифицирует опубликованный столбец.|  
|**table_id**|**int**|Определяет исходную таблицу из [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , к которой принадлежит столбец.|  
|**publisher_id**|**smallint**|Обозначает издателя, отличного от SQL Server, который публикует столбец.|  
|**name**|**sysname**|Имя публикуемого столбца.|  
|**column_ordinal**|**int**|Определяет порядковый номер столбца.|  
|**type**|**varchar (255)**|Тип данных исходного столбца издателя.|  
|**length**|**bigint**|Длина данных исходного столбца издателя.|  
|**прек**|**int**|Точность числовых данных исходного столбца издателя.|  
|**масштаб**|**int**|Масштаб данных исходного столбца издателя.|  
|**IsNullable**|**bit**|Указывает, допускает ли столбец значения NULL, где значение **1** означает, что значения NULL принимаются.|  
|**iscaptured**|**bit**|Указывает, существует ли триггер, связанный со столбцом; триггер может существовать, даже если столбец не публикуется в статье. Значение **1** означает, что триггер существует в столбце.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Системное представление sysarticlecolumns &#40;системного представления&#41; &#40;&#41;Transact-SQL ](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [Системное представление sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
