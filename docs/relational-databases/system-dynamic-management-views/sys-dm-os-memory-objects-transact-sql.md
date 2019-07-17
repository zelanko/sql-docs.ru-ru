---
title: sys.dm_os_memory_objects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_memory_objects
- sys.dm_os_memory_objects
- sys.dm_os_memory_objects_TSQL
- dm_os_memory_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_objects dynamic management view
ms.assetid: 5688bcf8-5da9-4ff9-960b-742b671d7096
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ca3a6a8891e74bd795f15e9a374194650e70b197
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265754"
---
# <a name="sysdmosmemoryobjects-transact-sql"></a>sys.dm_os_memory_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает объекты памяти, которые выделяются в настоящее время [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно использовать **sys.dm_os_memory_objects** для анализа использования памяти и для выявления возможных памяти утечек.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**memory_object_address**|**varbinary(8)**|Адрес объекта памяти. Не допускает значение NULL.|  
|**parent_address**|**varbinary(8)**|Адрес родительского объекта памяти. Допускает значение NULL.|  
|**pages_allocated_count**|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Число страниц, выделенных данным объектом. Не допускает значение NULL.|  
|**pages_in_bytes**|**bigint**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Объем памяти в байтах, выделяемый этим экземпляром объекта памяти. Не допускает значение NULL.|  
|**creation_options**|**int**|Только для внутреннего применения. Допускает значение NULL.|  
|**bytes_used**|**bigint**|Только для внутреннего применения. Допускает значение NULL.|  
|**type**|**nvarchar(60)**|Тип объекта памяти.<br /><br /> Указывает компонент, которому принадлежит данный объект памяти, либо функцию объекта памяти. Допускает значение NULL.|  
|**name**|**varchar(128)**|Только для внутреннего применения. Допускает значение NULL.|  
|**memory_node_id**|**smallint**|Идентификатор узла памяти, используемого данным объектом памяти. Не допускает значение NULL.|  
|**creation_time**|**datetime**|Только для внутреннего применения. Допускает значение NULL.|  
|**max_pages_allocated_count**|**int**|**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Максимальное число страниц, выделенных данным объектом. Не допускает значение NULL.|  
|**page_size_in_bytes**|**int**|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Размер страниц в байтах, выделенных данным объектом. Не допускает значение NULL.|  
|**max_pages_in_bytes**|**bigint**|Максимальный объем памяти, который когда-либо использовался данным объектом памяти. Не допускает значение NULL.|  
|**page_allocator_address**|**varbinary(8)**|Адрес средства выделения страниц в памяти. Не допускает значение NULL. Дополнительные сведения см. в разделе [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**creation_stack_address**|**varbinary(8)**|Только для внутреннего применения. Допускает значение NULL.|  
|**sequence_num**|**int**|Только для внутреннего применения. Допускает значение NULL.|  
|**partition_type**|**int**|Тип раздела:<br /><br /> 0 — неделимых объекта памяти<br /><br /> 1 - секционировать памяти объекта, в настоящее время не секционирована<br /><br /> 2 - объект секционировать памяти, секционированных по узлам NUMA. В среде с одним узлом NUMA это эквивалентно 1.<br /><br /> 3 - объект секционировать память, секционированные по ЦП.|  
|**contention_factor**|**real**|Значение, указывающее о конфликтах для данного объекта памяти, 0 означает, что конкуренции нет. Значения обновляются каждый раз, когда указанное число операций выделения памяти были внесены отражающие состязания за соответствующий период. Применяется только к объектам памяти поточно ориентированными.|  
|**waiting_tasks_count**|**bigint**|Число ожиданий данного объекта памяти. Значение этого счетчика увеличивается всякий раз, когда память выделяется из данного объекта памяти. Увеличение — число задач, которые в настоящее время ожидания для доступа к этому объекту памяти. Применяется только к объектам памяти поточно ориентированными. Это оптимальное значение усилий не гарантирует правильность.|  
|**exclusive_access_count**|**bigint**|Указывает, как часто исключительно осуществлялся данный объект памяти. Применяется только к объектам памяти поточно ориентированными.  Это оптимальное значение усилий не гарантирует правильность.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
 **partition_type**, **contention_factor**, **waiting_tasks_count**, и **exclusive_access_count** еще не реализованы в [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   

## <a name="remarks"></a>Примечания  
 Объекты памяти представляют собой кучи. Они обеспечивают выделение памяти с большей точностью, чем клерки памяти. Компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют вместо клерков памяти объекты памяти. Объекты памяти для выделения страниц используют интерфейс средства выделения памяти от клерка памяти. Виртуальные или общие интерфейсы памяти объектами памяти не используются. В зависимости от шаблонов выделения памяти компоненты могут создавать различные типы объектов для выделения областей памяти произвольного размера.  
  
 Стандартный размер страницы для объекта памяти равен 8 КБ. Однако для добавочных объектов памяти размеры страниц могут варьироваться от 512 байт до 8 килобайт.  
  
> [!NOTE]  
>  Размер страницы не означает максимально возможный размер выделенной памяти. Он представляет собой гранулярность выделения страниц, поддерживаемую средством выделения и реализуемую клерком памяти. От объекта памяти можно запросить выделение объема свыше 8 килобайт.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается объем памяти, выделенный каждым типом объектов памяти.  
  
```  
SELECT SUM (pages_in_bytes) as 'Bytes Used', type   
FROM sys.dm_os_memory_objects  
GROUP BY type   
ORDER BY 'Bytes Used' DESC;  
GO  
```  
  
## <a name="see-also"></a>См. также  
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)  
  
  


