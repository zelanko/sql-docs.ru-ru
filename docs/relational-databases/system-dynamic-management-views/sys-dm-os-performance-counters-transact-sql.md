---
title: sys.dm_os_performance_counters (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_performance_counters
- sys.dm_os_performance_counters_TSQL
- dm_os_performance_counters_TSQL
- sys.dm_os_performance_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_performance_counters dynamic management view
ms.assetid: a1c3e892-cd48-40d4-b6be-2a9246e8fbff
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dcfe7869767bc9178f9241c3ffa82d166685d7ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62939692"
---
# <a name="sysdmosperformancecounters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по строке на каждый счетчик производительности, хранимый на сервере. Сведения о всех счетчиках производительности, см. в разделе [использование объектов SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_performance_counters**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|Категория, к которой принадлежит счетчик.|  
|**counter_name**|**nchar(128)**|Имя счетчика. Чтобы получить дополнительные сведения о счетчике, это имя раздела, чтобы выбрать из списка счетчиков в [использование объектов SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md). |  
|**instance_name**|**nchar(128)**|Имя заданного экземпляра счетчика. Обычно содержит имя базы данных.|  
|**cntr_value**|**bigint**|Текущее значение счетчика.<br /><br /> **Примечание.** Для посекундных счетчиков данное значение является совокупным. Значение частоты должно быть вычислено выборкой значений в дискретные интервалы времени. Разность между двумя последовательными значениям выборки равна частоте используемого интервала времени.|  
|**cntr_type**|**int**|Тип счетчика, как определено архитектурой производительности Windows. См. в разделе [типы счетчиков производительности WMI](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-performance-counter-types) на документы или документации по Windows Server, Дополнительные сведения о типах счетчиков производительности.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="remarks"></a>Примечания  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображает счетчики производительности операционной системы Windows, выполните следующий запрос [!INCLUDE[tsql](../../includes/tsql-md.md)], чтобы убедиться, что счетчики производительности отключены.  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 Если возвращено 0 строк, значит, счетчики производительности отключены. Затем следует просмотреть журнал установки в поисках ошибки 3409 — «Переустановите файл sqlctr.ini для этого экземпляра и убедитесь, что учетная запись входа экземпляра имеет необходимые разрешения на доступ к реестру».  Эта ошибка означает, что счетчики производительности не включены. Ошибки, находящиеся непосредственно перед ошибкой 3409, должны указывать первопричину сбоя счетчиков производительности. Дополнительные сведения о файлах журнала установки см. в разделе [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="permission"></a>Разрешение

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
 
## <a name="examples"></a>Примеры  
 В следующем примере показан возврат значений счетчика производительности.  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>См. также  
  [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


