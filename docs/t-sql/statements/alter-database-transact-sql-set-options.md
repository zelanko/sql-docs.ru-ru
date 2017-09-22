---
title: "ИЗМЕНИТЬ параметры SET базы данных (Transact-SQL) | Документы Microsoft"
description: "Дополнительные сведения о том, как задать параметры базы данных, например автоматической настройки, шифрование хранилища запросов в SQL Server и базы данных SQL Azure"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
ms.assetid: f76fbd84-df59-4404-806b-8ecb4497c9cc
caps.latest.revision: 159
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: d3e4af471573ffa2220eb9dfb1ee7a129899b5eb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="alter-database-set-options-transact-sql"></a>Параметры ALTER DATABASE SET (Transact-SQL) 
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  В данном разделе приведен синтаксис инструкции ALTER DATABASE, связанный с установкой параметров базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для других Синтаксис инструкции ALTER DATABASE в следующих разделах.  
  
-   [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  

-   [ALTER DATABASE &#40; База данных Azure SQL &#41;](/sql-docs/docs/t-sql/statements/alter-database-azure-sql-database) 

-   [ALTER DATABASE &#40; Хранилище данных Azure SQL &#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)  
  
-   [ALTER DATABASE &#40; Параллельное хранилище данных &#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)  
  
Зеркальное отображение базы данных, [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], и уровни совместимости `SET` параметры но описаны в отдельных разделах из-за их длины. Дополнительные сведения см. в разделе [ALTER база данных зеркального отображения базы данных &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md), [ALTER DATABASE SET HADR &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-hadr.md), и [изменить уровень совместимости базы данных &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
> [!NOTE]  
>  Можно настроить многие параметры set базы данных для текущего сеанса с помощью [инструкции SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md) и они часто задаются приложениями при подключении. Параметры инструкции SET уровня сеанса переопределяют значения **ALTER DATABASE SET** . Описанные далее параметры баз данных являются значениями, которые можно задавать для сеансов, не предоставляющих явно другие значения параметров инструкции SET.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER DATABASE { database_name  | CURRENT }  
SET   
{  
    <optionspec> [ ,...n ] [ WITH <termination> ]   
}  
  
<optionspec> ::=   
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
}  
  
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
    ENCRYPTION { ON | OFF }  
  
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
    | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]  
    | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]  
    | MAX_PLANS_PER_QUERY = number
    | WAIT_STATS_CAPTURE_MODE = [ ON | OFF ]
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
                  {   CREDENTIAL = <db_scoped_credential_name>  
                     | FEDERATED_SERVICE_ACCOUNT =  ON | OFF   
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
  | COMPATIBILITY_LEVEL = { 90 | 100 | 110 | 120}  
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}  
  
<target_recovery_time_option> ::=  
    TARGET_RECOVERY_TIME = target_recovery_time { SECONDS | MINUTES }  
  
<termination>  ::=   
{  
    ROLLBACK AFTER integer [ SECONDS ]   
  | ROLLBACK IMMEDIATE   
  | NO_WAIT  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя изменяемой базы данных.  
  
 CURRENT  
 **Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 `CURRENT`выполняет действие в текущей базе данных. `CURRENT`не поддерживается для всех параметров во всех контекстах. Если `CURRENT` завершается ошибкой, укажите имя базы данных.  
  
 **\<auto_option >:: =**  
  
 Управляет автоматическими параметрами.  
  
 AUTO_CLOSE { ON | OFF }  
 ON  
 База данных закрыта правильно, а ее ресурсы освобождены после выхода последнего пользователя.  
  
 База данных автоматически открывается, если пользователь снова пытается подключиться к ней. Например, введя `USE database_name` инструкции. Если база данных аккуратно закрыта во время установки параметра AUTO_CLOSE в состояние ON, она не будет повторно открываться при попытках использовать ее, пока компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не будет перезапущен.  
  
 OFF  
 База данных остается открытой после того, как последний пользователь вышел.  
  
 Параметр AUTO_CLOSE полезен для настольных баз данных, поскольку он позволяет управлять файлами базы данных так же, как обычными файлами. Они могут быть перемещены, скопированы для создания резервной копии или даже отосланы по электронной почте другим пользователям. AUTO_CLOSE — это асинхронный процесс; многократное открытие и закрытие базы данных не влияет на производительность.  
  
> [!NOTE]  
>  Параметр AUTO_CLOSE недоступен в автономной базе данных или на [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_auto_close_on в представлении каталога sys.databases или свойства IsAutoClose функции DATABASEPROPERTYEX.  
  
> [!NOTE]  
>  Если параметр AUTO_CLOSE имеет значение ON, некоторые столбцы в представлении каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) и функция DATABASEPROPERTYEX будут возвращать значение NULL, так как база данных будет недоступна для извлечения данных. Для решения этой проблемы выполните инструкцию USE, чтобы открыть базу данных.  
  
> [!NOTE]  
>  Зеркальное отображение базы данных требует, чтобы параметр AUTO_CLOSE был установлен в состояние OFF.  
  
 Если параметр базы данных AUTOCLOSE установлен в значение ON, то действия, инициирующие автоматическое закрытие базы данных, очищают кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 2 (SP2) и выше для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных». Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
 AUTO_CREATE_STATISTICS { ON | OFF }  
 ON  
 Оптимизатор запросов в случае необходимости создает статистику по отдельным столбцам в предикатах запросов, чтобы улучшить планы запросов и повысить производительность запросов. Такая статистика по отдельным столбцам создается, когда оптимизатор запросов компилирует запросы. Статистика по отдельным столбцам создается только для столбцов, ни один из которых не является первым столбцом в существующем объекте статистики.  
  
 Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.  
  
 OFF  
 Оптимизатор запросов не создает статистику по отдельным столбцам в предикатах запросов во время компиляции запросов. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_auto_create_stats_on в представлении каталога sys.databases или свойства IsAutoCreateStatistics функции DATABASEPROPERTYEX.  
  
 Дополнительные сведения см. в подразделе «Использование параметров статистики уровня базы данных» в [статистики](../../relational-databases/statistics/statistics.md).  
  
 INCREMENTAL = ON | OFF  
 Если для AUTO_CREATE_STATISTICS установлено значение ON и для INCREMENTAL тоже ON, то автоматически создаваемые статистики создаются как добавочные везде, где поддерживаются добавочные статистики. Значение по умолчанию — OFF. Дополнительные сведения см. в разделе [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).  
  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 AUTO_SHRINK { ON | OFF }  
 ON  
 Файлы базы данных являются кандидатами на периодическое сжатие.  
  
 И файлы данных, и файлы журналов могут быть автоматически сжаты. AUTO_SHRINK уменьшает размер журнала транзакций только в том случае, если выбрана простая модель восстановления базы данных или была создана резервная копия журнала. Если этот параметр установлен в состояние OFF, файлы базы данных не будут автоматически сжиматься при периодической проверке на неиспользуемое пространство.  
  
 При включенном параметре AUTO_SHRINK файлы будут сжаты, если более 25 процентов файла содержит неиспользуемое пространство. Файл будет сжат до размера, в котором 25 процентов файла — неиспользуемое пространство, или до того размера, который был у файла при создании, каким бы большим он ни был.  
  
 Нельзя сжать базу данных, находящуюся в состоянии только для чтения.  
  
 OFF  
 Автоматическое сжатие файлов при периодической проверке на неиспользуемое пространство не производится.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_auto_shrink_on в представлении каталога sys.databases или свойства IsAutoShrink функции DATABASEPROPERTYEX.  
  
> [!NOTE]  
>  В автономной базе данных параметр AUTO_SHRINK недоступен.  
  
 AUTO_UPDATE_STATISTICS { ON | OFF }  
 ON  
 Указывает, что оптимизатор запросов обновляет статистику, если она используется в запросе и может оказаться устаревшей. Статистика становится устаревшей, после того как операции вставки, обновления, удаления или слияния изменяют распределение данных в таблице или индексированном представлении. Оптимизатор запросов определяет, когда статистика может оказаться устаревшей, подсчитывая операции изменения данных с момента последнего обновления статистики и сравнивая количество изменений с пороговым значением. Пороговое значение основано на количестве строк в таблице или индексированном представлении.  
  
 Оптимизатор запросов проверяет наличие устаревшей статистики перед компиляцией запроса и до выполнения кэшированного плана запроса. Перед компиляцией запроса оптимизатор запросов с помощью столбцов, таблиц и индексированных представлений в предикате запроса определяет, какая статистика могла устареть. Перед выполнением кэшированного плана запроса компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверяет, ссылается ли план запроса на актуальную статистику.  
  
 Параметр AUTO_UPDATE_STATISTICS применяется к статистике, создаваемой для индексов и отдельных столбцов в предикатах запросов, и к статистике, создаваемой инструкцией CREATE STATISTICS. Этот параметр также применяется к отфильтрованной статистике.  
  
 Значение по умолчанию — ON. Для большинства баз данных рекомендуется использовать значение по умолчанию.  
  
 Используйте параметр AUTO_UPDATE_STATISTICS_ASYNC, чтобы указать режим обновления статистики, синхронный или асинхронный.  
  
 OFF  
 Указывает, что оптимизатор запросов не обновляет статистику, если она используется в запросе и может оказаться устаревшей. Отключение этого параметра может повлечь создание неоптимальных планов запросов и снижение производительности запросов.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_auto_update_stats_on в представлении каталога sys.databases или свойства IsAutoUpdateStatistics функции DATABASEPROPERTYEX.  
  
 Дополнительные сведения см. в подразделе «Использование параметров статистики уровня базы данных» в [статистики](../../relational-databases/statistics/statistics.md).  
  
 AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
 ON  
 Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется асинхронно. Оптимизатор запросов не ожидает завершения обновления статистики перед компиляцией запросов.  
  
 Установка этого параметра в состояние ON не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в состояние ON.  
  
 По умолчанию параметр AUTO_UPDATE_STATISTICS_ASYNC имеет значение OFF, а оптимизатор запросов обновляет статистику в синхронном режиме.  
  
 OFF  
 Указывает, что обновление статистики для параметра AUTO_UPDATE_STATISTICS выполняется синхронно. Оптимизатор запросов ожидает завершения обновления статистики перед компиляцией запросов.  
  
 Установка этого параметра в значение OFF не будет иметь эффекта, если параметр AUTO_UPDATE_STATISTICS не установлен в значение ON.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_auto_update_stats_async_on в представлении каталога sys.databases.  
  
 Дополнительные сведения, описывающие условия обновления статистики, синхронный или асинхронный использовать, см. в подразделе «Использование параметров статистики уровня базы данных» в [статистики](../../relational-databases/statistics/statistics.md).  
  
 **\<automatic_tuning_option >:: =**  
 **Область применения**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)].  

 Включает или отключает `FORCE_LAST_GOOD_PLAN` [автоматической настройки](../../relational-databases/automatic-tuning/automatic-tuning.md) параметр.  
  
 FORCE_LAST_GOOD_PLAN = {ON | {OFF}  
 ON  
 [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Автоматически обеспечивает последнего известного хороший план на [!INCLUDE[tsql_md](../../includes/tsql_md.md)] запросы, когда новый план SQL приводит к снижению производительности. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Непрерывное отслеживает производительность запросов [!INCLUDE[tsql_md](../../includes/tsql_md.md)] запрос в форсированном плане. При наличии прироста производительности, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] будет продолжать использовать последние известные хороший план. Если производительность не обнаружены, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] будет создавать новый план SQL. Инструкция завершится ошибкой, если хранилище запросов не включено или не находится в *чтения и записи* режим.   

 OFF  
 [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Сообщает о потенциальных снижением производительности запросов, вызванным изменениями планов SQL в [sys.dm_db_tuning_recommendations](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) представления. Тем не менее эти рекомендации не применяются автоматически. Пользователю можно отслеживать active рекомендации и Устранение определенных проблем, применяя [!INCLUDE[tsql_md](../../includes/tsql_md.md)] сценарии, которые отображаются в представлении. Это значение по умолчанию.

 **\<change_tracking_option >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Определяет параметры отслеживания изменений. Отслеживание изменений можно включить или отключить, а также установить или изменить параметры. Примеры использования см. далее в этом разделе.  
  
 ON  
 Включает отслеживание изменений для базы данных. При включении отслеживания изменений также необходимо задать параметры AUTO CLEANUP и CHANGE RETENTION.  
  
 AUTO_CLEANUP = { ON | OFF }  
 ON  
 Данные отслеживания изменений автоматически удаляются по истечении заданного срока хранения.  
  
 OFF  
 Данные отслеживания изменений не удаляются из базы данных.  
  
 CHANGE_RETENTION =*retention_period* {дни | ЧАСЫ | МИН}  
 Указывает минимальный срок хранения данных отслеживания изменений в базе данных. Данные удаляются, только если для параметра AUTO_CLEANUP установлено значение ON.  
  
 *retention_period* представляет собой целое число, указывающее числовой компонент срока хранения.  
  
 Срок хранения по умолчанию — 2 дня. Минимальный срок хранения составляет 1 минуту. Тип хранения по умолчанию — дней.  
  
 OFF  
 Отключает отслеживание изменений для базы данных. Чтобы отключить отслеживание изменений для базы данных, необходимо предварительно отключить отслеживание изменений для всех таблиц.  
  
 **\<containment_option >:: =**  
  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет параметрами автономной работы базы данных.  
  
 ВКЛЮЧЕНИЯ = {NONE | ЧАСТИЧНОЕ}  
 None  
 База данных не является автономной.  
  
 PARTIAL  
 Это автономная база данных. Задать параметр частичной автономности базы данных невозможно, если в базе данных включена репликация, сбор данных об изменениях или отслеживание изменений. Проверка на наличие ошибок прекращается после обнаружения первой ошибки. Дополнительные сведения об автономных базах данных см. в разделе [Contained Databases](../../relational-databases/databases/contained-databases.md).  
  
> [!NOTE]  
>  Вложения не могут быть настроены на [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]. Вложения не поддерживают явно, но [!INCLUDE[ssSDS](../../includes/sssds-md.md)] можно использовать автономной функции например содержащихся пользователей базы данных.  
  
 **\<cursor_option >:: =**  
  
 Управляет параметрами курсора.  
  
 CURSOR_CLOSE_ON_COMMIT { ON | OFF }  
 ON  
 Любые курсоры, открытые при завершении или откате транзакции, будут закрыты.  
  
 OFF  
 Курсоры остаются открытыми при завершении транзакции; откат транзакции закрывает любые курсоры (кроме тех, которые имеют свойства INSENSITIVE или STATIC).  
  
 Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CURSOR_CLOSE_ON_COMMIT. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр CURSOR_CLOSE_ON_COMMIT инструкции SET уровня подключения в состояние OFF для сеанса. Дополнительные сведения см. в разделе [SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL)](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md).  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_cursor_close_on_commit_on в представлении каталога sys.databases или свойства IsCloseCursorsOnCommitEnabled функции DATABASEPROPERTYEX.  
  
 CURSOR_DEFAULT { LOCAL | GLOBAL }  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет тем, какую область (LOCAL или GLOBAL) использует курсор.  
  
 LOCAL  
 Если указано LOCAL и курсор не определен как GLOBAL при создании, то область курсора локальна по отношению к пакету, хранимой процедуре или триггеру, в которых он был создан. Имя курсора действительно только внутри этой области. На курсор могут ссылаться локальные переменные пакета, хранимые процедуры, триггеры или выходной параметр хранимой процедуры. Курсор будет неявно освобожден при завершении пакета, хранимой процедуры или триггера, если только он не был передан в выходном параметре. Если курсор передан в выходном параметре, курсор будет освобожден, когда последняя переменная, которая ссылается на него, будет освобождена или выйдет из области.  
  
 GLOBAL  
 Если параметр GLOBAL задан и курсор во время создания не определен как LOCAL, то область курсора глобальна относительно соединения. Имя курсора может использоваться любой хранимой процедурой или пакетом, которые выполняются в соединении.  
  
 Курсор неявно освобождается только при отключении. Дополнительные сведения см. в разделе [DECLARE CURSOR &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-cursor-transact-sql.md).  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_local_cursor_default в представлении каталога sys.databases или свойства IsLocalCursorsDefault функции DATABASEPROPERTYEX.  
  
 **\<database_mirroring >**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Описания аргументов см. в разделе [ALTER база данных зеркального отображения базы данных &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md).  
  
 **\<date_correlation_optimization_option >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет параметром date_correlation_optimization.  
  
 DATE_CORRELATION_OPTIMIZATION { ON | OFF }  
 ON  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]поддерживает статистику корреляции между любыми двумя таблицами в базе данных, которые связаны ограничением FOREIGN KEY и имеют **datetime** столбцов.  
  
 OFF  
 Статистика корреляции не поддерживается.  
  
 Для установки параметра DATE_CORRELATION_OPTIMIZATION в состояние ON не должно быть активных соединений с базой данных (за исключением соединения, в котором выполняется инструкция ALTER DATABASE). Впоследствии возможность нескольких соединений будет поддерживаться.  
  
 Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_date_correlation_on в представлении каталога sys.databases.  
  
 **\<db_encryption_option >:: =**  
  
 Определяет параметры шифрования базы данных.  
  
 ENCRYPTION {ON | OFF}  
 Включает шифрование базы данных (ON) или отключает его (OFF). Дополнительные сведения о шифровании баз данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md), и [прозрачное шифрование данных в базе данных Azure SQL](../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md).  
  
 Если включить шифрование на уровне базы данных, будут зашифрованы все файловые группы. Все новые файловые группы наследуют свойство шифрования. Если любая файловая группа базы данных установлена в состояние **READ ONLY**, операция шифрования базы завершится неуспешно.  
  
 Можно просмотреть состояние шифрования базы данных с помощью [sys.dm_database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) динамическое административное представление.  
  
 **\<db_state_option >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет состоянием базы данных.  
  
 OFFLINE  
 База данных аккуратно закрыта и помечена как вне сети. В режиме «вне сети» базу данных изменять нельзя.  
  
 ONLINE  
 База данных открыта и доступна для использования.  
  
 EMERGENCY  
 База данных помечена как READ_ONLY, ведение журнала отключено и доступ возможен только элементам предопределенной роли сервера sysadmin. EMERGENCY используется в основном для диагностики. Например, база данных, помеченная как подозрительная из-за поврежденного файла журнала, может быть переведена в состояние EMERGENCY. Таким образом, системный администратор может получить доступ к базе данных только для чтения. Только члены предопределенной роли сервера sysadmin могут перевести базу данных в состояние EMERGENCY.  
  
