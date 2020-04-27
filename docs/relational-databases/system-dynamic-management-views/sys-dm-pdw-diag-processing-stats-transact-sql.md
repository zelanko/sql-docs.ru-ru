---
title: sys. dm_pdw_diag_processing_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8b880820ac633402d1d3cdd679b16a54d1be358e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899539"
---
# <a name="sysdm_pdw_diag_processing_stats-transact-sql"></a>sys. dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Отображает сведения, относящиеся ко всем внутренним событиям диагностики, которые могут быть включены в диагностические сеансы, определенные администратором. Запросите это представление, чтобы понять статистику, связанную с подсистемами диагностики и событий, которые управляют заполнением всех остальных динамических административных представлений. Существует группа очередей для каждого процесса на каждом узле.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Узел устройства, из которого находится этот журнал.|  
|**process_id**|**int**|Идентификатор процесса, выполняющего отправку статистики.|  
|**target_name**|**nvarchar(255)**|Имя очереди.|  
|**queue_size**|**int**|Количество элементов в очереди процессов. Размер очереди обычно равен 0. Положительное число означает, что система находится под нагрузкой и создает журнал ожидания событий. Положительное число в других столбцах означает, что система повреждена для этой конкретной очереди и всех связанных динамических административных представлений.|  
|**lost_events_count**|**bigint**|Число потерянных событий.|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
