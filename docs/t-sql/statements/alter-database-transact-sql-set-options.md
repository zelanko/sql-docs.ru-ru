---
title: Параметры ALTER DATABASE SET (Transact-SQL) | Документы Майкрософт
description: Сведения о том, как задать параметры базы данных, например автоматическую настройку, шифрование, хранилище запросов в SQL Server и базе данных SQL Azure
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- online database state [SQL Server]
- database options [SQL Server]
- emergency database state [SQL Server]
- databases [SQL Server], options
- read-only databases
- recovery models [SQL Server], switching
- ALTER DATABASE statement, SET options
- offline database state [SQL Server]
- snapshot isolation framework option
- checksums [SQL Server]
- automatic tuning
- SQL plan regression correction
- auto_create_statistics
- auto_update_statistics
- query store options
ms.assetid: f76fbd84-df59-4404-806b-8ecb4497c9cc
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azure-sqldw-latest||=azuresqldb-mi-current
ms.openlocfilehash: ecd914603883f83d5434327c5528688936aee420
ms.sourcegitcommit: 63c6f3758aaacb8b72462c2002282d3582460e0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68495459"
---
# <a name="alter-database-set-options-transact-sql"></a>Параметры ALTER DATABASE SET (Transact-SQL)

Задает параметры базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. См. дополнительные сведения о [других параметрах ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).

Щелкните одну из следующих вкладок, чтобы просмотреть синтаксис, аргументы, примечания, разрешения и примеры для используемой вами версии SQL.

Дополнительные сведения о соглашениях о синтаксисе см. в статье [Соглашения о синтаксисе в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="click-a-product"></a>Выберите продукт!

В следующей строке щелкните имя продукта, который вас интересует. На этой веб-странице отобразится другой контент, относящийся к выбранному продукту.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

> |||||
> |---|---|---|---|
> |**\* _SQL Server \*_** &nbsp;|[Отдельная база данных/эластичный пул Базы данных SQL<br />](alter-database-transact-sql-set-options.md?view=azuresqldb-current)|[Управляемый экземпляр Базы данных SQL<br />](alter-database-transact-sql-set-options.md?view=azuresqldb-mi-current)|[Хранилище данных<br />SQL](alter-database-transact-sql-set-options.md?view=azure-sqldw-latest)|||

&nbsp;

## <a name="sql-server"></a>SQL Server

Зеркальное отображение базы данных, [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] и уровни совместимости баз данных являются параметрами инструкции `SET`, но описаны в отдельных статьях в связи с большим объемом материала. Дополнительные сведения см. в статьях [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md), [ALTER DATABASE (Transact-SQL) SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md) и [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).

Конфигурации уровня базы данных используются для задания нескольких конфигураций базы данных на уровне отдельных баз данных. Дополнительные сведения см. в статье [ALTER DATABASE SCOPED CONFIGURATION](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

> [!NOTE]
> Многие параметры инструкции DATABASE SET можно настроить только для текущего сеанса с помощью [инструкций SET](../../t-sql/statements/set-statements-transact-sql.md). Они часто задаются приложениями при подключении. Параметры инструкции SET уровня сеанса переопределяют значения **ALTER DATABASE SET**. Описанные далее параметры базы данных являются значениями, которые можно задавать для сеансов, не предоставляющих явно другие значения параметра SET.

## <a name="syntax"></a>Синтаксис

```
ALTER DATABASE { database_name | CURRENT }
SET
{
    <option_spec> [ ,...n ] [ WITH <termination> ]
}

<option_spec> ::=
{
    <auto_option>
  | <automatic_tuning_option>
  | <change_tracking_option>
  | <containment_option>
  | <cursor_option>
  | <database_mirroring_option>
  | <date_correlation_optimization_option>
  | <db_encryption_option>
  | <db_state_option>
  | <db_update_option>
  | <db_user_access_option>
  | <delayed_durability_option>
  | <external_access_option>
  | FILESTREAM ( <FILESTREAM_option> )
  | <HADR_options>
  | <mixed_page_allocation_option>
  | <parameterization_option>
  | <query_store_options>
  | <recovery_option>
  | <remote_data_archive_option>
  | <service_broker_option>
  | <snapshot_option>
  | <sql_option>
  | <target_recovery_time_option>
  | <termination>
  | <temporal_history_retention>
}
;

<auto_option> ::=
{
    AUTO_CLOSE { ON | OFF }
  | AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }
  | AUTO_SHRINK { ON | OFF }
  | AUTO_UPDATE_STATISTICS { ON | OFF }
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }
}

<automatic_tuning_option> ::=
{
  AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = { ON | OFF } )
}

<change_tracking_option> ::=
{
  CHANGE_TRACKING
   {
       = OFF
     | = ON [ ( <change_tracking_option_list > [,...n] ) ]
     | ( <change_tracking_option_list> [,...n] )
   }
}

<change_tracking_option_list> ::=
   {
       AUTO_CLEANUP = { ON | OFF }
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }
   }

<containment_option> ::=
   CONTAINMENT = { NONE | PARTIAL }

<cursor_option> ::=
{
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }
  | CURSOR_DEFAULT { LOCAL | GLOBAL }
}

<database_mirroring_option>
  ALTER DATABASE Database Mirroring

<date_correlation_optimization_option> ::=
    DATE_CORRELATION_OPTIMIZATION { ON | OFF }
  
<db_encryption_option> ::=
    ENCRYPTION { ON | OFF | SUSPEND | RESUME }

<db_state_option> ::=
    { ONLINE | OFFLINE | EMERGENCY }

<db_update_option> ::=
    { READ_ONLY | READ_WRITE }

<db_user_access_option> ::=
    { SINGLE_USER | RESTRICTED_USER | MULTI_USER }

<delayed_durability_option> ::=
    DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }

<external_access_option> ::=
{
    DB_CHAINING { ON | OFF }
  | TRUSTWORTHY { ON | OFF }
  | DEFAULT_FULLTEXT_LANGUAGE = { <lcid> | <language name> | <language alias> }
  | DEFAULT_LANGUAGE = { <lcid> | <language name> | <language alias> }
  | NESTED_TRIGGERS = { OFF | ON }
  | TRANSFORM_NOISE_WORDS = { OFF | ON }
  | TWO_DIGIT_YEAR_CUTOFF = { 1753, ..., 2049, ..., 9999 }
}
<FILESTREAM_option> ::=
{
    NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL
  | DIRECTORY_NAME = <directory_name>
}
<HADR_options> ::=
    ALTER DATABASE SET HADR

<mixed_page_allocation_option> ::=
    MIXED_PAGE_ALLOCATION { OFF | ON }

<parameterization_option> ::=
    PARAMETERIZATION { SIMPLE | FORCED }

<query_store_options> ::=
{
    QUERY_STORE
    {
          = OFF
        | = ON [ ( <query_store_option_list> [,...n] ) ]
        | ( < query_store_option_list> [,...n] )
        | CLEAR [ ALL ]
    }
}

<query_store_option_list> ::=
{
      OPERATION_MODE = { READ_WRITE | READ_ONLY }
    | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )
    | DATA_FLUSH_INTERVAL_SECONDS = number
    | MAX_STORAGE_SIZE_MB = number
    | INTERVAL_LENGTH_MINUTES = number
    | SIZE_BASED_CLEANUP_MODE = { AUTO | OFF }
    | QUERY_CAPTURE_MODE = { ALL | AUTO | CUSTOM | NONE }
    | MAX_PLANS_PER_QUERY = number
    | WAIT_STATS_CAPTURE_MODE = { ON | OFF }
    | QUERY_CAPTURE_POLICY = ( <query_capture_policy_option_list> [,...n] )
}

<query_capture_policy_option_list> :: =
{
    STALE_CAPTURE_POLICY_THRESHOLD = number { DAYS | HOURS }
    | EXECUTION_COUNT = number
    | TOTAL_COMPILE_CPU_TIME_MS = number
    | TOTAL_EXECUTION_CPU_TIME_MS = number      
}

<recovery_option> ::=
{
    RECOVERY { FULL | BULK_LOGGED | SIMPLE }
  | TORN_PAGE_DETECTION { ON | OFF }
  | PAGE_VERIFY { CHECKSUM | TORN_PAGE_DETECTION | NONE }
}

<remote_data_archive_option> ::=
{
    REMOTE_DATA_ARCHIVE =
    {
        ON ( SERVER = <server_name> ,
                  {CREDENTIAL = <db_scoped_credential_name>
                     | FEDERATED_SERVICE_ACCOUNT = ON | OFF
                  }
               )
      | OFF
    }
}

<service_broker_option> ::=
{
    ENABLE_BROKER
  | DISABLE_BROKER
  | NEW_BROKER
  | ERROR_BROKER_CONVERSATIONS  
  | HONOR_BROKER_PRIORITY { ON | OFF}
}

<snapshot_option> ::=
{
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }
  | READ_COMMITTED_SNAPSHOT {ON | OFF }
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = {ON | OFF }
}
<sql_option> ::=
{
    ANSI_NULL_DEFAULT { ON | OFF }
  | ANSI_NULLS { ON | OFF }
  | ANSI_PADDING { ON | OFF }
  | ANSI_WARNINGS { ON | OFF }
  | ARITHABORT { ON | OFF }
  | COMPATIBILITY_LEVEL = { 150 | 140 | 130 | 120 | 110 | 100 | 90 }
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }
  | NUMERIC_ROUNDABORT { ON | OFF }
  | QUOTED_IDENTIFIER { ON | OFF }
  | RECURSIVE_TRIGGERS { ON | OFF }
}

<target_recovery_time_option> ::=
    TARGET_RECOVERY_TIME = target_recovery_time { SECONDS | MINUTES }

<termination>::=
{
    ROLLBACK AFTER number [ SECONDS ]
  | ROLLBACK IMMEDIATE
  | NO_WAIT
}
<temporal_history_retention>::=TEMPORAL_HISTORY_RETENTION { ON | OFF }
```

## <a name="arguments"></a>Аргументы

*database_name*         
Имя изменяемой базы данных.

CURRENT         
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Выполняет действие в текущей базе данных. `CURRENT` работает не со всеми параметрами и не во всех контекстах. Если `CURRENT` не работает, укажите имя базы данных.

**\<auto_option> ::=**        

Управляет автоматическими параметрами.        

<a name="auto_close"></a> AUTO_CLOSE { ON | OFF }         
ON         
База данных закрыта правильно, а ее ресурсы освобождены после выхода последнего пользователя.

База данных автоматически открывается, если пользователь снова пытается подключиться к ней. Например, с помощью инструкции `USE database_name`. Работа базы данных может быть корректно завершена, если для параметра AUTO_CLOSE установлено значение ON. В этом случае база данных не открывается, пока пользователь не попытается использовать базу данных при следующем перезапуске [!INCLUDE[ssDE](../../includes/ssde-md.md)].

OFF         
База данных остается открытой после того, как последний пользователь вышел.

Параметр AUTO_CLOSE полезен для настольных баз данных, поскольку он позволяет управлять файлами базы данных так же, как обычными файлами. Они могут быть перемещены, скопированы для создания резервной копии или даже отосланы по электронной почте другим пользователям. AUTO_CLOSE — это асинхронный процесс. Многократное открытие и закрытие базы данных не влияет на производительность.

> [!NOTE]
> В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] или в автономной базе данных параметр AUTO_CLOSE недоступен.
> Состояние этого параметра можно определить, проверив значение столбца is_auto_close_on в представлении каталога sys.databases или свойства IsAutoClose функции DATABASEPROPERTYEX.
>
> Если параметр AUTO_CLOSE имеет значение ON, некоторые столбцы в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) и функция DATABASEPROPERTYEX будут возвращать значение NULL, так как база данных будет недоступна для извлечения данных. Для решения этой проблемы выполните инструкцию USE, чтобы открыть базу данных.
>
> Зеркальное отображение базы данных требует, чтобы параметр AUTO_CLOSE был установлен в состояние OFF.

Если параметр базы данных AUTOCLOSE установлен в значение ON, то действия, инициирующие автоматическое закрытие базы данных, очищают кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 2 (SP2) и выше для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных". Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.

<a name="auto_create_statistics"></a> AUTO_CREATE_STATISTICS { ON | OFF }         
ON         
Оптимизатор запросов в случае необходимости создает статистику по отдельным столбцам в предикатах запросов, чтобы улучшить планы запросов и повысить производительность запросов. Такая статистика по отдельным столбцам создается, когда оптимизатор запросов компилирует запросы. Статистика по отдельным столбцам создается только для столбцов, ни один из которых не является первым столбцом в существующем объекте статистики.

Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.

OFF         
Оптимизатор запросов не создает статистику по отдельным столбцам в предикатах запросов во время компиляции запросов. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_create_stats_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoCreateStatistics функции DATABASEPROPERTYEX.

Дополнительные сведения см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

INCREMENTAL = ON | OFF         
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

Присваивает AUTO_CREATE_STATISTICS значение ON, а INCREMENTAL — значение ON. Он создает автоматически создаваемые статистики как добавочные везде, где поддерживаются добавочные статистики. Значение по умолчанию — OFF. Дополнительные сведения см. в описании [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).

<a name="auto_shrink"></a> AUTO_SHRINK { ON | OFF }     
ON         
Файлы базы данных являются кандидатами на периодическое сжатие.

И файлы данных, и файлы журналов могут быть автоматически сжаты. AUTO_SHRINK уменьшает размер журнала транзакций только в том случае, если вы выбрали простую модель восстановления базы данных или создали резервную копию журнала. Если этот параметр установлен в состояние OFF, файлы базы данных не будут автоматически сжиматься при периодической проверке на неиспользуемое пространство.

При включенном параметре AUTO_SHRINK файлы будут сжаты, если более 25 процентов файла содержит неиспользуемое пространство. Параметр вызывает сжатие файла в один из двух размеров. Он сжимает до большего, если:

- размер, в котором 25 процентов файла не используется;
- размер файла при его создании.

Нельзя сжать базу данных, находящуюся в состоянии только для чтения.

OFF         
Автоматическое сжатие файлов при периодической проверке на неиспользуемое пространство не производится.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_shrink_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoShrink функции DATABASEPROPERTYEX.

> [!NOTE]
> В автономной базе данных параметр AUTO_SHRINK недоступен.

<a name="auto_update_statistics"></a> AUTO_UPDATE_STATISTICS { ON | OFF }         
ON         
Указывает, что оптимизатор запросов обновляет статистику, если она используется в запросе и может оказаться устаревшей. Статистика становится устаревшей, после того как операции вставки, обновления, удаления или слияния изменяют распределение данных в таблице или индексированном представлении. Оптимизатор запросов определяет, устарела ли статистика, подсчитывая операции изменения данных с момента последнего обновления статистики и сравнивая число изменений с пороговым значением. Пороговое значение основано на количестве строк в таблице или индексированном представлении.

Оптимизатор запросов проверяет наличие устаревшей статистики перед компиляцией запроса и выполняет кэшированный план запроса. Оптимизатор запросов с помощью столбцов, таблиц и индексированных представлений в предикате запроса определяет, какая статистика могла устареть. Оптимизатор запросов определяет эти сведения перед компиляцией запроса. Перед выполнением кэшированного плана запроса компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверяет, ссылается ли план запроса на актуальную статистику.

Параметр AUTO_UPDATE_STATISTICS применяется к статистике, создаваемой для индексов и отдельных столбцов в предикатах запросов, и к статистике, создаваемой инструкцией CREATE STATISTICS. Этот параметр также применяется к отфильтрованной статистике.

Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.

Используйте параметр AUTO_UPDATE_STATISTICS_ASYNC, чтобы указать режим обновления статистики: синхронный или асинхронный.

OFF         
Указывает, что оптимизатор запросов не обновляет статистику, если она используется в запросе. Оптимизатор запросов также не обновляет статистику, когда она становится устаревшей. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_update_stats_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoUpdateStatistics функции DATABASEPROPERTYEX.

Дополнительные сведения см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

<a name="auto_update_statistics_async"></a> AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }         
ON         
Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется асинхронно. Оптимизатор запросов не ожидает завершения обновления статистики перед компиляцией запросов.

Установка этого параметра в состояние ON не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в состояние ON.

По умолчанию параметр AUTO_UPDATE_STATISTICS_ASYNC имеет значение OFF, а оптимизатор запросов обновляет статистику в синхронном режиме.

OFF         
Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется синхронно. Оптимизатор запросов ожидает завершения обновления статистики перед компиляцией запросов.

Установка этого параметра в значение OFF не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в значение ON.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_update_stats_async_on в представлении каталога sys.databases.

Дополнительные сведения, описывающие условия применения синхронного и асинхронного обновлений статистики, см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

<a name="auto_tuning"></a> **\<automatic_tuning_option> ::=**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)])

Включает или отключает параметр [автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md) `FORCE_LAST_GOOD_PLAN`.

FORCE_LAST_GOOD_PLAN = { ON | OFF }         
ON         
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] автоматически включает последний известный удачный план для [!INCLUDE[tsql-md](../../includes/tsql-md.md)] запросов, когда новый план SQL приводит к снижению производительности. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] непрерывно отслеживает производительность запроса [!INCLUDE[tsql-md](../../includes/tsql-md.md)] в форсированном плане.

В случае повышения производительности [!INCLUDE[ssde_md](../../includes/ssde_md.md)] будет продолжать использовать последний известный удачный план. Если повышений производительности нет, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] создаст новый план SQL. Инструкция завершится ошибкой, если хранилище запросов не включено или не находится в режиме *Чтение и запись*.

OFF         
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] сообщает о потенциальном снижении производительности запросов, вызванном изменениями планов SQL в представлении [sys.dm_db_tuning_recommendations](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md). Однако эти рекомендации не применяются автоматически. Пользователь может отслеживать активные рекомендации и устранять выявленные проблемы, применяя сценарии [!INCLUDE[tsql-md](../../includes/tsql-md.md)], которые отображаются в представлении. Это значение по умолчанию.

**\<change_tracking_option> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDSFull](../../includes/sssds-md.md)]

Определяет параметры отслеживания изменений. Отслеживание изменений можно включить или отключить, а также установить или изменить параметры. Примеры использования см. далее в этой статье.

ON         
Включает отслеживание изменений для базы данных. При включении отслеживания изменений также необходимо задать параметры AUTO CLEANUP и CHANGE RETENTION.

AUTO_CLEANUP = { ON | OFF }        
ON         
Данные отслеживания изменений автоматически удаляются по истечении заданного срока хранения.

OFF         
Данные отслеживания изменений не удаляются из базы данных.

CHANGE_RETENTION =*retention_period* { DAYS | HOURS | MINUTES }       

Указывает минимальный срок хранения данных отслеживания изменений в базе данных. Данные удаляются, только если для параметра AUTO_CLEANUP установлено значение ON.

*retention_period* — целое число, указывающее числовой компонент срока хранения.

Срок хранения по умолчанию — 2 дня. Минимальный срок хранения составляет 1 минуту. Тип хранения по умолчанию — DAYS.

OFF         
Отключает отслеживание изменений для базы данных. Перед отключением отслеживания изменений для базы данных предварительно отключите отслеживание изменений для всех таблиц.

**\<containment_option> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Управляет параметрами автономной работы базы данных.

CONTAINMENT = { NONE | PARTIAL}         
None         
База данных не является автономной.

PARTIAL         
Это автономная база данных. Задать параметр частичной автономности базы данных невозможно, если в базе данных включена репликация, сбор данных об изменениях или отслеживание изменений. Проверка на наличие ошибок прекращается после обнаружения первой ошибки. Дополнительные сведения об автономных базах данных см. в разделе [Автономные базы данных](../../relational-databases/databases/contained-databases.md).

