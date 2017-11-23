---
title: "sys.dm_pdw_diag_processing_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 05dc9dc5854b970dd97227672f5f75eecbb34718
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Отображает сведения, относящиеся к все внутренние события диагностики, может быть включен в диагностические сеансы, определенных администратором. Запрос этого представления, чтобы разобраться в статистике диагностики и событий подсистемы диска заполнение всех других динамических административных представлений. Существуют группы очередей для каждого процесса на каждом узле.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Узел устройства извлекается этот журнал.|  
|**идентификатор_процесса**|**int**|Идентификатор процесса, выполняющего Отправка этот статистический показатель.|  
|**target_name**|**nvarchar(255)**|Имя очереди.|  
|**queue_size**|**int**|Число элементов в очереди процесса. Размер очереди обычно является 0. Положительное число указывает, что система находится в условиях высокой нагрузки и выполняется построение списка невыполненных работ для события. При положительном значении в других столбцах означает системы повреждена для данной конкретной очереди, и все связанные динамические административные представления.|  
|**lost_events_count**|**bigint**|Число потерянных событий.|  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и динамические административные представления хранилища параллельных данных &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
