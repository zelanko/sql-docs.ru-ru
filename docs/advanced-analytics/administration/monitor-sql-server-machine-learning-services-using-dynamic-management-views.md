---
title: Мониторинг выполнения скриптов R и Python с помощью динамических административных представлений (DMV)
description: Используйте динамические административные представления (DMV) для мониторинга выполнения внешних скриптов R и Python в SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 70c409af4e8cbca3d4005f54a0772a0fd4917381
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345224"
---
# <a name="monitor-sql-server-machine-learning-services-using-dynamic-management-views-dmvs"></a>Мониторинг SQL Server Службы машинного обучения с помощью динамических административных представлений
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Используйте динамические административные представления (DMV) для наблюдения за выполнением внешних скриптов (R и Python), используемых ресурсов, диагностики проблем и настройки производительности в SQL Server Службы машинного обучения.

В этой статье вы найдете динамические административные представления, относящиеся к SQL Server Службы машинного обучения. Кроме того, вы увидите примеры запросов, которые показывают:

+ Параметры и параметры конфигурации для машинного обучения
+ Активные сеансы с внешними скриптами R или Python
+ Статистика выполнения для внешней среды выполнения для R и Python
+ Счетчики производительности для внешних скриптов
+ Использование памяти для ОС, SQL Server и внешних пулов ресурсов
+ Конфигурация памяти для SQL Server и внешних пулов ресурсов
+ Пулы ресурсов Resource Governor, включая внешние пулы ресурсов
+ Установленные пакеты для R и Python

Дополнительные общие сведения о динамических административных представлениях см. в статье [системные динамические управления](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).

