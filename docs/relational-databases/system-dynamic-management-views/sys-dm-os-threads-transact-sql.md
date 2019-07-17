---
title: sys.dm_os_threads (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_threads_TSQL
- sys.dm_os_threads
- dm_os_threads
- sys.dm_os_threads_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_threads dynamic management view
ms.assetid: a5052701-edbf-4209-a7cb-afc9e65c41c1
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6ca20c4a8719ee6a80bd6a3c349dd50c8b0df81d
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68258714"
---
# <a name="sysdmosthreads-transact-sql"></a>sys.dm_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает список всех потоков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в операционной системе, запущенных процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Вызывать его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_threads**.  
  
|Имя столбца|Тип данных|Описание|  
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
|Priority|**int**|Приоритет данного потока.|  
|Локаль|**int**|Кэшированное значение идентификатора локали (LCID) для данного потока.|  
|Токен|**varbinary(8)**|Кэшированный дескриптор токена олицетворения для данного потока.|  
|is_impersonating|**int**|Указывает, использует ли данный поток олицетворение Win32:<br /><br /> 1 = поток использует учетные данные для обеспечения безопасности, отличающиеся от данных для процесса по умолчанию. Это значит, что поток олицетворяет сущность, отличную от созданной процессом.|  
|is_waiting_on_loader_lock|**int**|Состояние операционной системы, указывающее, ожидает ли поток завершения блокировки загрузчика.|  
|fiber_data|**varbinary(8)**|Текущее волокно Win32, запущенное для потока. Применимо только в случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для использования упрощенных пулов.|  
|thread_handle|**varbinary(8)**|Только для внутреннего применения.|  
|event_handle|**varbinary(8)**|Только для внутреннего применения.|  
|scheduler_address|**varbinary(8)**|Адрес в памяти связанного с данным потоком планировщика. Дополнительные сведения см. в разделе [sys.dm_os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|worker_address|**varbinary(8)**|Адрес в памяти связанного с данным потоком исполнителя. Дополнительные сведения см. в разделе [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|fiber_context_address|**varbinary(8)**|Адрес контекста внутреннего волокна. Применимо только в случае, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен для использования упрощенных пулов.|  
|self_address|**varbinary(8)**|Указатель для обеспечения внутренней согласованности.|  
|processor_group|**smallint**|**Применимо к**: с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор Processor_group.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение является на.|  
  
## <a name="permissions"></a>Разрешения

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратора сервера** или **администратор Azure Active Directory** учетной записи.   

## <a name="notes-on-linux-version"></a>Заметки о версии Linux

Из-за как ядро SQL работает в Linux некоторые из этих сведений не соответствует Linux диагностических данных. Например `os_thread_id` не совпадают с результатом средств, таких как `ps`,`top` или procfs (/proc/`pid`).  Это происходит из-за платформы абстракцию слоя (SQLPAL), слой между компонентами SQL Server и операционной системы.

## <a name="examples"></a>Примеры  
 При запуске сервера запускаются потоки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которыми затем связываются рабочие процессы. Однако внешние компоненты, например расширенные хранимые процедуры, могут запускать потоки в процессе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не управляет этими потоками. sys.dm_os_threads может предоставить сведения о неуправляемых потоках, потребляющих ресурсы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процесса.  
  
 Следующий запрос используется для поиска рабочих процессов, выполняющих потоки, не запущенные сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и для получения сведений о времени их выполнения.  
  
> [!NOTE]
>  Для краткости в следующем запросе в инструкции `*` используется звездочка (`SELECT`). Следует избегать использования звездочки (*) при выполнении запросов к представлениям каталога, динамическим административным представлениям и системным функциям с табличным значением. В будущих обновлениях и версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может добавить столбцы и изменить порядок столбцов в этих представлениях и функциях. Эти изменения могут повредить приложения, которые запрограммированы на определенный порядок и число столбцов.  
  
```  
SELECT *  
  FROM sys.dm_os_threads  
  WHERE started_by_sqlservr = 0;  
```  
  
## <a name="see-also"></a>См. также  
  [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)   
 [Динамические административные представления, относящиеся к операционной системе SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


