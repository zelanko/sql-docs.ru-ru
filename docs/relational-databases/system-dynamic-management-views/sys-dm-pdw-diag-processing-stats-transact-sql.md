---
title: sys.dm_pdw_diag_processing_stats (Transact-SQL) | Документация Майкрософт
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
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f96dd7be6de1415abb8a71425b083c58e7012d9d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62691372"
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Отображаются сведения, относящиеся ко всем внутренней диагностики событиям, может быть включен в диагностические сеансы, определенных администратором. Запрос в этом представлении, чтобы понять статистические данные диагностики и регистрации событий подсистемы диска совокупность всех других динамических административных представлений. Существует набор очередей для каждого процесса на каждом узле.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Устройство узла извлекается этот журнал.|  
|**process_id**|**int**|Идентификатор процесса, выполняющего отправки этот статистический показатель.|  
|**target_name**|**nvarchar(255)**|Имя очереди.|  
|**queue_size**|**int**|Число элементов в очередь процессов. Размер очереди обычно является 0. Положительное число означает, что система сильно загружена и создает журнала ожидания событий. При положительном значении в других столбцах означает, что для данной конкретной очереди оказались поврежденными системы и все связанные динамические административные представления.|  
|**lost_events_count**|**bigint**|Число потерянных событий.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
