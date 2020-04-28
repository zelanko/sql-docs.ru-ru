---
title: trace_xe_action_map (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_xe_action_map_TSQL
- trace_xe_action_map
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], tables
- trace_xe_action_map
ms.assetid: 208a1413-ce7f-4521-b765-d74723627302
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47931e56759191e8386a6890ec683adf0d5f69c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68056273"
---
# <a name="extended-events-tables---trace_xe_action_map"></a>Таблицы расширенных событий — trace_xe_action_map
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого действия из числа расширенных событий, сопоставленного с идентификатором столбца трассировки SQL. Эта таблица хранится в базе данных master в схеме sys.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|trace_column_id|**smallint**|Идентификатор сопоставленного столбца трассировки SQL.|  
|package_name|**nvarchar(60)**|Имя пакета расширенных событий, в котором находится сопоставленное действие.|  
|xe_action_name|**nvarchar(60)**|Имя действия расширенных событий, которое сопоставлено со столбцом трассировки SQL.|  
  
## <a name="remarks"></a>Remarks  
 Чтобы выявить действия расширенных событий, эквивалентные столбцам трассировки SQL, можно использовать следующий запрос.  
  
```  
SELECT tc.name AS trace_column, am.package_name, am.xe_action_name  
FROM sys.trace_columns AS tc  
INNER JOIN sys.trace_xe_action_map AS am  
   ON tc.trace_column_id = am.trace_column_id  
```  
  
 Столбцы трассировки SQL, которые не соответствуют действиям, не включаются в таблицу.  
  
## <a name="see-also"></a>См. также:  
 [trace_xe_event_map (Transact-SQL)](../../relational-databases/system-tables/extended-events-tables-trace-xe-event-map.md)  
  
  
