---
title: Мониторинг сценариев с использованием динамических административных представлений
description: Используйте динамические административные представления для мониторинга выполнения внешних скриптов Python и R в службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/14/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 09a01937611b239aeb6db1df406fc057063eb634
ms.sourcegitcommit: 22102f25db5ccca39aebf96bc861c92f2367c77a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2020
ms.locfileid: "92115553"
---
# <a name="monitor-sql-server-machine-learning-services-using-dynamic-management-views-dmvs"></a>Мониторинг служб машинного обучения SQL Server с помощью динамических административных представлений
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

Динамические административные представления можно использовать для отслеживания выполнения внешних скриптов (Python и R), мониторинга используемых ресурсов, диагностики проблем и настройки производительности в службах машинного обучения SQL Server.

В этой статье вы найдете динамические административные представления, относящиеся к службам машинного обучения SQL Server. Кроме того, в ней приводятся примеры запросов, которые демонстрируют:

+ Настройки и параметры конфигурации для служб машинного обучения
+ Активные сеансы, выполняющие внешние скрипты Python или R
+ Статистика выполнения для внешней среды выполнения Python и R
+ Счетчики производительности для внешних скриптов
+ Использование памяти для ОС, SQL Server и внешних пулов ресурсов
+ Конфигурация памяти для SQL Server и внешних пулов ресурсов
+ Пулы ресурсов регулятора ресурсов, включая внешние пулы ресурсов
+ Установленные пакеты для Python и R

Дополнительные общие сведения о динамических административных представлениях см. в разделе [Системные динамические административные представления](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).

> [!TIP]
> Пользовательские отчеты также можно использовать для наблюдения за службами машинного обучения SQL Server. Дополнительные сведения см. в статье [Мониторинг служб машинного обучения с помощью настраиваемых отчетов в Management Studio](monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md).

## <a name="dynamic-management-views"></a>Динамические административные представления

При наблюдении за рабочими нагрузками на службы машинного обучения в SQL Server можно использовать следующие динамические административные представления. Для запроса динамических административных представлений требуется разрешение `VIEW SERVER STATE` на экземпляр.

| Динамическое административное представление | Тип | Описание |
|-------------------------|------|-------------|
| [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) | Выполнение | Возвращает строку для каждой активной рабочей учетной записи, в которой выполняется внешний скрипт. |
| [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) | Выполнение | Возвращает по одной строке для каждого типа запроса внешнего скрипта. |
| [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) | Выполнение | Возвращает по строке на каждый счетчик производительности, хранимый на сервере. Если используется условие поиска `WHERE object_name LIKE '%External Scripts%'`, на основе этих сведений можно узнать, сколько скриптов выполнялось, какой режим проверки подлинности использовался для каждого из них или общее количество отправленных вызовов R или Python для экземпляра. |
| [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) | Resource Governor | Возвращает информацию о текущем состоянии внешнего пула ресурсов в Resource Governor, текущую конфигурацию пула ресурсов и статистику пула ресурсов. |
| [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md) | Resource Governor | Возвращает информацию о текущей конфигурации внешнего пула ресурсов в Resource Governor для фиксирования потоков на ЦП. Возвращает по одной строке для каждого планировщика [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], сопоставленного с отдельным процессором. Используйте это представление для мониторинга состояния планировщика или для определения отклонившихся от расписания задач. |