**\<cursor_option> ::=**        

Управляет параметрами курсора.

CURSOR_CLOSE_ON_COMMIT { ON | OFF }         
ON         
Любые курсоры, открытые при фиксации или откате транзакции, закрываются.

OFF         
Курсоры остаются открытыми при завершении транзакции; откат транзакции закрывает любые курсоры (кроме тех, которые имеют свойства INSENSITIVE или STATIC).

Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CURSOR_CLOSE_ON_COMMIT. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая CURSOR_CLOSE_ON_COMMIT в значение OFF для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md).

Состояние этого параметра можно определить, проверив значение столбца is_cursor_close_on_commit_on в представлении каталога sys.databases или свойства IsCloseCursorsOnCommitEnabled функции DATABASEPROPERTYEX.

CURSOR_DEFAULT { LOCAL | GLOBAL }         
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Управляет тем, какую область (LOCAL или GLOBAL) использует курсор.

LOCAL         
Когда вы указываете область LOCAL и не определяете курсор как GLOBAL при его создании, область действия курсора является локальной. В частности, область действия является локальной по отношению к пакету, хранимой процедуре или триггеру, в котором вы создали курсор. Имя курсора действительно только внутри этой области.

На курсор могут ссылаться локальные переменные пакета, хранимые процедуры, триггеры или выходной параметр хранимой процедуры. Курсор будет неявно освобожден при завершении пакета, хранимой процедуры или триггера. Курсор освобождается, если он не был передан обратно в параметре OUTPUT. Курсор может передаваться обратно в параметре OUTPUT. Если курсор передается таким образом, он будет освобожден, когда последняя переменная, которая ссылается на него, будет освобождена или выйдет из области.

GLOBAL         
Если параметр GLOBAL задан и курсор во время создания не определен как LOCAL, то область курсора глобальна относительно соединения. Имя курсора может использоваться любой хранимой процедурой или пакетом, которые выполняются в соединении.

Курсор неявно освобождается только при отключении. Дополнительные сведения см. в описании [DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_local_cursor_default в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsLocalCursorsDefault функции DATABASEPROPERTYEX.

**\<database_mirroring>**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Описания аргументов см. в статье [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md).

**\<date_correlation_optimization_option> ::=**         
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Управляет параметром date_correlation_optimization.

DATE_CORRELATION_OPTIMIZATION { ON | OFF }         
ON         
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает статистику корреляции, где ограничение FOREIGN KEY связывает любые две таблицы в базе данных, и таблицы имеют столбцы **datetime**.

OFF         
Статистика корреляции не поддерживается.

Для установки параметра DATE_CORRELATION_OPTIMIZATION в состояние ON не должно быть активных соединений с базой данных (за исключением соединения, в котором выполняется инструкция ALTER DATABASE). Впоследствии возможность нескольких соединений будет поддерживаться.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_date_correlation_on в представлении каталога sys.databases.

**\<db_encryption_option> ::=**        

Определяет параметры шифрования базы данных.

ENCRYPTION {ON | OFF | SUSPEND | RESUME}         
ON         
Включает шифрование базы данных.

OFF         
Отключает шифрование базы данных. 

SUSPEND         
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)])         
Позволяет приостанавливать сканирование шифрования после включения или отключения прозрачного шифрования данных либо после смены ключа шифрования.

RESUME         
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)])         
Позволяет возобновить ранее приостановленное сканирование шифрования.

Дополнительные сведения см. в статьях о [прозрачном шифровании данных](../../relational-databases/security/encryption/transparent-data-encryption.md) и [прозрачном шифровании данных для Базы данных SQL Azure](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md).

Если включить шифрование на уровне базы данных, будут зашифрованы все файловые группы. Все новые файловые группы наследуют свойство шифрования. Если любая файловая группа базы данных установлена в состояние **READ ONLY**, операция шифрования базы завершится неуспешно.

Состояние шифрования базы данных и состояние сканирования шифрования можно просмотреть с помощью динамического административного представления [sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md).

**\<db_state_option> ::=**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Управляет состоянием базы данных.

OFFLINE         
База данных аккуратно закрыта и помечена как вне сети. В автономном режиме базу данных невозможно изменить.

ONLINE         
База данных открыта и доступна для использования.

EMERGENCY         
База данных помечена как READ_ONLY, ведение журнала отключено и доступ возможен только элементам предопределенной роли сервера sysadmin. EMERGENCY используется в основном для диагностики. Например, база данных, помеченная как подозрительная из-за поврежденного файла журнала, может быть переведена в состояние EMERGENCY. Таким образом, системный администратор может получить доступ к базе данных только для чтения. Только члены предопределенной роли сервера sysadmin могут перевести базу данных в состояние EMERGENCY.

> [!NOTE]
> **Разрешения**. Разрешение `ALTER DATABASE` на базу данных необходимо для изменения режима базы данных с режима "вне сети" на режим "аварийный". Разрешение `ALTER ANY DATABASE` на уровне сервера требуется, чтобы перевести базу данных из режима "вне сети"в режим "в сети".

Вы можете определить состояние этого параметра с помощью проверки столбца state и state_desc в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md). Вы можете также определить состояние с помощью проверки свойства Status функции [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md). Дополнительные сведения см. в разделе [Состояния базы данных](../../relational-databases/databases/database-states.md).

База данных, находящаяся в состоянии RESTORING, не может быть переведена в состояние OFFLINE, ONLINE или EMERGENCY. База данных может находиться в состоянии RESTORING во время выполнения операции восстановления или тогда, когда при операции восстановления базы данных или файла журнала происходит сбой из-за поврежденного файла резервной копии.

**\<db_update_option> ::=**       

Управляет разрешениями на обновления базы данных.

READ_ONLY         
Пользователи могут считывать данные из базы данных, но не могут изменять их.

> [!NOTE]
> Для улучшения производительности запросов выполните обновление статистики перед тем, как перевести базу данных в режим доступа READ_ONLY. После перевода базы данных в режим READ_ONLY потребуется дополнительная статистика, она будет создана компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] в tempdb. Дополнительные сведения о статистике для базы данных, доступной только для чтения, см. в разделе [Статистика](../../relational-databases/statistics/statistics.md).

READ_WRITE         
База данных доступна для операций чтения и записи.

Чтобы изменить это состояние, необходимо обладать монопольным доступом к базе данных. Дополнительные сведения см. в описании предложения SINGLE_USER.

> [!NOTE]
> Применительно к федеративным базам данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)], инструкция SET { READ_ONLY | READ_WRITE } отключена.

**\<db_user_access_option> ::=**      

Управляет пользовательским доступом к базе данных.

SINGLE_USER         
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Указывает, что только один пользователь одновременно может обращаться к базе данных. Если параметр SINGLE_USER указан и к базе данных подключены другие пользователи, инструкция ALTER DATABASE будет заблокирована, пока все пользователи не отключатся от указанной базы данных. Чтобы переопределить это поведение, см. описание предложения WITH \<termination>.

База данных остается в режиме SINGLE_USER, даже если пользователь, который установил этот параметр, выполнил выход. В этот момент к базе данных могут подключаться и другие пользователи, но одновременно может быть подключен только один.

Перед заданием параметра SINGLE_USER проверьте, чтобы параметру AUTO_UPDATE_STATISTICS_ASYNC было присвоено значение OFF. Если он равен ON, то фоновый поток, используемый для обновления статистики, соединится с базой данных и доступ к базе данных в однопользовательском режиме будет невозможен. Чтобы просмотреть состояние этого параметра, запросите столбец is_auto_update_stats_async_on в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md). Если параметр установлен в значение ON, выполните следующие действия.

1. Установите AUTO_CREATE_STATISTICS_ASYNC в значение OFF.

2. Проверьте наличие активных асинхронных заданий статистики, выполнив запрос к динамическому административному представлению [sys.dm_exec_background_job_queue](../../relational-databases/system-dynamic-management-views/sys-dm-exec-background-job-queue-transact-sql.md).

При наличии активных задач следует либо разрешить завершение задач, либо вручную отменить их при помощи инструкции [KILL STATS JOB](../../t-sql/language-elements/kill-stats-job-transact-sql.md).

RESTRICTED_USER         
Позволяет подключаться к базе данных только членам предопределенной роли базы данных `db_owner` и предопределенной роли сервера `dbcreator` и `sysadmin`. Параметр RESTRICTED_USER не ограничивает их количество. Отключите все соединения с базой данных на период времени, определяемый завершающим предложением инструкции ALTER DATABASE. После того как база данных перешла в состояние RESTRICTED_USER, попытки подключения пользователей, не соответствующими описанным выше условиям, будут отклонены.

MULTI_USER         
Все пользователи, имеющие соответствующие разрешения на подключение к базе данных, будут допущены к базе данных.

Вы можете определить состояние этого параметра с помощью проверки столбца user_access в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства UserAccess функции DATABASEPROPERTYEX.

**\<delayed_durability_option> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Управляет тем, является ли фиксация транзакций полностью устойчивой или отложенной устойчивой.

DISABLED         
Все транзакции, следующие за SET DISABLED, являются полностью устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.

ALLOWED         
Все транзакции, следующие за SET ALLOWED, являются полностью устойчивыми или отложенными устойчивыми, в зависимости от параметра устойчивости, заданного в блоке ATOMIC или инструкции COMMIT.

FORCED         
Все транзакции, следующие за SET FORCED, являются отложенными устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.

**\<external_access_option> ::=**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Управляет возможностью обращения к базе данных из внешних ресурсов, таких как объекты другой базы данных.

DB_CHAINING { ON | OFF }         
ON         
База данных может быть источником или целевой базой данных межбазовой цепочки владения.

OFF         
База данных не может быть членом межбазовой цепочки владения.

> [!IMPORTANT]
> Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распознает эту настройку, если параметр сервера cross db ownership chaining имеет значение 0 (OFF). Если параметр cross db ownership chaining имеет значение 1 (ON), то все пользовательские базы данных могут участвовать в межбазовых цепочках владения, вне зависимости от значения этого параметра. Этот параметр задается с помощью процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).

Для установки этого параметра требуется разрешение CONTROL SERVER для базы данных.

Параметр DB_CHAINING не может быть задан для системных баз данных: master, model и tempdb.

Вы можете определить состояние этого параметра с помощью проверки столбца is_db_chaining_on в представлении каталога sys.databases.

TRUSTWORTHY { ON | OFF }         
ON         
Модули базы данных (например, определяемые пользователем функции или хранимые процедуры), которые используют контекст олицетворения, могут обращаться к ресурсам, находящимся вне базы данных.

OFF         
Модули базы данных в контексте олицетворения не могут обращаться к ресурсам, находящимся вне базы данных.

Параметр TRUSTWORTHY устанавливается в значение OFF при каждом присоединении базы данных.

По умолчанию для всех системных баз данных, кроме msdb, параметр TRUSTWORTHY установлен в значение OFF. Оно не изменяется для баз данных model и tempdb. Рекомендуется никогда не устанавливать параметр TRUSTWORTHY в состояние ON для базы данных master.

Для установки этого параметра требуется разрешение `CONTROL SERVER` для базы данных.

Вы можете определить состояние этого параметра с помощью проверки столбца is_trustworthy_on в представлении каталога sys.databases.

DEFAULT_FULLTEXT_LANGUAGE         
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Задает язык, используемый по умолчанию для полнотекстовых индексированных столбцов.

> [!IMPORTANT]
> Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.

DEFAULT_LANGUAGE         
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Указывает язык, используемый по умолчанию для всех созданных имен входа. Чтобы задать язык, можно указать локальный идентификатор (lcid), название языка или псевдоним языка. Список допустимых имен и псевдонимов языков см. в описании [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md). Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.

NESTED_TRIGGERS         
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Указывает, допустимо ли каскадирование триггеров AFTER, то есть выполнение действия, вызывающего срабатывание другого триггера, который может инициировать другой триггер и т. д. Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.

TRANSFORM_NOISE_WORDS         
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Используется для подавления сообщения об ошибке, если логическая операция по полнотекстовому запросу не срабатывает из-за пропускаемых слов или стоп-слов. Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.

TWO_DIGIT_YEAR_CUTOFF         
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Указывает целое число в промежутке от 1753 до 9999, представляющее пороговое значение года для преобразования двухзначной записи лет в четырехзначную. Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.

**\<FILESTREAM_option> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Управляет параметрами таблиц FileTables.

NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }         
OFF         
Нетранзакционный доступ к данным таблиц FileTable отключен.

READ_ONLY         
Данные FILESTREAM из таблиц FileTable в этой базе данных могут считываться нетранзакционными процессами.

FULL         
Включает полный нетранзакционный доступ к данным FILESTREAM в таблицах FileTable.

DIRECTORY_NAME = *\<directory_name>*          
Имя каталога, совместимое с Windows. Это имя должно быть уникальным среди всех имен каталогов уровня базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Проверка уникальности выполняется без учета регистра, независимо от параметров сортировки. Этот параметр должен быть задан до создания таблицы FileTable в этой базе данных.

**\<HADR_options> ::=**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Дополнительные сведения см. в описании [ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md).

**\<mixed_page_allocation_option> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Управляет возможностью базы данных создавать начальные страницы с использованием смешанного экстента для первых восьми страниц таблицы или индекса.

MIXED_PAGE_ALLOCATION { OFF | ON }         
OFF         
База данных всегда создает начальные страницы с помощью однородных экстентов. OFF — значение по умолчанию.

ON         
База данных может создавать начальные страницы с помощью смешанных экстентов.

Этот параметр имеет значение ON для всех системных баз данных. **tempdb** — это единственная системная база данных, которая поддерживает OFF.

**\<PARAMETERIZATION_option> ::=**         

Управляет параметром параметризации. Дополнительные сведения о параметризации: [Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md#SimpleParam).

PARAMETERIZATION { SIMPLE | FORCED }         
SIMPLE         
Запросы параметризуются на основании поведения базы данных по умолчанию.

FORCED         
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметризует все запросы в базе данных.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_parameterization_forced в представлении каталога sys.databases.

**\<query_store_options> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

ON | OFF | CLEAR [ ALL ]         
Указывает, включено ли хранилище запросов в этой базе данных, а также управляет удалением содержимого хранилища запросов. Дополнительные сведения: [Сценарии использования хранилища запросов](../../relational-databases/performance/query-store-usage-scenarios.md).     

ON         
Включает хранилище запросов.

OFF         
Отключает хранилище запросов. OFF — значение по умолчанию.

CLEAR         
Удаляет содержимое хранилища запросов.

> [!NOTE]
> Для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] необходимо выполнить `ALTER DATABASE SET QUERY_STORE` из пользовательской базы данных. Выполнение этой инструкции из другого экземпляра хранилища данных не поддерживается.

OPERATION_MODE { READ_ONLY | READ_WRITE }         
Описывает режим работы хранилища запросов. 

READ_WRITE         
Хранилище запросов собирает и сохраняет план запроса и статистические данные о выполнении. 

READ_ONLY         
Можно считывать данные из хранилища запросов, но новые сведения не добавляются. Если выделенное свободное место в хранилище запросов будет исчерпано, хранилище переключится в режим работы READ_ONLY.

CLEANUP_POLICY         
Описывает политику хранения данных хранилища запросов. STALE_QUERY_THRESHOLD_DAYS определяет количество дней хранения сведений о запросе в хранилище. STALE_QUERY_THRESHOLD_DAYS имеет тип **bigint**.

DATA_FLUSH_INTERVAL_SECONDS         
Определяет частоту, с которой данные, записанные в хранилище запросов, сохраняются на диск. Для оптимизации производительности данные, собранные хранилищем запросов, асинхронно записываются на диск. Для настройки частоты этой асинхронной передачи используется аргумент DATA_FLUSH_INTERVAL_SECONDS. DATA_FLUSH_INTERVAL_SECONDS имеет тип **bigint**.
 
MAX_STORAGE_SIZE_MB         
Определяет свободное место, выделенное для хранилища запросов. MAX_STORAGE_SIZE_MB имеет тип **bigint**.

INTERVAL_LENGTH_MINUTES         
Определяет временной интервал вычисления статистических данных о среде выполнения в хранилище запросов. Для оптимизации использования свободного места статистические данные о среде выполнения в хранилище вычисляются для фиксированного временного интервала. Этот интервал настраивается с помощью аргумента INTERVAL_LENGTH_MINUTES. INTERVAL_LENGTH_MINUTES имеет тип **bigint**.

SIZE_BASED_CLEANUP_MODE { AUTO | OFF }         
Определяет, активируется ли очистка автоматически, когда общий объем данных приблизится к верхней границе ограничения.

AUTO         
Очистка на основе размера активируется автоматически при достижении размера на диске 90 % от **max_storage_size_mb**. Эта очистка сначала удаляет самые дешевые и самые старые запросы. Она останавливается примерно на 80 % **max_storage_size_mb**. Это значение является значением конфигурации по умолчанию.

OFF         
Очистка на основе размера не будет автоматически активирована.

SIZE_BASED_CLEANUP_MODE имеет тип **nvarchar**.

QUERY_CAPTURE_MODE { ALL | AUTO | NONE | CUSTOM }         
Определяет режим записи текущего активного запроса. В каждом режиме определяются собственные политики записи.

> [!NOTE]
> Курсоры, запросы в хранимых процедурах и скомпилированные в собственном коде запросы всегда записываются, если задан режим записи запроса ALL, AUTO или CUSTOM.

ALL         
Записывает все запросы. ALL — значение по умолчанию. Это значение конфигурации по умолчанию, начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].

AUTO         
Записываются соответствующие запросы на основе показателя выполнения и объема потребления ресурсов. Это значение конфигурации по умолчанию, начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 3.0.

None         
Запись новых запросов останавливается. Хранилище запросов будет продолжать сбор статистики компиляции и времени выполнения для запросов, которые уже были записаны. Эту конфигурацию следует использовать с осторожностью, поскольку можно пропустить запись важных запросов.

CUSTOM         
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 3.0)

Позволяет управлять параметрами QUERY_CAPTURE_POLICY.

QUERY_CAPTURE_MODE имеет тип **nvarchar**.

MAX_PLANS_PER_QUERY         
Определяет максимальное количество поддерживаемых планов для каждого запроса. Значение по умолчанию равно 200. MAX_PLANS_PER_QUERY имеет тип **int**.

**\<query_capture_policy_option_list> :: =**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 3.0)

Управляет параметрами политики записи для хранилища запросов. За исключением STALE_CAPTURE_POLICY_THRESHOLD, эти параметры определяют условия OR, которые должны выполняться для запросов, записываемых в определенное пороговое значение устаревшей политики записи.

STALE_CAPTURE_POLICY_THRESHOLD = *number* { DAYS | HOURS }         
Определяет период интервала ознакомления для определения того, нужно ли записать запрос. Значение по умолчанию — 1 день, можно указать от 1 часа до 7 дней. *number* имеет тип **int**.

EXECUTION_COUNT         
Определяет количество выполнений запроса в течение ознакомительного периода. Значение по умолчанию — 30, то есть для порогового значения устаревшей политики записи по умолчанию запрос должен быть выполнен по меньшей мере 30 раз за один день, чтобы быть сохраненным в хранилище запросов. EXECUTION_COUNT имеет тип **int**.

