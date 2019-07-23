---
title: Управление Stretch Database и устранение связанных с ней неполадок | Документация Майкрософт
ms.date: 06/27/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, managing
- Stretch Database, troubleshooting
- managing Stretch Database
- troubleshooting Stretch Database
ms.assetid: 6334db3e-9297-44df-8d53-211187a95520
author: rothja
ms.author: jroth
ms.openlocfilehash: 282d712f1ebb870c236917d49beb50423957b2a4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68136109"
---
# <a name="manage-and-troubleshoot-stretch-database"></a>Управление Stretch Database и устранение связанных с ней неполадок
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Для управления Stretch Database и устранения связанных с ней неполадок используйте средства и методы, описанные в этой статье.  
## <a name="manage-local-data"></a>Управление локальными данными  
  
###  <a name="LocalInfo"></a> Получение сведений о локальных базах данных и таблицах, для которых можно включить Stretch Database  
 Откройте представления каталога **sys.databases** и **sys.tables** , чтобы просмотреть сведения о базах данных и таблицах SQL Server с поддержкой растяжения. Дополнительные сведения см. в статьях [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) и [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md).  
 
 Чтобы увидеть, сколько места занимает таблица с поддержкой Stretch в SQL Server, выполните указанную ниже инструкцию.
 
 ```sql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'LOCAL_ONLY';
GO
 ```
   
## <a name="manage-data-migration"></a>Управление переносом данных  
  
### <a name="check-the-filter-function-applied-to-a-table"></a>Проверка функции фильтра, примененного к таблице  
 Откройте представление каталога **sys.remote_data_archive_tables** и проверьте значение столбца **filter_predicate** , чтобы определить, какую функцию использует Stretch Database для выбора строк, которые нужно перенести. Если значение равно NULL, всю таблицу можно переносить. Дополнительные сведения см. в статье [sys.remote_data_archive_tables (Transact-SQL)](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md) и [Выбор строк для переноса с помощью функции фильтра](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).  
  
