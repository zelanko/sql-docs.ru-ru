---
title: Наблюдение за выполнением сценария R и Python с помощью динамических административных представлений (DMV) - машинного обучения SQL Server
description: Используйте динамические административные представления (DMV) для отслеживания выполнения внешнего скрипта R и Python в службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 8d701d9e8595eee3a583e913baabc2148af214fe
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681624"
---
# <a name="monitor-sql-server-machine-learning-services-using-dynamic-management-views-dmvs"></a>Служб монитора SQL Server машинного обучения с помощью динамических административных представлений (DMV)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Используйте динамические административные представления (DMV), чтобы отслеживать выполнение внешних скриптов (R и Python), ресурсы, используемые, диагностики проблем и настройки производительности в службах машинного обучения SQL Server.

В этой статье вы найдете динамические административные представления, характерные для служб машинного обучения SQL Server. Вы также найдете примеры запросов, в которых показано:

+ Настройки и параметры конфигурации для машинного обучения
+ Активные сеансы, выполнять внешние скрипты R или Python
+ Статистика выполнения для внешней среды выполнения R и Python
+ Счетчики производительности для внешних скриптов
+ Использование памяти для операционной системы, SQL Server и внешних пулов ресурсов
+ Конфигурация памяти для SQL Server и внешних пулов ресурсов
+ Пулы ресурсов регулятора ресурсов, включая внешние пулы ресурсов
+ Установленные пакеты R и Python

Более общие сведения о динамических административных представлениях см. в разделе [динамические административные представления системы](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).