TOTAL_COMPILE_CPU_TIME_MS         
Определяет общее время ЦП, затраченное на компиляцию, которое запрос использовал за ознакомительный период. Значение по умолчанию — 1000, то есть для порогового значения устаревшей политики записи по умолчанию запрос должен иметь общее время ЦП, затраченное на компиляцию, не менее одной секунды за один день, чтобы быть сохраненным в хранилище запросов. TOTAL_COMPILE_CPU_TIME_MS имеет тип **int**.

TOTAL_EXECUTION_CPU_TIME_MS         
Определяет общее время ЦП, затраченное на выполнение, которое запрос использовал за ознакомительный период. Значение по умолчанию — 100, то есть для порогового значения устаревшей политики записи по умолчанию запрос должен иметь общее время ЦП, затраченное на выполнение, не менее 100 мс за один день, чтобы быть сохраненным в хранилище запросов. TOTAL_EXECUTION_CPU_TIME_MS имеет тип **int**.

**\<recovery_option> ::=**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Управляет параметрами восстановления базы данных и проверкой ошибок дискового ввода-вывода.

FULL         
Обеспечивает полное восстановление после отказа носителя с помощью резервных копий журнала транзакций. Если файл данных поврежден, восстановление носителя может восстановить все зафиксированные транзакции. Дополнительные сведения см. в статье о [моделях восстановления](../../relational-databases/backup-restore/recovery-models-sql-server.md).

BULK_LOGGED         
Обеспечивает восстановление после сбоя носителя. Объединяет оптимальную производительность и минимальный объем пространства, занимаемого журналами; используется для больших систем или массовых операций. Сведения о том, к каким операциям можно применять минимальное протоколирование, см. в [описании журнала транзакций](../../relational-databases/logs/the-transaction-log-sql-server.md). В модели восстановления BULK_LOGGED ведение журнала для этих операций минимально. Дополнительные сведения см. в статье о [моделях восстановления](../../relational-databases/backup-restore/recovery-models-sql-server.md).

SIMPLE         
Предусматривается стратегия простого резервирования, которая использует минимальное пространство под журналы. Пространство, отведенное под журналы, может быть автоматически многократно использовано, если оно больше не требуется для восстановления сбоев сервера. Дополнительные сведения см. в статье о [моделях восстановления](../../relational-databases/backup-restore/recovery-models-sql-server.md).

> [!IMPORTANT]
> Простая модель восстановления проще в управлении, чем другие две модели, но больше подвержена потере данных, если файл данных поврежден. Все изменения, начиная с наиболее свежей резервной копии базы данных или разностной резервной копии базы данных, будут потеряны и должны быть повторно введены вручную.

Модель восстановления по умолчанию определяется моделью восстановления базы данных **model**. Дополнительные сведения о выборе подходящей модели восстановления см. в статье [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md).

Вы можете определить состояние этого параметра с помощью проверки столбца **recovery_model** и **recovery_model_desc** в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства Recovery функции DATABASEPROPERTYEX.

TORN_PAGE_DETECTION { ON | OFF }         
ON         
Неполные страницы могут быть обнаружены компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].

OFF         
Неполные страницы невозможно обнаружить с помощью [!INCLUDE[ssDE](../../includes/ssde-md.md)].

> [!IMPORTANT]
> Синтаксическая структура TORN_PAGE_DETECTION ON | OFF будет удалена в будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этой структуры в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Вместо этого используйте параметр PAGE_VERIFY.

<a name="page_verify"></a> PAGE_VERIFY { CHECKSUM | TORN_PAGE_DETECTION | NONE }         
Обнаруживает поврежденные страницы базы данных, вызванные ошибками пути дискового ввода-вывода. Ошибки пути дисковых операций ввода-вывода могут быть причиной повреждения базы данных. Эти ошибки чаще всего вызваны сбоями питания или сбоями оборудования диска, которые происходят во время записи страницы на диск.

CHECKSUM         
Вычисляет контрольную сумму по содержимому целой страницы и сохраняет полученное значение в ее заголовке при записи страницы на диск. При чтении страницы с диска контрольная сумма вычисляется повторно и сравнивается с сохраненным в заголовке страницы значением. Если значения не соответствуют, будет выведено сообщение об ошибке 824 (ошибка контрольной суммы) как в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и в журнал событий Windows. Ошибка контрольной суммы указывает на проблему пути ввода-вывода. Чтобы определить первопричину, необходимо исследовать оборудование, драйверы встроенного ПО, BIOS, фильтрующее программное обеспечение (например, антивирусное) и другие компоненты ввода-вывода.

TORN_PAGE_DETECTION         
Сохраняет определенный двухбитовый шаблон для каждого 512-байтового сектора в 8-килобайтной (КБ) странице базы данных и сохраняет в базе данных заголовок страницы при записи страницы на диск. При чтении страницы с диска биты разрыва, хранимые в заголовке страницы, сравниваются с действительными сведениями о секторах страницы.

Несовпадающие значения указывают, что только часть страницы была записана на диск. В этой ситуации сообщение об ошибке 824 (ошибка разрыва страницы) будет выведено как в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и в журнал событий Windows. Разорванные страницы обычно обнаруживаются при восстановлении базы данных, если они действительно не полностью записаны. Однако другие сбои пути ввода-вывода могут стать причиной разрыва страницы в любое время.

None         
Записи страниц базы данных не создают значение CHECKSUM или TORN_PAGE_DETECTION. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не будет проверять контрольную сумму и разрывы страниц при считывании, даже если значение CHECKSUM или TORN_PAGE_DETECTION будет присутствовать в заголовке страницы.

Рассмотрите следующие важные моменты при использовании параметра PAGE_VERIFY.

- Значение по умолчанию — CHECKSUM.
- При обновлении пользовательской или системной базы данных до версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней сохраняется значение PAGE_VERIFY (NONE или TORN_PAGE_DETECTION). Рекомендуется использовать CHECKSUM.

    > [!NOTE]
    > В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметру базы данных PAGE_VERIFY присваивается значение NONE применительно к базе данных tempdb, которая не может быть изменена. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях значением по умолчанию для базы данных tempdb является CHECKSUM для новых установок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После обновления установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значением по умолчанию остается NONE. Этот параметр можно изменять. Для работы с базой данных tempdb рекомендуется использовать CHECKSUM.

- Значение TORN_PAGE_DETECTION использует меньше ресурсов, но обеспечивает минимальный вариант защиты CHECKSUM.
- Аргумент PAGE_VERIFY можно установить, не производя перевод базы данных в режим "вне сети", блокировку или прочие действия, нарушающие ее параллелизм.
- Значения CHECKSUM и TORN_PAGE_DETECTION являются взаимоисключающими. Оба параметра не могут быть включены одновременно.

При обнаружении ошибки разрыва страницы или контрольной суммы ее можно устранить с помощью восстановления из копии или потенциального перестроения индекса, если сбой ограничен только страницами индекса. При обнаружении ошибки контрольной суммы выполните инструкцию DBCC CHECKDB, чтобы определить тип поврежденной страницы базы данных. Дополнительные сведения о параметрах восстановления см. в [описании аргументов инструкции RESTORE](../../t-sql/statements/restore-statements-arguments-transact-sql.md). Хотя восстановление данных решит проблему нарушения целостности данных, первопричина, например сбой оборудования диска, должна быть обнаружена и исправлена как можно скорее, чтобы предотвратить следующие ошибки.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторяет любую операцию считывания, которая закончилась ошибкой контрольной суммы, разрыва страницы или другой ошибкой ввода-вывода, четыре раза. Если чтение выполнено успешно в любой из повторных попыток, сообщение записывается в журнал ошибок. Команда, которая активировала считывание, продолжится. Команда закончит работу с сообщением об ошибке 824, если все повторные попытки закончатся ошибкой.

Дополнительные сведения о сообщениях об ошибках 823, 824 и 825 см. в разделе:

- [Устранение неполадок с ошибкой 823 сообщений в SQL Server](https://support.microsoft.com/help/2015755)
- [Устранение неполадок Msg 824 в SQL Server](https://support.microsoft.com/help/2015756)
- [Устранение неполадок с ошибкой повторного чтения](https://support.microsoft.com/help/2015757).

Состояние этого параметра можно определить с помощью проверки значения столбца *page_verify_option* в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) или свойства *IsTornPageDetectionEnabled* функции [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md).

**\<remote_data_archive_option> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Включает или отключает Stretch Database для базы данных. Дополнительные сведения см. в разделе [Stretch Database](../../sql-server/stretch-database/stretch-database.md).

REMOTE_DATA_ARCHIVE = { ON ( SERVER = \<server_name> , { CREDENTIAL = \<db_scoped_credential_name> | FEDERATED_SERVICE_ACCOUNT = ON | OFF } )| OFF         
ON         
Включает Stretch Database для базы данных. Дополнительные сведения, включая предварительные условия, см. в разделе [Включение Stretch Database для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).

**Разрешения**: Чтобы включить Stretch Database для таблицы или базы данных, требуются разрешения `db_owner`. Чтобы включить Stretch Database для базы данных, также нужны разрешения `CONTROL DATABASE`.

SERVER = \<server_name>         
Указывает адрес сервера Azure. Включает часть `.database.windows.net` имени. Например, `MyStretchDatabaseServer.database.windows.net`.

CREDENTIAL = \<db_scoped_credential_name>         
Указывает учетные данные для базы данных, используемые экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для подключения к серверу Azure. Перед выполнением этой команды убедитесь в наличии учетных данных. Дополнительные сведения см. в описании [CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

FEDERATED_SERVICE_ACCOUNT = { ON | OFF }         
Вы можете использовать федеративную учетную запись службы для взаимодействия локального SQL Server с удаленным сервером Azure при выполнении следующих условий.

- Учетная запись службы, под которой работает экземпляр SQL Server, является доменной учетной записью.
- Учетная запись домена принадлежит к домену, Active Directory которого входит в федерацию с Azure Active Directory.
- Удаленный сервер Azure настроен для поддержки проверки подлинности Azure Active Directory.
- Учетная запись службы, под которой выполняется экземпляр SQL Server, должна быть настроена как учетная запись `dbmanager` или `sysadmin` на удаленном сервере Azure.

Если указано значение ON для федеративной учетной записи службы, невозможно также указать аргумент CREDENTIAL. Следует указать аргумент CREDENTIAL, если указано значение OFF.

OFF         
Отключает Stretch Database для базы данных. Дополнительные сведения см. в разделе [Отключение Stretch Database и возврат удаленных данных](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).

Отключить Stretch Database можно только после того, как база данных больше не будет содержать таблицы, которые включены для Stretch Database. После отключения Stretch Database перенос данных останавливается. Кроме того, результаты запроса больше не содержат результаты из удаленной таблицы.

Отключение Stretch Database не приводит к стиранию удаленной базы данных. Если вам нужно удалить удаленную базу данных, воспользуйтесь порталом Azure.
 
**\<service_broker_option> ::=**          
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

Управляет следующими параметрами компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]: включает и отключает доставку сообщений, задает новый идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] или устанавливает приоритеты диалога в значение ON или OFF.

ENABLE_BROKER         
Определяет, что для указанной базы данных включен компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Запущена доставка сообщений, и флаг is_broker_enabled установлен в значение TRUE в представлении каталога sys.databases. В базе данных сохраняется существующий идентификатор [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Service Broker не может быть включен, пока база данных является субъектом в конфигурации зеркального отображения базы данных.

> [!NOTE]
> Параметр ENABLE_BROKER требует монопольной блокировки базы данных. Если ресурсы базы данных блокированы другими сеансами, параметр ENABLE_BROKER будет ожидать снятия блокировок этими сеансами. Чтобы включить компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] в пользовательской базе данных, до запуска инструкции ALTER DATABASE SET ENABLE_BROKER убедитесь, что никакие другие сеансы не используют базу данных; это можно сделать, например, переводом базы данных в однопользовательский режим. Чтобы включить компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] в базе данных msdb, сначала необходимо остановить службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] мог получить необходимую блокировку.

DISABLE_BROKER         
Указывает, что для заданной базы данных компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] отключен. Остановлена доставка сообщений, и флаг is_broker_enabled установлен в значение FALSE в представлении каталога sys.databases. В базе данных сохраняется существующий идентификатор [!INCLUDE[ssSB](../../includes/sssb-md.md)].

NEW_BROKER         
Указывает, что база данных должна получить новый идентификатор посредника. База данных действует как новый посредник службы. Все существующие сеансы связи в базе данных будут немедленно удалены, не выдавая диалоговых сообщений о завершении. Все маршруты, ссылающиеся на старый идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], необходимо создать повторно с новым идентификатором.

ERROR_BROKER_CONVERSATIONS         
Указывает, что включена доставка сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Параметр сохраняет имеющийся идентификатор [!INCLUDE[ssSB](../../includes/sssb-md.md)] для базы данных. [!INCLUDE[ssSB](../../includes/sssb-md.md)] завершает ошибкой все диалоги в базе данных. Параметр дает возможность приложениям выполнять регулярную очистку существующих диалогов.

HONOR_BROKER_PRIORITY {ON | OFF}         
ON         
Операции Send выполняются с учетом уровней приоритета, присвоенных диалогам. Сообщения от диалогов с высокими уровнями приоритета отправляются раньше сообщений от диалогов с низким приоритетом.

OFF         
Операции Send выполняются, как если бы все диалоги имели приоритет по умолчанию.

Изменение параметра HONOR_BROKER_PRIORITY имеет мгновенный эффект для новых диалогов или диалогов, ожидающих отправки сообщений. Диалоги, ожидающие отправки сообщений при выполнении ALTER DATABASE, не получат новое значение, пока им не будет отправлено несколько сообщений. Время, необходимое для начала использования нового значения всеми диалогами, может значительно изменяться.

Текущее значение этого свойства содержится в столбце is_broker_priority_honored представления каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).

**\<snapshot_option> ::=**         

Вычисляет уровень изоляции транзакции.

ALLOW_SNAPSHOT_ISOLATION { ON | OFF }         
ON         
Включает параметр моментальных снимков на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После установки этого параметра транзакции могут задавать уровень изоляции транзакций SNAPSHOT. Если транзакция выполняется на уровне изоляции SNAPSHOT, всем инструкциям видны данные из моментального снимка в состоянии, которое существовало в момент начала транзакции. Если транзакция выполняется с уровнем изоляции SNAPSHOT и обращается к данным нескольких баз данных, то либо параметр ALLOW_SNAPSHOT_ISOLATION должен быть установлен в состояние ON во всех базах данных, либо каждая инструкция в транзакции должна использовать подсказки блокировки при любом обращении предложения FROM к таблице базы данных, в которой параметр ALLOW_SNAPSHOT_ISOLATION установлен в состояние OFF.

OFF         
Отключает параметр моментальных снимков на уровне базы данных. Транзакции не могут указывать уровень изоляции SNAPSHOT.

Если вы изменяете состояние ALLOW_SNAPSHOT_ISOLATION (из ON в OFF или из OFF в ON), инструкция ALTER DATABASE не возвращает управление вызвавшей ее программе, пока все существующие транзакции в базе данных не будут зафиксированы. Если база данных уже находится в состоянии, указанном в инструкции ALTER DATABASE, управление вызвавшей программе будет возвращено немедленно. Используйте процедуру [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md), чтобы определить наличие длительно выполняющихся транзакций. Если инструкция ALTER DATABASE отменена, база данных останется в состоянии, в котором она находилась при запуске ALTER DATABASE. Представление каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) отображает состояние транзакций с уровнем изоляции моментальных снимков в базе данных. Если **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON, ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF, операция будет повторена через шесть секунд.

Изменить состояние ALLOW_SNAPSHOT_ISOLATION невозможно, если база данных находится в режиме OFFLINE.

При установке параметра ALLOW_SNAPSHOT_ISOLATION в базе данных, находящейся в режиме READ_ONLY, он будет сохранен при переводе базы данных в режим READ_WRITE.

Настройки ALLOW_SNAPSHOT_ISOLATION можно изменить и для баз данных master, model, msdb и tempdb. Если изменить значение для базы данных tempdb, оно будет сохраняться каждый раз при остановке и перезапуске экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.

Этот параметр для баз данных master и msdb по умолчанию установлен в состояние ON.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца snapshot_isolation_state в представлении каталога sys.databases.

READ_COMMITTED_SNAPSHOT { ON | OFF }         
ON         
Включает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После включения этого параметра транзакции, указывающие уровень изоляции READ COMMITTED, используют управление версиями строк вместо блокировки. Данные моментального снимка видны всем инструкциям в состоянии, которое существовало на момент начала выполнения инструкции, если транзакция выполняется с уровнем изоляции зафиксированной операции чтения.

OFF         
Отключает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Транзакции с уровнем изоляции READ COMMITTED используют блокировку.

Чтобы установить параметр READ_COMMITTED_SNAPSHOT в значение ON или OFF, с базой данных не должно быть активных соединений, за исключением соединения, выполняющего команду ALTER DATABASE. Однако это не означает, что база данных должна находиться в однопользовательском режиме. Изменить состояние этого параметра невозможно, если база данных находится в режиме OFFLINE.

При установке параметра READ_COMMITTED_SNAPSHOT в базе данных, которая находится в режиме READ_ONLY, это состояние будет сохранено при переводе базы данных в режим READ_WRITE.

Параметр READ_COMMITTED_SNAPSHOT не может быть установлен в ON для системных баз данных master, tempdb или msdb. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_read_committed_snapshot_on в представлении каталога sys.databases.

> [!WARNING]
>Если таблица создается с аргументом **DURABILITY = SCHEMA_ONLY**, а затем **READ_COMMITTED_SNAPSHOT** меняется с помощью **ALTER DATABASE**, данные в таблице будут утеряны.

MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }         
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

ON         
Если уровень изоляции транзакции установлен в любое значение ниже SNAPSHOT, все интерпретированные операции [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах, оптимизированных для памяти, выполняются с уровнем изоляции SNAPSHOT. Примеры уровней изоляции ниже, чем моментальный снимок — READ COMMITTED или READ UNCOMMITTED. Эти операции выполняются независимо от того, установлен ли уровень изоляции транзакции явно на уровне сеанса или неявно используется значение по умолчанию.

OFF         
Не повышает уровень изоляции транзакции для интерпретированных операций [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах, оптимизированных для памяти.

Изменить состояние MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT невозможно, если база данных находится в режиме OFFLINE.

Значение по умолчанию — OFF.

Текущее состояние этого параметра можно определить, проверив значение столбца **is_memory_optimized_elevate_to_snapshot_on** в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).

**\<sql_option> ::=**         

Управляет параметрами соответствия ANSI на уровне базы данных.

ANSI_NULL_DEFAULT { ON | OFF }         
Определяет значение по умолчанию, NULL или NOT NULL, для столбцов [определяемых пользователем типов CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md), для которых в инструкциях CREATE TABLE или ALTER TABLE не указана явно допустимость значений NULL. Столбцы, определенные с ограничениями, следуют правилам ограничения независимо от этой настройки.

ON         
Значение по умолчанию — NULL.

OFF         
Значением по умолчанию является NOT NULL.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_NULL_DEFAULT. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_NULL_DEFAULT в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md).

Для совместимости ANSI при установке параметра базы данных ANSI_NULL_DEFAULT в состояние ON изменяется значение по умолчанию базы данных на значение NULL.

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_null_default_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAnsiNullDefault функции DATABASEPROPERTYEX.

ANSI_NULLS { ON | OFF }         
ON         
Результатом любого сравнения со значением NULL будет UNKNOWN.

OFF         
Результатом сравнения значений не в Юникоде будет TRUE, если оба значения — NULL.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_NULLS всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_NULLS. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_NULLS в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md).

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_NULLS также должен быть установлен в ON.

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_nulls_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiNullsEnabled функции DATABASEPROPERTYEX.

