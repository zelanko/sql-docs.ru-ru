---
title: sys. dm_os_performance_counters (Transact-SQL) | Документация Майкрософт
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c7b4d78f73af003e93bc662f10f1f95acda2b6a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265714"
---
# <a name="sysdm_os_performance_counters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по строке на каждый счетчик производительности, хранимый на сервере. Сведения о каждом счетчике производительности см. в разделе [Use SQL Server Objects](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]или, используйте имя **sys. dm_pdw_nodes_os_performance_counters**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar (128)**|Категория, к которой принадлежит счетчик.|  
|**counter_name**|**nchar (128)**|Имя счетчика. Для получения дополнительных сведений о счетчике это имя раздела для выбора из списка счетчиков, [используемых SQL Server объектов](../../relational-databases/performance-monitor/use-sql-server-objects.md). |  
|**instance_name**|**nchar (128)**|Имя заданного экземпляра счетчика. Обычно содержит имя базы данных.|  
|**cntr_value**|**bigint**|Текущее значение счетчика.<br /><br /> **Примечание.** Для счетчиков за секунду это значение является кумулятивным. Значение частоты должно быть вычислено выборкой значений в дискретные интервалы времени. Разность между двумя последовательными значениям выборки равна частоте используемого интервала времени.|  
|**cntr_type**|**int**|Тип счетчика, как определено архитектурой производительности Windows. Дополнительные сведения о типах счетчиков производительности см. в разделе [типы счетчиков производительности WMI](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-performance-counter-types) в документации или на сервере Windows Server.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="remarks"></a>Remarks  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображает счетчики производительности операционной системы Windows, выполните следующий запрос [!INCLUDE[tsql](../../includes/tsql-md.md)], чтобы убедиться, что счетчики производительности отключены.  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 Если возвращено 0 строк, значит, счетчики производительности отключены. Затем следует просмотреть журнал установки в поисках ошибки 3409 — «Переустановите файл sqlctr.ini для этого экземпляра и убедитесь, что учетная запись входа экземпляра имеет необходимые разрешения на доступ к реестру».  Эта ошибка означает, что счетчики производительности не включены. Ошибки, находящиеся непосредственно перед ошибкой 3409, должны указывать первопричину сбоя счетчиков производительности. Дополнительные сведения о файлах журнала установки см. в разделе [Просмотр и чтение SQL Server файлов журнала установки](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="permission"></a>Разрешение

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
 
## <a name="examples"></a>Примеры  
 В следующем примере показан возврат значений счетчика производительности.  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>См. также:  
  [SQL Server динамические административные представления, связанные с операционной системой &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


