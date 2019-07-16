---
title: sys.dm_pdw_hadoop_operations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b4429585d735ee4eb51d2b0b421b53fdf06bf8ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899390"
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>sys.dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого как часть выполнения является переданы в Hadoop задания MAP-Reduce [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] запроса во внешней таблице Hadoop. Каждое задание MAP-Reduce представляет одно из предикаты в запросе. Используется, только при включении предиката для запросов во внешних таблицах Hadoop.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Идентификатор для этой внешней операции Hadoop.|Совпадение с кодом идентификатора в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Индекс этапа запроса, который ссылается на эту операцию Hadoop.|Совпадение с кодом step_index в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Описывает тип внешней операции.|«Операция внешних Hadoop»|  
|operation_name|**nvarchar(4000)**|Идентификатор задания для задания MAP-Reduce. Это значение возвращается с Hadoop после [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] отправляет задание.||  
|map_progress|**float**|Процент входных данных, которые были использованы до сих заданием карты.|Число с плавающей между и 0 до 100.|  
|reduce_progress|**int**|Процент завершения задания reduce...|Число с плавающей между и 0 до 100.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