###  <a name="Migration"></a> Проверка состояния переноса данных  
 В SQL Server Management Studio выберите **Задачи | Stretch | Монитор** для базы данных, чтобы отслеживать перенос данных в мониторе Stretch Database. Дополнительные сведения см. в статьях [Мониторинг переноса данных и устранение неполадок при этой операции (Stretch Database)](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
 Или откройте динамическое административное представление **sys.dm_db_rda_migration_status** , чтобы увидеть, сколько разделов и строк данных были перенесены.  
  
###  <a name="Firewall"></a> Устранение неполадок переноса данных  
 Рекомендации по диагностике см. в статье [Мониторинг переноса данных и устранение неполадок при этой операции (Stretch Database)](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
## <a name="manage-remote-data"></a>Управление удаленными данными  
  
###  <a name="RemoteInfo"></a> Получение сведений об удаленных базах данных и таблицах, используемых с Stretch Database  
 Откройте представления каталога **sys.remote_data_archive_databases** и **sys.remote_data_archive_tables** , чтобы увидеть информацию об удаленных базах данных и таблицах, в которых хранятся переносимые данные. Дополнительные сведения см. в статьях [sys.remote_data_archive_databases (Transact-SQL)](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-databases.md) и [sys.remote_data_archive_tables (Transact-SQL)](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md).  
 
Чтобы увидеть, сколько места занимает таблица с поддержкой Stretch в Azure, выполните указанную ниже инструкцию.
 
 ```sql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'REMOTE_ONLY';
GO
 ```

### <a name="delete-migrated-data"></a>Удаление перенесенных данных  
Если вы хотите удалить данные, уже перенесенные в Azure, выполните действия, описанные в статье [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md).  
  
## <a name="manage-table-schema"></a>Управление схемой таблицы

### <a name="dont-change-the-schema-of-the-remote-table"></a>Не изменяйте схему удаленной таблицы  
 Не изменяйте схему удаленной таблицы Azure, связанной с таблицей SQL Server, которая настроена для использования с Stretch Database. В частности, не следует изменять имя или тип данных столбца. При использовании Stretch Database нужно учитывать некоторые моменты, связанные со схемой удаленной таблицы в отношении схемы таблицы SQL Server. Если вы измените удаленную схему, Stretch Database не будет работать с измененной таблицей.  

### <a name="reconcile-table-columns"></a>Согласование столбцов таблицы  
Если вы случайно стерли столбцы из удаленной таблицы, выполните инструкцию **sp_rda_reconcile_columns** — она добавляет в удаленную таблицу столбцы, существующие в таблице SQL Server с поддержкой Stretch, но отсутствующие в удаленной таблице. Дополнительные сведения см. в статье [sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md).  
  
  > [!IMPORTANT]
  > Воссоздавая столбцы, случайно стертые из удаленной таблицы, процедура **sp_rda_reconcile_columns** не восстанавливает данные, которые прежде присутствовали в стертых столбцах.
  
Процедура**sp_rda_reconcile_columns** не стирает столбцы из удаленной таблицы, существующие в удаленной таблице, но отсутствующие в таблице SQL Server с поддержкой Stretch. Если в удаленной таблице Azure есть столбцы, больше не существующие в таблице SQL Server с поддержкой Stretch, они не мешают нормальной работе Stretch Database. При желании вы можете удалить такие столбцы вручную.  
 
## <a name="manage-performance-and-costs"></a>Управление производительностью и затратами  
  
### <a name="troubleshoot-query-performance"></a>Устранение неполадок с производительностью запросов  
  После включения в таблицах поддержки растяжения запросы, которые включают такие таблицы, выполняются гораздо медленнее. Если производительность запросов снизилась значительно, обратите внимание на следующие моменты.  
  
-   Сервер Azure находится не в одном географическом регионе с SQL Server? Сервер Azure и SQL Server должны находиться в одном географическом регионе для уменьшения задержек в сети.  
  
-   Проблемы с используемой сетью. Обратитесь к администратору сети, чтобы узнать о возможных неполадках или простоях.  
  
### <a name="increase-azure-performance-level-for-resource-intensive-operations-such-as-indexing"></a>Повышение уровня производительности Azure для таких ресурсоемких операций, как индексирование  
 Если вы выполняете сборку, повторную сборку или реорганизацию индекса для большой таблицы, настроенной для использования с Stretch Database, и предполагаете, что при этом в Azure будут активно запрашиваться перенесенные данные, увеличьте уровень производительности соответствующей удаленной базы данных на время операции. Дополнительные сведения об уровнях производительности и ценах см. на странице с [ценами на использование SQL Server Stretch Database](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### <a name="you-cant-pause-the-sql-server-stretch-database-service-on-azure"></a>Не удается приостановить службу SQL Server Stretch Database в Azure  
 Проверьте выбранные уровень производительности и цен. В случае временного увеличения производительности для выполнения ресурсоемкой операции не забудьте вернуть ее к прежнему уровню по завершении операции. Дополнительные сведения об уровнях производительности и ценах см. на странице с [ценами на использование SQL Server Stretch Database](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
   
 ## <a name="change-the-scope-of-queries"></a>Изменение области запросов  
 Запросы к таблицам с поддержкой Stretch по умолчанию возвращают локальные и удаленные данные. Вы можете изменить область запросов для всех запросов всех пользователей или только для отдельного запроса со стороны администратора.  
   
 ### <a name="change-the-scope-of-queries-for-all-queries-by-all-users"></a>Изменение области запросов для всех запросов всех пользователей  
 Чтобы изменить область всех запросов всех пользователей, запустите хранимую процедуру **sys.sp_rda_set_query_mode**. Вы можете ограничить область запросов локальными данными, отключить все запросы или восстановить параметры по умолчанию. Дополнительные сведения см. в статье [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md).  
   
 ### <a name="queryHints"></a>Изменение области запросов для отдельного запроса со стороны администратора  
 Чтобы изменить область отдельного запроса, отправляемого участником роли db_owner, добавьте к инструкции SELECT указание запроса **WITH ( REMOTE_DATA_ARCHIVE_OVERRIDE = *value* )** . Указание запроса REMOTE_DATA_ARCHIVE_OVERRIDE может иметь следующие значения:  
 -   **LOCAL_ONLY**. Запрашиваются только локальные данные.  
   
 -   **REMOTE_ONLY**. Запрашиваются только удаленные данные.  
   
 -   **STAGE_ONLY**. Запрашиваются только данные в таблицах, где Stretch Database подготавливает строки, подходящие для переноса, и хранит перенесенные строки в течение заданного периода времени. Указание запроса — единственный способ запроса промежуточной таблицы.  
  
Например, следующий запрос возвращает только локальные результаты.  
  
 ```sql  
USE <Stretch-enabled database name>;
GO
SELECT * FROM <Stretch_enabled table name> WITH (REMOTE_DATA_ARCHIVE_OVERRIDE = LOCAL_ONLY) WHERE ... ;
GO
```  
   
 ## <a name="adminHints"></a>Выполнение административных обновлений и удалений  
 По умолчанию обновлять или удалять из таблицы с поддержкой Stretch строки, подходящие для переноса, или уже перенесенные строки нельзя. После устранения проблемы участник роли db_owner может выполнить операцию обновления или удаления, добавив к инструкции указание запроса **WITH ( REMOTE_DATA_ARCHIVE_OVERRIDE = *value* )** . Указание запроса REMOTE_DATA_ARCHIVE_OVERRIDE может иметь следующие значения:  
 -   **LOCAL_ONLY**. Обновляются или удаляются только локальные данные.  
   
 -   **REMOTE_ONLY**. Обновляются или удаляются только удаленные данные.  
   
 -   **STAGE_ONLY**. Обновляются или удаляются только данные в таблице, где Stretch Database подготавливает строки, подходящие для переноса, и хранит перенесенные строки в течение заданного периода времени.  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг переноса данных и устранение неполадок при этой операции (Stretch Database)](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md)   
[Резервное копирование баз данных с поддержкой Stretch (Stretch Database)](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
[Восстановление баз данных с поддержкой Stretch (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
  