ANSI_PADDING { ON | OFF }         
ON         
Строки перед преобразованием дополняются до одной и той же длины. Выравнивание строк также выполняется перед вставкой в тип данных **varchar** или **nvarchar**.

OFF         
Вставляет замыкающие пробелы в значениях символов в столбцах **varchar** или **nvarchar**. Параметр также оставляет замыкающие нули в двоичных значениях, вставляемых в столбцы значений **varbinary**. Значения не подгоняются под длину столбца.

Состояние OFF касается только определения новых столбцов.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_PADDING всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Рекомендуется всегда задавать для параметра ANSI_PADDING значение ON. При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр ANSI_PADDING должен быть установлен в ON.

Столбцы с типами **char(_n_)** и **binary(_n_)** , допускающие значения NULL, выравниваются по длине столбца, если параметр ANSI_PADDING имеет значение ON. Конечные пробелы и нули отбрасываются, если параметр ANSI_PADDING имеет значение OFF. Столбцы с типами **char(_n_)** и **binary(_n_)** , которые не допускают значений NULL, всегда выравниваются по длине столбца.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_PADDING. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_PADDING в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_padding_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiPaddingEnabled функции DATABASEPROPERTYEX.

ANSI_WARNINGS { ON | OFF }         
ON         
В случае возникновения таких ситуаций, как деление на ноль, выдаются ошибки или предупреждения. Ошибки и предупреждения также возникают тогда, когда значения NULL появляются в агрегатных функциях.

OFF         
Предупреждения не выводятся, а в таких ситуациях, как деление на ноль, возвращается NULL.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_WARNINGS должен быть установлен в ON.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_WARNINGS. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_WARNINGS в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_warnings_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiWarningsEnabled функции DATABASEPROPERTYEX.

ARITHABORT { ON | OFF }         
ON         
Запрос будет завершен, если во время его выполнения возникла ошибка переполнения или деления на ноль.

OFF         
Когда возникает одна из этих ошибок, выводится предупреждающее сообщение. Запрос, пакет или транзакция продолжают выполняться, как если бы ошибки не произошло, даже если выводится предупреждение.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ARITHABORT должен быть установлен в ON.

Вы можете определить состояние этого параметра с помощью проверки столбца is_arithabort_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsArithmeticAbortEnabled функции DATABASEPROPERTYEX.

COMPATIBILITY_LEVEL = { 150 | 140 | 130 | 120 | 110 | 100 | 90 }         

Дополнительные сведения см. в статье [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).

CONCAT_NULL_YIELDS_NULL { ON | OFF }         
ON         
Результатом операции объединения будет NULL, если любой из операндов — NULL. Например, объединение строки символов "Это" со значением NULL приведет к результату NULL вместо "Это".

OFF         
Значение NULL будет обработано как пустая строка символов.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр CONCAT_NULL_YIELDS_NULL должен быть установлен в ON.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр CONCAT_NULL_YIELDS_NULL всегда будет иметь значение ON, а все приложения, явно устанавливающие значение параметра равным OFF, вызовут ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.

Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CONCAT_NULL_YIELDS_NULL. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр CONCAT_NULL_YIELDS_NULL инструкции SET уровня соединения в состояние ON для сеанса. Дополнительные сведения см. в описании [SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_concat_null_yields_null_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsNullConcat функции DATABASEPROPERTYEX.

QUOTED_IDENTIFIER { ON | OFF }         
ON         
Двойные кавычки могут использоваться для идентификаторов с разделителями.

Все строки, находящиеся в двойных кавычках, интерпретируются как идентификаторы объектов. Идентификаторы с разделителями не должны соответствовать правилам для идентификаторов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Они могут быть ключевыми словами и могут включать символы, не разрешенные в идентификаторах [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если в состав строки-литерала входит одиночная кавычка ('), строка может быть заключена в двойные кавычки (").

OFF         
Идентификаторы не могут быть заключены в кавычки и должны следовать всем правилам для идентификаторов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Литералы могут разделяться как одинарными, так и двойными кавычками.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также допускает разделение идентификаторов квадратными скобками ([]). Идентификаторы в скобках могут использоваться всегда, независимо от значения параметра QUOTED_IDENTIFIER. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).

При создании таблицы параметр QUOTED IDENTIFIER всегда сохраняется как ON в метаданных таблицы. Параметр сохраняется, даже если при создании таблицы он был установлен на OFF.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для QUOTED_IDENTIFIER. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая QUOTED_IDENTIFIER в значение ON, по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_quoted_identifier_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsQuotedIdentifiersEnabled функции DATABASEPROPERTYEX.

NUMERIC_ROUNDABORT { ON | OFF }         
ON         
Если в выражении происходит потеря точности, будет сформирована ошибка.

OFF         
Потеря точности вызывает сообщения об ошибках, а результат округляется до точности столбца или переменной, в которых сохраняется результат.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр NUMERIC_ROUNDABORT должен быть установлен в OFF.

Вы можете определить состояние этого параметра с помощью проверки столбца is_numeric_roundabort_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsNumericRoundAbortEnabled функции DATABASEPROPERTYEX.

RECURSIVE_TRIGGERS { ON | OFF }         
ON        
Рекурсивное срабатывание триггеров AFTER разрешено.

OFF         
Вы можете определить состояние этого параметра с помощью проверки столбца is_recursive_triggers_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsRecursiveTriggersEnabled функции DATABASEPROPERTYEX.

> [!NOTE]
> Если параметр RECURSIVE_TRIGGERS установлен в состояние OFF, будет запрещена только прямая рекурсия. Чтобы отключить косвенную рекурсию, нужно установить параметр сервера nested triggers в состояние 0.

Состояние этого параметра можно определить, проверив значение столбца is_recursive_triggers_on в представлении каталога sys.databases или свойства IsRecursiveTriggersEnabled функции DATABASEPROPERTYEX.

**\<target_recovery_time_option> ::=**          
**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Указывает частоту косвенных контрольных точек для каждой базы данных. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] значение по умолчанию для новых баз данных равно 1 минуте, что указывает, что база данных будет использовать косвенные контрольные точки. Для более старых версий по умолчанию установлено значение 0, при котором базой данных используются автоматические контрольные точки, а их частота зависит от параметра интервала для восстановления экземпляра сервера. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует 1 минуту для большинства систем.

TARGET_RECOVERY_TIME **=** *target_recovery_time* { SECONDS | MINUTES }         
*target_recovery_time*         
Указывает максимальное время для восстановления определенной базы данных в случае сбоя. *target_recovery_time* имеет тип **int**.

SECONDS         
Указывает, что значение *target_recovery_time* выражается в количестве секунд. 

MINUTES         
Указывает, что значение *target_recovery_time* выражается в количестве минут.

Сведения о косвенных контрольных точках см. в статье [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md).

**WITH \<termination> ::=**         

Указывает, когда откатывать незавершенные транзакции при переходе базы данных из одного состояния в другое. Если предложение завершения опущено, инструкция ALTER DATABASE будет бесконечно ожидать блокировки базы данных. Может быть указано только одно предложение завершения, которое должно следовать за предложением SET.

> [!NOTE]
> Не все параметры базы данных могут использоваться с предложением WITH \<termination>. Дополнительные сведения см. в таблице [Настройка параметров](#SettingOptions) в разделе "Примечания" этой статьи.

ROLLBACK AFTER *number* [SECONDS] | ROLLBACK IMMEDIATE         

Указывает, нужно ли откатить транзакцию через указанное количество секунд или немедленно. *number* имеет тип **int**.

NO_WAIT         
Указывает, что запрос завершится ошибкой, если нужное состояние базы данных или изменение параметра не может совершиться немедленно. Завершение работы сразу же означает завершение без ожидания фиксации транзакции или отката.

## <a name="SettingOptions"></a> Настройка параметров         
Для извлечения текущих параметров для параметров базы данных используйте представление каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) или [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md).

После установки параметра базы данных изменение вступает в силу немедленно.

Вы можете изменить значения по умолчанию для любого из параметров базы данных для всех созданных баз данных. Для этого измените соответствующий параметр базы данных в шаблоне.

Не все параметры базы данных используют предложение WITH \<termination> или могут быть указаны в сочетании с другими параметрами. В следующей таблице перечислены эти параметры.

|Категория параметров|Может быть указан с другими параметрами|Может использовать предложение WITH \<termination>|
|----------------------|-----------------------------------------|---------------------------------------------|
|\<db_state_option>|Да|Да|
|\<db_user_access_option>|Да|Да|
|\<db_update_option>|Да|Да|
|\<delayed_durability_option>|Да|Да|
|\<external_access_option>|Да|Нет|
|\<cursor_option>|Да|Нет|
|\<auto_option>|Да|Нет|
|\<sql_option>|Да|Нет|
|\<recovery_option>|Да|Нет|
|\<target_recovery_time_option>|Нет|Да|
|\<database_mirroring_option>|Нет|Нет|
|ALLOW_SNAPSHOT_ISOLATION|Нет|Нет|
|READ_COMMITTED_SNAPSHOT|Нет|Да|
|MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT|Да|Да|
|\<service_broker_option>|Да|Нет|
|DATE_CORRELATION_OPTIMIZATION|Да|Да|
|\<parameterization_option>|Да|Да|
|\<change_tracking_option>|Да|Да|
|\<db_encryption_option>|Да|Нет|

Кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очищается при установке одного из следующих параметров.

|||
|-|-|
|OFFLINE|READ_WRITE|
|ONLINE|MODIFY FILEGROUP DEFAULT|
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|
|COLLATE|MODIFY FILEGROUP READ_ONLY|
|READ_ONLY||

Кроме того, кэш процедур сбрасывается в следующих случаях.

- В базе данных включен параметр базы данных AUTO_CLOSE. Если отсутствуют ссылки соединений пользователя или базы данных, фоновая задача предпримет попытку закрыть и отключить базу данных автоматически.
- Выполняется несколько запросов в базе данных с параметрами по умолчанию. Затем база данных уничтожается.
- Моментальный снимок базы данных для базы данных-источника удален.
- Успешное перестроение журнала транзакций базы данных.
- Восстановление резервной копии базы данных.
- Отсоединение базы данных.

Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных". Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.

## <a name="examples"></a>Примеры

### <a name="a-setting-options-on-a-database"></a>A. Установка параметров для базы данных

В следующем примере задается модель восстановления и параметры проверки страницы данных для образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].

```sql
USE master;
GO
ALTER DATABASE AdventureWorks2012
SET RECOVERY FULL PAGE_VERIFY CHECKSUM;
GO

```

### <a name="b-setting-the-database-to-read_only"></a>Б. Перевод базы данных в состояние READ_ONLY

Для изменения состояния базы данных или файловой группы в READ_ONLY или READ_WRITE требуется монопольный доступ к базе данных. В следующем примере база данных устанавливается в режим `SINGLE_USER` для получения монопольного доступа. Затем состояние базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] устанавливается в `READ_ONLY`, а также возвращается доступ к базе данных всем пользователям.

> [!NOTE]
>В этом примере используется параметр завершения `WITH ROLLBACK IMMEDIATE` в первой инструкции `ALTER DATABASE`. Произойдет откат всех незавершенных транзакций, а любые другие подключения к базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] будут немедленно удалены.

```sql
USE master;
GO
ALTER DATABASE AdventureWorks2012
SET SINGLE_USER
WITH ROLLBACK IMMEDIATE;
GO
ALTER DATABASE AdventureWorks2012
SET READ_ONLY
GO
ALTER DATABASE AdventureWorks2012
SET MULTI_USER;
GO

```

### <a name="c-enabling-snapshot-isolation-on-a-database"></a>В. Включение изоляции моментального снимка для базы данных

Следующий пример включает параметр платформы изоляции моментального снимка для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].

```sql
USE AdventureWorks2012;
USE master;
GO
ALTER DATABASE AdventureWorks2012
SET ALLOW_SNAPSHOT_ISOLATION ON;
GO
-- Check the state of the snapshot_isolation_framework
-- in the database.
SELECT name, snapshot_isolation_state,
    snapshot_isolation_state_desc AS description
FROM sys.databases
WHERE name = N'AdventureWorks2012';
GO

```

Результирующий набор показывает, что платформа изоляции моментального снимка включена.

|name |snapshot_isolation_state |description|
|-------------------- |------------------------|----------|
|AdventureWorks2012 |1| ON |

### <a name="d-enabling-modifying-and-disabling-change-tracking"></a>Г. Включение, изменение и отключение отслеживания изменений

В следующем примере демонстрируется включение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и установка `2`-дневного срока хранения.

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING = ON
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);
```

В следующем примере демонстрируется уменьшение срока хранения до `3` дней.

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);
```

В следующем примере демонстрируется отключение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING = OFF;
```

### <a name="e-enabling-the-query-store"></a>Д. Включение хранилища запросов

**Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])

Следующий пример включает хранилище запросов и настраивает его параметры.

```sql
ALTER DATABASE AdventureWorks2012
SET QUERY_STORE = ON
    (
      OPERATION_MODE = READ_WRITE,
      CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 ),
      DATA_FLUSH_INTERVAL_SECONDS = 900,
      QUERY_CAPTURE_MODE = AUTO,
      MAX_STORAGE_SIZE_MB = 1024,
      INTERVAL_LENGTH_MINUTES = 60
    );
```

### <a name="f-enabling-the-query-store-with-wait-statistics"></a>Е. Включение хранилища запросов с использованием статистики ожидания

**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)])

Следующий пример включает хранилище запросов и настраивает его параметры.

```sql
ALTER DATABASE AdventureWorks2016
SET QUERY_STORE = ON
    (
      OPERATION_MODE = READ_WRITE, 
      CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 ),
      DATA_FLUSH_INTERVAL_SECONDS = 900,
      MAX_STORAGE_SIZE_MB = 1024, 
      INTERVAL_LENGTH_MINUTES = 60,
      SIZE_BASED_CLEANUP_MODE = AUTO, 
      MAX_PLANS_PER_QUERY = 200,
      WAIT_STATS_CAPTURE_MODE = ON,
    );
```

### <a name="g-enabling-the-query-store-with-custom-capture-policy-options"></a>Ж. Включение хранилища запросов с использованием параметров пользовательской политики записи

**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)])

Следующий пример включает хранилище запросов и настраивает его параметры.

```sql
ALTER DATABASE AdventureWorks2016 
SET QUERY_STORE = ON 
    (
      OPERATION_MODE = READ_WRITE, 
      CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 ),
      DATA_FLUSH_INTERVAL_SECONDS = 900,
      MAX_STORAGE_SIZE_MB = 1024, 
      INTERVAL_LENGTH_MINUTES = 60,
      SIZE_BASED_CLEANUP_MODE = AUTO, 
      MAX_PLANS_PER_QUERY = 200,
      WAIT_STATS_CAPTURE_MODE = ON,
      QUERY_CAPTURE_MODE = CUSTOM,
      QUERY_CAPTURE_POLICY = (
        STALE_CAPTURE_POLICY_THRESHOLD = 24 HOURS,
        EXECUTION_COUNT = 30,
        TOTAL_COMPILE_CPU_TIME_MS = 1000,
        TOTAL_EXECUTION_CPU_TIME_MS = 100 
      )
    );
```

## <a name="see-also"></a>См. также:

- [Уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)
- [Зеркальное отображение базы данных ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)
- [ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)
- [Статистика](../../relational-databases/statistics/statistics.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=sql-server-2017)
- [Включение и отключение отслеживания изменений](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)
- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)
- [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)
- [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
- [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)
- [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
- [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)
- [Рекомендации по хранилищу запросов](../../relational-databases/performance/best-practice-with-the-query-store.md)

::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](alter-database-transact-sql-set-options.md?view=sql-server-2017)|**_\* Отдельная база данных/эластичный пул Базы данных SQL<br /> \*_** &nbsp;|[Управляемый экземпляр Базы данных SQL<br />](alter-database-transact-sql-set-options.md?view=azuresqldb-mi-current)||[Хранилище данных<br />SQL](alter-database-transact-sql-set-options.md?view=azure-sqldw-latest)||||

&nbsp;

## <a name="azure-sql-database-single-databaseelastic-pool"></a>Отдельная база данных или эластичный пул Базы данных SQL Azure

Уровни совместимости являются параметрами инструкции `SET`, но описаны в отдельной статье [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).

> [!NOTE]
> Многие параметры инструкции DATABASE SET можно настроить только для текущего сеанса с помощью [инструкций SET](../../t-sql/statements/set-statements-transact-sql.md). Они часто задаются приложениями при подключении. Параметры инструкции SET уровня сеанса переопределяют значения **ALTER DATABASE SET**. Описанные далее параметры базы данных являются значениями, которые можно задавать для сеансов, не предоставляющих явно другие значения параметра SET.

## <a name="syntax"></a>Синтаксис

```
ALTER DATABASE { database_name | Current }
SET
{
    <option_spec> [ ,...n ] [ WITH <termination> ]
}
;

<option_spec> ::=
{
    <auto_option>
  | <automatic_tuning_option>
  | <change_tracking_option>
  | <cursor_option>
  | <db_encryption_option>
  | <db_update_option>
  | <db_user_access_option>
  | <delayed_durability_option>
  | <parameterization_option>
  | <query_store_options>
  | <snapshot_option>
  | <sql_option>
  | <target_recovery_time_option>
  | <termination>
  | <temporal_history_retention>
}
;
<auto_option> ::=
{
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }
  | AUTO_SHRINK { ON | OFF }
  | AUTO_UPDATE_STATISTICS { ON | OFF }
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }
}

<automatic_tuning_option> ::=
{AUTOMATIC_TUNING = { AUTO | INHERIT | CUSTOM }
  | AUTOMATIC_TUNING ( CREATE_INDEX = { DEFAULT | ON | OFF } )
  | AUTOMATIC_TUNING ( DROP_INDEX = { DEFAULT | ON | OFF } )
  | AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = { DEFAULT | ON | OFF } )
}

<change_tracking_option> ::=
{
  CHANGE_TRACKING
   {
       = OFF
     | = ON [ ( <change_tracking_option_list > [,...n] ) ]
     | ( <change_tracking_option_list> [,...n] )
   }
}

<change_tracking_option_list> ::=
   {
       AUTO_CLEANUP = { ON | OFF }
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }
   }

<cursor_option> ::=
{
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }
}

<db_encryption_option> ::=
  ENCRYPTION { ON | OFF }

<db_update_option> ::=
  { READ_ONLY | READ_WRITE }

<db_user_access_option> ::=
  { RESTRICTED_USER | MULTI_USER }

<delayed_durability_option> ::=DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }

<parameterization_option> ::=
  PARAMETERIZATION { SIMPLE | FORCED }

<query_store_options> ::=
{
  QUERY_STORE
  {
    = OFF
    | = ON [ ( <query_store_option_list> [,... n] ) ]
    | ( < query_store_option_list> [,... n] )
    | CLEAR [ ALL ]
  }
}

<query_store_option_list> ::=
{
  OPERATION_MODE = { READ_WRITE | READ_ONLY }
  | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )
  | DATA_FLUSH_INTERVAL_SECONDS = number
  | MAX_STORAGE_SIZE_MB = number
  | INTERVAL_LENGTH_MINUTES = number
  | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]
  | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]
  | MAX_PLANS_PER_QUERY = number
}