> [!TIP]
> Пользовательские отчеты также можно использовать для наблюдения за SQL Server Службы машинного обучения. Дополнительные сведения см. [в разделе Мониторинг машинного обучения с помощью пользовательских отчетов в Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="dynamic-management-views"></a>Динамические административные представления

При наблюдении за рабочими нагрузками машинного обучения в SQL Server можно использовать следующие динамические административные представления. Для запроса динамических административных представлений `VIEW SERVER STATE` необходимо разрешение на экземпляр.

| Динамическое административное представление | Type | Описание |
|-------------------------|------|-------------|
| [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) | Выполнение | Возвращает строку для каждой активной рабочей учетной записи, в которой выполняется внешний скрипт. |
| [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) | Выполнение | Возвращает по одной строке для каждого типа запроса внешнего скрипта. |
| [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) | Выполнение | Возвращает по строке на каждый счетчик производительности, хранимый на сервере. Если используется условие `WHERE object_name LIKE '%External Scripts%'`поиска, эти сведения можно использовать для просмотра количества выполненных скриптов, выполнения скриптов с использованием режима проверки подлинности или количества вызовов R или Python, выданных экземпляром в целом. |
| [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) | Resource Governor | Возвращает сведения о текущем состоянии внешнего пула ресурсов в Resource Governor, текущую конфигурацию пулов ресурсов и статистику пула ресурсов. |
| [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md) | Resource Governor | Возвращает сведения о сходстве ЦП с текущей внешней конфигурацией пула ресурсов в Resource Governor. Возвращает по одной строке для каждого планировщика [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], сопоставленного с отдельным процессором. Используйте это представление для мониторинга состояния планировщика или для определения отклонившихся от расписания задач. |

Сведения о мониторинге [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляров см. в разделе [представления каталога](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) и [динамические административные представления, связанные с RESOURCE GOVERNOR](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="settings-and-configuration"></a>Параметры и конфигурация

Просмотрите параметр установки Службы машинного обучения и параметры конфигурации.

![Выходные данные запроса параметров и конфигурации](media/dmv-settings-and-configuration.png "Выходные данные запроса параметров и конфигурации")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых представлениях и функциях см. в разделе [sys. DM _server_registry](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md), [sys. Configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)и [SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md).

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
| исмлсервицесинсталлед | Возвращает значение 1, если для экземпляра установлен SQL Server Службы машинного обучения. В противном случае возвращает 0. |
| екстерналскриптсенаблед | Возвращает значение 1, если для экземпляра включены внешние скрипты. В противном случае возвращает 0. |
| имплиедаусентикатионенаблед | Возвращает значение 1, если включена подразумеваемая проверка подлинности. В противном случае возвращает 0. Конфигурация для неявной проверки подлинности проверяется путем проверки наличия имени входа для SQLRUserGroup. |
| исткпенаблед | Возвращает значение 1, если для экземпляра включен протокол TCP/IP. В противном случае возвращает 0. Дополнительные сведения см. в разделе [Конфигурация сетевого протокола по умолчанию SQL Server](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md). |

## <a name="active-sessions"></a>Активные сеансы

Просмотр активных сеансов, выполняющих внешние скрипты.

![Выходные данные запроса активных параметров](media/dmv-active-sessions.png "Выходные данные запроса активных параметров")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых динамических административных представлениях см. в разделе [sys. DM _exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md), [sys. DM _external_script_requests](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)и [sys. DM _exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).

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
| login_name | SQL Server имя входа, под которым выполняется текущий сеанс. |
| wait_time | Если запрос в настоящий момент блокирован, в столбце содержится продолжительность текущего ожидания (в миллисекундах). Не допускает значение NULL. |
| wait_type | Если запрос в настоящий момент блокирован, в столбце содержится тип ожидания. Дополнительные сведения о типах ожиданий см. в разделе [sys. DM _os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). |
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

Просмотр статистики выполнения для внешней среды выполнения для R и Python. В настоящее время доступны только статистические функции пакетов RevoScaleR, revoscalepy и microsoftml.

![Выходные данные запроса статистики выполнения](media/dmv-execution-statistics.png "Выходные данные запроса статистики выполнения")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемом динамическом административном представлении см. в разделе [sys. DM _external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). Запрос возвращает только те функции, которые были выполнены несколько раз.

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

Просмотр счетчиков производительности, связанных с выполнением внешних скриптов.

![Выходные данные запроса счетчиков производительности](media/dmv-performance-counters.png "Выходные данные запроса счетчиков производительности")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемом динамическом административном представлении см. в разделе [sys. DM _os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md).

```sql
SELECT counter_name, cntr_value
FROM sys.dm_os_performance_counters 
WHERE object_name LIKE '%External Scripts%'
```

**sys. DM _os_performance_counters** выводит следующие счетчики производительности для внешних скриптов:

| Счетчик | Описание |
|---------|-------------|
| Всего выполнений | Количество внешних процессов, запущенных локальными или удаленными вызовами. |
| Параллельное выполнение | Количество раз, когда сценарий включал _@parallel_ спецификацию [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и мог создать и использовать параллельный план запроса. |
| Потоковое выполнение | Количество раз, когда была вызвана функция потоковой передачи. |
| Выполнение SQL CC | Количество внешних скриптов, в которых вызов был создан удаленно и SQL Server использовался в качестве контекста вычислений. |
| Имена входа с неявной проверкой подлинности Имена входа | Количество случаев, когда вызов обратной связи ODBC был выполнен с использованием подразумеваемой проверки подлинности; то есть, [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] выполняет вызов от имени пользователя, отправляющего запрос скрипта. |
| Общее время выполнения (мс) | Время, прошедшее между вызовом и завершением вызова. |
| Ошибки выполнения | Количество раз, когда скрипты сообщили об ошибках. Это число не включает ошибки R или Python. |

## <a name="memory-usage"></a>Использование памяти

Просмотр сведений о памяти, используемой ОС, SQL Server и внешних пулах.

![Выходные данные запроса на использование памяти](media/dmv-memory-usage.png "Выходные данные запроса на использование памяти")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых динамических административных представлениях см. в разделе [sys. DM _resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) и [sys. DM _os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md).

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
| external_pool_peak_memory_kb | Сумма максимального объема используемой памяти (в килобайтах) для всех внешних пулов ресурсов. |

## <a name="memory-configuration"></a>Настройка использования памяти

Просмотр сведений о максимальной конфигурации памяти в процентах от SQL Server и внешних пулов ресурсов. Если SQL Server работает со значением `max server memory (MB)`по умолчанию, то оно считается 100% памяти ОС.

![Выходные данные запроса конфигурации памяти](media/dmv-memory-configuration.png "Выходные данные запроса конфигурации памяти")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых представлениях см. в разделе [sys. Configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) и [sys. DM _resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

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
| max_memory_percent | Максимальный объем памяти, который может использоваться SQL Server или внешним пулом ресурсов. |

## <a name="resource-pools"></a>Пулы ресурсов

В [SQL Server Resource Governor](../../relational-databases/resource-governor/resource-governor.md) [пул ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md) представляет подмножество физических ресурсов экземпляра. Вы можете указать ограничения на объем ресурсов ЦП, физических операций ввода-вывода и памяти, которые поступают на входящие запросы приложений, включая выполнение внешних скриптов, в пуле ресурсов. Просмотр пулов ресурсов, используемых для SQL Server и внешних скриптов.

![Выходные данные запроса пулов ресурсов](media/dmv-resource-pools.png "Выходные данные запроса пулов ресурсов")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. Дополнительные сведения об используемых динамических административных представлениях см. в разделе [sys. DM _resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) и [sys. DM _resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

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
| pool_name | Имя пула ресурсов. SQL Server пулы ресурсов имеют префикс `SQL Server` , а внешние пулы ресурсов имеют `External Pool`префикс.
| total_cpu_usage_hours | Совокупное использование ЦП в миллисекундах с момента сброса статистики сброса регулятора ресурсов. |
| read_io_completed_total | Общая сумма завершенных операций ввода-вывода с момента сброса регулятора ресурсов. |
| write_io_completed_total | Общая сумма завершенных операций ввода-вывода записи с момента сброса регулятора ресурсов. |

## <a name="installed-packages"></a>Установленные пакеты

Вы можете просмотреть пакеты R и Python, установленные в SQL Server Службы машинного обучения, выполнив сценарий R или Python, который выводит эти данные.

### <a name="installed-packages-for-r"></a>Установленные пакеты для R

Просмотрите пакеты R, установленные в SQL Server Службы машинного обучения.

![Выходные данные установленных пакетов для запроса R](media/dmv-installed-packages-r.png "Выходные данные установленных пакетов для запроса R")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. В запросе используется скрипт R для определения пакетов R, установленных с помощью SQL Server.

```sql
EXEC sp_execute_external_script @language = N'R'
, @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
    , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
```

Возвращаются следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| Пакет | Имя установленного пакета. |
| Version | Версия пакета. |
| Зависит | Выводит список пакетов, от которых зависит установленный пакет. |
| Лицензия | Лицензия для установленного пакета. |
| Среды | Каталог, в котором можно найти пакет. |

### <a name="installed-packages-for-python"></a>Установленные пакеты для Python

Просмотрите пакеты Python, установленные в SQL Server Службы машинного обучения.

![Выходные данные из установленных пакетов для запроса Python](media/dmv-installed-packages-python.png "Выходные данные из установленных пакетов для запроса Python")

Чтобы получить эти выходные данные, выполните приведенный ниже запрос. В запросе используется скрипт Python для определения пакетов Python, установленных с помощью SQL Server.

```sql
EXEC sp_execute_external_script @language = N'Python'
, @script = N'
import pip
OutputDataSet = pandas.DataFrame([(i.key, i.version, i.location) for i in pip.get_installed_distributions()])'
WITH result sets((Package NVARCHAR(128), Version NVARCHAR(128), Location NVARCHAR(1000)));
```

Возвращаются следующие столбцы:

| Столбец | Описание |
|--------|-------------|
| Пакет | Имя установленного пакета. |
| Version | Версия пакета. |
| Location | Каталог, в котором можно найти пакет. |

## <a name="next-steps"></a>Следующие шаги

+ [Управление решениями машинного обучения и их мониторинг](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
+ [Расширенные события для машинного обучения](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)
+ [Динамические административные представления, связанные с Resource Governor](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)
+ [Системные динамические административные представления](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Мониторинг машинного обучения с помощью пользовательских отчетов в Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)