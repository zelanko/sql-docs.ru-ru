---
title: sys.dm_pdw_hadoop_operations (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a9158bacb9959691118c356e4c742dc62e862346
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34466600"
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>sys.dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого задания MAP-Reduce, как часть выполнения является переданы в Hadoop [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] запрос на внешнюю таблицу Hadoop. Каждое задание MAP-Reduce представляет один из предикатов в запросе. Используется, только если включение предиката включена для запросов во внешних таблицах Hadoop.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Идентификатор для этой внешней операции Hadoop.|То же, что идентификатор в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Индекс действия запроса, который ссылается на эту операцию Hadoop.|То же, что step_index в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Описывает тип внешней операции.|«Операция внешних Hadoop»|  
|operation_name|**nvarchar(4000)**|Идентификатор задания для задания MAP-Reduce. Это значение возвращается в с Hadoop после [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] отправляет задание.||  
|map_progress|**float**|Процент от входных данных, пока использовано заданием карты.|Значение с плавающей запятой от, включительно, 0 и 100.|  
|reduce_progress|**int**|Процент завершенного задания reduce...|Значение с плавающей запятой от, включительно, 0 и 100.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