<snapshot_option> ::=
{
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }
  | READ_COMMITTED_SNAPSHOT {ON | OFF }
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT {ON | OFF }
}
<sql_option> ::=
{
    ANSI_NULL_DEFAULT { ON | OFF }
  | ANSI_NULLS { ON | OFF }
  | ANSI_PADDING { ON | OFF }
  | ANSI_WARNINGS { ON | OFF }
  | ARITHABORT { ON | OFF }
  | COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }
  | NUMERIC_ROUNDABORT { ON | OFF }
  | QUOTED_IDENTIFIER { ON | OFF }
  | RECURSIVE_TRIGGERS { ON | OFF }
}

<termination>::=
{
    ROLLBACK AFTER integer [ SECONDS ]
  | ROLLBACK IMMEDIATE
  | NO_WAIT
}

<temporal_history_retention>::=TEMPORAL_HISTORY_RETENTION { ON | OFF }
```

## <a name="arguments"></a>Аргументы

*database_name*         
Имя изменяемой базы данных.

CURRENT         
`CURRENT` выполняет действие в текущей базе данных. `CURRENT` работает не со всеми параметрами и не во всех контекстах. Если `CURRENT` не работает, укажите имя базы данных.

**\<auto_option> ::=**

Управляет автоматическими параметрами.
<a name="auto_create_statistics"></a> AUTO_CREATE_STATISTICS { ON | OFF }         
ON         
Оптимизатор запросов в случае необходимости создает статистику по отдельным столбцам в предикатах запросов, чтобы улучшить планы запросов и повысить производительность запросов. Такая статистика по отдельным столбцам создается, когда оптимизатор запросов компилирует запросы. Статистика по отдельным столбцам создается только для столбцов, ни один из которых не является первым столбцом в существующем объекте статистики.

Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.

OFF         
Оптимизатор запросов не создает статистику по отдельным столбцам в предикатах запросов во время компиляции запросов. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_create_stats_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoCreateStatistics функции DATABASEPROPERTYEX.

Дополнительные сведения см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

INCREMENTAL = ON | OFF         
Присваивает AUTO_CREATE_STATISTICS значение ON, а INCREMENTAL — значение ON. Он создает автоматически создаваемые статистики как добавочные везде, где поддерживаются добавочные статистики. Значение по умолчанию — OFF. Дополнительные сведения см. в описании [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).

<a name="auto_shrink"></a> AUTO_SHRINK { ON | OFF }         
ON         
Файлы базы данных являются кандидатами на периодическое сжатие.

И файлы данных, и файлы журналов могут быть автоматически сжаты. AUTO_SHRINK уменьшает размер журнала транзакций только в том случае, если вы выбрали простую модель восстановления базы данных или создали резервную копию журнала. Если этот параметр установлен в состояние OFF, файлы базы данных не будут автоматически сжиматься при периодической проверке на неиспользуемое пространство.

При включенном параметре AUTO_SHRINK файлы будут сжаты, если более 25 процентов файла содержит неиспользуемое пространство. Параметр вызывает сжатие файла в один из двух размеров. Он сжимает до большего, если:

- размер, в котором 25 процентов файла не используется;
- размер файла при его создании.

Нельзя сжать базу данных, находящуюся в состоянии только для чтения.

OFF         
Автоматическое сжатие файлов при периодической проверке на неиспользуемое пространство не производится.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_shrink_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoShrink функции DATABASEPROPERTYEX.

> [!NOTE]
> В автономной базе данных параметр AUTO_SHRINK недоступен.

<a name="auto_update_statistics"></a> AUTO_UPDATE_STATISTICS { ON | OFF }         
ON         
Указывает, что оптимизатор запросов обновляет статистику, если она используется в запросе и может оказаться устаревшей. Статистика становится устаревшей, после того как операции вставки, обновления, удаления или слияния изменяют распределение данных в таблице или индексированном представлении. Оптимизатор запросов определяет, когда статистика может оказаться устаревшей, подсчитывая операции изменения данных с момента последнего обновления статистики и сравнивая количество изменений с пороговым значением. Пороговое значение основано на количестве строк в таблице или индексированном представлении.

Оптимизатор запросов проверяет наличие устаревшей статистики перед компиляцией запроса и выполняет кэшированный план запроса. Оптимизатор запросов с помощью столбцов, таблиц и индексированных представлений в предикате запроса определяет, какая статистика могла устареть. Оптимизатор запросов определяет эти сведения перед компиляцией запроса. Перед выполнением кэшированного плана запроса компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверяет, ссылается ли план запроса на актуальную статистику.

Параметр AUTO_UPDATE_STATISTICS применяется к статистике, создаваемой для индексов и отдельных столбцов в предикатах запросов, и к статистике, создаваемой инструкцией CREATE STATISTICS. Этот параметр также применяется к отфильтрованной статистике.

Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.

Используйте параметр AUTO_UPDATE_STATISTICS_ASYNC, чтобы указать режим обновления статистики: синхронный или асинхронный.

OFF         
Указывает, что оптимизатор запросов не обновляет статистику, если она используется в запросе. Оптимизатор запросов также не обновляет статистику, когда она становится устаревшей. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_update_stats_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoUpdateStatistics функции DATABASEPROPERTYEX.

Дополнительные сведения см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

<a name="auto_update_statistics_async"></a> AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }         
ON         
Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется асинхронно. Оптимизатор запросов не ожидает завершения обновления статистики перед компиляцией запросов.

Установка этого параметра в состояние ON не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в состояние ON.

По умолчанию параметр AUTO_UPDATE_STATISTICS_ASYNC имеет значение OFF, а оптимизатор запросов обновляет статистику в синхронном режиме.

OFF         
Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется синхронно. Оптимизатор запросов ожидает завершения обновления статистики перед компиляцией запросов.

Установка этого параметра в значение OFF не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в значение ON.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_update_stats_async_on в представлении каталога sys.databases.

Дополнительные сведения, описывающие условия применения синхронного и асинхронного обновлений статистики, см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

<a name="auto_tuning"></a> **\<automatic_tuning_option> ::=**          
**Применимо к**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)].

Управляет автоматическими параметрами для [автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md).

AUTOMATIC_TUNING = { AUTO | INHERIT | CUSTOM }         
AUTO         
Если для автоматической настройки задано значение AUTO, будут применяться значения конфигурации Azure по умолчанию.

INHERIT         
При использовании значения INHERIT с родительского сервера будет наследоваться конфигурация по умолчанию. Это особенно полезно, если вы хотите задать на родительском сервере пользовательские параметры автоматической настройки, которые будут наследовать все базы данных. Обратите внимание, что для корректного наследования нужно, чтобы три отдельных параметра настройки (FORCE_LAST_GOOD_PLAN, CREATE_INDEX и DROP_INDEX) имели значение DEFAULT в базах данных.

CUSTOM         
Значение CUSTOM потребует ручной настройки всех параметров, доступных в базах данных.

Включает или отключает параметр автоматического управления индексами `CREATE_INDEX` [автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md).

CREATE_INDEX = { DEFAULT | ON | OFF }         
DEFAULT         
Наследует параметры по умолчанию с сервера. В этом случае параметры включения и отключения отдельных функций автоматической настройки задаются на уровне сервера.

ON         
Если этот параметр включен, недостающие индексы в базе данных создаются автоматически. После создания индексов измеряется повышение производительности рабочей нагрузки. Если созданный таким образом индекс больше не повышает производительность, он автоматически отменяется. Автоматически созданные индексы отмечаются как созданные системой.

OFF         
Не создает автоматически недостающие индексы в базе данных.

Включает или отключает параметр автоматического управления индексами `DROP_INDEX` [автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md).

DROP_INDEX = { DEFAULT | ON | OFF }         
DEFAULT         
Наследует параметры по умолчанию с сервера. В этом случае параметры включения и отключения отдельных функций автоматической настройки задаются на уровне сервера.

ON         
Автоматически удаляет повторяющиеся или неиспользуемые индексы для повышения производительности рабочей нагрузки.

OFF         
Не удаляет автоматически недостающие индексы в базе данных.

Включает или отключает параметр автоматического исправления плана `FORCE_LAST_GOOD_PLAN` [автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md).

FORCE_LAST_GOOD_PLAN = { DEFAULT | ON | OFF }         
DEFAULT         
Наследует параметры по умолчанию с сервера. В этом случае параметры включения и отключения отдельных функций автоматической настройки задаются на уровне сервера.

ON         
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] автоматически включает последний известный удачный план для [!INCLUDE[tsql-md](../../includes/tsql-md.md)] запросов, когда новый план SQL приводит к снижению производительности. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] непрерывно отслеживает производительность запроса [!INCLUDE[tsql-md](../../includes/tsql-md.md)] в форсированном плане. В случае повышения производительности [!INCLUDE[ssde_md](../../includes/ssde_md.md)] будет продолжать использовать последний известный удачный план. Если повышений производительности нет, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] создаст новый план SQL. Инструкция завершится ошибкой, если хранилище запросов не включено или не находится в режиме *Чтение и запись*.

OFF         
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] сообщает о потенциальном снижении производительности запросов, вызванном изменениями планов SQL в представлении [sys.dm_db_tuning_recommendations](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md). Однако эти рекомендации не применяются автоматически. Пользователь может отслеживать активные рекомендации и устранять выявленные проблемы, применяя сценарии [!INCLUDE[tsql-md](../../includes/tsql-md.md)], которые отображаются в представлении. Это значение по умолчанию.

**\<change_tracking_option> ::=**         

Определяет параметры отслеживания изменений. Отслеживание изменений можно включить или отключить, а также установить или изменить параметры. Примеры использования см. далее в этой статье.

ON         
Включает отслеживание изменений для базы данных. При включении отслеживания изменений также необходимо задать параметры AUTO CLEANUP и CHANGE RETENTION.

AUTO_CLEANUP = { ON | OFF }         
ON         
Данные отслеживания изменений автоматически удаляются по истечении заданного срока хранения.

OFF         
Данные отслеживания изменений не удаляются из базы данных.

CHANGE_RETENTION =*retention_period* {DAYS | HOURS | MINUTES} указывает минимальный срок хранения данных отслеживания изменений в базе данных. Данные удаляются, только если для параметра AUTO_CLEANUP установлено значение ON.

*retention_period* — целое число, указывающее числовой компонент срока хранения.

Срок хранения по умолчанию — 2 дня. Минимальный срок хранения составляет 1 минуту. Тип хранения по умолчанию — DAYS.

OFF         
Отключает отслеживание изменений для базы данных. Перед отключением отслеживания изменений для базы данных предварительно отключите отслеживание изменений для всех таблиц.

**\<cursor_option> ::=**

Управляет параметрами курсора.

CURSOR_CLOSE_ON_COMMIT { ON | OFF }         
ON         
Любые курсоры, открытые при фиксации или откате транзакции, закрываются.

OFF         
Курсоры остаются открытыми при завершении транзакции; откат транзакции закрывает любые курсоры (кроме тех, которые имеют свойства INSENSITIVE или STATIC).

Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CURSOR_CLOSE_ON_COMMIT. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая CURSOR_CLOSE_ON_COMMIT в значение OFF для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md).

Состояние этого параметра можно определить, проверив значение столбца is_cursor_close_on_commit_on в представлении каталога sys.databases или свойства `IsCloseCursorsOnCommitEnabled` функции DATABASEPROPERTYEX. Курсор неявно освобождается только при отключении. Дополнительные сведения см. в описании [DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md).

**\<db_encryption_option> ::=**         

Определяет параметры шифрования базы данных.

ENCRYPTION {ON | OFF}         
Включает шифрование базы данных (ON) или отключает его (OFF). Дополнительные сведения см. в статьях о [прозрачном шифровании данных](../../relational-databases/security/encryption/transparent-data-encryption.md) и [прозрачном шифровании данных для Базы данных SQL Azure](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md).

Если включить шифрование на уровне базы данных, будут зашифрованы все файловые группы. Все новые файловые группы наследуют свойство шифрования. Если любая файловая группа базы данных установлена в состояние **READ ONLY**, операция шифрования базы завершится неуспешно.

Параметры шифрования базы данных можно просмотреть с помощью динамического административного представления [sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md).

**\<db_update_option> ::=**         

Управляет разрешениями на обновления базы данных.

READ_ONLY         
Пользователи могут считывать данные из базы данных, но не могут изменять их.

> [!NOTE]
>Для улучшения производительности запросов выполните обновление статистики перед тем, как перевести базу данных в режим доступа READ_ONLY. После перевода базы данных в режим READ_ONLY потребуется дополнительная статистика, она будет создана компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] в tempdb. Дополнительные сведения о статистике для базы данных, доступной только для чтения, см. в разделе [Статистика](../../relational-databases/statistics/statistics.md).

READ_WRITE         
База данных доступна для операций чтения и записи.

Чтобы изменить это состояние, необходимо обладать монопольным доступом к базе данных. Дополнительные сведения см. в описании предложения SINGLE_USER.

> [!NOTE]
> Применительно к федеративным базам данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)], инструкция SET { READ_ONLY | READ_WRITE } отключена.

**\<db_user_access_option> ::=**         

Управляет пользовательским доступом к базе данных.

RESTRICTED_USER         
Предложение RESTRICTED_USER позволяет подключаться к базе данных только членам предопределенных ролей базы данных db_owner и dbcreator и предопределенной роли сервера sysadmin, количество соединений при этом не ограничивается. Все соединения с базой данных будут отключены на период времени, определяемый завершающим предложением инструкции ALTER DATABASE. После того как база данных перешла в состояние RESTRICTED_USER, попытки подключения пользователей, не соответствующими описанным выше условиям, будут отклонены. **RESTRICTED_USER** нельзя изменить с помощью управляемого экземпляра Базы данных SQL.

MULTI_USER         
Все пользователи, имеющие соответствующие разрешения на подключение к базе данных, будут допущены к базе данных.

Состояние этого параметра можно определить, проверив значение столбца user_access в представлении каталога sys.databases или свойства UserAccess функции DATABASEPROPERTYEX.

**\<delayed_durability_option> ::=**         

Управляет тем, является ли фиксация транзакций полностью устойчивой или отложенной устойчивой.

DISABLED         
Все транзакции, следующие за SET DISABLED, являются полностью устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.

ALLOWED         
Все транзакции, следующие за SET ALLOWED, являются полностью устойчивыми или отложенными устойчивыми, в зависимости от параметра устойчивости, заданного в блоке ATOMIC или инструкции COMMIT.

FORCED         
Все транзакции, следующие за SET FORCED, являются отложенными устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.

**\<PARAMETERIZATION_option> ::=**         

Управляет параметром параметризации.

PARAMETERIZATION { SIMPLE | FORCED }         
SIMPLE         
Запросы параметризуются на основании поведения базы данных по умолчанию.

FORCED         
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметризует все запросы в базе данных.

Текущее состояние этого параметра можно определить по столбцу `is_parameterization_forced` в представлении каталога `sys.databases`.

**\<query_store_options> ::=**

ON | OFF | CLEAR [ ALL ]         
Указывает, включено ли хранилище запросов в этой базе данных, а также управляет удалением содержимого хранилища запросов.

ON         
Включает хранилище запросов.

OFF         
Отключает хранилище запросов. Это значение по умолчанию.

CLEAR         
Удаляет содержимое хранилища запросов.

OPERATION_MODE         
Описывает режим работы хранилища запросов. Допустимые значения: READ_ONLY и READ_WRITE. В режиме READ_WRITE хранилище запросов собирает и сохраняет план запросов и статистические данные о выполнении. В режиме READ_ONLY можно считывать данные из хранилища запросов, но новые сведения не добавляются. Если выделенное свободное место в хранилище запросов будет исчерпано, хранилище переключится в режим работы READ_ONLY.

CLEANUP_POLICY         
Описывает политику хранения данных хранилища запросов. STALE_QUERY_THRESHOLD_DAYS определяет количество дней хранения сведений о запросе в хранилище. STALE_QUERY_THRESHOLD_DAYS имеет тип **bigint**.

DATA_FLUSH_INTERVAL_SECONDS         
Определяет частоту, с которой данные, записанные в хранилище запросов, сохраняются на диск. Для оптимизации производительности данные, собранные хранилищем запросов, асинхронно записываются на диск. Для настройки частоты этой асинхронной передачи используется аргумент DATA_FLUSH_INTERVAL_SECONDS. DATA_FLUSH_INTERVAL_SECONDS имеет тип **bigint**.

MAX_STORAGE_SIZE_MB         
Определяет свободное место, выделенное для хранилища запросов. MAX_STORAGE_SIZE_MB имеет тип **bigint**.

INTERVAL_LENGTH_MINUTES         
Определяет временной интервал вычисления статистических данных о среде выполнения в хранилище запросов. Для оптимизации использования свободного места статистические данные о среде выполнения в хранилище вычисляются для фиксированного временного интервала. Этот интервал настраивается с помощью аргумента INTERVAL_LENGTH_MINUTES. INTERVAL_LENGTH_MINUTES имеет тип **bigint**.

SIZE_BASED_CLEANUP_MODE         
Определяет, будет ли автоматически активирована очистка, когда общий объем данных приблизится к верхней границе ограничения.

OFF         
Очистка на основе размера не будет автоматически активирована.

AUTO         
Очистка на основе размера активируется автоматически при достижении размера на диске 90 % от **max_storage_size_mb**. Эта очистка сначала удаляет самые дешевые и самые старые запросы. Она останавливается приблизительно на 80 % от **max_storage_size_mb**. Это значение конфигурации по умолчанию.

SIZE_BASED_CLEANUP_MODE имеет тип **nvarchar**.

QUERY_CAPTURE_MODE         
Определяет режим записи текущего активного запроса:

ALL         
Записываются все запросы. Это значение конфигурации по умолчанию.

AUTO         
Записываются соответствующие запросы на основе показателя выполнения и объема потребления ресурсов. Это значение конфигурации является значением по умолчанию для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].

None         
Запись новых запросов останавливается. Хранилище запросов будет продолжать сбор статистики компиляции и времени выполнения для запросов, которые уже были записаны. Эту конфигурацию следует использовать с осторожностью, поскольку можно пропустить запись важных запросов.

QUERY_CAPTURE_MODE имеет тип **nvarchar**.

MAX_PLANS_PER_QUERY         
Целое число, представляющее максимальное количество поддерживаемых планов для каждого запроса. Значение по умолчанию — 200.

**\<snapshot_option> ::=**         

Определяет уровень изоляции транзакции.

ALLOW_SNAPSHOT_ISOLATION { ON | OFF }         
ON         
Включает параметр моментальных снимков на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После установки этого параметра транзакции могут задавать уровень изоляции транзакций SNAPSHOT. Если транзакция выполняется на уровне изоляции SNAPSHOT, всем инструкциям видны данные из моментального снимка в состоянии, которое существовало в момент начала транзакции. Если транзакция выполняется с уровнем изоляции SNAPSHOT и обращается к данным нескольких баз данных, то либо параметр ALLOW_SNAPSHOT_ISOLATION должен быть установлен в состояние ON во всех базах данных, либо каждая инструкция в транзакции должна использовать подсказки блокировки при любом обращении предложения FROM к таблице базы данных, в которой параметр ALLOW_SNAPSHOT_ISOLATION установлен в состояние OFF.

OFF         
Отключает параметр моментальных снимков на уровне базы данных. Транзакции не могут указывать уровень изоляции SNAPSHOT.

Если вы изменяете состояние ALLOW_SNAPSHOT_ISOLATION (из ON в OFF или из OFF в ON), инструкция ALTER DATABASE не возвращает управление вызвавшей ее программе, пока все существующие транзакции в базе данных не будут зафиксированы. Если база данных уже находится в состоянии, указанном в инструкции ALTER DATABASE, управление вызвавшей программе будет возвращено немедленно. Используйте процедуру [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md), чтобы определить наличие длительно выполняющихся транзакций. Если инструкция ALTER DATABASE отменена, база данных останется в состоянии, в котором она находилась при запуске ALTER DATABASE. Представление каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) отображает состояние транзакций с уровнем изоляции моментальных снимков в базе данных. Если **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON, ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF, операция будет повторена через шесть секунд.

Изменить состояние ALLOW_SNAPSHOT_ISOLATION невозможно, если база данных находится в режиме OFFLINE.

При установке параметра ALLOW_SNAPSHOT_ISOLATION в базе данных, находящейся в режиме READ_ONLY, он будет сохранен при переводе базы данных в режим READ_WRITE.

Настройки ALLOW_SNAPSHOT_ISOLATION можно изменить и для баз данных master, model, msdb и tempdb. Если изменить значение для базы данных tempdb, оно будет сохраняться каждый раз при остановке и перезапуске экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.

Этот параметр для баз данных master и msdb по умолчанию установлен в состояние ON.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца snapshot_isolation_state в представлении каталога sys.databases.

READ_COMMITTED_SNAPSHOT { ON | OFF }         
ON         
Включает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После включения этого параметра транзакции, указывающие уровень изоляции READ COMMITTED, используют управление версиями строк вместо блокировки. Данные моментального снимка видны всем инструкциям в состоянии, которое существовало на момент начала выполнения инструкции, если транзакция выполняется с уровнем изоляции зафиксированной операции чтения.

OFF         
Отключает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Транзакции с уровнем изоляции READ COMMITTED используют блокировку.

Чтобы установить параметр READ_COMMITTED_SNAPSHOT в значение ON или OFF, с базой данных не должно быть активных соединений, за исключением соединения, выполняющего команду ALTER DATABASE. Однако это не означает, что база данных должна находиться в однопользовательском режиме. Изменить состояние этого параметра невозможно, если база данных находится в режиме OFFLINE.

При установке параметра READ_COMMITTED_SNAPSHOT в базе данных, которая находится в режиме READ_ONLY, это состояние будет сохранено при переводе базы данных в режим READ_WRITE.

Параметр READ_COMMITTED_SNAPSHOT не может быть установлен в ON для системных баз данных master, tempdb или msdb. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_read_committed_snapshot_on в представлении каталога sys.databases.

> [!WARNING]
> Если таблица была создана с использованием аргумента `DURABILITY = SCHEMA_ONLY`, а впоследствии значение **READ_COMMITTED_SNAPSHOT** было изменено с помощью инструкции `ALTER DATABASE`, данные в таблице будут потеряны.

MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }         
ON         
Если уровень изоляции транзакции установлен в любое значение ниже SNAPSHOT, все интерпретированные операции [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах, оптимизированных для памяти, выполняются с уровнем изоляции SNAPSHOT. Примеры уровней изоляции ниже, чем моментальный снимок — READ COMMITTED или READ UNCOMMITTED. Эти операции выполняются независимо от того, установлен ли уровень изоляции транзакции явно на уровне сеанса или неявно используется значение по умолчанию.

OFF         
Не повышает уровень изоляции транзакции для интерпретированных операций [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах, оптимизированных для памяти.

Изменить состояние MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT невозможно, если база данных находится в режиме OFFLINE.

Значение по умолчанию — OFF.

Текущее состояние этого параметра можно определить, проверив значение столбца **is_memory_optimized_elevate_to_snapshot_on** в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).

**\<sql_option> ::=**         

Управляет параметрами соответствия ANSI на уровне базы данных.

ANSI_NULL_DEFAULT { ON | OFF }         
Определяет значение по умолчанию, NULL или NOT NULL, для столбцов [определяемых пользователем типов CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md), для которых в инструкциях CREATE TABLE или ALTER TABLE не указана явно допустимость значений NULL. Столбцы, определенные с ограничениями, следуют правилам ограничения независимо от этой настройки.

ON         
Значение по умолчанию — NULL.

OFF         
Значением по умолчанию является NOT NULL.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_NULL_DEFAULT. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_NULL_DEFAULT в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md).

Для совместимости ANSI при установке параметра базы данных ANSI_NULL_DEFAULT в состояние ON изменяется значение по умолчанию базы данных на значение NULL.

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_null_default_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAnsiNullDefault функции DATABASEPROPERTYEX.

ANSI_NULLS { ON | OFF }         
ON         
Результатом любого сравнения со значением NULL будет UNKNOWN.

OFF         
Результатом сравнения значений не в Юникоде будет TRUE, если оба значения — NULL.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_NULLS всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.

  Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_NULLS. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_NULLS в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md).

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_NULLS также должен быть установлен в ON.

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_nulls_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiNullsEnabled функции DATABASEPROPERTYEX.

ANSI_PADDING { ON | OFF }         
ON         
Строки перед преобразованием дополняются до одной и той же длины. Выравнивание строк также выполняется перед вставкой в тип данных **varchar** или **nvarchar**.

OFF         
Вставляет замыкающие пробелы в значениях символов в столбцах **varchar** или **nvarchar**. Параметр также оставляет замыкающие нули в двоичных значениях, вставляемых в столбцы значений **varbinary**. Значения не подгоняются под длину столбца.

Состояние OFF касается только определения новых столбцов.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_PADDING всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Рекомендуется всегда задавать для параметра ANSI_PADDING значение ON. При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр ANSI_PADDING должен быть установлен в ON.

Столбцы с типами **char(_n_)** и **binary(_n_)** , допускающие значения NULL, выравниваются по длине столбца, если параметр ANSI_PADDING имеет значение ON. Конечные пробелы и нули отбрасываются, если параметр ANSI_PADDING имеет значение OFF. Столбцы с типами **char(_n_)** и **binary(_n_)** , которые не допускают значений NULL, всегда выравниваются по длине столбца.

  Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_PADDING. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_PADDING в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_padding_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiPaddingEnabled функции DATABASEPROPERTYEX.

ANSI_WARNINGS { ON | OFF }         
ON         
В случае возникновения таких ситуаций, как деление на ноль, выдаются ошибки или предупреждения. Ошибки и предупреждения также возникают тогда, когда значения NULL появляются в агрегатных функциях.

OFF         
Предупреждения не выводятся, а в таких ситуациях, как деление на ноль, возвращается NULL.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_WARNINGS должен быть установлен в ON.

  Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_WARNINGS. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_WARNINGS в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_warnings_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiWarningsEnabled функции DATABASEPROPERTYEX.

ARITHABORT { ON | OFF }         
ON         
Запрос будет завершен, если во время его выполнения возникла ошибка переполнения или деления на ноль.

OFF         
Когда возникает одна из этих ошибок, выводится предупреждающее сообщение. Запрос, пакет или транзакция продолжают выполняться, как если бы ошибки не произошло, даже если выводится предупреждение.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ARITHABORT должен быть установлен в ON.

  Вы можете определить состояние этого параметра с помощью проверки столбца is_arithabort_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства `IsArithmeticAbortEnabled` функции DATABASEPROPERTYEX.

COMPATIBILITY_LEVEL = { 150 | 140 | 130 | 120 | 110 | 100 }         
Дополнительные сведения см. в статье [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).

CONCAT_NULL_YIELDS_NULL { ON | OFF }         
ON         
Результатом операции объединения будет NULL, если любой из операндов — NULL. Например, объединение строки символов "Это" со значением NULL приведет к результату NULL вместо "Это".

OFF         
Значение NULL будет обработано как пустая строка символов.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр CONCAT_NULL_YIELDS_NULL должен быть установлен в ON.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр CONCAT_NULL_YIELDS_NULL всегда будет иметь значение ON, а все приложения, явно устанавливающие значение параметра равным OFF, вызовут ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.

Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CONCAT_NULL_YIELDS_NULL. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр CONCAT_NULL_YIELDS_NULL инструкции SET уровня соединения в состояние ON для сеанса. Дополнительные сведения см. в описании [SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_concat_null_yields_null_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsNullConcat функции DATABASEPROPERTYEX.

QUOTED_IDENTIFIER { ON | OFF }         
ON         
Двойные кавычки могут использоваться для идентификаторов с разделителями.

Все строки, находящиеся в двойных кавычках, интерпретируются как идентификаторы объектов. Идентификаторы с разделителями не должны соответствовать правилам для идентификаторов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Они могут быть ключевыми словами и могут включать символы, не разрешенные в идентификаторах [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если в состав строки-литерала входит одиночная кавычка ('), строка может быть заключена в двойные кавычки (").

OFF         
Идентификаторы не могут быть заключены в кавычки и должны следовать всем правилам для идентификаторов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Литералы могут разделяться как одинарными, так и двойными кавычками.

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также допускает разделение идентификаторов квадратными скобками ([]). Идентификаторы в скобках могут использоваться всегда, независимо от значения параметра QUOTED_IDENTIFIER. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).

  При создании таблицы параметр QUOTED IDENTIFIER всегда сохраняется как ON в метаданных таблицы. Параметр сохраняется, даже если при создании таблицы он был установлен на OFF.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для QUOTED_IDENTIFIER. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая QUOTED_IDENTIFIER в значение ON, по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md).

  Вы можете определить состояние этого параметра с помощью проверки столбца is_quoted_identifier_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsQuotedIdentifiersEnabled функции DATABASEPROPERTYEX.

NUMERIC_ROUNDABORT { ON | OFF }         
ON         
Если в выражении происходит потеря точности, будет сформирована ошибка.

OFF         
Потеря точности вызывает сообщения об ошибках, а результат округляется до точности столбца или переменной, в которых сохраняется результат.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр NUMERIC_ROUNDABORT должен быть установлен в OFF.

Вы можете определить состояние этого параметра с помощью проверки столбца is_numeric_roundabort_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsNumericRoundAbortEnabled функции DATABASEPROPERTYEX.

RECURSIVE_TRIGGERS { ON | OFF }         
ON         
Рекурсивное срабатывание триггеров AFTER разрешено.

OFF         
Вы можете определить состояние этого параметра с помощью проверки столбца is_recursive_triggers_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsRecursiveTriggersEnabled функции DATABASEPROPERTYEX.

> [!NOTE]
> Если параметр RECURSIVE_TRIGGERS установлен в состояние OFF, будет запрещена только прямая рекурсия. Чтобы отключить косвенную рекурсию, нужно установить параметр сервера nested triggers в состояние 0.

Состояние этого параметра можно определить, проверив значение столбца is_recursive_triggers_on в представлении каталога sys.databases или свойства IsRecursiveTriggersEnabled функции DATABASEPROPERTYEX.

**\<target_recovery_time_option> ::=**         

Указывает частоту косвенных контрольных точек для каждой базы данных. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], значение по умолчанию для новых баз данных равно 1 минуте, что указывает, что база данных будет использовать косвенные контрольные точки. Для более старых версий по умолчанию установлено значение 0, при котором базой данных используются автоматические контрольные точки, а их частота зависит от параметра интервала для восстановления экземпляра сервера. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует 1 минуту для большинства систем.

TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS | MINUTES }         
*target_recovery_time*         
Указывает максимальное время для восстановления определенной базы данных в случае сбоя.

SECONDS         
Указывает, что значение *target_recovery_time* выражается в количестве секунд.

MINUTES         
Указывает, что значение *target_recovery_time* выражается в количестве минут.

Сведения о косвенных контрольных точках см. в статье [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md).

**WITH \<termination> ::=**         

Указывает, когда откатывать незавершенные транзакции при переходе базы данных из одного состояния в другое. Если предложение завершения опущено, инструкция ALTER DATABASE будет бесконечно ожидать блокировки базы данных. Может быть указано только одно предложение завершения, которое должно следовать за предложением SET.

> [!NOTE]
> Не все параметры базы данных могут использоваться с предложением WITH \<termination>. Дополнительные сведения см. в таблице [Настройка параметров](#SettingOptions) в разделе "Примечания" этой статьи.

ROLLBACK AFTER *integer* [SECONDS] | ROLLBACK IMMEDIATE         
Указывает, нужно ли откатить транзакцию через указанное количество секунд или немедленно.

NO_WAIT         
Указывает, что запрос завершится ошибкой, если нужное состояние базы данных или изменение параметра не может совершиться немедленно. Завершение работы сразу же означает завершение без ожидания фиксации транзакции или отката.

## <a name="SettingOptions"></a> Настройка параметров         

Для извлечения текущих параметров для параметров базы данных используйте представление каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) или [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md).

После установки параметра базы данных изменение вступает в силу немедленно.

Вы можете изменить значения по умолчанию для любого из параметров базы данных для всех созданных баз данных. Для этого измените соответствующий параметр базы данных в шаблоне.

Не все параметры базы данных используют предложение WITH \<termination> или могут быть указаны в сочетании с другими параметрами. В следующей таблице перечислены эти параметры.

|Категория параметров|Может быть указан с другими параметрами|Может использовать предложение WITH \<termination>|
|----------------------|-----------------------------------------|---------------------------------------------|
|\<auto_option>|Да|нет|
|\<change_tracking_option>|Да|Да|
|\<cursor_option>|Да|нет|
|\<db_encryption_option>|Да|нет|
|\<db_update_option>|Да|Да|
|\<db_user_access_option>|Да|Да|
|\<delayed_durability_option>|Да|Да|
|\<parameterization_option>|Да|Да|
|ALLOW_SNAPSHOT_ISOLATION|Нет|Нет|
|READ_COMMITTED_SNAPSHOT|Нет|Да|
|MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT|Да|Да|
|DATE_CORRELATION_OPTIMIZATION|Да|Да|
|\<sql_option>|Да|Нет|
|\<target_recovery_time_option>|Нет|Да|

## <a name="examples"></a>Примеры

### <a name="a-setting-the-database-to-read_only"></a>A. Перевод базы данных в состояние READ_ONLY
Для изменения состояния базы данных или файловой группы в READ_ONLY или READ_WRITE требуется монопольный доступ к базе данных. В следующем примере для базы данных устанавливается режим `RESTRICTED_USER`, ограничивающий доступ к ней. Затем состояние базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] устанавливается в `READ_ONLY`, а также возвращается доступ к базе данных всем пользователям.

```sql
USE master;
GO
ALTER DATABASE AdventureWorks2012
SET RESTRICTED_USER;
GO
ALTER DATABASE AdventureWorks2012
SET READ_ONLY
GO
ALTER DATABASE AdventureWorks2012
SET MULTI_USER;
GO