Информацию об отслеживании экземпляров [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] см. в статьях [Представления каталога](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) и [Динамические административные представления, связанные с Resource Governor](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="settings-and-configuration"></a>Параметры и конфигурация

Просмотр параметров установки и конфигурации служб машинного обучения.

![Выходные данные запроса параметров и конфигурации](media/dmv-settings-and-configuration.png "Выходные данные запроса параметров и конфигурации")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых представлениях и функциях см. в разделах [sys. dm_server_registry](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md), [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) и [SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md).

```sql
SELECT CAST(SERVERPROPERTY('IsAdvancedAnalyticsInstalled') AS INT) AS IsMLServicesInstalled
    , CAST(value_in_use AS INT) AS ExternalScriptsEnabled
    , COALESCE(SIGN(SUSER_ID(CONCAT (
                    CAST(SERVERPROPERTY('MachineName') AS NVARCHAR(128))
                    , '\SQLRUserGroup'
                    , CAST(serverproperty('InstanceName') AS NVARCHAR(128))
                    ))), 0) AS ImpliedAuthenticationEnabled
    , COALESCE((
            SELECT CAST(r.value_data AS INT)
            FROM sys.dm_server_registry AS r
            WHERE r.registry_key LIKE 'HKLM\Software\Microsoft\Microsoft SQL Server\%\SuperSocketNetLib\Tcp'
            AND r.value_name = 'Enabled'
            ), - 1) AS IsTcpEnabled
FROM sys.configurations
WHERE name = 'external scripts enabled';
```

Этот запрос возвращает следующие столбцы:

| Столбец                       | Описание |
|------------------------------|-------------|
| IsMLServicesInstalled        | Возвращает значение 1, если для экземпляра установлены службы машинного обучения SQL Server. В противном случае возвращается 0. |
| ExternalScriptsEnabled       | Возвращает значение 1, если для экземпляра включены внешние скрипты. В противном случае возвращается 0. |
| ImpliedAuthenticationEnabled | Возвращает значение 1, если включена подразумеваемая проверка подлинности. В противном случае возвращается 0. Конфигурация для неявной проверки подлинности проверяется путем проверки наличия имени входа для SQLRUserGroup. |
| IsTcpEnabled                 | Возвращает значение 1, если для экземпляра включен протокол TCP/IP. В противном случае возвращается 0. Для получения дополнительных сведений см. раздел [Конфигурация сетевого протокола SQL Server по умолчанию](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md). |

## <a name="active-sessions"></a>Активные сеансы

Просмотр активных сеансов, выполняющих внешние скрипты.

![Выходные данные запроса активных параметров](media/dmv-active-sessions.png "Выходные данные запроса активных параметров")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых динамических административных представлениях см. в разделах [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md), [sys.dm_external_script_requests](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) и [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).

```sql
SELECT r.session_id, r.blocking_session_id, r.status, DB_NAME(s.database_id) AS database_name
    , s.login_name, r.wait_time, r.wait_type, r.last_wait_type, r.total_elapsed_time, r.cpu_time
    , r.reads, r.logical_reads, r.writes, er.language, er.degree_of_parallelism, er.external_user_name
FROM sys.dm_exec_requests AS r
INNER JOIN sys.dm_external_script_requests AS er
ON r.external_script_request_id = er.external_script_request_id
INNER JOIN sys.dm_exec_sessions AS s
ON s.session_id = r.session_id;
```

Этот запрос возвращает следующие столбцы:

| Столбец                | Описание |
|-----------------------|-------------|
| session_id            | Идентификатор сеанса, связанный со всеми активными первичными соединениями. |
| blocking_session_id   | Идентификатор сеанса, блокирующего данный запрос. Если этот столбец содержит значение NULL, то запрос не блокирован или сведения о сеансе блокировки недоступны (или не могут быть идентифицированы). |
| status                | Состояние запроса. |
| database_name         | Имя текущей базы данных для каждого сеанса. |
| login_name            | Имя входа SQL Server, под которым выполняется текущий сеанс. |
| wait_time             | Если запрос в настоящий момент блокирован, в столбце содержится продолжительность текущего ожидания (в миллисекундах). Не допускает значение NULL. |
| wait_type             | Если запрос в настоящий момент блокирован, в столбце содержится тип ожидания. Сведения о типах ожиданий см. в разделе [sys.dm_os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). |
| last_wait_type        | Если запрос был блокирован ранее, в столбце содержится тип последнего ожидания. |
| total_elapsed_time    | Общее время, истекшее с момента поступления запроса (в миллисекундах). |
| cpu_time              | Время ЦП (в миллисекундах), затраченное на выполнение запроса. |
| reads                 | Число операций чтения, выполненных данным запросом. |
| logical_reads         | Число логических операций чтения, выполненных данным запросом. |
| writes                | Число операций записи, выполненных данным запросом. |
| Язык              | Ключевое слово, которое представляет поддерживаемый язык скриптов. |
| degree_of_parallelism | Число, указывающее количество созданных параллельных процессов. Это значение может отличаться от количества запрошенных параллельных процессов. |
| external_user_name    | Рабочая учетная запись Windows, под которой был выполнен скрипт. |

## <a name="execution-statistics"></a>Статистика выполнения.

Просмотр статистики выполнения для внешней среды выполнения R и Python. В настоящее время доступна статистика по функциям пакетов RevoScaleR, revoscalepy или microsoftml.

![Выходные данные запроса статистики выполнений](media/dmv-execution-statistics.png "Выходные данные запроса статистики выполнений")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемом динамическом административном представлении см. в разделе [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). Запрос возвращает только те функции, которые были выполнены несколько раз.

```sql
SELECT language, counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE counter_value > 0
ORDER BY language, counter_name;
```

Этот запрос возвращает следующие столбцы:

| Столбец        | Описание |
|---------------|-------------|
| Язык      | Имя зарегистрированного языка внешних скриптов. |
| counter_name  | Имя зарегистрированной функции внешних скриптов. |
| counter_value | Общее количество экземпляров, где вызывалась зарегистрированная функция внешних скриптов на сервере. Данное значение является совокупным (подсчет ведется с момента установки компонента на экземпляре) и не может быть сброшено. |

## <a name="performance-counters"></a>Счетчики производительности

Просмотр счетчиков производительности, связанных с выполнением внешних скриптов.

![Выходные данные запроса счетчиков производительности](media/dmv-performance-counters.png "Выходные данные запроса счетчиков производительности")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемом динамическом административном представлении см. в разделе [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md).

```sql
SELECT counter_name, cntr_value
FROM sys.dm_os_performance_counters 
WHERE object_name LIKE '%External Scripts%'
```

В результате запроса **sys.dm_os_performance_counters** выдаются следующие счетчики производительности для внешних скриптов:

| Счетчик                   | Описание |
|---------------------------|-------------|
| Всего выполнений          | Количество внешний процессов, запущенных с помощью локальных или удаленных вызовов. |
| Параллельное выполнение       | Сколько раз скрипт содержал спецификацию _\@parallel_ и удалось ли [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] создать и использовать планов параллельных запросов. |
| Потоковое выполнение      | Сколько раз была вызвана функция потоковой передачи. |
| Выполнение SQL CC         | Количество внешний скриптов, в которых вызов был создан удаленно, а SQL Server использовался в качестве контекста вычислений. |
| Имена входа с неявной проверкой подлинности Имена входа      | Сколько раз петлевой вызов ODBC выполнялся с использованием подразумеваемой проверки подлинности, то есть [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] выполнял вызов от имени пользователя, отправившего запрос скрипта. |
| Общее время выполнения (мс) | Время, прошедшее между вызовом и его завершением. |
| Ошибки выполнения          | Количество ошибок, возникших при выполнении скриптов. Этот счетчик не содержит ошибки R или Python. |

## <a name="memory-usage"></a>Использование памяти

Просмотр сведений о памяти, используемой ОС, SQL Server и внешними пулами.

![Выходные данные запроса об использовании памяти](media/dmv-memory-usage.png "Выходные данные запроса об использовании памяти")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых динамических административных представлениях см. в разделе [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) и [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md).

```sql
SELECT physical_memory_kb, committed_kb
    , (SELECT SUM(peak_memory_kb)
        FROM sys.dm_resource_governor_external_resource_pools AS ep
        ) AS external_pool_peak_memory_kb
FROM sys.dm_os_sys_info;
```

Этот запрос возвращает следующие столбцы:

| Столбец                       | Описание                                                                                                           |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| physical_memory_kb           | Общий объем физической памяти компьютера.                                                                   |
| committed_kb                 | Фиксированная физическая память в килобайтах (КБ) в диспетчере памяти. Не включает зарезервированную память в диспетчере памяти. |
| external_pool_peak_memory_kb | Максимальный суммарный объем памяти (в килобайтах), используемой всеми внешними пулами ресурсов.                          |

## <a name="memory-configuration"></a>Настройка использования памяти

Просмотр сведений о максимальной конфигурации памяти (в процентах) для SQL Server и внешних пулов ресурсов. Если SQL Server работает со значением `max server memory (MB)` по умолчанию, оно принимается за 100% памяти ОС.

![Выходные данные запроса конфигурации памяти](media/dmv-memory-configuration.png "Выходные данные запроса конфигурации памяти")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых динамических административных представлениях см. в разделе [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) и [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT 'SQL Server' AS name
    , CASE CAST(c.value AS BIGINT)
        WHEN 2147483647 THEN 100
        ELSE (SELECT CAST(c.value AS BIGINT) / (physical_memory_kb / 1024.0) * 100 FROM sys.dm_os_sys_info)
        END AS max_memory_percent
FROM sys.configurations AS c
WHERE c.name LIKE 'max server memory (MB)'
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name, ep.max_memory_percent
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

Этот запрос возвращает следующие столбцы:

| Столбец             | Описание |
|--------------------|-------------|
| name               | Имя внешнего пула ресурсов или SQL Server. |
| max_memory_percent | Максимальный объем памяти, который может использовать SQL Server или внешний пул ресурсов. |

## <a name="resource-pools"></a>Пулы ресурсов

В [регуляторе ресурсов SQL Server](../../relational-databases/resource-governor/resource-governor.md)[пул ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md) представляет подмножество физических ресурсов экземпляра. Вы можете задать ограничения на загрузку ЦП, физические средства ввода-вывода и объем памяти, доступный для входящих запросов приложений, включая выполнение внешних скриптов, в пуле ресурсов. Просмотр пулов ресурсов, используемых для SQL Server и внешних скриптов.

![Выходные данные запроса пулов ресурсов](media/dmv-resource-pools.png "Выходные данные запроса пулов ресурсов")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых динамических административных представлениях см. в разделах [sys.dm_resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) и [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT CONCAT ('SQL Server - ', p.name) AS pool_name
    , p.total_cpu_usage_ms, p.read_io_completed_total, p.write_io_completed_total
FROM sys.dm_resource_governor_resource_pools AS p
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name
    , ep.total_cpu_user_ms, ep.read_io_count, ep.write_io_count
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

Этот запрос возвращает следующие столбцы:

| Столбец                   | Описание  |
|--------------------------|--------------|
| pool_name                | Имя пула ресурсов. Пулы ресурсов SQL Server имеют префикс `SQL Server`, а внешние пулы ресурсов — префикс `External Pool`. |
| total_cpu_usage_hours    | Совокупное использование ЦП (в миллисекундах) с момента сброса статистики регулятора ресурсов. |
| read_io_completed_total  | Общая сумма завершенных операций ввода-вывода с момента сброса регулятора ресурсов.              |
| write_io_completed_total | Общая сумма завершенных операций ввода-вывода записи с момента сброса регулятора ресурсов.             |

## <a name="installed-packages"></a>Установленные пакеты

Вы можете узнать, какие пакеты R и Python установлены в службах машинного обучения SQL Server, выполнив сценарий R или Python, который выводит эти данные.

### <a name="installed-packages-for-r"></a>Установленные пакеты для R

Просмотр пакетов R, установленных в службах машинного обучения SQL Server.

![Выходные данные запроса установленных пакетов для R](media/dmv-installed-packages-r.png "Выходные данные запроса установленных пакетов для R")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. В запросе используется скрипт R, позволяющий определить, какие пакеты R установлены в SQL Server.

```sql
EXECUTE sp_execute_external_script @language = N'R'
, @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
    , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
```

Возвращаются следующие столбцы:

| Столбец  | Описание                                                 |
|---------|-------------------------------------------------------------|
| Пакет | Имя установленного пакета.                              |
| Версия | Версия пакета.                                     |
| Зависит | Выводит список пакетов, от которых зависит установленный пакет. |
| Лицензия | Лицензия установленного пакета.                          |
| LibPath | Каталог, в котором находится пакет.                   |

### <a name="installed-packages-for-python"></a>Установленные пакеты для Python

Просмотр пакетов Python, установленных в службах машинного обучения SQL Server.

![Выходные данные запроса установленных пакетов для Python](media/dmv-installed-packages-python.png "Выходные данные запроса установленных пакетов для Python")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. В запросе используется скрипт Python, позволяющий определить, какие пакеты Python установлены в SQL Server.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
, @script = N'
import pkg_resources
import pandas
OutputDataSet = pandas.DataFrame(sorted([(i.key, i.version, i.location) for i in pkg_resources.working_set]))'
WITH result sets((Package NVARCHAR(128), Version NVARCHAR(128), Location NVARCHAR(1000)));
```

Возвращаются следующие столбцы:

| Столбец   | Описание                               |
|----------|-------------------------------------------|
| Пакет  | Имя установленного пакета.            |
| Версия  | Версия пакета.                   |
| Расположение | Каталог, в котором находится пакет. |

## <a name="next-steps"></a>Дальнейшие действия

+ [Расширенные события для служб машинного обучения](extended-events.md)
+ [Динамические административные представления регулятора ресурсов](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)
+ [Системные динамические административные представления](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Мониторинг служб машинного обучения с помощью настраиваемых отчетов в Management Studio](monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md)
