---
description: sys. dm_pdw_diag_processing_stats (Transact-SQL)
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
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e93ebebc4f82786537d4a16ac015eca34bc0efc3
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89531014"
---
# <a name="sysdm_pdw_diag_processing_stats-transact-sql"></a>sys. dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

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
  
  
