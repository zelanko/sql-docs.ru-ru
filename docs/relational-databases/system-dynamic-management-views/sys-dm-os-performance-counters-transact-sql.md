---
title: sys.dm_os_performance_counters (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6b96eb24b9b4d9b7a4ca29c610bf3cae2b79a589
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmosperformancecounters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Возвращает по строке на каждый счетчик производительности, хранимый на сервере. Сведения о каждом счетчике производительности см. в разделе [использование объектов SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_performance_counters**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|Категория, к которой принадлежит счетчик.|  
|**counter_name**|**nchar(128)**|Имя счетчика. Чтобы получить дополнительные сведения о счетчике, это имя раздела, выберите в списке счетчиков в [использование объектов SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md). |  
|**имя_экземпляра**|**nchar(128)**|Имя заданного экземпляра счетчика. Обычно содержит имя базы данных.|  
|**cntr_value**|**bigint**|Текущее значение счетчика.<br /><br /> **Примечание:** для посекундных счетчиков данное значение является совокупным. Значение частоты должно быть вычислено выборкой значений в дискретные интервалы времени. Разность между двумя последовательными значениям выборки равна частоте используемого интервала времени.|  
|**cntr_type**|**int**|Тип счетчика, как определено архитектурой производительности Windows. В разделе [типы счетчиков производительности WMI](http://msdn2.microsoft.com/library/aa394569.aspx) на MSDN или в документации Windows Server, Дополнительные сведения о типах счетчиков производительности.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="remarks"></a>Замечания  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображает счетчики производительности операционной системы Windows, выполните следующий запрос [!INCLUDE[tsql](../../includes/tsql-md.md)], чтобы убедиться, что счетчики производительности отключены.  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 Если возвращено 0 строк, значит, счетчики производительности отключены. Затем следует просмотреть журнал установки в поисках ошибки 3409 — «Переустановите файл sqlctr.ini для этого экземпляра и убедитесь, что учетная запись входа экземпляра имеет необходимые разрешения на доступ к реестру».  Эта ошибка означает, что счетчики производительности не включены. Ошибки, находящиеся непосредственно перед ошибкой 3409, должны указывать первопричину сбоя счетчиков производительности. Дополнительные сведения о файлах журналов установки см. в разделе [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
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
  
  