> [!TIP]
> Пользовательские отчеты также можно отслеживать службы машинного обучения SQL Server. Дополнительные сведения см. в разделе [отслеживать машинного обучения с помощью настраиваемых отчетов в среде Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="dynamic-management-views"></a>Динамические административные представления

При наблюдении за рабочих нагрузок машины обучения в SQL Server можно использовать следующие динамические административные представления. Для выполнения запроса динамических административных представлений, вам потребуется `VIEW SERVER STATE` разрешения на экземпляр.

| Динамическое административное представление | Тип | Описание |
|-------------------------|------|-------------|
| [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) | Выполнение | Возвращает строку для каждой активной рабочей учетной записи, в которой выполняется внешний скрипт. |
| [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) | Выполнение | Возвращает по одной строке для каждого типа запроса внешнего скрипта. |
| [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) | Выполнение | Возвращает по строке на каждый счетчик производительности, хранимый на сервере. Если вы используете условие поиска `WHERE object_name LIKE '%External Scripts%'`, эти сведения можно использовать, чтобы увидеть, сколько скриптов выполнялось, скриптов, выполненных с помощью режим проверки подлинности, или сколько R или Python вызовы были выданы на общий экземпляр. |
| [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) | Resource Governor | Возвращает сведения о текущем состоянии пула внешних ресурсов в регуляторе ресурсов текущей конфигурации пулов ресурсов и статистику пула ресурсов. |
| [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md) | Resource Governor | Возвращает сведения о сходстве ЦП о текущей конфигурации пула внешних ресурсов в регуляторе ресурсов. Возвращает по одной строке для каждого планировщика [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], сопоставленного с отдельным процессором. Используйте это представление для мониторинга состояния планировщика или для определения отклонившихся от расписания задач. |

Дополнительные сведения о мониторинге [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляров, см. в разделе [представления каталога](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) и [Resource Governor динамические административные представления](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="settings-and-configuration"></a>Параметры и конфигурация

Просмотр параметров настройки и конфигурации установки служб машинного обучения.

![Выходные параметры и настройки запросов](media/dmv-settings-and-configuration.png "выходные параметры и настройки запросов")

Выполните запрос ниже, чтобы получить эти выходные данные. Дополнительные сведения о представлениях и функциях, используемых см. в разделе [sys.dm_server_registry](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md), [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md), и [SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md).

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

Запрос возвращает следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| IsMLServicesInstalled | Возвращает 1, если службы машинного обучения SQL Server устанавливается для экземпляра. В противном случае возвращает 0. |
| ExternalScriptsEnabled | Возвращает 1, если для экземпляра включен внешних скриптов. В противном случае возвращает 0. |
| ImpliedAuthenticationEnabled | Возвращает 1, если подразумеваемой проверки подлинности включена. В противном случае возвращает 0. Конфигурация для неявной проверки подлинности проверяется, проверяя, существует ли имя входа для SQLRUserGroup. |
| IsTcpEnabled | Возвращает значение 1, если протокол TCP/IP включен для экземпляра. В противном случае возвращает 0. Дополнительные сведения см. в разделе [по умолчанию сетевая конфигурация SQL Server протокол](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md). |

## <a name="active-sessions"></a>Активные сеансы

Просмотрите активные сеансы, выполнения внешних скриптов.

![Выходные данные из запроса в настройках](media/dmv-active-sessions.png "выходные данные из текущих параметров запроса")

Выполните запрос ниже, чтобы получить эти выходные данные. Дополнительные сведения о динамических административных представлений, которые используются, см. в разделе [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md), [sys.dm_external_script_requests](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md), и [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).

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

Запрос возвращает следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| session_id | Идентификатор сеанса, связанный со всеми активными первичными соединениями. |
| blocking_session_id | Идентификатор сеанса, блокирующего данный запрос. Если этот столбец содержит значение NULL, то запрос не блокирован или сведения о сеансе блокировки недоступны (или не могут быть идентифицированы). |
| status | Состояние запроса. |
| database_name | Имя текущей базы данных для каждого сеанса. |
| login_name | Имя входа SQL Server, под которой выполняется текущий сеанс. |
| wait_time | Если запрос в настоящий момент блокирован, в столбце содержится продолжительность текущего ожидания (в миллисекундах). Не допускает значение NULL. |
| wait_type | Если запрос в настоящий момент блокирован, в столбце содержится тип ожидания. Сведения о типах ожиданий см. в разделе [sys.dm_os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). |
| last_wait_type | Если запрос был блокирован ранее, в столбце содержится тип последнего ожидания. |
| total_elapsed_time | Общее время, истекшее с момента поступления запроса (в миллисекундах). |
| cpu_time | Время ЦП (в миллисекундах), затраченное на выполнение запроса. |
| reads | Число операций чтения, выполненных данным запросом. |
| logical_reads | Число логических операций чтения, выполненных данным запросом. |
| writes | Число операций записи, выполненных данным запросом. |
| language | Ключевое слово, которое представляет поддерживаемый язык скриптов. |
| degree_of_parallelism | Число, указывающее количество созданных параллельных процессов. Это значение может отличаться от количества запрошенных параллельных процессов. |
| external_user_name | Рабочая учетная запись Windows, под которой был выполнен скрипт. |

## <a name="execution-statistics"></a>Статистика выполнения.

Просмотр статистики выполнения для внешней среды выполнения R и Python. Только статистика RevoScaleR, revoscalepy или функции пакета microsoftml в настоящее время доступны.

![Выходные данные из запроса Статистика выполнения](media/dmv-execution-statistics.png "выходные данные из запроса Статистика выполнения")

Выполните запрос ниже, чтобы получить эти выходные данные. Дополнительные сведения о используется динамическое административное представление, см. в разделе [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). Запрос возвращает только те функции, которые были выполнены несколько раз.

```sql
SELECT language, counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE counter_value > 0
ORDER BY language, counter_name;
```

Запрос возвращает следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| language | Имя зарегистрированного языка внешних скриптов. |
| counter_name | Имя зарегистрированной функции внешних скриптов. |
| counter_value | Общее количество экземпляров, где вызывалась зарегистрированная функция внешних скриптов на сервере. Данное значение является совокупным (подсчет ведется с момента установки компонента на экземпляре) и не может быть сброшено. |

## <a name="performance-counters"></a>Счетчики производительности

Просмотрите счетчики производительности, связанных с выполнением внешних скриптов.

![Выходные данные производительности счетчиков запросов](media/dmv-performance-counters.png "выходные данные производительности счетчиков запросов")

Выполните запрос ниже, чтобы получить эти выходные данные. Дополнительные сведения о используется динамическое административное представление, см. в разделе [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md).

```sql
SELECT counter_name, cntr_value
FROM sys.dm_os_performance_counters 
WHERE object_name LIKE '%External Scripts%'
```

**sys.dm_os_performance_counters** выводит следующие счетчики производительности для внешних скриптов:

| Счетчик | Описание |
|---------|-------------|
| Всего выполнений | Количество внешних процессов, запущенных с локальных или удаленных вызовов. |
| Параллельное выполнение | Сколько раз скрипт содержал _@parallel_ спецификации и что [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] смогла создать и использовать параллельный план запроса. |
| Потоковое выполнение | Сколько раз была вызвана функция потоковой передачи. |
| Выполнение SQL CC | Количество внешних скриптов, выполнения которых вызов был создан удаленно и SQL Server был использован в качестве контекста вычисления. |
| Имена входа с неявной проверкой подлинности Имена входа | Сколько раз ODBC петлевых вызовов с помощью неявной проверки подлинности; то есть [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] выполнял вызов от имени пользователя, отправившего запрос скрипта. |
| Общее время выполнения (мс) | Время, прошедшее между вызовом и его завершением вызова. |
| Ошибки выполнения | Количество раз, скрипты, сообщила об ошибках. Этот счетчик не включает ошибки R или Python. |

## <a name="memory-usage"></a>Использование памяти

Просмотр сведений о памяти, используемой операционной системы, SQL Server и внешние пулы.

![Выходные данные из запроса об использовании памяти](media/dmv-memory-usage.png "выходные данные из запроса об использовании памяти")

Выполните запрос ниже, чтобы получить эти выходные данные. Дополнительные сведения о динамических административных представлений, которые используются, см. в разделе [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) и [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md).

```sql
SELECT physical_memory_kb, committed_kb
    , (SELECT SUM(peak_memory_kb)
        FROM sys.dm_resource_governor_external_resource_pools AS ep
        ) AS external_pool_peak_memory_kb
FROM sys.dm_os_sys_info;
```

Запрос возвращает следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| physical_memory_kb | Общий объем физической памяти на компьютере. |
| committed_kb | Выделенная память в килобайтах (КБ) в диспетчере памяти. Не включает зарезервированную память в диспетчере памяти. |
| external_pool_peak_memory_kb | Сумма максимальный объем памяти, используются в килобайтах, для всех внешних пулов ресурсов. |

## <a name="memory-configuration"></a>Настройка использования памяти

Просмотр сведений о конфигурации максимальный объем памяти в процентах от SQL Server и внешних пулов ресурсов. Если SQL Server выполняется со значением по умолчанию `max server memory (MB)`, он рассматривается как 100% от памяти операционной системы.

![Выходные данные из запроса конфигурации памяти](media/dmv-memory-configuration.png "выходные данные из запроса конфигурации памяти")

Выполните запрос ниже, чтобы получить эти выходные данные. Дополнительные сведения о представления, используемые, см. в разделе [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) и [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

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

Запрос возвращает следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| name | Имя внешнего пула ресурсов или SQL Server. |
| max_memory_percent | Максимальный объем памяти, который можно использовать SQL Server или внешнего пула ресурсов. |

## <a name="resource-pools"></a>Пулы ресурсов

В [регулятор ресурсов SQL Server](../../relational-databases/resource-governor/resource-governor.md), [пул ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md) представляет подмножество физических ресурсов экземпляра. Вы можете указать ограничения на объем ЦП, физических операций ввода-ВЫВОДА и памяти, что входящих запросов приложений, включая выполнение внешних скриптов, можно использовать в пуле ресурсов. Просмотр пулов ресурсов, используемых для SQL Server и внешних скриптов.

![Выходные данные из ресурса пулов запроса](media/dmv-resource-pools.png "выходные данные из ресурса пула запросов")

Выполните запрос ниже, чтобы получить эти выходные данные. Дополнительные сведения о динамических административных представлений, которые используются, см. в разделе [sys.dm_resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) и [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT CONCAT ('SQL Server - ', p.name) AS pool_name
    , p.total_cpu_usage_ms, p.read_io_completed_total, p.write_io_completed_total
FROM sys.dm_resource_governor_resource_pools AS p
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name
    , ep.total_cpu_user_ms, ep.read_io_count, ep.write_io_count
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

Запрос возвращает следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| pool_name | Имя пула ресурсов. Пулы ресурсов SQL Server начинаются с префикса `SQL Server` и внешние пулы ресурсов имеют префикс `External Pool`.
| total_cpu_usage_hours | Совокупное использование ЦП в миллисекундах с момента сброса статистики регулятора ресурсов. |
| read_io_completed_total | Общая сумма завершенных операций ввода-вывода с момента сброса регулятора ресурсов. |
| write_io_completed_total | Общая сумма завершенных операций ввода-вывода записи с момента сброса регулятора ресурсов. |

## <a name="installed-packages"></a>Установленные пакеты

Можно просмотреть установленные в службах машинного обучения SQL Server, выполнив сценарий R или Python, который выводит эти пакеты R и Python.

### <a name="installed-packages-for-r"></a>Установленные пакеты для R

Просмотр пакетов R, установленных в службах машинного обучения SQL Server.

![Выходные данные из установленных пакетов для запроса R](media/dmv-installed-packages-r.png "выходные данные из установленных пакетов для запроса R")

Выполните запрос ниже, чтобы получить эти выходные данные. Использование запросов скрипт R для определения пакетов R, установленная с SQL Server.

```sql
EXEC sp_execute_external_script @language = N'R'
, @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
    , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
```

Ниже приведены столбцы, возвращаемые.

| Столбец | Описание |
|--------|-------------|
| Пакет | Имя установленного пакета. |
| Version | Версия пакета. |
| Зависит | Список пакетов, который зависит от установленного пакета. |
| Лицензия | Лицензии для установленного пакета. |
| LibPath | Каталог, где можно найти пакет. |

### <a name="installed-packages-for-python"></a>Установленные пакеты для Python

Просмотр пакетов Python, установленных в службах машинного обучения SQL Server.

![Выходные данные из установленных пакетов для запроса Python](media/dmv-installed-packages-python.png "выходные данные из установленных пакетов для запроса Python")

Выполните запрос ниже, чтобы получить эти выходные данные. Запрос использовать сценарий Python для определения пакетов Python, установленная с SQL Server.

```sql
EXEC sp_execute_external_script @language = N'Python'
, @script = N'
import pip
OutputDataSet = pandas.DataFrame([(i.key, i.version, i.location) for i in pip.get_installed_distributions()])'
WITH result sets((Package NVARCHAR(128), Version NVARCHAR(128), Location NVARCHAR(1000)));
```

Ниже приведены столбцы, возвращаемые.

| Столбец | Описание |
|--------|-------------|
| Пакет | Имя установленного пакета. |
| Version | Версия пакета. |
| Местоположение | Каталог, где можно найти пакет. |

## <a name="next-steps"></a>Следующие шаги

+ [Управление решениями машинного обучения и их мониторинг](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
+ [Расширенные события для машинного обучения](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)
+ [Динамические административные представления, связанные с регулятора ресурсов](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)
+ [Системные динамические административные представления](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Монитор машинного обучения с помощью настраиваемых отчетов в среде Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)