> [!NOTE]  
>  **Разрешения:** для изменения базы данных в состояние вне сети или в аварийном требуется разрешение ALTER DATABASE для базы данных предметной. Разрешение ALTER ANY DATABASE на уровне сервера требуется, чтобы перевести базу данных из режима «вне сети» в режим «в сети».  
  
 Состояние этого параметра можно определить с помощью проверки столбцов state и state_desc в [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представление каталога или свойства Status [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) функции. Дополнительные сведения см. в разделе [Database States](../../relational-databases/databases/database-states.md).  
  
 База данных, находящаяся в состоянии RESTORING, не может быть переведена в состояние OFFLINE, ONLINE или EMERGENCY. База данных может находиться в состоянии RESTORING во время выполнения операции восстановления или тогда, когда при операции восстановления базы данных или файла журнала происходит сбой из-за поврежденного файла резервной копии.  
  
 **\<db_update_option >:: =**  
  
 Управляет разрешениями на обновления базы данных.  
  
 READ_ONLY  
 Пользователи могут считывать данные из базы данных, но не могут изменять их.  
  
> [!NOTE]  
>  Для улучшения производительности запросов выполните обновление статистики перед тем, как перевести базу данных в режим доступа READ_ONLY. После перевода базы данных в режим READ_ONLY потребуется дополнительная статистика, она будет создана компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] в tempdb. Дополнительные сведения о статистике для базы данных только для чтения см. в разделе [статистики](../../relational-databases/statistics/statistics.md).  
  
 READ_WRITE  
 База данных доступна для операций чтения и записи.  
  
 Чтобы изменить это состояние, необходимо обладать монопольным доступом к базе данных. Дополнительные сведения см. в описании предложения SINGLE_USER.  
  
