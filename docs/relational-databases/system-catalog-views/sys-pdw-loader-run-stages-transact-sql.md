---
description: sys.pdw_loader_run_stages (Transact-SQL)
title: sys.pdw_loader_run_stages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 288810d6143bcdb98e7bf3257f5958b2cf5f91ee
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036742"
---
# <a name="syspdw_loader_run_stages-transact-sql"></a>sys.pdw_loader_run_stages (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Содержит сведения о текущих и завершенных операциях загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] . Эта информация сохраняется и после перезапуска системы.  
  
| Имя столбца | Тип данных | Description | Диапазон |
| ----------- | --------- | ----------- | ----- |
|run_id|**int**|Уникальный идентификатор запуска загрузчика.||  
|разместить|**nvarchar(30)**|Текущий этап выполнения.|"CREATE_STAGING", "DMS_LOAD", "LOAD_INSERT", "LOAD_CLEANUP"|  
|request_id|**nvarchar(32)**|Идентификатор запроса, выполняющего этот этап.||  
|status|**nvarchar (16)**|Состояние этого этапа.||  
|start_time|**datetime**|Время запуска этапа.||  
|end_time|**datetime**|Время завершения этапа (при наличии).|Значение NULL, если не началось или не выполняется.|  
|total_elapsed_time|**int**|Общее время (или затраченное на данный момент) выполнения этого этапа.|Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дней в миллисекундах), это приведет к сбою материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога Azure Synapse Analytics и Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
