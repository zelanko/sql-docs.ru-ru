---
description: sys.dm_db_page_info (Transact-SQL)
title: sys. dm_db_page_info (Transact-SQL) | Документация Майкрософт
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
author: bluefooted
ms.author: pamela
manager: amitban
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 60df2ed8bf279bf7da8193282768124815aa6ab3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493697"
---
# <a name="sysdm_db_page_info-transact-sql"></a>sys.dm_db_page_info (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Возвращает сведения о странице в базе данных.  Функция возвращает одну строку, содержащую сведения о заголовке со страницы, включая `object_id` , `index_id` и `partition_id` .  В большинстве случаев эта функция заменяет потребность в использовании `DBCC PAGE`.

> [!NOTE]
> `sys.dm_db_page_info` в настоящее время поддерживается только в [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] и более поздних версиях.


## <a name="syntax"></a>Синтаксис   
```  
sys.dm_db_page_info ( DatabaseId, FileId, PageId, Mode )  
``` 

## <a name="arguments"></a>Аргументы  
*DatabaseID* | NULL | ПАРАМЕТРЫ     
Идентификатор базы данных. *DatabaseID* — это **smallint**. Допустимые входные данные — это ИДЕНТИФИКАЦИОНный номер базы данных. Значение по умолчанию равно NULL, однако Отправка значения NULL для этого параметра приведет к ошибке.
 
*ИД* объекта | NULL | ПАРАМЕТРЫ   
Идентификатор файла. *ИД* имеет **тип int**.  Допустимые входные данные — это ИДЕНТИФИКАЦИОНный номер файла в базе данных, указанной в параметре *DatabaseID*. Значение по умолчанию равно NULL, однако Отправка значения NULL для этого параметра приведет к ошибке.

*Идентификатор страницы* | NULL | ПАРАМЕТРЫ   
Идентификатор страницы.  *Идентификатор страницы* имеет **тип int**.  Допустимые входные данные — это идентификационный номер страницы в файле, указанном как идентификатор *файла.* Значение по умолчанию равно NULL, однако Отправка значения NULL для этого параметра приведет к ошибке.

*Режим* | NULL | ПАРАМЕТРЫ   
Определяет уровень детализации в выходных данных функции. "LIMITED" будет возвращать значения NULL для всех столбцов описания, "DETAILed" заполнит столбцы описания.  Значение по умолчанию — "LIMITED".