> [!NOTE]  
>  Применительно к федеративным базам данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)], инструкция SET { READ_ONLY | READ_WRITE } отключена.  
  
 **\<db_user_access_option >:: =**  
  
 Управляет пользовательским доступом к базе данных.  
  
 SINGLE_USER  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Указывает, что только один пользователь одновременно может обращаться к базе данных. Если параметр SINGLE_USER указан и есть другие пользователи, подключенные к базе данных, инструкция ALTER DATABASE будет блокирована, пока все пользователи не отключатся от указанной базы данных. Чтобы переопределить это поведение, см. предложение WITH \<завершения > предложения.  
  
 База данных остается в режиме SINGLE_USER, даже если пользователь, который установил этот параметр, отключился. В этот момент к базе данных могут подключаться и другие пользователи, но одновременно может быть подключен только один.  
  
 Перед заданием параметра SINGLE_USER проверьте, чтобы параметру AUTO_UPDATE_STATISTICS_ASYNC было присвоено значение OFF. Если он равен ON, то фоновый поток, используемый для обновления статистики, соединится с базой данных и доступ к базе данных в однопользовательском режиме будет невозможен. Чтобы просмотреть состояние этого параметра, запросите столбец is_auto_update_stats_async_on в [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога. Если параметр установлен в значение ON, выполните следующие действия.  
  
1.  Установите AUTO_CREATE_STATISTICS_ASYNC в значение OFF.  
  
2.  Проверьте наличие активных асинхронных заданий статистики, запрос [sys.dm_exec_background_job_queue](../../relational-databases/system-dynamic-management-views/sys-dm-exec-background-job-queue-transact-sql.md) динамическое административное представление.  
  
 При наличии активных задач, либо разрешить заданий, которые необходимо завершить или отменить их вручную при помощи [KILL STATS JOB](../../t-sql/language-elements/kill-stats-job-transact-sql.md).  
  
RESTRICTED_USER  
 Предложение RESTRICTED_USER позволяет подключаться к базе данных только членам предопределенных ролей базы данных db_owner и dbcreator и предопределенной роли сервера sysadmin, количество соединений при этом не ограничивается. Все соединения с базой данных будут отключены на период времени, определяемый завершающим предложением инструкции ALTER DATABASE. После того как база данных перешла в состояние RESTRICTED_USER, попытки подключения пользователей, не соответствующими описанным выше условиям, будут отклонены.  
  
MULTI_USER  
 Все пользователи, имеющие соответствующие разрешения на подключение к базе данных, будут допущены к базе данных.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца user_access в представлении каталога sys.databases или свойства UserAccess функции DATABASEPROPERTYEX.  
  
 **\<delayed_durability_option >:: =**  
  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет тем, является ли фиксация транзакций полностью устойчивой или отложенной устойчивой.  
  
 DISABLED  
 Все транзакции, следующие за SET DISABLED, являются полностью устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.  
  
 ALLOWED  
 Все транзакции, следующие за SET ALLOWED, являются полностью устойчивыми или отложенными устойчивыми, в зависимости от параметра устойчивости, заданного в блоке ATOMIC или инструкции COMMIT.  
  
 FORCED  
 Все транзакции, следующие за SET FORCED, являются отложенными устойчивыми. Все параметры устойчивости, заданные в блоке ATOMIC или инструкции COMMIT, не учитываются.  
  
 **\<external_access_option >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет возможностью обращения к базе данных из внешних ресурсов, таких как объекты другой базы данных.  
  
 DB_CHAINING { ON | OFF }  
 ON  
 База данных может быть источником или целевой базой данных межбазовой цепочки владения.  
  
 OFF  
 База данных не может быть членом межбазовой цепочки владения.  
  
> [!IMPORTANT]  
>  Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распознает эту настройку, если параметр сервера cross db ownership chaining имеет значение 0 (OFF). Если параметр cross db ownership chaining имеет значение 1 (ON), то все пользовательские базы данных могут участвовать в межбазовых цепочках владения, вне зависимости от значения этого параметра. Этот параметр задается с помощью [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 Установка этого параметра требуется разрешение CONTROL SERVER для базы данных.  
  
 Параметр DB_CHAINING не может устанавливаться на этих системных баз данных: master, model и tempdb.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_db_chaining_on в представлении каталога sys.databases.  
  
 TRUSTWORTHY { ON | OFF }  
 ON  
 Модули базы данных (например, определяемые пользователем функции или хранимые процедуры), которые используют контекст олицетворения, могут обращаться к ресурсам, находящимся вне базы данных.  
  
 OFF  
 Модули базы данных в контексте олицетворения не могут обращаться к ресурсам, находящимся вне базы данных.  
  
 Параметр TRUSTWORTHY устанавливается в значение OFF при каждом присоединении базы данных.  
  
 По умолчанию для всех системных баз данных, кроме msdb, параметр TRUSTWORTHY установлен в значение OFF. Оно не изменяется для баз данных model и tempdb. Рекомендуется никогда не устанавливать параметр TRUSTWORTHY в состояние ON для базы данных master.  
  
 Установка этого параметра требуется разрешение CONTROL SERVER для базы данных.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_trustworthy_on в представлении каталога sys.databases.  
  
 DEFAULT_FULLTEXT_LANGUAGE  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает язык, используемый по умолчанию для полнотекстовых индексированных столбцов.  
  
> [!IMPORTANT]  
>  Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.  
  
 DEFAULT_LANGUAGE  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает язык, используемый по умолчанию для всех созданных имен входа. Чтобы задать язык, можно указать идентификатор локали (lcid), название языка или псевдоним языка. Список допустимых языка имена и псевдонимы. в разделе [sys.syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md). Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.  
  
 NESTED_TRIGGERS  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает, допустимо ли каскадирование триггеров AFTER, то есть выполнение действия, вызывающего срабатывание другого триггера, который может инициировать другой триггер, и т. д. Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.  
  
 TRANSFORM_NOISE_WORDS  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Используется для подавления сообщения об ошибке, если логическая операция по полнотекстовому запросу не срабатывает из-за пропускаемых слов или стоп-слов. Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.  
  
 TWO_DIGIT_YEAR_CUTOFF  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает целое число в промежутке от 1753 до 9999, представляющее пороговое значение года для преобразования двухзначной записи лет в четырехзначную. Этот параметр допустим только в случае, если параметр CONTAINMENT равен PARTIAL. Если параметр CONTAINMENT установлен в состояние NONE, возникнут ошибки.  
  
 **\<FILESTREAM_option >:: =**  
  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Управляет параметрами таблиц FileTables.  
  
 NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }  
 OFF  
 Нетранзакционный доступ к данным таблиц FileTable отключен.  
  
 READ_ONLY  
 Данные FILESTREAM из таблиц FileTable в этой базе данных могут считываться нетранзакционными процессами.  
  
 ПОЛНОЕ  
 Включен полный нетранзакционный доступ к данным FILESTREAM в таблицах FileTable.  
  
 Имя_каталога = * \<directory_name >*  
 Имя каталога, совместимое с Windows. Это имя должно быть уникальным среди всех имен каталогов уровня базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Проверка уникальности выполняется без учета регистра, независимо от параметров сортировки. Этот параметр должен быть задан до создания таблицы FileTable в этой базе данных.  
  
 **\<HADR_options >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 В разделе [ALTER DATABASE SET HADR &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-hadr.md).  
  
 **\<mixed_page_allocation_option >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)). Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 MIXED_PAGE_ALLOCATION {OFF | НА} элементов управления ли базы данных можно создать начальной страницы, использование смешанного экстента для первых восьми страниц таблицы или индекса.  
  
 OFF  
 База данных всегда создавать начальной страницы, использование однородных экстентов. Это значение по умолчанию.  
  
 ON  
 В базе данных можно создавать начальной страницы, использующие смешанных экстентов.  
  
 Этот параметр включен для всех системных баз данных. **База данных tempdb** — база данных только для системы, которая поддерживает OFF.  
  
 **\<PARAMETERIZATION_option >:: =**  
  
 Управляет параметром параметризации.  
  
 PARAMETERIZATION { SIMPLE | FORCED }  
 SIMPLE  
 Запросы параметризуются на основании поведения базы данных по умолчанию.  
  
 FORCED  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметризует все запросы в базе данных.  
  
 Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_parameterization_forced в представлении каталога sys.databases.  
  
 **\<query_store_options >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (от[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 ON | OFF | CLEAR [ ALL ]  
 Указывает, включено ли хранилище запросов в этой базе данных, а также управляет удалением содержимого хранилища запросов.  
  
ON  
 Включает хранилище запросов.  
  
OFF  
 Отключает хранилище запросов.  Это значение по умолчанию.   
  
CLEAR  
 Удалите содержимое хранилища запросов.  
  
OPERATION_MODE  
 Описывает режим работы хранилища запросов. Допустимые значения: READ_ONLY и READ_WRITE. В режиме READ_WRITE хранилище запросов собирает и сохраняет план запросов и статистические данные о выполнении. В режиме READ_ONLY можно считывать данные из хранилища запросов, но новые сведения не добавляется. Если выделенное свободное место в хранилище запросов будет исчерпано, хранилище переключится в режим работы READ_ONLY.  
  
 CLEANUP_POLICY  
 Описание политики хранения данных хранилища запросов. STALE_QUERY_THRESHOLD_DAYS определяет количество дней, для которых сохраняются сведения для запроса в хранилище запросов. STALE_QUERY_THRESHOLD_DAYS имеет тип **bigint**.  
  
 DATA_FLUSH_INTERVAL_SECONDS  
 Определяет частоту, с которой данные, записанные в хранилище запросов, сохраняются на диск. Для оптимизации производительности данные, собранные хранилищем запросов, асинхронно записываются на диск. Для настройки частоты этой асинхронной передачи используется аргумент DATA_FLUSH_INTERVAL_SECONDS. DATA_FLUSH_INTERVAL_SECONDS имеет тип **bigint**.  
  
 MAX_STORAGE_SIZE_MB  
 Определяет свободное место, выделенное для хранилища запросов. Тип — MAX_STORAGE_SIZE_MB **bigint**.  
  
 INTERVAL_LENGTH_MINUTES  
 Определяет временной интервал вычисления статистических данных о среде выполнения в хранилище запросов. Для оптимизации использования свободного места статистические данные о среде выполнения в хранилище вычисляются для фиксированного временного интервала. Этот интервал настраивается с помощью аргумента INTERVAL_LENGTH_MINUTES. INTERVAL_LENGTH_MINUTES имеет тип **bigint**.  
  
 SIZE_BASED_CLEANUP_MODE  
 Определяет, будет ли очистка автоматически активирована когда общий объем данных приблизится к максимальный размер:  
  
 OFF  
 Не будет автоматически активирована Очистка на основе размера. 
  
 AUTO  
 Размер, на основе Очистка активируется автоматически при размер на диске достигает 90% **max_storage_size_mb**. На основе размера очистки удаляет запросы бы дорогостоящий и старые сначала. Он останавливается на около 80% **max_storage_size_mb**.  Это конфигурация по умолчанию.  
  
 Тип — SIZE_BASED_CLEANUP_MODE **nvarchar**.  
  
 QUERY_CAPTURE_MODE  
 Определяет режим записи активного запроса:  
  
 Регистрируются все все запросы. Это конфигурация по умолчанию.  Это конфигурация по умолчанию[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]
  
 АВТОМАТИЧЕСКОГО отслеживания соответствующие запросы на основе выполнения count и потребления ресурсов.  Это конфигурация по умолчанию[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 Нет остановить запись новых запросов. Хранилище запросов будет продолжать сбор статистики компиляции и времени выполнения для запросов, которые уже были собраны. Эту конфигурацию следует используйте с осторожностью, поскольку можно пропустить для записи важных запросов.  
  
 Тип — QUERY_CAPTURE_MODE **nvarchar**.  
  
 max_plans_per_query  
 Целое число, представляющее максимальное количество поддерживаемых планов для каждого запроса. По умолчанию — 200.  
  
 **\<recovery_option >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет параметрами восстановления базы данных и проверкой ошибок дискового ввода-вывода.  
  
 ПОЛНОЕ  
 Обеспечивает полное восстановление после отказа носителя с помощью резервных копий журнала транзакций. Если файл данных поврежден, восстановление носителя может восстановить все зафиксированные транзакции. Дополнительные сведения см. в разделе [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
 BULK_LOGGED  
 Обеспечивает восстановление после отказа носителя, объединяя оптимальную производительность и минимальный объем пространства, занимаемого журналами; используется для больших систем или массовых операций. Чтобы узнать, какие операции можно выполнять с минимальным протоколированием, в разделе [резервная копия журнала транзакций &#40; SQL Server &#41; ](../../relational-databases/logs/the-transaction-log-sql-server.md). В модели восстановления BULK_LOGGED ведение журнала для этих операций минимально. Дополнительные сведения см. в разделе [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
 SIMPLE  
 Предусматривается стратегия простого резервирования, которая использует минимальное пространство под журналы. Пространство, отведенное под журналы, может быть автоматически многократно использовано, если оно больше не требуется для восстановления сбоев сервера. Дополнительные сведения см. в разделе [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
> [!IMPORTANT]  
>  Простая модель восстановления проще в управлении, чем другие две модели, но больше подвержена потере данных, если файл данных поврежден. Все изменения, начиная с наиболее свежей резервной копии базы данных или разностной резервной копии базы данных, будут потеряны и должны быть повторно введены вручную.  
  
 Модель восстановления по умолчанию определяется моделью восстановления базы данных **model** . Дополнительные сведения о выборе подходящей модели восстановления см. в разделе [моделей восстановления &#40; SQL Server &#41; ](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
 Состояние этого параметра можно определить с помощью проверки **recovery_model** и **recovery_model_desc** столбцы в представлении каталога sys.databases или свойства Recovery DATABASEPROPERTYEX функция.  
  
 TORN_PAGE_DETECTION { ON | OFF }  
 ON  
 Неполные страницы могут быть обнаружены компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 OFF  
 Неполные страницы не могут быть обнаружены компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
> [!IMPORTANT]  
>  Синтаксическая структура TORN_PAGE_DETECTION ON | OFF будет удалена в будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этой структуры в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Вместо этого используйте параметр PAGE_VERIFY.  
  
 PAGE_VERIFY { CHECKSUM | TORN_PAGE_DETECTION | NONE }  
 Обнаруживает поврежденные страницы базы данных, вызванные ошибками пути дискового ввода-вывода. Ошибки пути дискового ввода-вывода могут быть причиной повреждения базы данных и обычно происходят при сбоях питания или сбоях оборудования диска, происходящих во время записи страницы на диск.  
  
 CHECKSUM  
 Вычисляет контрольную сумму по содержимому целой страницы и сохраняет полученное значение в ее заголовке при записи страницы на диск. При чтении страницы с диска контрольная сумма вычисляется повторно и сравнивается с сохраненным в заголовке страницы значением. Если значения не соответствуют, будет выведено сообщение об ошибке 824 (ошибка контрольной суммы) как в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и в журнал событий Windows. Ошибка контрольной суммы указывает на проблему пути ввода-вывода. Чтобы определить первопричину, необходимо исследовать оборудование, драйверы встроенного ПО, BIOS, фильтрующее программное обеспечение (например, антивирусное) и другие компоненты ввода-вывода.  
  
 TORN_PAGE_DETECTION  
 Сохраняет определенный двухбитовый шаблон для каждого 512-байтового сектора в 8-килобайтной (КБ) странице базы данных и сохраняет в базе данных заголовок страницы при записи страницы на диск. При чтении страницы с диска биты разрыва, хранимые в заголовке страницы, сравниваются с действительными сведениями о секторах страницы. Несовпадающие значения указывают, что только часть страницы была записана на диск. В этой ситуации сообщение об ошибке 824 (ошибка разрыва страницы) будет выведено как в журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так и в журнал событий Windows. Разорванные страницы обычно обнаруживаются при восстановлении базы данных, если они действительно не полностью записаны. Однако другие сбои пути ввода-вывода могут стать причиной разрыва страницы в любое время.  
  
 None  
 Операции записи страниц базы данных не создают значение CHECKSUM или TORN_PAGE_DETECTION. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не будет проверять контрольную сумму и разрывы страниц при считывании, даже если значение CHECKSUM или TORN_PAGE_DETECTION будет присутствовать в заголовке страницы.  
  
 Рассмотрите следующие важные моменты при использовании параметра PAGE_VERIFY.  
  
-   Значение по умолчанию — CHECKSUM.  
  
-   При обновлении пользовательской или системной базы данных до версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней значение PAGE_VERIFY (NONE или TORN_PAGE_DETECTION) сохраняется. Рекомендуется использовать CHECKSUM.  
  
    > [!NOTE]  
    >  В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметру базы данных PAGE_VERIFY присваивается значение NONE применительно к базе данных tempdb, которая не может быть изменена. В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях значение по умолчанию для базы данных tempdb является CHECKSUM для новых установок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После обновления установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значением по умолчанию остается NONE. Этот параметр можно изменять. Для работы с базой данных tempdb рекомендуется использовать CHECKSUM.  
  
-   Значение TORN_PAGE_DETECTION использует меньше ресурсов, но обеспечивает минимальный вариант защиты CHECKSUM.  
  
-   Аргумент PAGE_VERIFY можно установить, не производя перевод базы данных в режим «вне сети», блокировку или прочие действия, нарушающие ее параллелизм.  
  
-   Значения CHECKSUM и TORN_PAGE_DETECTION являются взаимоисключающими. Оба параметра не могут быть включены одновременно.  
  
 При обнаружении ошибки разрыва страницы или контрольной суммы ее можно устранить с помощью восстановления из копии или потенциального перестроения индекса, если сбой ограничен только страницами индекса. При обнаружении ошибки контрольной суммы выполните инструкцию DBCC CHECKDB, чтобы определить тип поврежденной страницы базы данных. Дополнительные сведения о параметрах восстановления см. в разделе [аргументы инструкции RESTORE &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-arguments-transact-sql.md). Хотя восстановление данных решит проблему нарушения целостности данных, первопричина, например сбой оборудования диска, должна быть обнаружена и исправлена как можно скорее, чтобы предотвратить следующие ошибки.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторяет любую операцию считывания, которая закончилась ошибкой контрольной суммы, разрыва страницы или другой ошибкой ввода-вывода, четыре раза. Если считывание закончится успешно в любой из попыток, то в журнал ошибок будет записано сообщение и команда, вызвавшая считывание, продолжится. Если все повторные попытки закончатся ошибкой, команда закончит работу с сообщением об ошибке 824.  
  
 Дополнительные сведения о контрольной суммы, разрыва страницы, повторном считывании сообщения об ошибках 823 и 824 и других [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] характеристиках аудита ввода-вывода см. Эти [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkId=47160).  
  
 Текущее состояние этого параметра можно определить с помощью проверки значения столбца page_verify_option в [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представление каталога или свойства IsTornPageDetectionEnabled [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)функции.  
  
**\<remote_data_archive_option >:: =**  
  
 **Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Включает или отключает базы данных Stretch для базы данных. Дополнительные сведения см. в разделе [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
REMOTE_DATA_ARCHIVE = {ON (SERVER = \<имя_сервера >, {учетных данных = \<db_scoped_credential_name > | FEDERATED_SERVICE_ACCOUNT = ON | {OFF}) | OFF ON  
 Включает базу данных Stretch для базы данных. Дополнительные сведения, включая предварительные условия, в разделе [Enable Stretch Database для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 **Разрешения**. Включение базы данных Stretch для базы данных или таблицы требуются права db_owner. Включение базы данных Stretch для базы данных также требует разрешения CONTROL DATABASE.  
  
SERVER = \<имя_сервера >  
 Задает адрес сервера Azure. Включить `.database.windows.net` часть имени. Например, `MyStretchDatabaseServer.database.windows.net`.  
  
Учетные данные = \<db_scoped_credential_name >  
 Указывает учетные данные уровня базы данных, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует для подключения к серверу Azure. Убедитесь, что учетные данные существуют, перед выполнением этой команды. Дополнительные сведения см. в разделе [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  
  
FEDERATED_SERVICE_ACCOUNT = ON | ОТКЛЮЧЕНИЕ  
 Можно использовать федеративную учетную запись службы для локальным SQL Server для взаимодействия с удаленным сервером Azure при следующих условий.  
  
-   Учетная запись службы, под которой работает экземпляр SQL Server, является доменной учетной записью.  
  
-   Учетная запись домена принадлежит к домену, Active Directory которого входит в федерацию с Azure Active Directory.  
  
-   Удаленный сервер Azure настроен для поддержки проверки подлинности Azure Active Directory.  
  
-   Учетная запись службы, под которой выполняется экземпляр SQL Server, должна быть настроена как учетная запись dbmanager или sysadmin на удаленном сервере Azure.  
  
 Если будет указано значение ON, нельзя указывать аргумент учетных данных. При указании OFF, вы должны предоставить аргумент учетных данных.  
  
 OFF  
 Отключение базы данных Stretch для базы данных. Дополнительные сведения см. в разделе [Отключение Stretch Database и возврат удаленных данных](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
 Только после можно отключить базу данных Stretch для базы данных базы данных больше не содержит таблицы, которые включены для базы данных Stretch. Когда вы отключите базу данных Stretch, перенос данных остановится, а результаты запроса больше не будут включать результаты из удаленных таблиц.  
  
 Отключение растягивания не приводит к удалению удаленной базы данных. Если вы хотите удалить расположенную удаленно базу данных, вам потребуется сделать это с помощью портала управления Azure.  
  
**\<service_broker_option >:: =**  
  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Управляет следующими [!INCLUDE[ssSB](../../includes/sssb-md.md)] параметров: включает и отключает доставку сообщений, задает новый [!INCLUDE[ssSB](../../includes/sssb-md.md)] идентификатор или устанавливает приоритеты диалога в значение ON или OFF.  
  
 ENABLE_BROKER  
 Определяет, что для указанной базы данных включен компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Запущена доставка сообщений, и флаг is_broker_enabled установлен в значение TRUE в представлении каталога sys.databases. В базе данных сохраняется существующий идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Service Broker не может быть включен, пока база данных является основной в конфигурации зеркального отображения базы данных.  
  
> [!NOTE]  
>  Параметр ENABLE_BROKER требует монопольной блокировки базы данных. Если ресурсы базы данных блокированы другими сеансами, параметр ENABLE_BROKER будет ожидать снятия блокировок этими сеансами. Чтобы включить компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] в пользовательской базе данных, до запуска инструкции ALTER DATABASE SET ENABLE_BROKER убедитесь, что никакие другие сеансы не используют базу данных; это можно сделать, например, переводом базы данных в однопользовательский режим. Чтобы включить компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] в базе данных msdb, сначала необходимо остановить службу агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]», чтобы компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] мог получить необходимую блокировку.  
  
 DISABLE_BROKER  
 Указывает, что для заданной базы данных компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] отключен. Остановлена доставка сообщений, и флаг is_broker_enabled установлен в значение FALSE в представлении каталога sys.databases. В базе данных сохраняется существующий идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 NEW_BROKER  
 Указывает, что база данных должна получить новый идентификатор посредника. Поскольку база данных предполагает наличие нового компонента Service Broker, все существующие сеансы связи в базе данных будут немедленно удалены, не выдавая диалоговых сообщений о завершении. Все маршруты, ссылающиеся на старый идентификатор компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], необходимо создать повторно с новым идентификатором.  
  
 ERROR_BROKER_CONVERSATIONS  
 Указывает, что включена доставка сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Это позволяет сохранить существующий [!INCLUDE[ssSB](../../includes/sssb-md.md)] идентификатор для базы данных. [!INCLUDE[ssSB](../../includes/sssb-md.md)] завершает ошибкой все диалоги в базе данных. Это дает возможность приложениям выполнять регулярную очистку существующих диалогов.  
  
 HONOR_BROKER_PRIORITY {ON | OFF}  
 ON  
 Операции Send выполняются с учетом уровней приоритета, присвоенных диалогам. Сообщения от диалогов с высоким приоритетом отправляются раньше сообщений от диалогов с низким приоритетом.  
  
 OFF  
 Операции Send выполняются, как если бы все диалоги имели приоритет по умолчанию.  
  
 Изменение параметра HONOR_BROKER_PRIORITY имеет мгновенный эффект для новых диалогов или диалогов, ожидающих отправки сообщений. Диалоги, ожидающие отправки сообщений при выполнении ALTER DATABASE, не получат новое значение, пока им не будет отправлено несколько сообщений. Время, необходимое для начала использования нового значения всеми диалогами, может значительно изменяться.  
  
 Текущее значение этого свойства передается в столбце is_broker_priority_honored [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
 **\<snapshot_option >:: =**  
  
 Определяет уровень изоляции транзакции.  
  
 ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
 ON  
 Включает параметр моментальных снимков на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После установки этого параметра транзакции могут задавать уровень изоляции транзакций SNAPSHOT. Если транзакция выполняется на уровне изоляции SNAPSHOT, всем инструкциям видны данные из моментального снимка в состоянии, которое существовало в момент начала транзакции. Если транзакция выполняется с уровнем изоляции SNAPSHOT и обращается к данным нескольких баз данных, то либо параметр ALLOW_SNAPSHOT_ISOLATION должен быть установлен в состояние ON во всех базах данных, либо каждая инструкция в транзакции должна использовать подсказки блокировки при любом обращении предложения FROM к таблице базы данных, в которой параметр ALLOW_SNAPSHOT_ISOLATION установлен в состояние OFF.  
  
 OFF  
 Отключает параметр моментальных снимков на уровне базы данных. Транзакции не могут указывать уровень изоляции SNAPSHOT.  
  
 При изменении состояния параметра ALLOW_SNAPSHOT_ISOLATION (из ON в OFF или из OFF в ON) инструкция ALTER DATABASE не возвращает управления вызвавшей ее программе, пока все существующие транзакции в базе данных не будут зафиксированы. Если база данных уже находится в состоянии, указанном в инструкции ALTER DATABASE, управление вызвавшей программе будет возвращено немедленно. Если инструкция ALTER DATABASE не возвращает управление, используйте [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) определить необходимость длительные транзакции. Если инструкция ALTER DATABASE отменена, база данных останется в состоянии, в котором она находилась при запуске ALTER DATABASE. [Sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представление каталога указывает состояние транзакций изоляции моментальных снимков в базе данных. Если **snapshot_isolation_state_desc** = IN_TRANSITION_TO_ON, ALTER DATABASE ALLOW_SNAPSHOT_ISOLATION OFF будет шесть секунд и повторите операцию.  
  
 Изменить состояние ALLOW_SNAPSHOT_ISOLATION невозможно, если база данных находится в режиме OFFLINE.  
  
 При установке параметра ALLOW_SNAPSHOT_ISOLATION в базе данных, находящейся в режиме READ_ONLY, установка будет сохранена при переводе базы данных в режим READ_WRITE.  
  
 Настройки ALLOW_SNAPSHOT_ISOLATION можно изменить и для баз данных master, model, msdb и tempdb. Если изменить значение для базы данных tempdb, оно будет сохраняться каждый раз при остановке и перезапуске экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.  
  
 Этот параметр для баз данных master и msdb по умолчанию установлен в состояние ON.  
  
 Текущее состояние этого параметра можно определить с помощью проверки значения столбца snapshot_isolation_state в представлении каталога sys.databases.  
  
 READ_COMMITTED_SNAPSHOT { ON | OFF }  
 ON  
 Включает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Если параметр включен, инструкции DML начинают создавать версии строк, даже если ни одна транзакция не использует изоляцию моментальных снимков. После включения этого параметра транзакции, указывающие уровень изоляции READ COMMITTED, используют управление версиями строк вместо блокировки. Если транзакция выполняется с уровнем изоляции read committed, данные моментального снимка видны всем инструкциям в состоянии, которое существовало на момент начала выполнения инструкции.  
  
 OFF  
 Отключает параметр уровня изоляции моментальных снимков READ COMMITTED на уровне базы данных. Транзакции с уровнем изоляции READ COMMITTED используют блокировку.  
  
 Чтобы установить параметр READ_COMMITTED_SNAPSHOT в значение ON или OFF, с базой данных не должно быть активных соединений, за исключением соединения, выполняющего команду ALTER DATABASE. Однако это не означает, что база данных должна находиться в однопользовательском режиме. Изменить состояние этого параметра невозможно, если база данных находится в режиме OFFLINE.  
  
 При установке параметра READ_COMMITTED_SNAPSHOT в базе данных, которая находится в режиме READ_ONLY, это состояние будет сохранено при переводе базы данных в режим READ_WRITE.  
  
 Параметр READ_COMMITTED_SNAPSHOT не может быть установлен в ON для системных баз данных master, tempdb или msdb. При изменении настройки для базы данных model эта настройка становится значением по умолчанию для любых вновь создаваемых баз данных, за исключением tempdb.  
  
 Текущее состояние этого параметра можно определить с помощью проверки значения столбца is_read_committed_snapshot_on в представлении каталога sys.databases.  
  
> [!WARNING]  
>  При создании таблицы с **DURABILITY = SCHEMA_ONLY**, и **READ_COMMITTED_SNAPSHOT** впоследствии изменяется с помощью **инструкции ALTER DATABASE**, данные в таблице будут утеряны.  
  
 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT { ON | OFF }  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 ON  
 Если уровень изоляции транзакции установлен в любое значение ниже SNAPSHOT (например, READ COMMITTED или READ UNCOMMITTED), все интерпретированные операции [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах с оптимизацией для памяти выполняются с уровнем изоляции SNAPSHOT. Это делается независимо от того, установлен ли уровень изоляции транзакции явно на уровне сеанса, или неявно используется значение по умолчанию.  
  
 OFF  
 Не повышает уровень изоляции транзакции для интерпретированных операций [!INCLUDE[tsql](../../includes/tsql-md.md)] в таблицах с оптимизацией для памяти.  
  
 Изменить состояние MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT невозможно, если база данных находится в режиме OFFLINE.  
  
 Значение этого параметра по умолчанию — OFF.  
  
 Текущее состояние этого параметра можно определить с помощью проверки **is_memory_optimized_elevate_to_snapshot_on** столбца в [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
 **\<sql_option >:: =**  
  
 Управляет параметрами соответствия ANSI на уровне базы данных.  
  
 ANSI_NULL_DEFAULT { ON | OFF }  
 Определяет значение по умолчанию, NULL или NOT NULL для столбца или [определяемого пользователем типа CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) для которой не определена явно в инструкциях CREATE TABLE или ALTER TABLE. Столбцы, определенные с ограничениями, следуют правилам ограничения независимо от этой настройки.  
  
 ON  
 Значение по умолчанию — NULL.  
  
 OFF  
 Значением по умолчанию является NOT NULL.  
  
 Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_NULL_DEFAULT. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр ANSI_NULL_DEFAULT инструкции SET уровня соединения в состояние ON для сеанса. Дополнительные сведения см. в разделе [SET ANSI_NULL_DFLT_ON &#40; Transact-SQL &#41; ](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md).  
  
 Для совместимости ANSI при установке параметра базы данных ANSI_NULL_DEFAULT в состояние ON изменяется значение по умолчанию базы данных на значение NULL.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_ansi_null_default_on в представлении каталога sys.databases или свойства IsAnsiNullDefault функции DATABASEPROPERTYEX.  
  
 ANSI_NULLS { ON | OFF }  
 ON  
 Результатом любого сравнения со значением NULL будет UNKNOWN.  
  
 OFF  
 Результатом сравнения значений не в Юникоде будет TRUE, если оба значения — NULL.  
  
> [!IMPORTANT]  
>  В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_NULLS всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_NULLS. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр ANSI_NULLS инструкции SET уровня соединения в состояние ON для сеанса. Дополнительные сведения см. в разделе [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md).  
  
 При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_NULLS также должен быть установлен в ON.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_ansi_nulls_on в представлении каталога sys.databases или свойства IsAnsiNullsEnabled функции DATABASEPROPERTYEX.  
  
 ANSI_PADDING { ON | OFF }  
 ON  
 Строки дополняются до нужной длины перед преобразованием или вставкой в **varchar** или **nvarchar** тип данных.  
  
 Конечные пробелы в символьных значениях, вставляемых в столбцы **varchar** или **nvarchar** , и конечные нули в двоичных значениях, вставляемых в столбцы **varbinary** , не отбрасываются. Значения не подгоняются под длину столбца.  
  
 OFF  
 Замыкающие пробелы для **varchar** или **nvarchar** и нули для **varbinary** , усекаются.  
  
 Состояние OFF касается только определения новых столбцов.  
  
> [!IMPORTANT]  
>  В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_PADDING всегда будет иметь значение ON, а все приложения, явно присваивающие ему значение OFF, будут вызывать ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Рекомендуется всегда задавать для параметра ANSI_PADDING значение ON. При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр ANSI_PADDING должен быть установлен в ON.  
  
 **char (*n*) ** и * *двоичный (*n*) ** столбцы, допускающие значения NULL, дополняются до длины столбца, если параметр ANSI_PADDING имеет значение On но конечные пробелы и нули отбрасываются, если параметр ANSI_PADDING имеет значение OFF. **char (*n*) ** и * *двоичный (*n*) ** столбцы, которые не допускают значения NULL всегда подгоняются по длине столбца.  
  
 Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют настройки уровня базы данных по умолчанию для ANSI_PADDING. По умолчанию клиенты ODBC и OLE DB при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр ANSI_PADDING инструкции SET на уровне соединения с состоянием ON для сеанса. Дополнительные сведения см. в разделе [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_ansi_padding_on в представлении каталога sys.databases или свойства IsAnsiPaddingEnabled функции DATABASEPROPERTYEX.  
  
 ANSI_WARNINGS { ON | OFF }  
 ON  
 В таких ситуациях, как деление на ноль или использование значения NULL в агрегатных функциях, выводятся ошибки или предупреждения.  
  
 OFF  
 Предупреждения не выводятся, а в таких ситуациях, как деление на ноль, возвращается NULL.  
  
 При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ANSI_WARNINGS должен быть установлен в ON.  
  
 Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для ANSI_WARNINGS. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр ANSI_WARNINGS инструкции SET уровня соединения в состояние ON для сеанса. Дополнительные сведения см. в разделе [SET ANSI_WARNINGS (Transact-SQL)](../../t-sql/statements/set-ansi-warnings-transact-sql.md).  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_ansi_warnings_on в представлении каталога sys.databases или свойства IsAnsiWarningsEnabled функции DATABASEPROPERTYEX.  
  
 ARITHABORT { ON | OFF }  
 ON  
 Запрос будет завершен, если во время его выполнения возникла ошибка переполнения или деления на ноль.  
  
 OFF  
 При возникновении одной из этих ошибок будет выдано предупреждающее сообщение, однако запрос, пакет или транзакция продолжит работу, как будто никакой ошибки не произошло.  
  
 При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр SET ARITHABORT должен быть установлен в ON.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_arithabort_on в представлении каталога sys.databases или свойства IsArithmeticAbortEnabled функции DATABASEPROPERTYEX.  
  
 COMPATIBILITY_LEVEL { 90 | 100 | 110 | 120}  
 Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
 CONCAT_NULL_YIELDS_NULL { ON | OFF }  
 ON  
 Результатом операции объединения будет NULL, если любой из операндов — NULL. Например, объединение строки символов «Это» со значением NULL приведет к результату NULL вместо «Это».  
  
 OFF  
 Значение NULL будет обработано как пустая строка символов.  
  
 При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр CONCAT_NULL_YIELDS_NULL должен быть установлен в ON.  
  
> [!IMPORTANT]  
>  В будущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр CONCAT_NULL_YIELDS_NULL всегда будет иметь значение ON, а все приложения, явно устанавливающие значение параметра равным OFF, вызовут ошибку. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 Настройки уровня соединения, которые установлены с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для CONCAT_NULL_YIELDS_NULL. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр CONCAT_NULL_YIELDS_NULL инструкции SET уровня соединения в состояние ON для сеанса. Дополнительные сведения см. в разделе [SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_concat_null_yields_null_on в представлении каталога sys.databases или свойства IsNullConcat функции DATABASEPROPERTYEX.  
  
 QUOTED_IDENTIFIER { ON | OFF }  
 ON  
 Двойные кавычки могут использоваться для идентификаторов с разделителями.  
  
 Все строки, находящиеся в двойных кавычках, интерпретируются как идентификаторы объектов. Идентификаторы, заключенные в кавычки, не должны удовлетворять правилам языка [!INCLUDE[tsql](../../includes/tsql-md.md)] для идентификаторов. Они могут быть ключевыми словами и могут включать символы, не разрешенные в идентификаторах [!INCLUDE[tsql](../../includes/tsql-md.md)]. Если в состав строки-литерала входит одиночная кавычка ('), строка может быть заключена в двойные кавычки (").  
  
 OFF  
 Идентификаторы не могут быть заключены в кавычки и должны следовать всем правилам для идентификаторов языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Литералы могут разделяться как одинарными, так и двойными кавычками.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также допускает разделение идентификаторов квадратными скобками ([]). Идентификаторы в скобках могут использоваться всегда (независимо от настройки параметра QUOTED_IDENTIFIER). Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 После создания таблицы параметр QUOTED IDENTIFIER всегда сохраняется в метаданных таблицы со значением ON, даже если при создании таблицы для него было задано OFF.  
  
 Настройки уровня соединения, установленные с помощью инструкции SET, переопределяют параметры базы данных по умолчанию для QUOTED_IDENTIFIER. По умолчанию клиенты ODBC и OLE DB при соединении с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливают параметр QUOTED_IDENTIFIER инструкции SET уровня соединения в состояние ON. Дополнительные сведения см. в разделе [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_quoted_identifier_on в представлении каталога sys.databases или свойства IsQuotedIdentifiersEnabled функции DATABASEPROPERTYEX.  
  
 NUMERIC_ROUNDABORT { ON | OFF }  
 ON  
 Если в выражении происходит потеря точности, будет сформирована ошибка.  
  
 OFF  
 Потери точности не приводят к формированию сообщений об ошибках, а результат округляется с точностью столбца или переменной, в которых сохраняется результат.  
  
 При создании или управлении индексами, основанными на вычисляемых столбцах или индексированных представлениях, параметр NUMERIC_ROUNDABORT должен быть установлен в OFF.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_numeric_roundabort_on в представлении каталога sys.databases или свойства IsNumericRoundAbortEnabled функции DATABASEPROPERTYEX.  
  
 RECURSIVE_TRIGGERS { ON | OFF }  
 ON  
 Рекурсивное срабатывание триггеров AFTER разрешено.  
  
 OFF  
 Не разрешено только прямое рекурсивное срабатывание триггеров AFTER. Также можно отключить косвенную рекурсию триггеров AFTER, вложенные триггеры сервера для параметра **0** с помощью **sp_configure**.  
  
> [!NOTE]  
>  Если параметр RECURSIVE_TRIGGERS установлен в состояние OFF, будет запрещена только прямая рекурсия. Чтобы отключить косвенную рекурсию, нужно установить параметр сервера nested triggers в состояние 0.  
  
 Состояние этого параметра можно определить с помощью проверки значения столбца is_recursive_triggers_on в представлении каталога sys.databases или свойства IsRecursiveTriggersEnabled функции DATABASEPROPERTYEX.  
  
 **\<target_recovery_time_option >:: =**  
  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Недоступно в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Указывает частоту косвенных контрольных точек для каждой базы данных. Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] значение по умолчанию для новых баз данных — 1 минута, который указывает, база данных будет использовать косвенные контрольные точки. Для более старых версий значение по умолчанию — 0, что указывает на использование базы данных автоматические контрольные точки, их частота зависит от параметра для интервала восстановления экземпляра сервера. [!INCLUDE[msCoName](../../includes/msconame-md.md)]Корпорация Майкрософт рекомендует 1 минута для большинства систем.  
  
 TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS | MINUTES }  
 *target_recovery_time*  
 Указывает максимальное время для восстановления определенной базы данных в случае сбоя.  
  
 SECONDS  
 Указывает, что значение *target_recovery_time* выражается в количестве секунд.  
  
 MINUTES  
 Указывает, что значение *target_recovery_time* выражается в количестве минут.  
  
 Дополнительные сведения о косвенных контрольных точках см. в разделе [контрольные точки базы данных &#40; SQL Server &#41; ](../../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 **С \<завершения >:: =**  
  
 Указывает, когда откатывать незавершенные транзакции при переходе базы данных из одного состояния в другое. Если предложение завершения опущено, инструкция ALTER DATABASE бесконечно ожидает блокировки базы данных. Может быть указано только одно предложение завершения, которое должно следовать за предложением SET.  
  
> [!NOTE]  
>  Не все параметры базы данных могут использоваться с \<завершения > предложения. Дополнительные сведения см. в таблице, расположенной в подразделе[Настройка параметров](#SettingOptions) раздела «Примечания».  
  
 ОТКАТ после *целое* [SECONDS] | ОТКАТ НЕМЕДЛЕННО  
 Указывает, нужно ли откатить транзакцию через указанное количество секунд или немедленно.  
  
 NO_WAIT  
 Указывает, что если требуемое изменение состояния или параметра базы данных не может быть выполнено немедленно без ожидания фиксации или отката содержащей его транзакции, то запрос потерпит неудачу.  
  
##  <a name="SettingOptions"></a>Настройка параметров  
 Чтобы получить текущие параметры для параметров базы данных, используйте [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога или [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)  
  
 После установки параметра базы данных изменение вступает в силу немедленно.  
  
 Чтобы изменить значения по умолчанию любого из параметров для всех вновь создаваемых баз данных, измените соответствующий параметр в базе данных model.  
  
 Не все параметры базы данных могут использоваться с \<завершения > предложения или могут быть указаны в сочетании с другими параметрами. В следующей таблице перечислены эти параметры.  
  
|Категория параметров|Может быть указан с другими параметрами|Можно использовать предложение WITH \<завершения > предложения|  
|----------------------|-----------------------------------------|---------------------------------------------|  
|\<db_state_option >|Да|Да|  
|\<db_user_access_option >|Да|Да|  
|\<db_update_option >|Да|Да|  
|\<delayed_durability_option >|Да|Да|  
|\<external_access_option >|Да|Нет|  
|\<cursor_option >|Да|Нет|  
|\<auto_option >|Да|Нет|  
|\<sql_option >|Да|Нет|  
|\<recovery_option >|Да|Нет|  
|\<target_recovery_time_option >|Нет|Да|  
|\<database_mirroring_option >|Нет|Нет|  
|ALLOW_SNAPSHOT_ISOLATION|Нет|Нет|  
|READ_COMMITTED_SNAPSHOT|Нет|Да|  
|MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT|Да|Да|  
|\<service_broker_option >|Да|Нет|  
|DATE_CORRELATION_OPTIMIZATION|Да|Да|  
|\<parameterization_option >|Да|Да|  
|\<change_tracking_option >|Да|Да|  
|\<db_encryption >|Да|Нет|  
  
 Кэш планов для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очищается при установке одного из следующих параметров.  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY||  
  
 Кроме того, кэш процедур сбрасывается в следующих случаях.  
  
-   В базе данных включен параметр базы данных AUTO_CLOSE. Если отсутствуют ссылки соединений пользователя или базы данных, фоновая задача предпримет попытку закрыть и отключить базу данных автоматически.  
  
-   Выполняется нескольких запросов в базе данных с параметрами по умолчанию. Затем база данных уничтожается.  
  
-   Моментальный снимок базы данных для базы данных-источника удален.  
  
-   Успешное перестроение журнала транзакций базы данных.  
  
-   Восстановление резервной копии базы данных.  
  
-   Отсоединение базы данных.  
  
 Очистка кэша планов становится причиной перекомпиляции всех последующих планов выполнения и приводит к непредвиденному временному снижению производительности обработки запросов. Для каждого удаленного хранилища кэша в кэше планов журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит следующее информационное сообщение: «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил %d экземпляров, записанных на диск хранилищ кэша для хранилища кэша "%s" (части кэша планов) в результате операций по обслуживанию или изменению конфигурации базы данных». Это сообщение добавляется в журнал каждые пять минут при сбросе кэша в течение этого интервала времени.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-setting-options-on-a-database"></a>A. Установка параметров для базы данных  
 В следующем примере задается модель восстановления и параметры проверки страницы данных для образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL PAGE_VERIFY CHECKSUM;  
GO  
  
```  
  
### <a name="b-setting-the-database-to-readonly"></a>Б. Перевод базы данных в состояние READ_ONLY  
 Для изменения состояния базы данных или файловой группы в READ_ONLY или READ_WRITE требуется монопольный доступ к базе данных. В следующем примере база данных устанавливается в режим `SINGLE_USER` для получения монопольного доступа. Затем состояние базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] устанавливается в `READ_ONLY`, а также возвращается доступ к базе данных всем пользователям.  
  
> [!NOTE]  
>  В этом примере используется параметр завершения `WITH ROLLBACK IMMEDIATE` в первой инструкции `ALTER DATABASE` . Произойдет откат всех незавершенных транзакций, а любые другие подключения к базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] будут немедленно удалены.  
  
```  
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
  
```  
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
  
 |имя |snapshot_isolation_state |description|  
 |-------------------- |------------------------  |----------|  
 |AdventureWorks2012   |1                        | ON |  
  
### <a name="d-enabling-modifying-and-disabling-change-tracking"></a>Г. Включение, изменение и отключение отслеживания изменений  
 В следующем примере демонстрируется включение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и установка `2`-дневного срока хранения.  
  
```  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(AUTO_CLEANUP = ON, CHANGE_RETENTION = 2 DAYS);  
```  
  
 В следующем примере демонстрируется уменьшение срока хранения до `3` дней.  
  
```  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING (CHANGE_RETENTION = 3 DAYS);  
```  
  
 В следующем примере демонстрируется отключение отслеживания изменений для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF;  
```  
  
### <a name="e-enabling-the-query-store"></a>Д. Включение хранилища запросов  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (от[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Следующий пример включает хранилище запросов и настраивает его параметры.  
  
```  
ALTER DATABASE AdventureWorks2012  
SET QUERY_STORE = ON   
    (  
      OPERATION_MODE = READ_ONLY   
    , CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = 5 )  
    , DATA_FLUSH_INTERVAL_SECONDS = 2000   
    , MAX_STORAGE_SIZE_MB = 10   
    , INTERVAL_LENGTH_MINUTES = 10   
    );  
```  
  
## <a name="see-also"></a>См. также:  
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [ALTER DATABASE SET HADR (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [Статистика](../../relational-databases/statistics/statistics.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Включение и отключение отслеживания изменений (SQL Server)](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md)   
 [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)  
  
  

