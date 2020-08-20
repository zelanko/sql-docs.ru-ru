---
description: Системные хранимые процедуры (Transact-SQL)
title: Системные хранимые процедуры (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
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
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 05be8467516ff84c45268357eb6ab743d5599a05
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645115"
---
# <a name="system-stored-procedures-transact-sql"></a>Системные хранимые процедуры (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] многие задачи администрирования и сбора информации можно выполнять с помощью системных хранимых процедур. Системные хранимые процедуры объединяются в категории, перечисленные в следующей таблице.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Категория|Описание|  
|--------------|-----------------|  
|[Активные хранимые процедуры георепликации](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)|Используется для управления конфигурациями активной георепликации в базе данных SQL Azure|  
|[Хранимые процедуры для работы с каталогом](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)|Используются для реализации функций словаря данных ODBC и изоляции ODBC-приложений от изменений во внутренних системных таблицах.|  
|[Хранимые процедуры системы отслеживания измененных данных](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)|Используются для включения, отключения или подготовки отчетов об объектах системы отслеживания измененных данных.|  
|[Хранимые процедуры для работы с курсорами](../../relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql.md)|Используются для реализации переменной функциональности курсоров.|  
|[Хранимые процедуры сборщика данных](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)|Используется для работы со сборщиком данных и следующими компонентами: наборами элементов сбора, элементами коллекций и типами коллекций.|  
|[Хранимые процедуры для работы с ядром СУБД](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)|Используются для выполнения общих задач по обслуживанию компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Database Mail хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)|Используются для работы с электронной почтой в пределах экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Хранимые процедуры для работы с планами обслуживания базы данных](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)|Используются для выполнения основных задач, необходимых для управления производительностью базы данных.|  
|[Хранимые процедуры распределенных запросов](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)|Используются для реализации распределенных запросов и управления ими.|  
|[Хранимые процедуры FILESTREAM и FileTable &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/54beca08-c012-4ebd-aa68-d8a10d221b64)|Используется для настройки и управления функциями FILESTREAM и FileTable.|  
|[Правила брандмауэра хранимые процедуры &#40;базе данных SQL Azure&#41;](../../relational-databases/system-stored-procedures/firewall-rules-stored-procedures-azure-sql-database.md)|Используется для настройки брандмауэра базы данных SQL Azure.|  
|[Хранимые процедуры для работы с полнотекстовым поиском](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)|Используются для создания полнотекстовых индексов и запросов к ним.|  
|[Общие расширенные хранимые процедуры](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)|Используются, чтобы предоставить внешним программам интерфейс к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения различных задач обслуживания.|  
|[Хранимые процедуры для работы с доставкой журналов](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)|Используются для создания, изменения и отслеживания конфигураций доставки журналов.|  
|[Хранимые процедуры хранилища данных управления (Transact-SQL)](../../relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql.md)|Используется для настройки хранилища управляющих данных.|  
|[Хранимые процедуры OLE Automation](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)|Используются, чтобы включить стандартные объекты OLE-автоматизации использования в стандартном пакете [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Хранимые процедуры управления на основе политики](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)|Используется для управления на основе политики.|  
|[Хранимые процедуры PolyBase](https://msdn.microsoft.com/library/a522b303-bd1b-410b-92d1-29c950a15ede)|Добавление или удаление компьютера из масштабируемой группы Polybase.|  
|[Хранимые процедуры хранилища запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)|Используется для настройки производительности.|  
|[Хранимые процедуры репликации](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)|Используются для управления репликацией.|  
|[Хранимые процедуры для обеспечения безопасности](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)|Используются для управления безопасностью.|  
|[Хранимые процедуры резервного копирования моментальных снимков](https://msdn.microsoft.com/library/c278db87-5770-4037-a1e6-b9853a943339)|Используется для удаления резервной копии FILE_SNAPSHOT вместе со всеми ее моментальными снимками или для удаления отдельного моментального снимка файла резервной копии.|  
|[Хранимые процедуры пространственного индекса ](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)|Используется для анализа и повышения производительности пространственных индексов.|  
|[Хранимые процедуры для работы с агентом SQL Server](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)|Используются приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для наблюдения за производительностью и активностью.|  
|[Хранимые процедуры для работы с приложением SQL Server Profiler](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|Используются агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для управления запланированных или зависящих от событий действий.|  
|[Stretch Database хранимых процедур](../../relational-databases/system-stored-procedures/stretch-database-extended-stored-procedures-transact-sql.md)|Используется для управления Stretch Database.|  
|[Хранимые процедуры временных таблиц](https://msdn.microsoft.com/library/f28ca74e-7876-4592-b794-e78e3690fff6)|Использование для временных таблиц|  
|[Хранимые процедуры для работы с XML](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)|Используются для работы с текстом в формате XML.|  
  
> [!NOTE]  
>  Если не оговорено другое, все системные хранимые процедуры возвращают значение 0, что означает успешное выполнение процедуры. Для сигнализации об ошибке возвращается ненулевое значение.  
  
## <a name="api-system-stored-procedures"></a>Системные хранимые процедуры для работы с API  
 Пользователи, запускающие приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для приложений ADO, OLE DB и ODBC, могут заметить, что эти приложения используют системные хранимые процедуры, не описанные в справочнике по [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эти хранимые процедуры используются [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком собственного клиента OLE DB и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвером ODBC собственного клиента для реализации функций API базы данных. Эти хранимые процедуры — всего лишь механизм, задействованный поставщиком или драйвером для передачи запросов пользователя экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Они предназначены только для внутреннего использования поставщиком или драйвером. Явное обращение из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения на основе не поддерживается.  
  
 Хранимые процедуры sp_createorphan и sp_droporphans используются для обработки в ODBC **ntext**, **Text**и **Image** .  
  
 Хранимая процедура sp_reset_connection используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для поддержки вызовов в транзакциях удаленных хранимых процедур. Кроме того, эта хранимая процедура инициирует события Audit Login и Audit Logout при повторном использовании соединения из пула соединений.  
  
 Системные хранимые процедуры в следующих таблицах используются внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или через клиентские API и не предназначены для общего пользования. Они подвержены изменению, и совместимость не гарантируется.  
  
 Следующие хранимые процедуры описаны в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
:::row:::
    :::column:::
        sp_catalogs
    :::column-end:::
    :::column:::
        sp_column_privileges, хранимая процедура
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_ex
    :::column-end:::
    :::column:::
        sp_columns
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_ex
    :::column-end:::
    :::column:::
        sp_databases
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursor
    :::column-end:::
    :::column:::
        sp_cursorclose
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursorexecute
    :::column-end:::
    :::column:::
        sp_cursorfetch
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursoroption
    :::column-end:::
    :::column:::
        sp_cursoropen
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursorprepare
    :::column-end:::
    :::column:::
        sp_cursorprepexec
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_cursorunprepare
    :::column-end:::
    :::column:::
        sp_execute
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_datatype_info
    :::column-end:::
    :::column:::
        sp_fkeys
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreignkeys
    :::column-end:::
    :::column:::
        sp_indexes
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_pkeys, хранимая процедура
    :::column-end:::
    :::column:::
        sp_primarykeys
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_prepare
    :::column-end:::
    :::column:::
        sp_prepexec
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_prepexecrpc
    :::column-end:::
    :::column:::
        sp_unprepare
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_server_info
    :::column-end:::
    :::column:::
        sp_special_columns
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_sproc_columns
    :::column-end:::
    :::column:::
        sp_statistics
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges
    :::column-end:::
    :::column:::
        sp_table_privileges_ex
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables
    :::column-end:::
    :::column:::
        sp_tables_ex
    :::column-end:::
:::row-end:::

&nbsp;
  
Следующие хранимые процедуры в документации не описаны:  

:::row:::
    :::column:::
        sp_assemblies_rowset
    :::column-end:::
    :::column:::
        sp_assemblies_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_assemblies_rowset2
    :::column-end:::
    :::column:::
        sp_assembly_dependencies_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_assembly_dependencies_rowset_rmt
    :::column-end:::
    :::column:::
        sp_assembly_dependencies_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_bcp_dbcmptlevel
    :::column-end:::
    :::column:::
        sp_catalogs_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_catalogs_rowset;2
    :::column-end:::
    :::column:::
        sp_catalogs_rowset;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_catalogs_rowset_rmt
    :::column-end:::
    :::column:::
        sp_catalogs_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_check_constbytable_rowset
    :::column-end:::
    :::column:::
        sp_check_constbytable_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_check_constbytable_rowset2
    :::column-end:::
    :::column:::
        sp_check_constraints_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_check_constraints_rowset;2
    :::column-end:::
    :::column:::
        sp_check_constraints_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_rowset
    :::column-end:::
    :::column:::
        sp_column_privileges_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_rowset;5
    :::column-end:::
    :::column:::
        sp_column_privileges_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_column_privileges_rowset2
    :::column-end:::
    :::column:::
        sp_columns_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_90_rowset
    :::column-end:::
    :::column:::
        sp_columns_90_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_90_rowset2
    :::column-end:::
    :::column:::
        sp_columns_ex_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_rowset
    :::column-end:::
    :::column:::
        sp_columns_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_rowset;5
    :::column-end:::
    :::column:::
        sp_columns_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_columns_rowset2
    :::column-end:::
    :::column:::
        sp_constr_col_usage_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_datatype_info_90
    :::column-end:::
    :::column:::
        sp_ddopen;1
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;10
    :::column-end:::
    :::column:::
        sp_ddopen;11
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;12
    :::column-end:::
    :::column:::
        sp_ddopen;13
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;2
    :::column-end:::
    :::column:::
        sp_ddopen;3
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;4
    :::column-end:::
    :::column:::
        sp_ddopen;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;6
    :::column-end:::
    :::column:::
        sp_ddopen;7
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_ddopen;8
    :::column-end:::
    :::column:::
        sp_ddopen;9
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset
    :::column-end:::
    :::column:::
        sp_foreign_keys_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset;3
    :::column-end:::
    :::column:::
        sp_foreign_keys_rowset;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset_rmt
    :::column-end:::
    :::column:::
        sp_foreign_keys_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_foreign_keys_rowset3
    :::column-end:::
    :::column:::
        sp_indexes_90_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_90_rowset_rmt
    :::column-end:::
    :::column:::
        sp_indexes_90_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_rowset
    :::column-end:::
    :::column:::
        sp_indexes_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_rowset;5
    :::column-end:::
    :::column:::
        sp_indexes_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_indexes_rowset2
    :::column-end:::
    :::column:::
        sp_linkedservers_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_linkedservers_rowset;2
    :::column-end:::
    :::column:::
        sp_linkedservers_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_oledb_database
    :::column-end:::
    :::column:::
        sp_oledb_defdb
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_oledb_deflang
    :::column-end:::
    :::column:::
        sp_oledb_language
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_oledb_ro_usrname
    :::column-end:::
    :::column:::
        sp_primary_keys_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_primary_keys_rowset;2
    :::column-end:::
    :::column:::
        sp_primary_keys_rowset;3
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_primary_keys_rowset;5
    :::column-end:::
    :::column:::
        sp_primary_keys_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_primary_keys_rowset2
    :::column-end:::
    :::column:::
        sp_procedure_params_90_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedure_params_90_rowset2
    :::column-end:::
    :::column:::
        sp_procedure_params_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedure_params_rowset;2
    :::column-end:::
    :::column:::
        sp_procedure_params_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedures_rowset
    :::column-end:::
    :::column:::
        sp_procedures_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_procedures_rowset2
    :::column-end:::
    :::column:::
        sp_provider_types_90_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_provider_types_rowset
    :::column-end:::
    :::column:::
        sp_schemata_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_schemata_rowset;3
    :::column-end:::
    :::column:::
        sp_special_columns_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_sproc_columns_90
    :::column-end:::
    :::column:::
        sp_statistics_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_statistics_rowset;2
    :::column-end:::
    :::column:::
        sp_statistics_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_stored_procedures
    :::column-end:::
    :::column:::
        sp_table_constraints_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_constraints_rowset;2
    :::column-end:::
    :::column:::
        sp_table_constraints_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges_rowset
    :::column-end:::
    :::column:::
        sp_table_privileges_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges_rowset;5
    :::column-end:::
    :::column:::
        sp_table_privileges_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_privileges_rowset2
    :::column-end:::
    :::column:::
        sp_table_statistics_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_table_statistics_rowset;2
    :::column-end:::
    :::column:::
        sp_table_statistics2_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tablecollations
    :::column-end:::
    :::column:::
        sp_tablecollations_90
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_90_rowset
    :::column-end:::
    :::column:::
        sp_tables_info_90_rowset_64
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_90_rowset2
    :::column-end:::
    :::column:::
        sp_tables_info_90_rowset2_64
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_rowset
    :::column-end:::
    :::column:::
        sp_tables_info_rowset;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_rowset_64
    :::column-end:::
    :::column:::
        sp_tables_info_rowset_64;2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_info_rowset2
    :::column-end:::
    :::column:::
        sp_tables_info_rowset2_64
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_rowset;2
    :::column-end:::
    :::column:::
        sp_tables_rowset;5
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_tables_rowset_rmt
    :::column-end:::
    :::column:::
        sp_tables_rowset2
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_usertypes_rowset
    :::column-end:::
    :::column:::
        sp_usertypes_rowset_rmt
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_usertypes_rowset2
    :::column-end:::
    :::column:::
        sp_views_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_views_rowset2
    :::column-end:::
    :::column:::
        sp_xml_schema_rowset
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        sp_xml_schema_rowset2
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  

## <a name="see-also"></a>См. также  
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Хранимые процедуры (ядро СУБД)](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [Выполнение хранимых процедур &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)   
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
