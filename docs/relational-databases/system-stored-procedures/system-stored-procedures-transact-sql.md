---
title: Системные хранимые процедуры (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2016 CTP3)
f1_keywords:
- sql13.TSQLSysNoExpandPortal.f1
- sql13.TSQLSysNoExpandPortal.f1_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server]
- APIs [SQL Server]
- stored procedures [SQL Server], categories
- system stored procedures [SQL Server], categories
- system stored procedures [SQL Server]
ms.assetid: a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 912a2c7dbe6f67d67a4ed43b9d51147bbab08ede
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="system-stored-procedures-transact-sql"></a>Системные хранимые процедуры (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] многие задачи администрирования и сбора информации можно выполнять с помощью системных хранимых процедур. Системные хранимые процедуры объединяются в категории, перечисленные в следующей таблице.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Категория|Описание|  
|--------------|-----------------|  
|[Активная Георепликация хранимых процедур](http://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)|Используется для управления для управления конфигурациями активная Георепликация в базе данных SQL Azure|  
|[Хранимые процедуры каталога](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)|Используются для реализации функций словаря данных ODBC и изоляции ODBC-приложений от изменений во внутренних системных таблицах.|  
|[Хранимые процедуры системы отслеживания измененных данных](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)|Используются для включения, отключения или подготовки отчетов об объектах системы отслеживания измененных данных.|  
|[Хранимые процедуры для работы с курсорами](../../relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql.md)|Используются для реализации переменной функциональности курсоров.|  
|[Хранимые процедуры сборщика данных](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)|Используется для работы со сборщиком данных и следующими компонентами: наборами элементов сбора, элементами коллекций и типами коллекций.|  
|[Компонент Database Engine хранимых процедур](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)|Используются для выполнения общих задач по обслуживанию компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)|Используются для работы с электронной почтой в пределах экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Хранимые процедуры плана обслуживания базы данных](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)|Используются для выполнения основных задач, необходимых для управления производительностью базы данных.|  
|[Хранимые процедуры распределенных запросов](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)|Используются для реализации распределенных запросов и управления ими.|  
|[FileStream и хранимые процедуры FileTable &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/54beca08-c012-4ebd-aa68-d8a10d221b64)|Используется для настройки и управления функциями FILESTREAM и FileTable.|  
|[Хранимые процедуры правил брандмауэра &#40;база данных Azure SQL&#41;](../../relational-databases/system-stored-procedures/firewall-rules-stored-procedures-azure-sql-database.md)|Используется для настройки брандмауэра базы данных SQL Azure.|  
|[Компонент Full-Text Search хранимых процедур](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)|Используются для создания полнотекстовых индексов и запросов к ним.|  
|[Общие расширенные хранимые процедуры](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)|Используются, чтобы предоставить внешним программам интерфейс к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения различных задач обслуживания.|  
|[Доставка журналов хранимых процедур](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)|Используются для создания, изменения и отслеживания конфигураций доставки журналов.|  
|[Хранимые процедуры хранилища данных управления &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql.md)|Используется для настройки хранилища данных управления.|  
|[OLE Automation хранимых процедур](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)|Используются, чтобы включить стандартные объекты OLE-автоматизации использования в стандартном пакете [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Хранимые процедуры управления на основе политик](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)|Используется для управления на основе политики.|  
|[Хранимые процедуры PolyBase](http://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)|Добавить или удалить компьютер из группы горизонтального масштабирования PolyBase.|  
|[Хранимые процедуры в хранилище запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)|Используется для настройки производительности.|  
|[Хранимые процедуры репликации](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)|Используются для управления репликацией.|  
|[Безопасность хранимых процедур](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)|Используются для управления безопасностью.|  
|[Моментальный снимок резервной копии хранимых процедур](http://msdn.microsoft.com/library/c278db87-5770-4037-a1e6-b9853a943339)|Использовать удалять архивацию FILE_SNAPSHOT вместе со всеми моментальными снимками или для удаления отдельных файла резервной копии моментальных снимков.|  
|[Хранимые процедуры пространственного индекса](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)|Используется для анализа и повышения производительности индексирования пространственных индексов.|  
|[Хранимые процедуры агента SQL Server](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)|Используются приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для наблюдения за производительностью и активностью.|  
|[Приложение SQL Server Profiler хранимых процедур](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|Используются агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для управления запланированных или зависящих от событий действий.|  
|[Растяжение базы данных, сохраненной процедуры](../../relational-databases/system-stored-procedures/stretch-database-extended-stored-procedures-transact-sql.md)|Используется для переноса баз данных управления.|  
|[Хранимые процедуры временных таблиц](http://msdn.microsoft.com/library/f28ca74e-7876-4592-b794-e78e3690fff6)|Используйте для временных таблиц|  
|[Хранимые процедуры XML](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)|Используются для работы с текстом в формате XML.|  
  
> [!NOTE]  
>  Если не оговорено другое, все системные хранимые процедуры возвращают значение 0, что означает успешное выполнение процедуры. Для сигнализации об ошибке возвращается ненулевое значение.  
  
## <a name="api-system-stored-procedures"></a>Системные хранимые процедуры для работы с API  
 Пользователи, запускающие приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для приложений ADO, OLE DB и ODBC, могут заметить, что эти приложения используют системные хранимые процедуры, не описанные в справочнике по [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эти хранимые процедуры используются [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком Native Client OLE DB и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента для реализации функциональности API базы данных. Эти хранимые процедуры — всего лишь механизм, задействованный поставщиком или драйвером для передачи запросов пользователя экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Они предназначены только для внутреннего использования поставщиком или драйвером. Вызов их явно из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-приложения не поддерживается.  
  
 Sp_createorphan и sp_droporphans хранимые процедуры используются для ODBC **ntext**, **текст**, и **изображения** обработки.  
  
 Хранимая процедура sp_reset_connection используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для поддержки вызовов в транзакциях удаленных хранимых процедур. Кроме того, эта хранимая процедура инициирует события Audit Login и Audit Logout при повторном использовании соединения из пула соединений.  
  
 Системные хранимые процедуры в следующих таблицах используются внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или через клиентские API и не предназначены для общего пользования. Они подвержены изменению, и совместимость не гарантируется.  
  
 Следующие хранимые процедуры описаны в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
|||  
|-|-|  
|sp_catalogs|sp_column_privileges, хранимая процедура|  
|sp_column_privileges_ex|sp_columns|  
|sp_columns_ex|sp_databases|  
|sp_cursor|sp_cursorclose|  
|sp_cursorexecute|sp_cursorfetch|  
|sp_cursoroption|sp_cursoropen|  
|sp_cursorprepare|sp_cursorprepexec|  
|sp_cursorunprepare|sp_execute|  
|sp_datatype_info|sp_fkeys|  
|sp_foreignkeys|sp_indexes|  
|sp_pkeys, хранимая процедура|sp_primarykeys|  
|sp_prepare|sp_prepexec|  
|sp_prepexecrpc|sp_unprepare|  
|sp_server_info|sp_special_columns|  
|sp_sproc_columns|sp_statistics|  
|sp_table_privileges|sp_table_privileges_ex|  
|sp_tables|sp_tables_ex|  
  
 Следующие хранимые процедуры в документации не описаны:  
  
|||  
|-|-|  
|sp_assemblies_rowset|sp_assemblies_rowset_rmt|  
|sp_assemblies_rowset2|sp_assembly_dependencies_rowset|  
|sp_assembly_dependencies_rowset_rmt|sp_assembly_dependencies_rowset2|  
|sp_bcp_dbcmptlevel|sp_catalogs_rowset|  
|sp_catalogs_rowset;2|sp_catalogs_rowset;5|  
|sp_catalogs_rowset_rmt|sp_catalogs_rowset2|  
|sp_check_constbytable_rowset|sp_check_constbytable_rowset;2|  
|sp_check_constbytable_rowset2|sp_check_constraints_rowset|  
|sp_check_constraints_rowset;2|sp_check_constraints_rowset2|  
|sp_column_privileges_rowset|sp_column_privileges_rowset;2|  
|sp_column_privileges_rowset;5|sp_column_privileges_rowset_rmt|  
|sp_column_privileges_rowset2|sp_columns_90|  
|sp_columns_90_rowset|sp_columns_90_rowset_rmt|  
|sp_columns_90_rowset2|sp_columns_ex_90|  
|sp_columns_rowset|sp_columns_rowset;2|  
|sp_columns_rowset;5|sp_columns_rowset_rmt|  
|sp_columns_rowset2|sp_constr_col_usage_rowset|  
|sp_datatype_info_90|sp_ddopen;1|  
|sp_ddopen;10|sp_ddopen;11|  
|sp_ddopen;12|sp_ddopen;13|  
|sp_ddopen;2|sp_ddopen;3|  
|sp_ddopen;4|sp_ddopen;5|  
|sp_ddopen;6|sp_ddopen;7|  
|sp_ddopen;8|sp_ddopen;9|  
|sp_foreign_keys_rowset|sp_foreign_keys_rowset;2|  
|sp_foreign_keys_rowset;3|sp_foreign_keys_rowset;5|  
|sp_foreign_keys_rowset_rmt|sp_foreign_keys_rowset2|  
|sp_foreign_keys_rowset3|sp_indexes_90_rowset|  
|sp_indexes_90_rowset_rmt|sp_indexes_90_rowset2|  
|sp_indexes_rowset|sp_indexes_rowset;2|  
|sp_indexes_rowset;5|sp_indexes_rowset_rmt|  
|sp_indexes_rowset2|sp_linkedservers_rowset|  
|sp_linkedservers_rowset;2|sp_linkedservers_rowset2|  
|sp_oledb_database|sp_oledb_defdb|  
|sp_oledb_deflang|sp_oledb_language|  
|sp_oledb_ro_usrname|sp_primary_keys_rowset|  
|sp_primary_keys_rowset;2|sp_primary_keys_rowset;3|  
|sp_primary_keys_rowset;5|sp_primary_keys_rowset_rmt|  
|sp_primary_keys_rowset2|sp_procedure_params_90_rowset|  
|sp_procedure_params_90_rowset2|sp_procedure_params_rowset|  
|sp_procedure_params_rowset;2|sp_procedure_params_rowset2|  
|sp_procedures_rowset|sp_procedures_rowset;2|  
|sp_procedures_rowset2|sp_provider_types_90_rowset|  
|sp_provider_types_rowset|sp_schemata_rowset|  
|sp_schemata_rowset;3|sp_special_columns_90|  
|sp_sproc_columns_90|sp_statistics_rowset|  
|sp_statistics_rowset;2|sp_statistics_rowset2|  
|sp_stored_procedures|sp_table_constraints_rowset|  
|sp_table_constraints_rowset;2|sp_table_constraints_rowset2|  
|sp_table_privileges_rowset|sp_table_privileges_rowset;2|  
|sp_table_privileges_rowset;5|sp_table_privileges_rowset_rmt|  
|sp_table_privileges_rowset2|sp_table_statistics_rowset|  
|sp_table_statistics_rowset;2|sp_table_statistics2_rowset|  
|sp_tablecollations|sp_tablecollations_90|  
|sp_tables_info_90_rowset|sp_tables_info_90_rowset_64|  
|sp_tables_info_90_rowset2|sp_tables_info_90_rowset2_64|  
|sp_tables_info_rowset|sp_tables_info_rowset;2|  
|sp_tables_info_rowset_64|sp_tables_info_rowset_64;2|  
|sp_tables_info_rowset2|sp_tables_info_rowset2_64|  
|sp_tables_rowset;2|sp_tables_rowset;5|  
|sp_tables_rowset_rmt|sp_tables_rowset2|  
|sp_usertypes_rowset|sp_usertypes_rowset_rmt|  
|sp_usertypes_rowset2|sp_views_rowset|  
|sp_views_rowset2|sp_xml_schema_rowset|  
|sp_xml_schema_rowset2||  
  
## <a name="see-also"></a>См. также  
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Хранимые процедуры (компонент Database Engine)](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [Выполнение хранимых процедур &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)   
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
