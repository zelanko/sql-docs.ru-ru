---
title: "sys.dm_db_missing_index_group_stats (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_group_stats_TSQL
- sys.dm_db_missing_index_group_stats
- dm_db_missing_index_group_stats_TSQL
- dm_db_missing_index_group_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_group_stats dynamic management view
- missing indexes feature [SQL Server], sys.dm_db_missing_index_group_stats dynamic management view
ms.assetid: c2886986-9e07-44ea-a350-feeac05ee4f4
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 62088e8f8f331748e9af63641c89039d38c80ed8
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbmissingindexgroupstats-transact-sql"></a>sys.dm_db_missing_index_group_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает сводку сведений о группах отсутствующих индексов, за исключением пространственных индексов.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются.  
    
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_handle**|**int**|Идентифицирует группу отсутствующих индексов. Этот идентификатор уникален в пределах сервера.<br /><br /> Другие столбцы содержат сведения обо всех запросах, для которых индекс в группе считается отсутствующим.<br /><br /> Группа индексов содержит только один индекс.|  
|**unique_compiles**|**bigint**|Число компиляций и повторных компиляций, которые получают преимущества от этой группы отсутствующих индексов. Компиляции и повторные компиляции многих различных запросов могут влиять на значение этого столбца.|  
|**user_seeks**|**bigint**|Количество операций поиска по запросам пользователя, для которых мог бы использоваться рекомендованный индекс в группе.|  
|**user_scans**|**bigint**|Количество операций просмотра по запросам пользователя, для которых мог бы использоваться рекомендованный индекс в группе.|  
|**last_user_seek**|**datetime**|Дата и время последней операции поиска по запросам пользователя, для которых мог бы использоваться рекомендованный индекс в группе.|  
|**last_user_scan**|**datetime**|Дата и время последней операции просмотра по запросам пользователя, для которых мог бы использоваться рекомендованный индекс в группе.|  
|**avg_total_user_cost**|**float**|Средняя стоимость запросов пользователя, которая могла быть уменьшена с помощью индекса в группе.|  
|**avg_user_impact**|**float**|Средний процент выигрыша, который могли получить запросы пользователя, если создать эту группу отсутствующих индексов. Значение показывает, что стоимость запроса в среднем уменьшится на этот процент, если создать эту группу отсутствующих индексов.|  
|**system_seeks**|**bigint**|Количество операций поиска по запросам системы, таким как запросы auto stats, для которых мог бы использоваться рекомендованный индекс в группе. Дополнительные сведения см. в разделе [класс событий Auto Stats](../../relational-databases/event-classes/auto-stats-event-class.md).|  
|**system_scans**|**bigint**|Количество операций просмотра по запросам системы, для которых мог бы использоваться рекомендованный индекс в группе.|  
|**last_system_seek**|**datetime**|Дата и время последней операции системного поиска по запросам системы, для которых мог бы использоваться рекомендованный индекс в группе.|  
|**last_system_scan**|**datetime**|Дата и время последней операции системного просмотра по запросам системы, для которых мог бы использоваться рекомендованный индекс в группе.|  
|**avg_total_system_cost**|**float**|Средняя стоимость системных запросов, которая могла быть уменьшена с помощью индекса в группе.|  
|**avg_system_impact**|**float**|Средний процент выигрыша, который могли получить запросы системы, если создать эту группу отсутствующих индексов. Значение показывает, что стоимость запроса в среднем уменьшится на этот процент, если создать эту группу отсутствующих индексов.|  
  
## <a name="remarks"></a>Remarks  
 Сведения, возвращаемые функцией **sys.dm_db_missing_index_group_stats** , обновляются при каждом выполнении запроса, не при каждой компиляции или повторной компиляции запроса. Статистика использования не сохраняется и хранится только до перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Администраторы базы данных должны периодически делать резервные копии сведений об отсутствующих индексах, если необходимо сохранить статистику использования после перезагрузки сервера.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения запроса к этому динамическому административному представлению пользователям должно быть предоставлено разрешение VIEW SERVER STATE или любое другое, подразумевающее разрешение VIEW SERVER STATE.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано использование **sys.dm_db_missing_index_group_stats** динамическое административное представление.  
  
### <a name="a-find-the-10-missing-indexes-with-the-highest-anticipated-improvement-for-user-queries"></a>A. Поиск 10 отсутствующих индексов с самым высоким ожидаемым улучшением производительности пользовательских запросов  
 Следующий запрос определяет, какие 10 отсутствующих индексов окажут самое высокое ожидаемое совокупное улучшение производительности запросов пользователя в порядке убывания.  
  
```  
SELECT TOP 10 *  
FROM sys.dm_db_missing_index_group_stats  
ORDER BY avg_total_user_cost * avg_user_impact * (user_seeks + user_scans)DESC;  
```  
  
### <a name="b-find-the-individual-missing-indexes-and-their-column-details-for-a-particular-missing-index-group"></a>Б. Поиск отдельных отсутствующих индексов и подробных сведений об их столбцах для определенной группы отсутствующих индексов  
 Следующий запрос определяет, какие отсутствующие индексы составляют отдельную группу отсутствующих индексов, и отображает подробные сведения об их столбцах. Для данного примера дескриптор группы отсутствующих индексов равен 24.  
  
```  
SELECT migs.group_handle, mid.*  
FROM sys.dm_db_missing_index_group_stats AS migs  
INNER JOIN sys.dm_db_missing_index_groups AS mig  
    ON (migs.group_handle = mig.index_group_handle)  
INNER JOIN sys.dm_db_missing_index_details AS mid  
    ON (mig.index_handle = mid.index_handle)  
WHERE migs.group_handle = 24;  
```  
  
 Этот запрос предоставляет имя базы данных, схемы и таблицы, в которой отсутствует индекс. Он также предоставляет имена столбцов, которые должны использоваться для ключа индекса. При записи инструкции CREATE INDEX DDL для создания отсутствующих индексов, вначале Перечислите столбцы равенства, а затем столбцы неравенства в предложении ON \< *table_name*> инструкции CREATE INDEX. Включенные столбцы должны быть перечислены в предложении INCLUDE инструкции CREATE INDEX. Чтобы определить эффективный порядок столбцов равенства, расположите их на основе их выборности, перечисляя наиболее выбираемые столбцы первыми (крайние левые в списке столбцов).  
  
## <a name="see-also"></a>См. также  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)  
  
  
