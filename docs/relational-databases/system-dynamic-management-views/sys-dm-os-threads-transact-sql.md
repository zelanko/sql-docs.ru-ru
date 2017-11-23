---
title: "sys.dm_os_threads (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_threads_TSQL
- sys.dm_os_threads
- dm_os_threads
- sys.dm_os_threads_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_threads dynamic management view
ms.assetid: a5052701-edbf-4209-a7cb-afc9e65c41c1
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9108fa8c4af25be975394a3388cd26da99b9b595
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosthreads-transact-sql"></a>sys.dm_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает список всех потоков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в операционной системе, запущенных процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_threads**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|thread_address|**varbinary(8)**|Адрес потока в памяти (первичный ключ).|  
|started_by_sqlservr|**bit**|Указывает, кто создал поток:<br /><br /> 1 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запустил поток.<br /><br /> 0 = поток создан другим компонентом, например расширенной хранимой процедурой внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|os_thread_id|**int**|Идентификатор потока, назначенный операционной системой.|  
|status|**int**|Флаг внутреннего состояния.|  
|instruction_address|**varbinary(8)**|Адрес выполняющейся в данный момент инструкции.|  
|creation_time|**datetime**|Время создания потока.|  
|kernel_time|**bigint**|Время работы потока в режиме ядра.|  
|usermode_time|**bigint**|Время работы потока в режиме пользователя.|  
|stack_base_address|**varbinary(8)**|Самый высокий адрес в стеке для данного потока.|  
|stack_end_address|**varbinary(8)**|Самый низкий адрес в стеке для данного потока.|  
|stack_bytes_committed|**int**|Число байтов, сохраненных в стеке.|  
|stack_bytes_used|**int**|Число байтов, используемых потоком в данный момент.|  
|affinity|**bigint**|Маска ЦП, на которой выполняется данный поток. Это зависит от значения, установленного **ALTER SERVER CONFIGURATION SET PROCESS AFFINITY** инструкции. Может отличаться от планировщика в случае мягкой привязки.|  
|Приоритет|**int**|Приоритет данного потока.|  
|Локаль|**int**|Кэшированное значение идентификатора локали (LCID) для данного потока.|  
|Токен|**varbinary(8)**|Кэшированный дескриптор токена олицетворения для данного потока.|  
|is_impersonating|**int**|Указывает, использует ли данный поток олицетворение Win32:<br /><br /> 1 = поток использует учетные данные для обеспечения безопасности, отличающиеся от данных для процесса по умолчанию. Это значит, что поток олицетворяет сущность, отличную от созданной процессом.|  
|is_waiting_on_loader_lock|**int**|Состояние операционной системы, указывающее, ожидает ли поток завершения блокировки загрузчика.|  
|fiber_data|**varbinary(8)**|Текущее волокно Win32, запущенное для потока. Применимо только в случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для использования упрощенных пулов.|  
|thread_handle|**varbinary(8)**|Только для внутреннего применения.|  
|event_handle|**varbinary(8)**|Только для внутреннего применения.|  
|scheduler_address|**varbinary(8)**|Адрес в памяти связанного с данным потоком планировщика. Дополнительные сведения см. в разделе [sys.dm_os_schedulers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|worker_address|**varbinary(8)**|Адрес в памяти связанного с данным потоком исполнителя. Дополнительные сведения см. в разделе [sys.dm_os_workers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|fiber_context_address|**varbinary(8)**|Адрес контекста внутреннего волокна. Применимо только в случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для использования упрощенных пулов.|  
|self_address|**varbinary(8)**|Указатель для обеспечения внутренней согласованности.|  
|processor_group|**smallint**|**Область применения**: начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор Processor_group.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
  
## <a name="examples"></a>Примеры  
 При запуске сервера запускаются потоки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которыми затем связываются рабочие процессы. Однако внешние компоненты, например расширенные хранимые процедуры, могут запускать потоки в процессе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не управляет этими потоками. sys.dm_os_threads может предоставить сведения о неуправляемых потоках, потребляющих ресурсы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процесса.  
  
 Следующий запрос используется для поиска рабочих процессов, выполняющих потоки, не запущенные сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и для получения сведений о времени их выполнения.  
  
> [!NOTE]  
>  Для краткости в следующем запросе в инструкции `*` используется звездочка (`SELECT`). Следует избегать использования звездочки (*) при выполнении запросов к представлениям каталога, динамическим административным представлениям и системным функциям с табличным значением. В будущих обновлениях и версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может добавить столбцы и изменение порядка столбцов в этих представлениях и функциях. Эти изменения могут повредить приложения, которые запрограммированы на определенный порядок и число столбцов.  
  
```  
SELECT *  
  FROM sys.dm_os_threads  
  WHERE started_by_sqlservr = 0;  
```  
  
## <a name="see-also"></a>См. также:  
  [sys.dm_os_workers &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)   
 [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


