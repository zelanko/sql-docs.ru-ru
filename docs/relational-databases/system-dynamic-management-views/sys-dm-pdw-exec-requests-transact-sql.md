---
title: sys.dm_pdw_exec_requests (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: cafea3f29f25ab7eb29ce25c108e2a05c7f320af
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех запросов в настоящее время или недавно активны в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Он содержит одну строку для каждого запроса или запрос.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникален в пределах всех запросов в системе.|  
|session_id|**nvarchar(32)**|Уникальный числовой идентификатор, связанный с сеансом, в котором был запущен этот запрос. В разделе [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Текущее состояние запроса.|«Выполняется», «Приостановлено», «Завершено», «Отменено», «Сбой».|  
|submit_time|**datetime**|Время отправки запроса для выполнения.|Допустимые **datetime** меньше или равно значению текущего времени и start_time.|  
|start_time|**datetime**|Время начала выполнения запроса.|Значение NULL для запросов в очереди; в противном случае — допустимое **datetime** меньше или равно значению текущего времени.|  
|end_compile_time|**datetime**|Время, обработчик завершения компиляции запроса.|Значение NULL для запросов, которые не были скомпилированы еще; в противном случае значение является допустимым **datetime** меньше, чем start_time и не больше текущего времени.|
|end_time|**datetime**|Время, когда выполнение запроса завершено, ошибкой или был отменен.|Значение NULL для запросов в очереди или активный. в противном случае является допустимым **datetime** меньше или равно значению текущего времени.|  
|total_elapsed_time|**int**|Затраченное время на выполнение с момента запуска запроса в миллисекундах.|Между 0 и разницу между start_time и end_time.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time продолжает оставаться максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24.8 дней.|  
|Метка|**nvarchar(255)**|Строку необязательную метку, связанную с некоторые инструкции запроса SELECT.|Любая строка, содержащая «a-z», «A-Z», "0-9', «_».|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибки, связанные с запросом, если таковые имеются.|В разделе [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); значение NULL, если не возникло ошибок.|  
|database_id|**int**|Идентификатор базы данных, используемые контекстом явное (например, используйте DB_X).|Код в разделе [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Содержит полный текст запроса, предоставленных пользователем.|Любой допустимый текст, запроса или запроса. Запросы, в которых превышает 4 000 байт, усекаются.|  
|resource_class|**nvarchar(20)**|Класс ресурсов для данного запроса. См. в разделе связанных **concurrency_slots_used** в [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="security"></a>безопасность  
 sys.dm_pdw_exec_requests не выполняет фильтрацию результатов запроса в соответствии с разрешениями для конкретной базы данных. Имена входа с разрешением VIEW SERVER STATE результаты можно получить результаты запроса для всех баз данных  
  
> [!WARNING]  
>  Злоумышленник может использовать sys.dm_pdw_exec_requests для получения сведений о конкретных объектов базы данных с простого наличия разрешения VIEW SERVER STATE, не имеющий разрешения конкретной базе данных.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
