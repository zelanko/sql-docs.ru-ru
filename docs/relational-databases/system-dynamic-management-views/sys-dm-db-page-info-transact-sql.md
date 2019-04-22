---
title: sys.dm_db_page_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_page_info
- sys.dm_db_page_info_TSQL
- dm_db_page_info
- dm_db_page_info_TSQL
- dbcc page
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_page_info dynamic management view
author: ''
ms.author: pamela
manager: amitban
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2246abe2343622f2aece785a31e1e31f7166822b
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58899720"
---
# <a name="sysdmdbpageinfo-transact-sql"></a>sys.dm_db_page_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Возвращает сведения о странице в базе данных.  Функция возвращает одну строку, содержащим данные заголовков со страницы, включая `object_id`, `index_id`, и `partition_id`.  В большинстве случаев эта функция заменяет потребность в использовании `DBCC PAGE`.

## <a name="syntax"></a>Синтаксис   
```  
sys.dm_db_page_info ( DatabaseId, FileId, PageId, Mode )  
``` 

## <a name="arguments"></a>Аргументы  
*DatabaseId* | NULL | ПО УМОЛЧАНИЮ     
Идентификатор базы данных. *DatabaseId* — **smallint**. Допустимые входные данные — номер идентификатора базы данных. Значение по умолчанию имеет значение NULL, однако Отправка значение NULL для этого параметра приведет к ошибке.
 
*FileId* | NULL | ПО УМОЛЧАНИЮ   
Идентификатор файла. *FileId* — **int**.  Допустимые входные данные — номер идентификатора файла в базы данных, указанной *DatabaseId*. Значение по умолчанию имеет значение NULL, однако Отправка значение NULL для этого параметра приведет к ошибке.

*Идентификатор страницы* | NULL | ПО УМОЛЧАНИЮ   
Это идентификатор страницы.  *Идентификатор страницы* — **int**.  Допустимые входные данные — номер идентификатора страницы в файл, указанный параметром *FileId*. Значение по умолчанию имеет значение NULL, однако Отправка значение NULL для этого параметра приведет к ошибке.

*режим* | NULL | ПО УМОЛЧАНИЮ   
Определяет уровень детализации в выходных данных функции. «ОГРАНИЧЕННЫЙ» будут возвращать значения NULL для всех столбцов, описание, «ПОДРОБНЫЙ» заполнит описание столбцов.  Значение по умолчанию — «ОГРАНИЧЕННЫЙ».

## <a name="table-returned"></a>Возвращаемая таблица  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id |ssNoversion |Идентификатор базы данных |
|file_id |ssNoversion |Идентификатор файла |
|page_id |ssNoversion |Идентификатор страницы |
|page_type |ssNoversion |Тип страницы |
|page_type_desc |nvarchar(64) |Описание типа страницы |
|page_flag_bits |nvarchar(64) |Флаговые биты в заголовке страницы |
|page_flag_bits_desc |nvarchar(256) |Описание bits флаг в заголовке страницы |
|page_type_flag_bits |nvarchar(64) |Введите флаговые биты в заголовке страницы |
|page_type_flag_bits_desc |nvarchar(64) |Описание bits флаг типа в заголовке страницы |
|object_id |ssNoversion |Идентификатор объекта, получившего страницы |
|index_id |ssNoversion |Идентификатор индекса (0 для страниц данных кучи) |
|partition_id |BIGINT |Идентификатор секции |
|alloc_unit_id |BIGINT |Идентификатор единицы распределения |
|page_level |ssNoversion |Уровня страницы в индексе (конечного = 0) |
|slot_count |smallint |Общее число слотов (используемое и неиспользуемое) <br> Для страницы данных это число соответствует числу строк. |
|ghost_rec_count |smallint |Число записей, помеченных как фантомную. на странице <br> Фантомных записей — это приложения, была помечена для удаления, но еще не удалены. |
|torn_bits |ssNoversion |1 бит на сектор для обнаружения оборванных записей. Также используется для хранения контрольной суммы <br> Это значение используется для обнаружения повреждения данных |
|is_iam_pg |bit |Бит, чтобы указать, является ли страницы IAM-страницы  |
|is_mixed_ext |bit |Чтобы указать, если бит выделенных в смешанный экстент |
|pfs_file_id |smallint |Идентификатор файла соответствующий PFS-страницы |
|pfs_page_id |ssNoversion |Идентификатор соответствующего PFS-страницы |
|pfs_alloc_percent |ssNoversion |Процент распределения, как указано в PFS байтов |
|pfs_status |nvarchar(64) |PFS байтов |
|pfs_status_desc |nvarchar(64) |Описание PFS байта |
|gam_file_id |smallint |Идентификатор файла, соответствующей страницы GAM |
|gam_page_id |ssNoversion |Идентификатор страницы, соответствующей страницы GAM |
|gam_status |bit |Чтобы указать, если бит выделенный в GAM |
|gam_status_desc |nvarchar(64) |Описание состояния бита на карте GAM |
|sgam_file_id |smallint |Идентификатор файла, соответствующий SGAM-страницы |
|sgam_page_id |ssNoversion |Идентификатор страницы, соответствующий SGAM-страницы |
|sgam_status |bit |Чтобы указать, если бит выделенных в SGAM |
|sgam_status_desc |nvarchar(64) |Описание состояния соответствующий бит SGAM |
|diff_map_file_id |smallint |Идентификатор соответствующей страницы битовой карте разностного файла |
|diff_map_page_id |ssNoversion |Идентификатор страницы, соответствующей страницы разностная битовая карта |
|diff_status |bit |Бит, чтобы указать, если изменяется состояние копирования |
|diff_status_desc |nvarchar(64) |Описание состояния бита diff |
|ml_file_id |smallint |Идентификатор файла на соответствующей странице точечного рисунка минимальное протоколирование |
|ml_page_id |ssNoversion |Идентификатор страницы, соответствующей страницы точечного рисунка минимальное протоколирование |
|ml_status |bit |Бит, чтобы указать, если страницы минимальный журнал |
|ml_status_desc |nvarchar(64) |Описание состояния минимальное протоколирование бит |
|free_bytes |smallint |Количество свободных байт на страницу |
|free_data_offset |ssNoversion |Смещение свободного места в конце области данных |
|reserved_bytes |smallint |Количество свободных байт, зарезервированной с помощью все транзакции (Если куча) <br> Количество фантомных строк (если конечный индекс) |
|reserved_xdes_id |smallint |Пространство, порожденного m_xdesID для m_reservedCnt <br> Только для отладки |
|xdes_id |nvarchar(64) |Последняя транзакция, порожденного m_reserved <br> Только для отладки |
|prev_page_file_id |smallint |Предыдущий идентификатор файла страницы |
|prev_page_page_id |ssNoversion |Предыдущей страницы, идентификатор страницы |
|next_page_file_id |smallint |Следующий идентификатор файла страницы |
|next_page_page_id |ssNoversion |Следующая страница идентификатор страницы |
|min_len |smallint |Длина строки фиксированного размера |
|lsn |nvarchar(64) |Регистрационный номер / метки времени |
|header_version |ssNoversion |Версия заголовка страницы |

