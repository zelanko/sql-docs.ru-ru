---
description: sys.dm_pdw_dms_external_work (Transact-SQL)
title: sys.dm_pdw_dms_external_work (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 2baa21665d7fae6f87acbbebb88e55ca6c4624fc
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482635"
---
# <a name="sysdm_pdw_dms_external_work-transact-sql"></a>sys.dm_pdw_dms_external_work (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Системное представление, содержащее сведения обо всех шагах службы перемещения данных (DMS) для внешних операций.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Запрос, использующий эту рабочую роль DMS.<br /><br /> request_id, step_index и dms_step_index образуют ключ для этого представления.|То же, что и request_id в [sys.dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Шаг запроса, вызывающий эту рабочую роль DMS.<br /><br /> request_id, step_index и dms_step_index образуют ключ для этого представления.|То же, что и step_index в [sys.dm_pdw_request_steps &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Текущий шаг в плане DMS.<br /><br /> request_id, step_index и dms_step_index образуют ключ для этого представления.|То же, что и dms___step_index в [sys.dm_pdw_dms_workers &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md).|  
|pdw_node_id|**int**|Узел, на котором работает Рабочая роль DMS.|То же, что и node_id в [sys.dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|тип|**nvarchar(60)**|Тип внешней операции, выполняемой на этом узле.<br /><br /> РАЗБИЕНИе файлов — это операция над внешним файлом Hadoop, который разбит на несколько меньших.|"РАЗДЕЛЕНИЕ ФАЙЛОВ"|  
|work_id|**int**|Идентификатор разбиения файла.|Больше или равно 0.<br /><br /> Уникальный для каждого расчетного узла.|  
|input_name|**nvarchar(60)**|Строковое имя для считываемых входных данных.|Для файла Hadoop это имя файла Hadoop.|  
|read_location|**bigint**|Смещение места чтения.||  
|estimated_bytes_processed|**bigint**|Число байтов, обработанных этим исполнителем.|Больше или равно 0.|  
|length|**bigint**|Число байтов в разбиении файла.<br /><br /> Для Hadoop это размер блока HDFS.|Определяется пользователем. Значение по умолчанию — 64 МБ.|  
|status|**nvarchar(32)**|Состояние рабочей роли.|Ожидание, обработка, завершение, сбой, прервано|  
|start_time|**datetime**|Время начала выполнения этого рабочего процесса.|Больше или равно времени начала шага запроса, к которому относится этот рабочий процесс. См. раздел [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Время, когда выполнение завершилось, завершилось сбоем или было отменено.|Значение NULL для текущих или рабочих процессов в очереди. В противном случае — значение больше start_time.|  
|total_elapsed_time|**int**|Общее время, затраченное на выполнение, в миллисекундах.|Больше или равно 0.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение".<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе метаданные статьи [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40;&#41;Transact-SQL ](../../t-sql/language-reference.md)  
  
