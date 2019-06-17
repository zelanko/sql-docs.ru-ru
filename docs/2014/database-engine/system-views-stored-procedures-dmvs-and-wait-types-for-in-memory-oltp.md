---
title: Системные представления, хранимые процедуры, динамические административные представления и типы ожидания для выполняющейся в памяти OLTP | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d047cbc4fe3ba3f4945acd9da4f627a05992e779
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62842403"
---
# <a name="system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp"></a>Системные представления, хранимые процедуры, динамические административные представления и типы ожидания для выполняющейся в памяти OLTP
  В этой статье представлены краткие описания многих объектов баз данных, которые поддерживают In-Memory OLTP, и ссылки на них.  
  
### <a name="system-views"></a>Системные представления  
  
|Системное представление|Описание|Функция In-Memory OLTP|  
|-----------------|-----------------|-----------------------------|  
|[sys.data_spaces (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-data-spaces-transact-sql)|Проверьте, содержит ли файловая группа данные, оптимизированные для памяти.|Следующие столбцы показывают дополнительные значения: **тип** и **type_desc**.|  
|[sys.indexes (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)|Проверьте, находится ли индекс в таблице, оптимизированной для памяти.|Следующие столбцы показывают дополнительные значения: **тип** и **type_desc**.|  
|[sys.parameters (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql)|Убедитесь, параметр не допускает значения NULL (для более эффективного выполнения компилируемых в собственном коде хранимых процедур).|**is_nullable** столбца.|  
|[sys.all_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql)|Убедитесь, что хранимая процедура компилируется в собственном режиме.|**uses_native_compilation** столбца.|  
|[sys.sql_modules (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)|Убедитесь, что хранимая процедура компилируется в собственном режиме.|**uses_native_compilation** столбца.|  
|[sys.table_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-table-types-transact-sql)|Проверьте, оптимизирована ли таблица для памяти.|**is_memory_optimized** столбца.|  
|[sys.tables (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Проверьте, если в таблице, оптимизированной для памяти и проверьте параметр устойчивости таблицы.|**Устойчивость**, **durability_desc**, и **is_memory_optimized** столбцы.|  
|[sys.hash_indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-hash-indexes-transact-sql)|Показывают индексы хэша таблицы, оптимизированной для памяти.|Они уникальны для In-memory OLTP.|  
  
### <a name="metadata-functions"></a>Функции метаданных  
  
|Функция метаданных|Описание|Функция In-Memory OLTP|  
|-----------------------|-----------------|-----------------------------|  
|[OBJECTPROPERTYEX (Transact-SQL)](/sql/t-sql/functions/objectproperty-transact-sql)|Проверьте, оптимизированы ли объекты базы данных для памяти.|**ExecIsWithNativeCompilation** и **TableIsMemoryOptimized** свойства.<br /><br /> **IsSchemaBound** свойство поддерживает тип объекта Procedure (возвращают 0 для процедур вместо NULL).|  
|[SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql)|Проверьте, поддерживает ли сервер In-Memory OLTP.|**IsXTPSupported** свойство.|  
  
### <a name="system-stored-procedures"></a>Системные хранимые процедуры  
  
|Хранимая процедура|Описание|  
|----------------------|-----------------|  
|[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)|Привязка базы данных In-Memory OLTP к пулу ресурсов.|  
|[sys.sp_xtp_checkpoint_force_garbage_collection &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-checkpoint-force-garbage-collection-transact-sql)|Запуск сборки мусора в базе данных In-Memory OLTP.|  
|[sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql)|Включение сбора статистики для скомпилированных в собственном коде хранимых процедур.|  
|[sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql)|Включение сбора статистики по запросам для скомпилированных в собственном коде хранимых процедур|  
|[sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)|Слияние данных и разностных файлов.|  
|[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)|Удаление привязки между базой данных и пулом ресурсов.|  
  
## <a name="dynamic-management-views-dmvs"></a>Динамические административные представления  
 Существует несколько динамических административных представлений для таблиц, оптимизированных для памяти.  
  
 Дополнительные сведения см. в разделе [оптимизированных для памяти таблицы динамических административных представлений &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql).  
  
## <a name="wait-types"></a>Типы ожидания  
 Есть несколько типов ожидания, поддерживающих In-Memory OLTP.  
  
 Дополнительные сведения см. в разделе типы ожиданий, которые начинаются с префикса **WAIT_XTP**, и **XTPPROC** в [sys.dm_os_wait_stats &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql) раздела.  
  
## <a name="see-also"></a>См. также  
 [In-Memory OLTP (оптимизация в памяти)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Поддержка Transact-SQL для выполняющейся в памяти OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