## <a name="table-returned"></a>Возвращаемая таблица  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|database_id |INT |Идентификатор базы данных |
|file_id |INT |Идентификатор файла |
|page_id |INT |Идентификатор страницы |
|page_header_version |INT |Версия верхнего колонтитула страницы |
|page_type |INT |Тип страницы |
|page_type_desc |nvarchar (64) |Описание типа страницы |
|page_type_flag_bits |nvarchar (64) |Биты флага типа в заголовке страницы |
|page_type_flag_bits_desc |nvarchar (64) |Описание типа битового флага в заголовке страницы |
|page_flag_bits |nvarchar (64) |Отметить биты в заголовке страницы |
|page_flag_bits_desc |nvarchar(256) |Описание флага битов в заголовке страницы |
|page_lsn |nvarchar (64) |Регистрационный номер или отметка времени в журнале |
|page_level |INT |Уровень страницы в индексе (лист = 0) |
|object_id |INT |Идентификатор объекта, владеющего страницей |
|index_id |INT |Идентификатор индекса (0 для страниц данных кучи) |
|partition_id |BIGINT |Идентификатор секции |
|alloc_unit_id |BIGINT |Идентификатор единицы распределения |
|is_encrypted |bit |Бит, указывающий, зашифрована ли страница |
|has_checksum |bit |Бит, указывающий, имеет ли страница значение контрольной суммы |
|контрольная сумма |INT |Хранит значение контрольной суммы, используемое для обнаружения повреждений данных |
|is_iam_pg |bit |Бит, указывающий, является ли страница IAM-страницей  |
|is_mixed_ext |bit |Бит, указывающий, выделено ли в смешанном экстенте |
|has_ghost_records |bit |Бит, указывающий, содержит ли страница фантомные записи <br> Фантомная запись — это одна из записей, которая была помечена для удаления, но еще не была удалена.|
|has_version_records |bit |Бит, указывающий, содержит ли страница записи версий, используемые для [восстановления базы данных с ускорением](../backup-restore/restore-and-recovery-overview-sql-server.md#adr) |
|pfs_page_id |INT |Идентификатор соответствующей страницы PFS |
|pfs_is_allocated |bit |Бит, указывающий, помечена ли страница как выделенная на соответствующей странице PFS |
|pfs_alloc_percent |INT |Процент выделения, указанный в соответствующем байте PFS |
|pfs_status |nvarchar (64) |Байт PFS |
|pfs_status_desc |nvarchar (64) |Описание байта PFS |
|gam_page_id |INT |Идентификатор соответствующей страницы GAM |
|gam_status |bit |Бит, указывающий, выделено ли в GAM |
|gam_status_desc |nvarchar (64) |Описание бита состояния GAM |
|sgam_page_id |INT |Идентификатор соответствующей страницы SGAM |
|sgam_status |bit |Бит, указывающий, выделено ли в SGAM |
|sgam_status_desc |nvarchar (64) |Описание бита состояния SGAM |
|diff_map_page_id |INT |Идентификатор страницы соответствующей разностной битовой страницы |
|diff_status |bit |Бит, указывающий, изменяется ли состояние diff |
|diff_status_desc |nvarchar (64) |Описание бита состояния diff |
|ml_map_page_id |INT |Идентификатор страницы соответствующей страницы битовой карты минимального журнала |
|ml_status |bit |Бит, указывающий, является ли страница минимальным протоколированием |
|ml_status_desc |nvarchar (64) |Описание минимального бита состояния ведения журнала |
|prev_page_file_id |smallint |Идентификатор файла предыдущей страницы |
|prev_page_page_id |INT |Идентификатор страницы предыдущей страницы |
|next_page_file_id |smallint |Идентификатор файла следующей страницы |
|next_page_page_id |INT |Идентификатор страницы следующей страницы |
|fixed_length |smallint |Длина строк фиксированного размера |
|slot_count |smallint |Общее число слотов (используемых и не используемых) <br> Для страницы данных это число эквивалентно числу строк. |
|ghost_rec_count |smallint |Число записей, помеченных как фантомные на странице <br> Фантомная запись — это одна из записей, которая была помечена для удаления, но еще не была удалена. |
|free_bytes |smallint |Количество свободных байтов на странице |
|free_data_offset |INT |Смещение свободного места в конце области данных |
|reserved_bytes |smallint |Число свободных байтов, зарезервированных всеми транзакциями (если куча) <br> Число фантомных строк (если индексный лист) |
|reserved_bytes_by_xdes_id |smallint |Пространство, задействованное m_xdesID для m_reservedCnt <br> Только в целях отладки |
|xdes_id |nvarchar (64) |Последняя транзакция, созданная m_reserved <br> Только в целях отладки |
||||

## <a name="remarks"></a>Комментарии
`sys.dm_db_page_info`Функция динамического управления возвращает сведения о странице, такие как `page_id` ,, `file_id` `index_id` и `object_id` т. д., которые находятся в заголовке страницы. Эта информация полезна для устранения неполадок и отладки различных показателей производительности (состязание за блокировки и кратковременные блокировки) и проблем повреждения.

`sys.dm_db_page_info` может использоваться вместо `DBCC PAGE` инструкции во многих случаях, но она возвращает только сведения о заголовке страницы, а не текст страницы. `DBCC PAGE` по-прежнему потребуется для случаев использования, когда все содержимое страницы является обязательным.

## <a name="using-in-conjunction-with-other-dmvs"></a>Использование в сочетании с другими динамическими представлениями динамических административных представлений
Одним из важных вариантов использования `sys.dm_db_page_info` является соединение с другими динамическими административными представлениями, которые предоставляют сведения о странице.  Чтобы упростить этот вариант использования, добавлен новый столбец, `page_resource` который предоставляет сведения о странице в 8-байтовом шестнадцатеричном формате. Этот столбец был добавлен в `sys.dm_exec_requests` и `sys.sysprocesses` и будет добавлен в другие динамические административные представления в будущем по мере необходимости.

Новая функция, `sys.fn_PageResCracker` , принимает в `page_resource` качестве входных данных и выводит одну строку, содержащую `database_id` , `file_id` и `page_id` .  Эта функция затем может использоваться для упрощения соединений между `sys.dm_exec_requests` или `sys.sysprocesses` и `sys.dm_db_page_info` .

## <a name="permissions"></a>Разрешения  
Требуется `VIEW DATABASE STATE` разрешение в базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-all-the-properties-of-a-page"></a>A. Отображение всех свойств страницы
Следующий запрос возвращает одну строку со всеми сведениями о странице для заданного `database_id` `file_id` `page_id` сочетания с режимом по умолчанию (Limited).

```sql
SELECT *  
FROM sys.dm_db_page_info (5, 1, 15, DEFAULT)
```

### <a name="b-using-sysdm_db_page_info-with-other-dmvs"></a>Б. Использование Sys. dm_db_page_info с другими динамическими представлениями DMV 

Следующий запрос возвращает одну строку для каждого `wait_resource` предоставляемого, `sys.dm_exec_requests` Если строка содержит значение, отличное от NULL. `page_resource`

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 'LIMITED') AS page_info
```

## <a name="see-also"></a>См. также  
[Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Динамические административные представления, связанные с базами данных &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)     
[sys.fn_PageResCracker](../../relational-databases/system-functions/sys-fn-pagerescracker-transact-sql.md)


