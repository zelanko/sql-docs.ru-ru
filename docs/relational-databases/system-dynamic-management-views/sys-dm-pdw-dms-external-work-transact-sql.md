---
title: sys.dm_pdw_dms_external_work (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
caps.latest.revision: 5
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 781ab0fb027a16ab50235221c6118a93dfa53342
ms.sourcegitcommit: b8e2e3e6e04368aac54100c403cc15fd4e4ec13a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45563621"
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
|Тип|**nvarchar(60)**|Тип внешней операции, которые этот узел работает под управлением.<br /><br /> РАЗДЕЛИТЬ ФАЙЛ представляет собой операцию на внешний файл Hadoop, был разбит на несколько небольших падает.|«ФАЙЛ РАЗБИЕНИЕ»|  
|work_id|**int**|Файл разделить код.|Больше или равно 0.<br /><br /> Уникальным для каждого вычислительного узла.|  
|input_name|**nvarchar(60)**|Строковое имя для входных данных, для чтения.|Для файла Hadoop это имя файла Hadoop.|  
|read_location|**bigint**|Смещение расположения для чтения.||  
|estimated_bytes_processed|**bigint**|Число байтов, обработанных этим исполнителем.|Больше или равно 0.|  
|length|**bigint**|Количество байтов в файле разбиения.<br /><br /> Для Hadoop это размер блока HDFS.|Определяемые пользователем. Значение по умолчанию — 64 МБ.|  
|status|**nvarchar(32)**|Состояние рабочего процесса.|Ожидающие обработки, сделать, не удалось, прервана|  
|start_time|**datetime**|Время начала выполнения этого исполнителя.|Больше или равно для запуска этапа запроса, к которому принадлежит этот рабочий процесс. См. в разделе [sys.dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Время, по которому выполнение завершено, ошибкой или был отменен.|Значение NULL для текущих или в очереди рабочих ролей. В противном случае — больше, чем start_time.|  
|total_elapsed_time|**int**|Общее время, затраченное на выполнение, в миллисекундах.|Больше или равно 0.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будут продолжать максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе [максимальные значения представление системы](http://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9).  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