## <a name="remarks"></a>Примечания
`sys.dm_db_page_info` Функции динамического управления возвращает сведения о странице как `page_id`, `file_id`, `index_id`, `object_id` и т.д., которые присутствуют в верхнем колонтитуле страницы. Эта информация полезна для устранения неполадок и отладки различных производительности (конфликты блокировок и кратковременных блокировок) и повреждений.

`sys.dm_db_page_info` может использоваться вместо `DBCC PAGE` инструкция на многих случаях, но возвращает только заголовок сведения страницы, не основной области страницы. `DBCC PAGE` по-прежнему необходимы для вариантов использования, где необходимы все содержимое страницы.

## <a name="using-in-conjunction-with-other-dmvs"></a>В сочетании с помощью других динамических административных представлений
Одно из важных варианты использования `sys.dm_db_page_info` является присоединение его с помощью других динамических административных представлений, которые предоставляют сведения о странице.  Чтобы упростить этот вариант использования, новый столбец с именем `page_resource` был добавлен для предоставления сведения о странице в шестнадцатеричном формате размером 8 байт. Этот столбец был добавлен `sys.dm_exec_requests` и `sys.sysprocesses` и будут добавлены другие динамические административные представления, в будущем при необходимости.

Новая функция `sys.fn_PageResCracker`, принимает `page_resource` качестве входных данных и выводит строку, которая содержит `database_id`, `file_id` и `page_id`.  Затем эту функцию можно использовать для упрощения соединения между `sys.dm_exec_requests` или `sys.sysprocesses` и `sys.dm_db_page_info`.

## <a name="permissions"></a>Разрешения  
Требуется `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-all-the-properties-of-a-page"></a>A. Отображение всех свойств страницы
Следующий запрос возвращает одну строку со всеми сведениями страницы для заданного `database_id`, `file_id`, `page_id` совместно с режимом по умолчанию («ОГРАНИЧЕНО»)

```sql
SELECT *  
FROM sys.dm_db_page_info (5, 1, 15, DEFAULT)
```

### <a name="b-using-sysdmdbpageinfo-with-other-dmvs"></a>Б. С помощью sys.dm_db_page_info с помощью других динамических административных представлений 

Следующий запрос возвращает одну строку для каждого `wait_resource` предоставляемые `sys.dm_exec_requests` когда строка содержит отличный от null `page_resource`

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 'LIMITED') AS page_info
```

## <a name="see-also"></a>См. также  
[Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Динамические административные представления, относящиеся к базе данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)     
[sys.fn_PageResCracker](../../relational-databases/system-functions/sys-fn-pagerescracker-transact-sql.md)


