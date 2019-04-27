---
title: syscollector_execution_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_stats
- syscollector_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_execution_stats view
- data collector view
ms.assetid: 23e35ac5-fbbf-4922-970c-f4fac44c1263
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b89823af1295b329046395a8f3c345401ca61805
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760184"
---
# <a name="syscollectorexecutionstats-transact-sql"></a>syscollector_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о ходе выполнения задачи для набора элементов сбора или пакета.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**log_id**|**bigint**|Определяет выполнение каждого набора элементов сбора. Используется для соединения этого представления с другими подробными журналами. Не допускает значение NULL.|  
|**task_name**|**nvarchar(128)**|Имя набора сбора или задачи пакета, для которого производится отображение текущей информации. Не допускает значение NULL.|  
|**execution_row_count_in**|**int**|Количество обработанных строк на момент запуска потока данных. Допускает значение NULL.|  
|**execution_row_count_out**|**int**|Количество обработанных строк на момент окончания потока данных. Допускает значение NULL.|  
|**execution_row_count_errors**|**int**|Количество строк с ошибками, обработанных в потоке данных. Допускает значение NULL.|  
|**execution_time_ms**|**int**|Время, требуемое для завершения задачи, в миллисекундах. Допускает значение NULL.|  
|**log_time**|**datetime**|Время занесения данной информации в журнал. Не допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для **dc_operator**.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Представления сборщика данных (Transact-SQL)](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