```

### <a name="b-enabling-snapshot-isolation-on-a-database"></a>Б. Включение изоляции моментального снимка для базы данных
Следующий пример включает параметр платформы изоляции моментального снимка для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].

```sql
USE AdventureWorks2012;
USE master;
GO
ALTER DATABASE AdventureWorks2012
SET ALLOW_SNAPSHOT_ISOLATION ON;
GO
-- Check the state of the snapshot_isolation_framework
-- in the database.
SELECT name, snapshot_isolation_state,
    snapshot_isolation_state_desc AS description
FROM sys.databases
WHERE name = N'AdventureWorks2012';
GO
```

Результирующий набор показывает, что платформа изоляции моментального снимка включена.

|name |snapshot_isolation_state |description|
|-------------------- |------------------------|----------|
|AdventureWorks2012 |1| ON |

### <a name="c-enabling-modifying-and-disabling-change-tracking"></a>В. Включение, изменение и отключение отслеживания изменений

В следующем примере демонстрируется включение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и установка `2`-дневного срока хранения.

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING = ON
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);
```

В следующем примере демонстрируется уменьшение срока хранения до `3` дней.

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);
```

В следующем примере демонстрируется отключение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING = OFF;
```

### <a name="d-enabling-the-query-store"></a>Г. Включение хранилища запросов

Следующий пример включает хранилище запросов и настраивает его параметры.

```sql
ALTER DATABASE AdventureWorks2012
SET QUERY_STORE = ON
(
      OPERATION_MODE = READ_WRITE
    , CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 )
    , DATA_FLUSH_INTERVAL_SECONDS = 900
    , MAX_STORAGE_SIZE_MB = 1024
    , INTERVAL_LENGTH_MINUTES = 60
    );
```

## <a name="see-also"></a>См. также:

