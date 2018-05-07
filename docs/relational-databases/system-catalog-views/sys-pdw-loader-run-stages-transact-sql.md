---
title: sys.pdw_loader_run_stages (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
caps.latest.revision: 8
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5521b046d49fe27c7dd1a174f960caec54e8626e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwloaderrunstages-transact-sql"></a>sys.pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения об операциях выполняющихся и завершенных загрузки в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Эта информация сохраняется и после перезапуска системы.  
  
|||||  
|-|-|-|-|  
|Имя столбца|Тип данных|Описание|Диапазон|  
|run_id|**int**|Уникальный идентификатор запуска загрузчика.||  
|Этап|**nvarchar(30)**|Текущий этап для выполнения.|«CREATE_STAGING», «DMS_LOAD», «LOAD_INSERT», «LOAD_CLEANUP»|  
|request_id|**nvarchar(32)**|Идентификатор запроса, выполнение этого этапа.||  
|status|**nvarchar(16) в формате**|Состояние этого этапа.||  
|start_time|**datetime**|Время начала этапа.||  
|end_time|**datetime**|Время окончания рабочей области, если таковые имеются.|Значение NULL, если не запущена или выполняется.|  
|total_elapsed_time|**int**|Общее время этого этапа, затраченное на (или затраченное на данный момент) запущена.|Если total_elapsed_time превышает максимальное значение для целого числа (24.8 дней в миллисекундах), это приведет к переполнению материализации сбой из-за.<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
