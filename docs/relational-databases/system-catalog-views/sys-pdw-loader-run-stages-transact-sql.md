---
title: sys. pdw_loader_run_stages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5d10a3bcbf02e88e054c12060299e9462af3004d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127453"
---
# <a name="syspdw_loader_run_stages-transact-sql"></a>sys. pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о текущих и завершенных операциях [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]загрузки в. Эта информация сохраняется и после перезапуска системы.  
  
|||||  
|-|-|-|-|  
|Имя столбца|Тип данных|Описание|Диапазон|  
|run_id|**int**|Уникальный идентификатор запуска загрузчика.||  
|разместить|**nvarchar(30)**|Текущий этап выполнения.|"CREATE_STAGING", "DMS_LOAD", "LOAD_INSERT", "LOAD_CLEANUP"|  
|request_id|**nvarchar(32)**|Идентификатор запроса, выполняющего этот этап.||  
|status|**nvarchar (16)**|Состояние этого этапа.||  
|start_time|**datetime**|Время запуска этапа.||  
|end_time|**datetime**|Время завершения этапа (при наличии).|Значение NULL, если не началось или не выполняется.|  
|total_elapsed_time|**int**|Общее время (или затраченное на данный момент) выполнения этого этапа.|Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дней в миллисекундах), это приведет к сбою материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
  
## <a name="see-also"></a>См. также:  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md) (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
  
  
