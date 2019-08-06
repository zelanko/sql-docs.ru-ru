---
title: sys. DM _pdw_exec_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 72af3975378b2450e51b3880e8814705bb514c1a
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811397"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys. DM _pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех текущих или недавно активных запросах [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]в. В нем отображается одна строка для каждого запроса или запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникальный для всех запросов в системе.|  
|session_id|**nvarchar(32)**|Уникальный числовой идентификатор, связанный с сеансом, в котором выполнялся этот запрос. См. раздел [sys. &#40;DM _PDW_EXEC_SESSIONS Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Текущее состояние запроса.|"Выполняется", "suspended", "Completed", "Canceled", "Failed".|  
|submit_time|**datetime**|Время отправки запроса на выполнение.|Допустимое **значение DateTime** меньше или равно текущему времени и start_time.|  
|start_time|**datetime**|Время начала выполнения запроса.|Значение NULL для запросов в очереди; в противном случае допустимое **значение DateTime** меньше или равно текущему времени.|  
|end_compile_time|**datetime**|Время, когда обработчик завершил компиляцию запроса.|Значение NULL для запросов, которые еще не были скомпилированы; в противном случае допустимое значение **DateTime** меньше start_time и меньше или равно текущему времени.|
|end_time|**datetime**|Время, когда выполнение запроса завершилось, завершилось сбоем или было отменено.|Значение NULL для очереди или активных запросов; в противном случае допустимое **значение DateTime** меньше или равно текущему времени.|  
|total_elapsed_time|**int**|Время, затраченное на выполнение с момента запуска запроса, в миллисекундах.|Между 0 и разностью между start_time и end_time.</br></br> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение".</br></br> Максимальное значение в миллисекундах равно 24,8 дням.|  
|заголовка|**nvarchar(255)**|Необязательная строка метки, связанная с некоторыми инструкциями запроса SELECT.|Любая строка, содержащая "a-z", "A-Z", "0-9", "_".|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с запросом, если он есть.|См [. раздел sys. &#40;DM _PDW_ERRORS Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); Если ошибка не возникала, задайте значение NULL.|  
|database_id|**int**|Идентификатор базы данных, используемой явным контекстом (например, используйте DB_X).|См. идентификатор в [представлении sys &#40;. databases&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Содержит полный текст запроса, отправленный пользователем.|Любой допустимый запрос или текст запроса. Запросы, длина которых превышает 4000 байт, усекаются.|  
|resource_class|**nvarchar (20)**|Класс ресурса для этого запроса. См. связанные **concurrency_slots_used** в [sys. DM &#40;_pdw_resource_waits Transact-&#41;SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).  Дополнительные сведения о классах ресурсов см. в разделе [классы ресурсов & Управление рабочей](https://docs.microsoft.com/azure/sql-data-warehouse/resource-classes-for-workload-management) нагрузкой. |Статические классы ресурсов</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Динамические классы ресурсов</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance|**nvarchar(32)**|Параметр важности, с которым был отправлен запрос. Запросы с более низкой важностью остаются в очереди в приостановленном состоянии, если отправляются запросы с более высоким уровнем важности.  Запросы с более высоким уровнем важности будут выполняться до более низких приоритетных запросов, которые были отправлены ранее.  Дополнительные сведения о важности см. в статье [важность рабочей нагрузки](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-workload-importance).  |NULL</br>low</br>below_normal</br>Обычная (по умолчанию)</br>above_normal</br>high|
|group_name| |Зарезервировано для внутреннего использования.</br>Применимо для следующих объектов: Хранилище данных SQL Azure|
|resource_allocation_percentage| |Зарезервировано для внутреннего использования.</br>Применимо для следующих объектов: Хранилище данных SQL Azure|
|result_set_cache|**bit**|Сведения о том, является ли выполненный запрос попаданием в кэш результатов (1) или нет (0).|0, 1|
||||
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе метаданные статьи [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .   
  
## <a name="permissions"></a>Разрешения

 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="security"></a>Безопасность

 sys. DM _pdw_exec_requests не фильтрует результаты запроса в соответствии с разрешениями для конкретной базы данных. Имена входа с разрешением VIEW SERVER STATE могут получать результаты запроса для всех баз данных.  
  
>[!WARNING]  
>Злоумышленник может использовать sys. DM _pdw_exec_requests для получения сведений о конкретных объектах базы данных, просто выполнив разрешение VIEW SERVER STATE и не имея разрешения для конкретной базы данных.  
  
## <a name="see-also"></a>См. также

 [Динамические административные представления &#40;хранилища данных SQL и параллельного хранилища данных TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md) 