- [Уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)
- [Зеркальное отображение базы данных ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)
- [Статистика](../../relational-databases/statistics/statistics.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=azuresqldb-currentls)
- [Включение и отключение отслеживания изменений](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)
- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)
- [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)
- [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
- [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)
- [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
- [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)
- [Рекомендации по хранилищу запросов](../../relational-databases/performance/best-practice-with-the-query-store.md)

::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](alter-database-transact-sql-set-options.md?view=sql-server-2017)|[Отдельная база данных/эластичный пул Базы данных SQL<br />](alter-database-transact-sql-set-options.md?view=azuresqldb-current) |**_\* Управляемый экземпляр Базы данных SQL<br /> \*_** &nbsp;||[Хранилище данных<br />SQL](alter-database-transact-sql-set-options.md?view=azure-sqldw-latest)||||

&nbsp;

## <a name="azure-sql-database-managed-instance"></a>Управляемый экземпляр Базы данных SQL Azure

Уровни совместимости являются параметрами инструкции `SET`, но описаны в отдельной статье [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).

> [!NOTE]
> Многие параметры инструкции DATABASE SET можно настроить только для текущего сеанса с помощью [инструкций SET](../../t-sql/statements/set-statements-transact-sql.md). Они часто задаются приложениями при подключении. Параметры инструкции SET уровня сеанса переопределяют значения **ALTER DATABASE SET**. Описанные далее параметры базы данных являются значениями, которые можно задавать для сеансов, не предоставляющих явно другие значения параметра SET.

## <a name="syntax"></a>Синтаксис

```
ALTER DATABASE { database_name | Current }
SET
{
    <optionspec> [ ,...n ]
}
;

<optionspec> ::=
{
    <auto_option>
  | <change_tracking_option>
  | <cursor_option>
  | <db_encryption_option>
  | <delayed_durability_option>
  | <parameterization_option>
  | <query_store_options>
  | <snapshot_option>
  | <sql_option>
  | <target_recovery_time_option>
  | <termination>
  | <temporal_history_retention>
}
;
<auto_option> ::=
{
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }
  | AUTO_SHRINK { ON | OFF }
  | AUTO_UPDATE_STATISTICS { ON | OFF }
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }
}

<automatic_tuning_option> ::=
{
  AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = { ON | OFF } )
}

<change_tracking_option> ::=
{
  CHANGE_TRACKING
   {
       = OFF
     | = ON [ ( <change_tracking_option_list > [,...n] ) ]
     | ( <change_tracking_option_list> [,...n] )
   }
}

<change_tracking_option_list> ::=
   {
       AUTO_CLEANUP = { ON | OFF }
     | CHANGE_RETENTION = retention_period { DAYS | HOURS | MINUTES }
   }

<cursor_option> ::=
{
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }
}

<db_encryption_option> ::=
  ENCRYPTION { ON | OFF }

<delayed_durability_option> ::=DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }

<parameterization_option> ::=
  PARAMETERIZATION { SIMPLE | FORCED }

<query_store_options> ::=
{
  QUERY_STORE
  {
    = OFF
    | = ON [ ( <query_store_option_list> [,... n] ) ]
    | ( < query_store_option_list> [,... n] )
    | CLEAR [ ALL ]
  }
}

<query_store_option_list> ::=
{
  OPERATION_MODE = { READ_WRITE | READ_ONLY }
  | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )
  | DATA_FLUSH_INTERVAL_SECONDS = number
  | MAX_STORAGE_SIZE_MB = number
  | INTERVAL_LENGTH_MINUTES = number
  | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]
  | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]
  | MAX_PLANS_PER_QUERY = number
}

<snapshot_option> ::=
{
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }
  | READ_COMMITTED_SNAPSHOT {ON | OFF }
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT {ON | OFF }
}
<sql_option> ::=
{
    ANSI_NULL_DEFAULT { ON | OFF }
  | ANSI_NULLS { ON | OFF }
  | ANSI_PADDING { ON | OFF }
  | ANSI_WARNINGS { ON | OFF }
  | ARITHABORT { ON | OFF }
  | COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }
  | NUMERIC_ROUNDABORT { ON | OFF }
  | QUOTED_IDENTIFIER { ON | OFF }
  | RECURSIVE_TRIGGERS { ON | OFF }
}

<temporal_history_retention>::=TEMPORAL_HISTORY_RETENTION { ON | OFF }
```

## <a name="arguments"></a>Аргументы

*database_name*         
Имя изменяемой базы данных.

CURRENT         
`CURRENT` выполняет действие в текущей базе данных. `CURRENT` работает не со всеми параметрами и не во всех контекстах. Если `CURRENT` не работает, укажите имя базы данных.

**\<auto_option> ::=**         

Управляет автоматическими параметрами.

<a name="auto_create_statistics"></a> AUTO_CREATE_STATISTICS { ON | OFF }         
ON         
Оптимизатор запросов в случае необходимости создает статистику по отдельным столбцам в предикатах запросов, чтобы улучшить планы запросов и повысить производительность запросов. Такая статистика по отдельным столбцам создается, когда оптимизатор запросов компилирует запросы. Статистика по отдельным столбцам создается только для столбцов, ни один из которых не является первым столбцом в существующем объекте статистики.

Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.

OFF         
Оптимизатор запросов не создает статистику по отдельным столбцам в предикатах запросов во время компиляции запросов. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_create_stats_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoCreateStatistics функции DATABASEPROPERTYEX.

Дополнительные сведения см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

INCREMENTAL = ON | OFF         
Присваивает AUTO_CREATE_STATISTICS значение ON, а INCREMENTAL — значение ON. Он создает автоматически создаваемые статистики как добавочные везде, где поддерживаются добавочные статистики. Значение по умолчанию — OFF. Дополнительные сведения см. в описании [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).

<a name="auto_shrink"></a> AUTO_SHRINK { ON | OFF }         
ON         
Файлы базы данных являются кандидатами на периодическое сжатие.

И файлы данных, и файлы журналов могут быть автоматически сжаты. AUTO_SHRINK уменьшает размер журнала транзакций только в том случае, если вы выбрали простую модель восстановления базы данных или создали резервную копию журнала. Если этот параметр установлен в состояние OFF, файлы базы данных не будут автоматически сжиматься при периодической проверке на неиспользуемое пространство.

При включенном параметре AUTO_SHRINK файлы будут сжаты, если более 25 процентов файла содержит неиспользуемое пространство. Параметр вызывает сжатие файла в один из двух размеров. Он сжимает до большего, если:

- размер, в котором 25 процентов файла не используется;
- размер файла при его создании.

Нельзя сжать базу данных, находящуюся в состоянии только для чтения.

OFF         
Автоматическое сжатие файлов при периодической проверке на неиспользуемое пространство не производится.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_shrink_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoShrink функции DATABASEPROPERTYEX.

> [!NOTE]
> В автономной базе данных параметр AUTO_SHRINK недоступен.

<a name="auto_update_statistics"></a> AUTO_UPDATE_STATISTICS { ON | OFF }         
ON         
Указывает, что оптимизатор запросов обновляет статистику, если она используется в запросе и может оказаться устаревшей. Статистика становится устаревшей, после того как операции вставки, обновления, удаления или слияния изменяют распределение данных в таблице или индексированном представлении. Оптимизатор запросов определяет, когда статистика может оказаться устаревшей, подсчитывая операции изменения данных с момента последнего обновления статистики и сравнивая количество изменений с пороговым значением. Пороговое значение основано на количестве строк в таблице или индексированном представлении.

Оптимизатор запросов проверяет наличие устаревшей статистики перед компиляцией запроса и выполняет кэшированный план запроса. Оптимизатор запросов с помощью столбцов, таблиц и индексированных представлений в предикате запроса определяет, какая статистика могла устареть. Оптимизатор запросов определяет эти сведения перед компиляцией запроса. Перед выполнением кэшированного плана запроса компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверяет, ссылается ли план запроса на актуальную статистику.

Параметр AUTO_UPDATE_STATISTICS применяется к статистике, создаваемой для индексов и отдельных столбцов в предикатах запросов, и к статистике, создаваемой инструкцией CREATE STATISTICS. Этот параметр также применяется к отфильтрованной статистике.

Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.

Используйте параметр AUTO_UPDATE_STATISTICS_ASYNC, чтобы указать режим обновления статистики: синхронный или асинхронный.

OFF         
Указывает, что оптимизатор запросов не обновляет статистику, если она используется в запросе. Оптимизатор запросов также не обновляет статистику, когда она становится устаревшей. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_update_stats_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAutoUpdateStatistics функции DATABASEPROPERTYEX.

Дополнительные сведения см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

<a name="auto_update_statistics_async"></a> AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }         
ON         
Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется асинхронно. Оптимизатор запросов не ожидает завершения обновления статистики перед компиляцией запросов.

Установка этого параметра в состояние ON не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в состояние ON.

По умолчанию параметр AUTO_UPDATE_STATISTICS_ASYNC имеет значение OFF, а оптимизатор запросов обновляет статистику в синхронном режиме.

OFF         
Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется синхронно. Оптимизатор запросов ожидает завершения обновления статистики перед компиляцией запросов.

Установка этого параметра в значение OFF не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в значение ON.

Вы можете определить состояние этого параметра с помощью проверки столбца is_auto_update_stats_async_on в представлении каталога sys.databases.

Дополнительные сведения, описывающие условия применения синхронного и асинхронного обновлений статистики, см. в подразделе "Использование параметров статистики на уровне базы данных" раздела [Статистика](../../relational-databases/statistics/statistics.md).

<a name="auto_tuning"></a> **\<automatic_tuning_option> ::=**          
**Применимо к**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)].

Включает или отключает параметр [автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md) `FORCE_LAST_GOOD_PLAN`.

FORCE_LAST_GOOD_PLAN = { ON | OFF }         
ON         
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] автоматически включает последний известный удачный план для [!INCLUDE[tsql-md](../../includes/tsql-md.md)] запросов, когда новый план SQL приводит к снижению производительности. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] непрерывно отслеживает производительность запроса [!INCLUDE[tsql-md](../../includes/tsql-md.md)] в форсированном плане. В случае повышения производительности [!INCLUDE[ssde_md](../../includes/ssde_md.md)] будет продолжать использовать последний известный удачный план. Если повышений производительности нет, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] создаст новый план SQL. Инструкция завершится ошибкой, если хранилище запросов не включено или не находится в режиме *Чтение и запись*. 

OFF         
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] сообщает о потенциальном снижении производительности запросов, вызванном изменениями планов SQL в представлении [sys.dm_db_tuning_recommendations](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md). Однако эти рекомендации не применяются автоматически. Пользователь может отслеживать активные рекомендации и устранять выявленные проблемы, применяя сценарии [!INCLUDE[tsql-md](../../includes/tsql-md.md)], которые отображаются в представлении. Это значение по умолчанию.

**\<change_tracking_option> ::=**

Определяет параметры отслеживания изменений. Отслеживание изменений можно включить или отключить, а также установить или изменить параметры. Примеры использования см. далее в этой статье.

ON         
Включает отслеживание изменений для базы данных. При включении отслеживания изменений также необходимо задать параметры AUTO CLEANUP и CHANGE RETENTION.

AUTO_CLEANUP = { ON | OFF }         
ON         
Данные отслеживания изменений автоматически удаляются по истечении заданного срока хранения.

OFF         
Данные отслеживания изменений не удаляются из базы данных.

CHANGE_RETENTION =*retention_period* { DAYS | HOURS | MINUTES }         
Указывает минимальный срок хранения данных отслеживания изменений в базе данных. Данные удаляются, только если для параметра AUTO_CLEANUP установлено значение ON.

*retention_period* — целое число, указывающее числовой компонент срока хранения.

Срок хранения по умолчанию — 2 дня. Минимальный срок хранения составляет 1 минуту. Тип хранения по умолчанию — DAYS.

OFF         
Отключает отслеживание изменений для базы данных. Перед отключением отслеживания изменений для базы данных предварительно отключите отслеживание изменений для всех таблиц.

**\<cursor_option> ::=**         

Управляет параметрами курсора.

CURSOR_CLOSE_ON_COMMIT { ON | OFF }         
ON         
Любые курсоры, открытые при фиксации или откате транзакции, закрываются.

OFF         
Курсоры остаются открытыми при завершении транзакции; откат транзакции закрывает любые курсоры (кроме тех, которые имеют свойства INSENSITIVE или STATIC).

Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CURSOR_CLOSE_ON_COMMIT. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая CURSOR_CLOSE_ON_COMMIT в значение OFF для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md).

Состояние этого параметра можно определить, проверив значение столбца is_cursor_close_on_commit_on в представлении каталога sys.databases или свойства IsCloseCursorsOnCommitEnabled функции DATABASEPROPERTYEX. Курсор неявно освобождается только при отключении. Дополнительные сведения см. в описании [DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md).

**\<db_encryption_option> ::=**         

Определяет параметры шифрования базы данных.

ENCRYPTION { ON | OFF }         
Включает шифрование базы данных (ON) или отключает его (OFF). Дополнительные сведения см. в статьях о [прозрачном шифровании данных](../../relational-databases/security/encryption/transparent-data-encryption.md) и [прозрачном шифровании данных для Базы данных SQL Azure](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md).

Если включить шифрование на уровне базы данных, будут зашифрованы все файловые группы. Все новые файловые группы наследуют свойство шифрования. Если любая файловая группа базы данных установлена в состояние **READ ONLY**, операция шифрования базы завершится неуспешно.

Параметры шифрования базы данных можно просмотреть с помощью динамического административного представления [sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md).

**\<db_update_option> ::=**         

Управляет разрешениями на обновления базы данных.

READ_ONLY         
Пользователи могут считывать данные из базы данных, но не могут изменять их.

> [!NOTE]
> Для улучшения производительности запросов выполните обновление статистики перед тем, как перевести базу данных в режим доступа READ_ONLY. После перевода базы данных в режим READ_ONLY потребуется дополнительная статистика, она будет создана компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] в tempdb. Дополнительные сведения о статистике для базы данных, доступной только для чтения, см. в разделе [Статистика](../../relational-databases/statistics/statistics.md).

READ_WRITE         
База данных доступна для операций чтения и записи.

Чтобы изменить это состояние, необходимо обладать монопольным доступом к базе данных.

**\<db_user_access_option> ::=**         

Управляет пользовательским доступом к базе данных.

RESTRICTED_USER         
Предложение RESTRICTED_USER позволяет подключаться к базе данных только членам предопределенных ролей базы данных db_owner и dbcreator и предопределенной роли сервера sysadmin, количество соединений при этом не ограничивается. Все соединения с базой данных будут отключены на период времени, определяемый завершающим предложением инструкции ALTER DATABASE. После того как база данных перешла в состояние RESTRICTED_USER, попытки подключения пользователей, не соответствующими описанным выше условиям, будут отклонены. **RESTRICTED_USER** нельзя изменить с помощью управляемого экземпляра Базы данных SQL.

MULTI_USER         
Все пользователи, имеющие соответствующие разрешения на подключение к базе данных, будут допущены к базе данных.

Состояние этого параметра можно определить, проверив значение столбца user_access в представлении каталога sys.databases или свойства UserAccess функции DATABASEPROPERTYEX.

**\<delayed_durability_option> ::=**         

Управляет тем, является ли фиксация транзакций полностью устойчивой или отложенной устойчивой.

DISABLED         
Все транзакции, следующие за SET DISABLED, являются полностью устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.

ALLOWED         
Все транзакции, следующие за SET ALLOWED, являются полностью устойчивыми или отложенными устойчивыми, в зависимости от параметра устойчивости, заданного в блоке ATOMIC или инструкции COMMIT.

FORCED         
Все транзакции, следующие за SET FORCED, являются отложенными устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.

**\<PARAMETERIZATION_option> ::=**         

Управляет параметром параметризации.

PARAMETERIZATION { SIMPLE | FORCED }         
SIMPLE         
Запросы параметризуются на основании поведения базы данных по умолчанию.

FORCED         
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметризует все запросы в базе данных.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_parameterization_forced в представлении каталога sys.databases.

**\<query_store_options> ::=**         

ON | OFF | CLEAR [ ALL ]         
Указывает, включено ли хранилище запросов в этой базе данных, а также управляет удалением содержимого хранилища запросов.

ON         
Включает хранилище запросов.

OFF         
Отключает хранилище запросов. Это значение по умолчанию.

CLEAR         
Удаляет содержимое хранилища запросов.

OPERATION_MODE         
Описывает режим работы хранилища запросов. Допустимые значения: READ_ONLY и READ_WRITE. В режиме READ_WRITE хранилище запросов собирает и сохраняет план запросов и статистические данные о выполнении. В режиме READ_ONLY можно считывать данные из хранилища запросов, но новые сведения не добавляются. Если выделенное свободное место в хранилище запросов будет исчерпано, хранилище переключится в режим работы READ_ONLY.

CLEANUP_POLICY         
Описывает политику хранения данных хранилища запросов. STALE_QUERY_THRESHOLD_DAYS определяет количество дней хранения сведений о запросе в хранилище. STALE_QUERY_THRESHOLD_DAYS имеет тип **bigint**.

DATA_FLUSH_INTERVAL_SECONDS         
Определяет частоту, с которой данные, записанные в хранилище запросов, сохраняются на диск. Для оптимизации производительности данные, собранные хранилищем запросов, асинхронно записываются на диск. Для настройки частоты этой асинхронной передачи используется аргумент DATA_FLUSH_INTERVAL_SECONDS. DATA_FLUSH_INTERVAL_SECONDS имеет тип **bigint**.

MAX_STORAGE_SIZE_MB         
Определяет свободное место, выделенное для хранилища запросов. MAX_STORAGE_SIZE_MB имеет тип **bigint**.

INTERVAL_LENGTH_MINUTES         
Определяет временной интервал вычисления статистических данных о среде выполнения в хранилище запросов. Для оптимизации использования свободного места статистические данные о среде выполнения в хранилище вычисляются для фиксированного временного интервала. Этот интервал настраивается с помощью аргумента INTERVAL_LENGTH_MINUTES. INTERVAL_LENGTH_MINUTES имеет тип **bigint**.

SIZE_BASED_CLEANUP_MODE         
Определяет, будет ли автоматически активирована очистка, когда общий объем данных приблизится к верхней границе ограничения.

OFF         
Очистка на основе размера не будет автоматически активирована.

AUTO         
Очистка на основе размера активируется автоматически при достижении размера на диске 90 % от **max_storage_size_mb**. Эта очистка сначала удаляет самые дешевые и самые старые запросы. Она останавливается приблизительно на 80 % от **max_storage_size_mb**. Это значение конфигурации по умолчанию.

SIZE_BASED_CLEANUP_MODE имеет тип **nvarchar**.

QUERY_CAPTURE_MODE         
Определяет режим записи текущего активного запроса.

ALL         
Записываются все запросы. Это значение конфигурации по умолчанию.

AUTO         
Записываются соответствующие запросы на основе показателя выполнения и объема потребления ресурсов. Это значение конфигурации является значением по умолчанию для [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].

None         
Запись новых запросов останавливается. Хранилище запросов будет продолжать сбор статистики компиляции и времени выполнения для запросов, которые уже были записаны. Эту конфигурацию следует использовать с осторожностью, поскольку можно пропустить запись важных запросов.

QUERY_CAPTURE_MODE имеет тип **nvarchar**.

MAX_PLANS_PER_QUERY         
Целое число, представляющее максимальное количество поддерживаемых планов для каждого запроса. Значение по умолчанию — 200.

**\<snapshot_option> ::=**         

Определяет уровень изоляции транзакции.

ALLOW_SNAPSHOT_ISOLATION { ON | OFF }         
ON         
Включает параметр моментальных снимков на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После установки этого параметра транзакции могут задавать уровень изоляции транзакций SNAPSHOT. Если транзакция выполняется на уровне изоляции SNAPSHOT, всем инструкциям видны данные из моментального снимка в состоянии, которое существовало в момент начала транзакции. Если транзакция выполняется с уровнем изоляции SNAPSHOT и обращается к данным нескольких баз данных, то либо параметр ALLOW_SNAPSHOT_ISOLATION должен быть установлен в состояние ON во всех базах данных, либо каждая инструкция в транзакции должна использовать подсказки блокировки при любом обращении предложения FROM к таблице базы данных, в которой параметр ALLOW_SNAPSHOT_ISOLATION установлен в состояние OFF.

OFF         
Отключает параметр моментальных снимков на уровне базы данных. Транзакции не могут указывать уровень изоляции SNAPSHOT.

Если вы изменяете состояние ALLOW_SNAPSHOT_ISOLATION (из ON в OFF или из OFF в ON), инструкция ALTER DATABASE не возвращает управление вызвавшей ее программе, пока все существующие транзакции в базе данных не будут зафиксированы. Если база данных уже находится в состоянии, указанном в инструкции ALTER DATABASE, управление вызвавшей программе будет возвращено немедленно. Используйте процедуру [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md), чтобы определить наличие длительно выполняющихся транзакций. Если инструкция ALTER DATABASE отменена, база данных останется в состоянии, в котором она находилась при запуске ALTER DATABASE. Представление каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) отображает состояние транзакций с уровнем изоляции моментальных снимков в базе данных. Если **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON, ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF, операция будет повторена через шесть секунд.

Изменить состояние ALLOW_SNAPSHOT_ISOLATION невозможно, если база данных находится в режиме OFFLINE.

При установке параметра ALLOW_SNAPSHOT_ISOLATION в базе данных, находящейся в режиме READ_ONLY, он будет сохранен при переводе базы данных в режим READ_WRITE.

Настройки ALLOW_SNAPSHOT_ISOLATION можно изменить и для баз данных master, model, msdb и tempdb. Если изменить значение для базы данных tempdb, оно будет сохраняться каждый раз при остановке и перезапуске экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.

Этот параметр для баз данных master и msdb по умолчанию установлен в состояние ON.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца snapshot_isolation_state в представлении каталога sys.databases.

READ_COMMITTED_SNAPSHOT { ON | OFF }         
ON         
Включает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После включения этого параметра транзакции, указывающие уровень изоляции READ COMMITTED, используют управление версиями строк вместо блокировки. Данные моментального снимка видны всем инструкциям в состоянии, которое существовало на момент начала выполнения инструкции, если транзакция выполняется с уровнем изоляции зафиксированной операции чтения.

OFF         
Отключает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Транзакции с уровнем изоляции READ COMMITTED используют блокировку.

Чтобы установить параметр READ_COMMITTED_SNAPSHOT в значение ON или OFF, с базой данных не должно быть активных соединений, за исключением соединения, выполняющего команду ALTER DATABASE. Однако это не означает, что база данных должна находиться в однопользовательском режиме. Изменить состояние этого параметра невозможно, если база данных находится в режиме OFFLINE.

При установке параметра READ_COMMITTED_SNAPSHOT в базе данных, которая находится в режиме READ_ONLY, это состояние будет сохранено при переводе базы данных в режим READ_WRITE.

