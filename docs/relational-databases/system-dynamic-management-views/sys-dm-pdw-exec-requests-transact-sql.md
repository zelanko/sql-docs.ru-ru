---
title: sys.dm_pdw_exec_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ed96138b4808448fef815fad90342e671f37ed5f
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52409599"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о всех запросов в настоящее время или недавно active в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. В ней перечислены одну строку для каждого запроса или запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникально для всех запросов в системе.|  
|session_id|**nvarchar(32)**|Уникальный числовой идентификатор, связанный с сеансом, в котором был запущен этот запрос. См. в разделе [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Текущее состояние запроса.|«Выполняется», «Приостановлено», «Завершено», «Отменено», «Сбой».|  
|submit_time|**datetime**|Время отправки запроса для выполнения.|Допустимые **datetime** меньше или равна start_time и текущего времени.|  
|start_time|**datetime**|Время начала выполнения запроса.|Значение NULL для запросов в очереди; в противном случае допустимый **datetime** меньше или равна текущее время.|  
|end_compile_time|**datetime**|Время, обработчик завершения компиляции запроса.|Значение NULL для запросов, которые не были скомпилированы еще; в противном случае допустимый **datetime** меньше, чем start_time и меньше или равно текущее время.|
|end_time|**datetime**|Время, по которому выполнение запроса завершено, ошибкой или был отменен.|Значение NULL для запросов в очереди, либо active; в противном случае допустимый **datetime** меньше или равна текущее время.|  
|total_elapsed_time|**int**|Время затраченное на выполнение с момента запуска запроса, в миллисекундах.|Между 0 и разница между start_time и end_time.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будут продолжать максимальное значение. Это условие будет создавать предупреждение «превышено максимальное значение.»<br /><br /> Максимальное значение в миллисекундах соответствует 24,8 дня.|  
|Метка|**nvarchar(255)**|Строку необязательную метку, связанную с некоторые операторы запроса SELECT.|Любая строка, содержащая «a – z», «A – Z», "0-9", «_».|  
|error_id|**nvarchar(36)**|Уникальный идентификатор ошибку, связанную с запросом, если таковые имеются.|См. в разделе [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); значение NULL, если не возникло ошибок.|  
|database_id|**int**|Идентификатор базы данных, используемой явный контекст (например, используйте DB_X).|См. в разделе с кодом в [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Содержит полный текст запроса, предоставленных пользователю.|Любой допустимый текст, запроса или запроса. Запросы, в которых превышает 4 000 байт, усекаются.|  
|resource_class|**nvarchar(20)**|Класс ресурсов для данного запроса. См. связанные **concurrency_slots_used** в [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении см. в разделе «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="security"></a>безопасность  
 sys.dm_pdw_exec_requests не фильтрует результаты запроса в соответствии с конкретной базы данных разрешения. Имена входа с разрешением VIEW SERVER STATE можно получить результаты запроса результаты для всех баз данных  
  
> [!WARNING]  
>  Злоумышленник может использовать sys.dm_pdw_exec_requests для получения сведений о конкретных объектов базы данных, путем простого наличия разрешения VIEW SERVER STATE и при отсутствии разрешений для базы данных.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
