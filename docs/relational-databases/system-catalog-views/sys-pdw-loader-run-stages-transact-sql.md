---
title: sys.pdw_loader_run_stages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 52e2946ea70425e32d6157c704ffaa36af17df5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642542"
---
# <a name="syspdwloaderrunstages-transact-sql"></a>sys.pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о текущих и выполненных операциях в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Эта информация сохраняется и после перезапуска системы.  
  
|||||  
|-|-|-|-|  
|Имя столбца|Тип данных|Описание|Диапазон|  
|run_id|**int**|Уникальный идентификатор запуска загрузчика.||  
|рабочей области|**nvarchar(30)**|Текущий этап для запуска.|«CREATE_STAGING», «DMS_LOAD», «LOAD_INSERT», «LOAD_CLEANUP»|  
|request_id|**nvarchar(32)**|Идентификатор запроса, выполнение этого этапа.||  
|status|**nvarchar(16) в формате**|Состояние этого этапа.||  
|start_time|**datetime**|Время начала рабочей области.||  
|end_time|**datetime**|Время окончания рабочей области, если таковые имеются.|Значение NULL, если не запущена или выполняется.|  
|total_elapsed_time|**int**|Общее время этого этапа, затраченное на (или затраченное на данный момент) запущена.|Если total_elapsed_time превышает максимальное значение для целого числа (24,8 дня в миллисекундах), он вызывает ошибку материализации из-за переполнения.<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