Параметр READ_COMMITTED_SNAPSHOT не может быть установлен в ON для системных баз данных master, tempdb или msdb. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.

Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_read_committed_snapshot_on в представлении каталога sys.databases.

> [!WARNING]
>Если таблица создается с аргументом **DURABILITY = SCHEMA_ONLY**, а затем **READ_COMMITTED_SNAPSHOT** меняется с помощью **ALTER DATABASE**, данные в таблице будут утеряны.

MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }         
ON         
Если уровень изоляции транзакции установлен в любое значение ниже SNAPSHOT, все интерпретированные операции [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах, оптимизированных для памяти, выполняются с уровнем изоляции SNAPSHOT. Примеры уровней изоляции ниже, чем моментальный снимок — READ COMMITTED или READ UNCOMMITTED. Эти операции выполняются независимо от того, установлен ли уровень изоляции транзакции явно на уровне сеанса или неявно используется значение по умолчанию.

OFF         
Не повышает уровень изоляции транзакции для интерпретированных операций [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах, оптимизированных для памяти.

Изменить состояние MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT невозможно, если база данных находится в режиме OFFLINE.

Значение по умолчанию — OFF.

Текущее состояние этого параметра можно определить, проверив значение столбца **is_memory_optimized_elevate_to_snapshot_on** в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).

**\<sql_option> ::=**         

Управляет параметрами соответствия ANSI на уровне базы данных.

ANSI_NULL_DEFAULT { ON | OFF }         
Определяет значение по умолчанию, NULL или NOT NULL, для столбцов [определяемых пользователем типов CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md), для которых в инструкциях CREATE TABLE или ALTER TABLE не указана явно допустимость значений NULL. Столбцы, определенные с ограничениями, следуют правилам ограничения независимо от этой настройки.

ON         
Значение по умолчанию — NULL.

OFF         
Значением по умолчанию является NOT NULL.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_NULL_DEFAULT. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_NULL_DEFAULT в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md).

Для совместимости ANSI при установке параметра базы данных ANSI_NULL_DEFAULT в состояние ON изменяется значение по умолчанию базы данных на значение NULL.

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_null_default_on в представлении каталога sys.databases. Вы можете также определить состояние с помощью проверки свойства IsAnsiNullDefault функции DATABASEPROPERTYEX.

ANSI_NULLS { ON | OFF }         
ON         
Результатом любого сравнения со значением NULL будет UNKNOWN.

OFF         
Результатом сравнения значений не в Юникоде будет TRUE, если оба значения — NULL.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_NULLS всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.

  Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_NULLS. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_NULLS в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md).

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_NULLS также должен быть установлен в ON.

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_nulls_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiNullsEnabled функции DATABASEPROPERTYEX.

ANSI_PADDING { ON | OFF }         
ON         
Строки перед преобразованием дополняются до одной и той же длины. Выравнивание строк также выполняется перед вставкой в тип данных **varchar** или **nvarchar**.

OFF         
Вставляет замыкающие пробелы в значениях символов в столбцах **varchar** или **nvarchar**. Параметр также оставляет замыкающие нули в двоичных значениях, вставляемых в столбцы значений **varbinary**. Значения не подгоняются под длину столбца.

Состояние OFF касается только определения новых столбцов.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_PADDING всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Рекомендуется всегда задавать для параметра ANSI_PADDING значение ON. При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр ANSI_PADDING должен быть установлен в ON.

Столбцы с типами **char(_n_)** и **binary(_n_)** , допускающие значения NULL, выравниваются по длине столбца, если параметр ANSI_PADDING имеет значение ON. Конечные пробелы и нули отбрасываются, если параметр ANSI_PADDING имеет значение OFF. Столбцы с типами **char(_n_)** и **binary(_n_)** , которые не допускают значений NULL, всегда выравниваются по длине столбца.

  Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_PADDING. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_PADDING в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_padding_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiPaddingEnabled функции DATABASEPROPERTYEX.

ANSI_WARNINGS { ON | OFF }         
ON         
В случае возникновения таких ситуаций, как деление на ноль, выдаются ошибки или предупреждения. Ошибки и предупреждения также возникают тогда, когда значения NULL появляются в агрегатных функциях.

OFF         
Предупреждения не выводятся, а в таких ситуациях, как деление на ноль, возвращается NULL.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_WARNINGS должен быть установлен в ON.

  Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_WARNINGS. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая ANSI_WARNINGS в значение ON для сеанса по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_ansi_warnings_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsAnsiWarningsEnabled функции DATABASEPROPERTYEX.

ARITHABORT { ON | OFF }         
ON         
Запрос будет завершен, если во время его выполнения возникла ошибка переполнения или деления на ноль.

OFF         
Когда возникает одна из этих ошибок, выводится предупреждающее сообщение. Запрос, пакет или транзакция продолжают выполняться, как если бы ошибки не произошло, даже если выводится предупреждение.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ARITHABORT должен быть установлен в ON.

  Вы можете определить состояние этого параметра с помощью проверки столбца is_arithabort_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsArithmeticAbortEnabled функции DATABASEPROPERTYEX.

COMPATIBILITY_LEVEL = { 150 | 140 | 130 | 120 | 110 | 100 }         
Дополнительные сведения см. в статье [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).

CONCAT_NULL_YIELDS_NULL { ON | OFF }         
ON         
Результатом операции объединения будет NULL, если любой из операндов — NULL. Например, объединение строки символов "Это" со значением NULL приведет к результату NULL вместо "Это".

OFF         
Значение NULL будет обработано как пустая строка символов.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр CONCAT_NULL_YIELDS_NULL должен быть установлен в ON.

> [!IMPORTANT]
> В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр CONCAT_NULL_YIELDS_NULL всегда будет иметь значение ON, а все приложения, явно устанавливающие значение параметра равным OFF, вызовут ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.

Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CONCAT_NULL_YIELDS_NULL. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр CONCAT_NULL_YIELDS_NULL инструкции SET уровня соединения в состояние ON для сеанса. Дополнительные сведения см. в описании [SET CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).

Вы можете определить состояние этого параметра с помощью проверки столбца is_concat_null_yields_null_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsNullConcat функции DATABASEPROPERTYEX.

QUOTED_IDENTIFIER { ON | OFF }         
ON         
Двойные кавычки могут использоваться для идентификаторов с разделителями.

Все строки, находящиеся в двойных кавычках, интерпретируются как идентификаторы объектов. Идентификаторы с разделителями не должны соответствовать правилам для идентификаторов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Они могут быть ключевыми словами и могут включать символы, не разрешенные в идентификаторах [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если в состав строки-литерала входит одиночная кавычка ('), строка может быть заключена в двойные кавычки (").

OFF         
Идентификаторы не могут быть заключены в кавычки и должны следовать всем правилам для идентификаторов [!INCLUDE[tsql](../../includes/tsql-md.md)]. Литералы могут разделяться как одинарными, так и двойными кавычками.

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также допускает разделение идентификаторов квадратными скобками ([]). Идентификаторы в скобках могут использоваться всегда, независимо от значения параметра QUOTED_IDENTIFIER. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).

  При создании таблицы параметр QUOTED IDENTIFIER всегда сохраняется как ON в метаданных таблицы. Параметр сохраняется, даже если при создании таблицы он был установлен на OFF.

Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для QUOTED_IDENTIFIER. Клиенты ODBC и OLE DB задают параметр уровня соединения инструкции SET, устанавливая QUOTED_IDENTIFIER в значение ON, по умолчанию. Клиенты выполняют инструкцию при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в описании [SET QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md).

  Вы можете определить состояние этого параметра с помощью проверки столбца is_quoted_identifier_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsQuotedIdentifiersEnabled функции DATABASEPROPERTYEX.

NUMERIC_ROUNDABORT { ON | OFF }         
ON         
Если в выражении происходит потеря точности, будет сформирована ошибка.

OFF         
Потеря точности вызывает сообщения об ошибках, а результат округляется до точности столбца или переменной, в которых сохраняется результат.

При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр NUMERIC_ROUNDABORT должен быть установлен в OFF.

Вы можете определить состояние этого параметра с помощью проверки столбца is_numeric_roundabort_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsNumericRoundAbortEnabled функции DATABASEPROPERTYEX.

RECURSIVE_TRIGGERS { ON | OFF }         
ON         
Рекурсивное срабатывание триггеров AFTER разрешено.

OFF         
Вы можете определить состояние этого параметра с помощью проверки столбца is_recursive_triggers_on в представлении каталога sys.databases. Вы также можете определить состояние с помощью проверки свойства IsRecursiveTriggersEnabled функции DATABASEPROPERTYEX.

> [!NOTE]
> Если параметр RECURSIVE_TRIGGERS установлен в состояние OFF, будет запрещена только прямая рекурсия. Чтобы отключить косвенную рекурсию, нужно установить параметр сервера nested triggers в состояние 0.

Состояние этого параметра можно определить, проверив значение столбца is_recursive_triggers_on в представлении каталога sys.databases или свойства IsRecursiveTriggersEnabled функции DATABASEPROPERTYEX.

**\<target_recovery_time_option> ::=**         

Указывает частоту косвенных контрольных точек для каждой базы данных. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], значение по умолчанию для новых баз данных равно 1 минуте, что указывает, что база данных будет использовать косвенные контрольные точки. Для более старых версий по умолчанию установлено значение 0, при котором базой данных используются автоматические контрольные точки, а их частота зависит от параметра интервала для восстановления экземпляра сервера. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует 1 минуту для большинства систем.

TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS | MINUTES }         
*target_recovery_time*         
Указывает максимальное время для восстановления определенной базы данных в случае сбоя.

SECONDS         
Указывает, что значение *target_recovery_time* выражается в количестве секунд.

MINUTES         
Указывает, что значение *target_recovery_time* выражается в количестве минут.

Сведения о косвенных контрольных точках см. в статье [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md).

ROLLBACK AFTER *integer* [SECONDS] | ROLLBACK IMMEDIATE         
Указывает, нужно ли откатить транзакцию через указанное количество секунд или немедленно.

NO_WAIT         
Указывает, что запрос завершится ошибкой, если нужное состояние базы данных или изменение параметра не может совершиться немедленно. Завершение работы сразу же означает завершение без ожидания фиксации транзакции или отката.

## <a name="SettingOptions"></a> Настройка параметров         
Для извлечения текущих параметров для параметров базы данных используйте представление каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) или [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md).

После установки параметра базы данных изменение вступает в силу немедленно.

Вы можете изменить значения по умолчанию для любого из параметров базы данных для всех созданных баз данных. Для этого измените соответствующий параметр базы данных в шаблоне.

## <a name="examples"></a>Примеры

### <a name="a-setting-the-database-to-read_only"></a>A. Перевод базы данных в состояние READ_ONLY
Для изменения состояния базы данных или файловой группы в READ_ONLY или READ_WRITE требуется монопольный доступ к базе данных. В следующем примере для базы данных устанавливается режим `RESTRICTED_USER` для ограничения доступа. Затем состояние базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] устанавливается в `READ_ONLY`, а также возвращается доступ к базе данных всем пользователям.

```sql
USE master;
GO
ALTER DATABASE AdventureWorks2012
SET RESTRICTED_USER;
GO
ALTER DATABASE AdventureWorks2012
SET READ_ONLY
GO
ALTER DATABASE AdventureWorks2012
SET MULTI_USER;
GO

```

### <a name="b-enabling-snapshot-isolation-on-a-database"></a>Б. Включение изоляции моментального снимка для базы данных
Следующий пример включает параметр платформы изоляции моментального снимка для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].

```sql
USE AdventureWorks2012;
USE master;
GO
ALTER DATABASE AdventureWorks2012
SET ALLOW_SNAPSHOT_ISOLATION ON;
GO
-- Check the state of the snapshot_isolation_framework
-- in the database.
SELECT name, snapshot_isolation_state,
    snapshot_isolation_state_desc AS description
FROM sys.databases
WHERE name = N'AdventureWorks2012';
GO
```

Результирующий набор показывает, что платформа изоляции моментального снимка включена.

|name |snapshot_isolation_state |description|
|-------------------- |------------------------|----------|
|AdventureWorks2012 |1| ON |

### <a name="c-enabling-modifying-and-disabling-change-tracking"></a>В. Включение, изменение и отключение отслеживания изменений
В следующем примере демонстрируется включение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и установка `2`-дневного срока хранения.

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING = ON
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);
```

В следующем примере демонстрируется уменьшение срока хранения до `3` дней.

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);
```

В следующем примере демонстрируется отключение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].

```sql
ALTER DATABASE AdventureWorks2012
SET CHANGE_TRACKING = OFF;
```

### <a name="d-enabling-the-query-store"></a>Г. Включение хранилища запросов
Следующий пример включает хранилище запросов и настраивает его параметры.

```sql
ALTER DATABASE AdventureWorks2012
SET QUERY_STORE = ON 
  (  
      OPERATION_MODE = READ_WRITE
    , CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 90 )
    , DATA_FLUSH_INTERVAL_SECONDS = 900
    , MAX_STORAGE_SIZE_MB = 1024
    , INTERVAL_LENGTH_MINUTES = 60
    );
```

## <a name="see-also"></a>См. также:

- [Уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)
- [Зеркальное отображение базы данных ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)
- [Статистика](../../relational-databases/statistics/statistics.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=azuresqldb-mi-current)
- [Включение и отключение отслеживания изменений](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)
- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)
- [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)
- [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
- [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)
- [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
- [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)
- [Рекомендации по хранилищу запросов](../../relational-databases/performance/best-practice-with-the-query-store.md)

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](alter-database-transact-sql-set-options.md?view=sql-server-2017)|[Отдельная база данных/эластичный пул Базы данных SQL<br />](alter-database-transact-sql-set-options.md?view=azuresqldb-current)|[Управляемый экземпляр Базы данных SQL<br />](alter-database-transact-sql-set-options.md?view=azuresqldb-mi-current)|**_\* Хранилище данных<br />SQL \*_** &nbsp;||||

&nbsp;

## <a name="azure-sql-data-warehouse"></a>Хранилище данных SQL Azure

## <a name="syntax"></a>Синтаксис

```
ALTER DATABASE { database_name }
SET
{
    <optionspec> [ ,...n ]
}
;

<option_spec>::=
{
<RESULT_SET_CACHING>
}
;

<RESULT_SET_CACHING>::=
{
RESULT_SET_CACHING {ON | OFF}
}

```

## <a name="arguments"></a>Аргументы

*database_name*

Имя изменяемой базы данных.

<a name="result_set_caching"></a> RESULT_SET_CACHING { ON | OFF }   
Область применения этой статьи: хранилище данных SQL Azure (предварительная версия)

Эта команда должна выполняться при подключении к базе данных `master`.  Изменение данного параметра базы данных применяется немедленно.  Затраты на хранение связаны с кэшированием результирующих наборов запроса. После отключения кэширования результатов для базы данных ранее сохраненный кэш результатов немедленно удаляется из Хранилища данных SQL Azure. В `sys.databases` появился новый столбец с именем is_result_set_caching_on. В нем отображаются параметры кэширования результатов для базы данных.  

ON   
Указывает, что результирующие наборы запросов, возвращаемые из этой базы данных, будут кэшироваться в Хранилище данных SQL Azure.

OFF   
Указывает, что результирующие наборы запросов, возвращаемые из этой базы данных, не будут кэшироваться в Хранилище данных SQL Azure. Пользователи могут определить, был ли запрос результатов выполнен с попаданием в кэше или промахом кэша, запросив sys.pdw_request_steps с конкретным идентификатором запроса request_id.   Если имеет место попадание в кэше, результат запроса будет содержать один шаг со следующими сведениями:

|**Имя столбца** |**Оператор** |**Значение** |
|----|----|----|
| operation_type|=|ReturnOperation|
|step_index|=|0|
|location_type|=|Control|
command|Похоже|%DWResultCacheDb%|
| | |

## <a name="remarks"></a>Remarks

Для запроса повторно используется кэшированный результирующий набор при соблюдении всех следующих требований:

1. Пользователь, выполняющий запрос, имеет доступ ко всем таблицам, на которые ссылается запрос.
1. Имеется точное соответствие между новым запросом и предыдущим запросом, породившим результирующий набор в кэше.
1. Нет изменений в данных или схеме в таблицах, на основе которых создан кэшированный результирующий набор.  

После включения кэширования результирующих наборов для базы данных результаты сохраняются в кэше для всех запросов, за исключением запросов с недетерминированными функциями, такими как DateTime.Now(), пока кэш не заполнится.   Запросы с большими результирующими наборами (например, свыше 1 млн строк) могут вызывать снижение производительности во время первого запуска, так как результат кэшируется.

## <a name="permissions"></a>Разрешения

Требуются следующие разрешения:

- имя входа субъекта серверного уровня, созданное процессом подготовки, или
- член роли базы данных `dbmanager`.

Владелец базы данных не может изменять базу данных, если он не является членом роли dbmanager.

## <a name="examples"></a>Примеры

### <a name="enable-result-set-caching-for-a-database"></a>Включение кэширования результирующих наборов для базы данных

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING ON;
```

### <a name="disable-result-set-caching-for-a-database"></a>Выключение кэширования результирующих наборов для базы данных

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING OFF;
```

### <a name="check-result-set-caching-setting-for-a-database"></a>Проверка кэширования результирующих наборов для базы данных

```sql
SELECT name, is_result_set_caching_on
FROM sys.databases;
```

### <a name="check-for-number-of-queries-with-result-set-cache-hit-and-cache-miss"></a>Проверка количества запросов результирующих наборов с попаданием в кэше и промахом кэша

```sql
SELECT  
Queries=CacheHits+CacheMisses,
CacheHits,
CacheMisses 
CacheHitPct=CacheHits*1.0/(CacheHits+CacheMisses)
FROM  
(SELECT  
CacheHits=count(distinct case when s.command like '%DWResultCacheDb%' and
r.resource_class IS NULL and s.operation_type = 'ReturnOperation' and  
s.step_index = 0 then s.request_id else null end) , 
CacheMisses=count(distinct case when r.resource_class IS NOT NULL then  
s.request_id else null end) 
     FROM sys.dm_pdw_request_steps s  
     JOIN sys.dm_pdw_exec_requests r  
     ON s.request_id = r.request_id) A;
```

### <a name="check-for-result-set-cache-hit-or-cache-miss-for-a-query"></a>Проверка попадания в кэше и промаха кэша результирующих наборов для запроса

```sql
If
(SELECT step_index  
FROM sys.dm_pdw_request_steps  
WHERE request_id = 'QID58286' and operation_type = 'ReturnOperation' and command like '%DWResultCacheDb%') = 0
SELECT 1 as is_cache_hit  
ELSE
SELECT 0 as is_cache_hit;
```

### <a name="check-for-all-queries-with-result-set-cache-hits"></a>Проверка всех запросов с попаданием в кэше результирующих наборов

```sql
SELECT *  
FROM sys.dm_pdw_request_steps  
WHERE command like '%DWResultCacheDb%' and step_index = 0;
```

## <a name="see-also"></a>См. также раздел

- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)
- [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)
- [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
- [Рекомендации по использованию Хранилища данных SQL Azure](/azure/sql-data-warehouse/sql-data-warehouse-best-practices#maintain-statistics)
- [Разработка таблиц в Хранилище данных SQL Azure](/azure/sql-data-warehouse/sql-data-warehouse-tables-overview#statistics)
- [Элементы языка для Хранилища данных SQL](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-language-elements)

::: moniker-end
