---
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a1778cbb88fcd6a4142e800cd45109602509125d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899507"
---
# <a name="sysdmpdwdmsexternalwork-transact-sql"></a>sys.dm_pdw_dms_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Системное представление, в котором содержатся сведения о всех шагов служба перемещения данных (DMS) для внешних операций.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Запрос, который используется этим исполнителем DMS.<br /><br /> Идентификатор request_id step_index и dms_step_index формируют ключ для этого представления.|Совпадение с кодом request_id в [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Этап запроса, который вызывает этот рабочий процесс DMS.<br /><br /> Идентификатор request_id step_index и dms_step_index формируют ключ для этого представления.|Совпадение с кодом step_index в [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Текущий шаг в плане DMS.<br /><br /> Идентификатор request_id step_index и dms_step_index формируют ключ для этого представления.|Совпадение с кодом dms___step_index в [sys.dm_pdw_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md).|  
|pdw_node_id|**int**|Узел, на котором выполняется рабочий DMS.|Совпадение с кодом node_id в [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|type|**nvarchar(60)**|Тип внешней операции, которые этот узел работает под управлением.<br /><br /> РАЗДЕЛИТЬ ФАЙЛ представляет собой операцию на внешний файл Hadoop, был разбит на несколько небольших падает.|«ФАЙЛ РАЗБИЕНИЕ»|  
|work_id|**int**|Файл разделить код.|Больше или равно 0.<br /><br /> Уникальным для каждого вычислительного узла.|  
|input_name|**nvarchar(60)**|Строковое имя для входных данных, для чтения.|Для файла Hadoop это имя файла Hadoop.|  
|read_location|**bigint**|Смещение расположения для чтения.||  
|estimated_bytes_processed|**bigint**|Число байтов, обработанных этим исполнителем.|Больше или равно 0.|  
|length|**bigint**|Количество байтов в файле разбиения.<br /><br /> Для Hadoop это размер блока HDFS.|Определяемые пользователем. Значение по умолчанию — 64 МБ.|  
|status|**nvarchar(32)**|Состояние рабочего процесса.|Ожидающие обработки, сделать, не удалось, прервана|  
|start_time|**datetime**|Время начала выполнения этого исполнителя.|Больше или равно для запуска этапа запроса, к которому принадлежит этот рабочий процесс. См. в разделе [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Время, по которому выполнение завершено, ошибкой или был отменен.|Значение NULL для текущих или в очереди рабочих ролей. В противном случае — больше, чем start_time.|  
|total_elapsed_time|**int**|Общее время, затраченное на выполнение, в миллисекундах.|Больше или равно 0.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будут продолжать максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе метаданных в [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) раздела.
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
