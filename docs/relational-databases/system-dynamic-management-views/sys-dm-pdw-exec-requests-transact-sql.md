---
title: sys. dm_pdw_exec_requests (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/05/2019
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
ms.openlocfilehash: 15d27881378a88c8f4ae6d65640be6218ecd3530
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632769"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys. dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех запросах, которые в данный момент или недавно активны в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. В нем отображается одна строка для каждого запроса или запроса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Ключ для этого представления. Уникальный числовой идентификатор, связанный с запросом.|Уникальный для всех запросов в системе.|  
|session_id|**nvarchar(32)**|Уникальный числовой идентификатор, связанный с сеансом, в котором выполнялся этот запрос. См. раздел [sys &#40;. DM_PDW_EXEC_SESSIONS Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Текущее состояние запроса.|"Выполняется", "suspended", "Completed", "Canceled", "Failed".|  
|submit_time|**datetime**|Время отправки запроса на выполнение.|Допустимое **значение DateTime** меньше или равно текущему времени и start_time.|  
|start_time|**datetime**|Время начала выполнения запроса.|Значение NULL для запросов в очереди; в противном случае допустимое **значение DateTime** меньше или равно текущему времени.|  
|end_compile_time|**datetime**|Время, когда обработчик завершил компиляцию запроса.|Значение NULL для запросов, которые еще не были скомпилированы; в противном случае допустимое значение **DateTime** меньше start_time и меньше или равно текущему времени.|
|end_time|**datetime**|Время, когда выполнение запроса завершилось, завершилось сбоем или было отменено.|Значение NULL для очереди или активных запросов; в противном случае допустимое **значение DateTime** меньше или равно текущему времени.|  
|total_elapsed_time|**int**|Время, затраченное на выполнение с момента запуска запроса, в миллисекундах.|Между 0 и разностью между start_time и end_time.</br></br> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение".</br></br> Максимальное значение в миллисекундах равно 24,8 дням.|  
|заголовка|**nvarchar(255)**|Необязательная строка метки, связанная с некоторыми инструкциями запроса SELECT.|Любая строка, содержащая "a-z", "A-Z", "0-9", "_".|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с запросом, если он есть.|См [. раздел sys &#40;. DM_PDW_ERRORS Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); Если ошибка не возникала, задайте значение NULL.|  
|database_id|**int**|Идентификатор базы данных, используемой явным контекстом (например, DB_X).|См. идентификатор в [представлении sys &#40;. databases&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Содержит полный текст запроса, отправленный пользователем.|Любой допустимый запрос или текст запроса. Запросы, длина которых превышает 4000 байт, усекаются.|  
|resource_class|**nvarchar (20)**|Группа рабочей нагрузки, используемая для этого запроса. |Статические классы ресурсов</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Динамические классы ресурсов</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance|**nvarchar(128)**|Важность, с которой был выполнен запрос.  Это относительная важность запроса в этой группе рабочей нагрузки и в группах рабочей нагрузки для общих ресурсов.  Важность, указанная в классификаторе, переопределяет параметр важности группы рабочей нагрузки.</br>Область применения этой статьи: Хранилище данных SQL Azure|NULL</br>low</br>below_normal</br>Обычная (по умолчанию)</br>above_normal</br>high|
|group_name|**sysname** |Для запросов, использующих ресурсы, group_name — имя группы рабочей нагрузки, в которой выполняется запрос.  Если запрос не использует ресурсы, group_name имеет значение null.</br>Область применения этой статьи: Хранилище данных SQL Azure|
|classifier_name|**sysname**|Для запросов, использующих ресурсы, имя классификатора, используемого для назначения ресурсов и важности.||
|resource_allocation_percentage|**Decimal (5, 2)**|Процентный объем ресурсов, выделенных для запроса.</br>Область применения этой статьи: Хранилище данных SQL Azure|
|result_set_cache|**bit**|Сведения о том, является ли выполненный запрос попаданием в кэш результатов (1) или нет (0). </br>Область применения этой статьи: Хранилище данных SQL Azure|0, 1|
||||
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см. в разделе метаданные статьи [ограничения емкости](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .
  
## <a name="permissions"></a>Разрешения

 Необходимо разрешение VIEW SERVER STATE.  
  
## <a name="security"></a>Безопасность

 sys. dm_pdw_exec_requests не фильтрует результаты запроса в соответствии с разрешениями, определенными для базы данных. Имена входа с разрешением VIEW SERVER STATE могут получать результаты запроса для всех баз данных.  
  
>[!WARNING]  
>Злоумышленник может использовать sys. dm_pdw_exec_requests для получения сведений о конкретных объектах базы данных, просто выполняя разрешение VIEW SERVER STATE и не требуя разрешения для конкретной базы данных.  
  
## <a name="see-also"></a>См. также раздел

 [Динамические административные представления &#40;хранилища данных SQL и параллельного хранилища данных TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)
