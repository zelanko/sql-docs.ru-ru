---
title: CREATE WORKLOAD GROUP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 01/14/2020
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD GROUP
- WORKLOAD_GROUP_TSQL
- CREATE WORKLOAD GROUP
- CREATE_WORKLOAD_GROUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD GROUP statement
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azure-sqldw-latest||=azuresqldb-mi-current'
ms.openlocfilehash: ca80b2f95ee049d763d22f35e4ff6d35e344a8c0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75956502"
---
# <a name="create-workload-group-transact-sql"></a>CREATE WORKLOAD GROUP (Transact-SQL)

## <a name="click-a-product"></a>Выберите продукт!

В следующей строке щелкните имя продукта, который вас интересует. На этой веб-странице отобразится другой контент, относящийся к выбранному продукту.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current||=sqlallproducts-allversions"

> |||||
> |---|---|---|---|
> |**_\* SQL Server \*_** &nbsp;|[Управляемый экземпляр Базы данных SQL<br />](create-workload-group-transact-sql.md?view=azuresqldb-mi-current)|[Azure Synapse<br />Analytics](create-workload-group-transact-sql.md?view=azure-sqldw-latest)|

&nbsp;

## <a name="sql-server-and-sql-database-managed-instance"></a>SQL Server и управляемый экземпляр базы данных SQL Azure

Создает группу рабочей нагрузки регулятора ресурсов и связывает ее с пулом ресурсов регулятора ресурсов. Регулятор ресурсов доступен не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Синтаксис

```
CREATE WORKLOAD GROUP group_name
[ WITH
    ( [ IMPORTANCE = { LOW | MEDIUM | HIGH } ]
      [ [ , ] REQUEST_MAX_MEMORY_GRANT_PERCENT = value ]
      [ [ , ] REQUEST_MAX_CPU_TIME_SEC = value ]
      [ [ , ] REQUEST_MEMORY_GRANT_TIMEOUT_SEC = value ]
      [ [ , ] MAX_DOP = value ]
      [ [ , ] GROUP_MAX_REQUESTS = value ] )
 ]
[ USING {
    [ pool_name | "default" ]
    [ [ , ] EXTERNAL external_pool_name | "default" ] ]
    } ]
[ ; ]
```

## <a name="arguments"></a>Аргументы

*group_name*. Определяемое пользователем имя группы рабочей нагрузки. Аргумент *group_name* является алфавитно-цифровым и может содержать до 128 символов. Данный аргумент должен быть уникальным в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).

IMPORTANCE = { LOW | **MEDIUM** | HIGH }. Указывает относительную важность запроса в группе рабочей нагрузки. Важность представлена одним из следующих значений, причем значением по умолчанию является MEDIUM.

- LOW
- MEDIUM (по умолчанию);
- HIGH.

> [!NOTE]
> Внутри системы каждое значение важности хранится в виде числа, используемого для вычислений.

Значение IMPORTANCE локально для пула ресурсов; группы рабочей нагрузки разной важности внутри одного пула ресурсов влияют друг на друга, но не влияют на рабочие группы в других пулов ресурсов.

REQUEST_MAX_MEMORY_GRANT_PERCENT = *value*. Укажите максимальный объем памяти, который может использоваться одним запросом из пула. *value* — это процентное соотношение относительно размера пула ресурсов, указанное в MAX_MEMORY_PERCENT.

*value* является целым числом в версиях до [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] и числом с плавающей точкой начиная с [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]. Значение по умолчанию равно 25. Диапазон допустимых значений для *value* — от 1 до 100.

> [!IMPORTANT]  
> Указанное значение ссылается только на доступную для выполнения запроса память.
>
> Установка параметра *value* в значение 0 блокирует выполнение запросов с операциями SORT и HASH JOIN в определяемых пользователем группах рабочей нагрузки.
>
> Не рекомендуется устанавливать значение *value* более 70, так как возможно, что серверу не удастся зарезервировать достаточно памяти, если выполняются другие параллельные запросы. Со временем это может привести к ошибке 8645 (истечение времени ожидания запроса).
>
> Если требования к памяти запроса превышают ограничение, заданное этим параметром, сервер выполняет следующие действия.
>
> - Для определяемых пользователем групп рабочей нагрузки сервер пытается снизить степень параллелизма для запроса, пока требования к памяти не снизятся до ограничения, либо пока степень параллелизма не станет равной 1. Если в этом случае требования к запросам памяти по-прежнему превышают ограничение, возникает ошибка 8657.
>
> - Для внутренних групп рабочей нагрузки и группы по умолчанию сервер разрешает запросу получить необходимый объем памяти.
>
> Учтите, что в обоих случаях может возникнуть ошибка 8645 (истечение времени ожидания), если на сервере недостаточно физической памяти.

REQUEST_MAX_CPU_TIME_SEC = *value*. Указывает максимальное количество времени ЦП в секундах, которое может использоваться запросом. *value* должно быть 0 или положительным целым числом. Значение *value* по умолчанию равно 0, что означает неограниченное время.

> [!NOTE]
> По умолчанию по истечении лимита времени Resource Governor не прекращает выполнение запроса. Однако будет сформировано событие. Дополнительные сведения см. в разделе [Класс событий CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).
> [!IMPORTANT]
> Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 2 (SP2) и [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] с накопительным пакетом обновления 3 и в случае использования [флага трассировки 2422](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) при превышении максимального значения времени Resource Governor прервет запрос.

REQUEST_MEMORY_GRANT_TIMEOUT_SEC = *value*. Задает максимальное время (в секундах), в течение которого запрос может ожидать выделения памяти (памяти рабочего буфера). *value* должно быть 0 или положительным целым числом. Значение *value* по умолчанию равно 0 и использует внутренние вычисления, основанные на затратах запроса, для определения максимального времени.

> [!NOTE]
> При истечении времени ожидания предоставления памяти запрос не всегда завершается ошибкой. Запрос завершится ошибкой только в случае, если одновременно запущено слишком много запросов. В остальных случаях запрос может получить лишь минимальный объем памяти, что приведет к снижению его производительности.

MAX_DOP = *значение* Указывает **максимальную степень параллелизма (MAXDOP)** для выполнения параллельных запросов. *value* должно быть 0 или положительным целым числом. Диапазон допустимых значений для *value* — от 0 до 64. Значение *value* по умолчанию, равное 0, использует глобальные настройки. MAX_DOP обрабатывается следующим образом.

> [!NOTE]
> Группа рабочей нагрузки MAX_DOP переопределяет [конфигурацию сервера для максимальной степени параллелизма](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) и [конфигурацию области баз данных](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) **MAXDOP**.
> [!TIP]
> Для выполнения этого на уровне запросов используйте [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) **MAXDOP**. Указание максимальной степени параллелизма в качестве указания запроса эффективно до тех пор, пока его значение не превышает значения MAX_DOP группы рабочей нагрузки. Если значение указания запроса MAXDOP превышает значение, которое настроено с помощью Resource Governor, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] использует значение `MAX_DOP` Resource Governor. [Указание запроса](../../t-sql/queries/hints-transact-sql-query.md) MAXDOP всегда переопределяет [конфигурацию сервера для максимальной степени параллелизма](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).
>
> На уровне базы данных используйте [конфигурацию области баз данных ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)**MAXDOP**.
>
> На уровне сервера используйте [параметр конфигурации сервера](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) **максимальной степени параллелизма (MAXDOP)** .

GROUP_MAX_REQUESTS = *value*. Указывает максимальное число одновременных запросов, разрешенных для выполнения в группе рабочей нагрузки. Значение *value* должно быть равно 0 или быть положительным целым числом. Значение *value* по умолчанию равно 0, что разрешает неограниченные запросы. Если достигнуто максимальное количество параллельных запросов, пользователь из этой группы сможет войти в систему, но переводится в состоянии ожидания до тех пор, пока количество параллельных запросов не станет меньше указанного значения.

USING { *pool_name* |  **"default"** }. Связывает группу рабочей нагрузки с пулом ресурсов, определяемых пользователем, который идентифицируется по значению *pool_name*. При этом группа рабочей нагрузки помещается в пул ресурсов. Если значение *pool_name* не предоставлено либо если не использован аргумент USING, группа рабочей нагрузки помещается в стандартный пул по умолчанию регулятора ресурсов.

Слово «default» является зарезервированным словом и при использовании с аргументом USING должно быть заключено в кавычки ("") либо квадратные скобки ([]).

> [!NOTE]
> Все стандартные группы рабочей нагрузки и пулы ресурсов используют имена в нижнем регистре, например «default». Это необходимо учитывать при работе с серверами, где параметры сортировки учитывают регистр символов. Серверы, параметры сортировки которых не учитывают регистр (например, SQL_Latin1_General_CP1_CI_AS), будут рассматривать строки «default» и «Default» как одинаковые.

EXTERNAL external_pool_name | "default" **Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более поздние версии).

Группа рабочей нагрузки может указывать внешний пул ресурсов. Можно определить группу рабочей нагрузки и связать ее с двумя пулами:

- пулом ресурсов для рабочих нагрузок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и запросов;
- внешним пулом ресурсов для внешних процессов. Дополнительные сведения см. в разделе [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="remarks"></a>Remarks

При использовании `REQUEST_MEMORY_GRANT_PERCENT` разрешено создание индексов для использования большего объема памяти рабочей области, чем было предоставлено изначально, в целях повышения производительности. Эта специальная обработка поддерживается регулятором ресурсов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Однако изначально предоставленная память и любая дополнительная выделенная память ограничены пулом ресурсов и настройками группы рабочей нагрузки.

Ограничение параметра `MAX_DOP` задается для каждой [задачи](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md). Оно не задается для каждого [запроса](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). Это означает, что во время параллельного выполнения один запрос может порождать множество задач, назначаемых [планировщику](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md). Дополнительные сведения см. в статье [Руководство по архитектуре потоков и задач](../../relational-databases/thread-and-task-architecture-guide.md).

Если используется `MAX_DOP` и запрос помечен как последовательный на стадии компиляции, изменить его состояние на параллельный во время выполнения невозможно независимо от параметров группы рабочей нагрузки или конфигурации сервера. После того как `MAX_DOP` настроен, он может быть только снижен при нехватке доступной памяти. Перенастройка группы рабочей нагрузки невидима при ожидании в очереди на предоставление памяти.

### <a name="index-creation-on-a-partitioned-table"></a>Создание индексов для секционированной таблицы

Объем памяти, затрачиваемой на создание индекса в невыровненной секционированной таблице, пропорционален количеству секций, охватываемых индексом. Если общий объем необходимой памяти превышает предел на запрос `REQUEST_MAX_MEMORY_GRANT_PERCENT`, устанавливаемый Resource Governor для группы рабочей нагрузки, создание такого индекса может завершиться ошибкой. Настройки группы рабочей нагрузки *"default"* позволяют запросу превосходить установленный для запросов предел памяти, нужной при запуске. Поэтому пользователь может запустить тот же процесс создания индекса в группе рабочей нагрузки *"default"* , если в пуле ресурсов *"default"* настроено достаточно памяти для выполнения такого запроса.

## <a name="permissions"></a>Разрешения

Требуется разрешение `CONTROL SERVER`.

## <a name="example"></a>Пример

Создайте группу рабочей нагрузки с именем `newReports`, для которой используются параметры по умолчанию Resource Governor и которая располагается в пуле по умолчанию Resource Governor. В примере указывается пул `default`, однако это не является обязательным.

```sql
CREATE WORKLOAD GROUP newReports
    USING "default" ;
GO
```

## <a name="see-also"></a>См. также:

- [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)
- [DROP WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/drop-workload-group-transact-sql.md)
- [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)
- [ALTER RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-resource-pool-transact-sql.md)
- [DROP RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-resource-pool-transact-sql.md)
- [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](create-workload-group-transact-sql.md?view=sql-server-2017)||[Управляемый экземпляр Базы данных SQL<br />](create-workload-group-transact-sql.md?view=azuresqldb-mi-current)||**_\* Azure Synapse<br />Analytics \*_** &nbsp;||||

&nbsp;

## <a name="azure-synapse-analytics-preview"></a>Azure Synapse Analytics (предварительная версия)

Создает группу рабочей нагрузки. Группы рабочей нагрузки являются контейнерами для набора запросов и служат основой для настройки управления рабочими нагрузками в системе. Группы рабочей нагрузки позволяют резервировать ресурсы для изоляции рабочей нагрузки, сохранять ресурсы, определять ресурсы для каждого запроса и соблюдать правила выполнения. После выполнения инструкции вступают в действие параметры.

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

```
CREATE WORKLOAD GROUP group_name
 WITH
 (        MIN_PERCENTAGE_RESOURCE = value
      ,   CAP_PERCENTAGE_RESOURCE = value
      ,   REQUEST_MIN_RESOURCE_GRANT_PERCENT = value
  [ [ , ] REQUEST_MAX_RESOURCE_GRANT_PERCENT = value ]
  [ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH }]
  [ [ , ] QUERY_EXECUTION_TIMEOUT_SEC = value ] )
  [ ; ]
```

*group_name*</br>
Указывает имя, по которому идентифицируется группа рабочей нагрузки. *group_name* имеет тип sysname. Оно может иметь длину до 128 символов и должно быть уникальным в пределах экземпляра.

*MIN_PERCENTAGE_RESOURCE* = value</br>
Указывает гарантированное минимальное выделение ресурсов для этой группы рабочей нагрузки, не используемое совместно с другими группами рабочей нагрузки. *value* является целым числом в диапазоне от 0 до 100. Сумма значений min_percentage_resource во всех группах рабочей нагрузки не может превышать 100. Значение min_percentage_resource не может превышать значение cap_percentage_resource. Для каждого уровня обслуживания предусмотрены минимальные действующие значения. Дополнительные сведения см. в разделе о [действующих значениях](#effective-values).

*CAP_PERCENTAGE_RESOURCE* = value</br>
Указывает максимальное использование ресурсов для всех запросов в группе рабочей нагрузки. Диапазон допустимых целых значений для value — от 1 до 100. Значение cap_percentage_resource не может превышать значение min_percentage_resource. Действующее значение для cap_percentage_resource можно уменьшить, если min_percentage_resource настраивается со значением больше нуля в других группах рабочей нагрузки.

*REQUEST_MIN_RESOURCE_GRANT_PERCENT* = value</br>
Задает минимальный объем ресурсов, выделяемых для каждого запроса. *value* является обязательным параметром с диапазоном десятичных значений от 0,75 до 100,00. Значение request_min_resource_grant_percent должно делиться на 0,25, быть кратно min_percentage_resource и быть меньше cap_percentage_resource. Для каждого уровня обслуживания предусмотрены минимальные действующие значения. Дополнительные сведения см. в разделе о [действующих значениях](#effective-values).

Пример:

```sql
CREATE WORKLOAD GROUP wgSample WITH
( MIN_PERCENTAGE_RESOURCE = 26              -- integer value
 ,REQUEST_MIN_RESOURCE_GRANT_PERCENT = 3.25 -- factor of 26 (guaranteed a minimum of 8 concurrency)
 ,CAP_PERCENTAGE_RESOURCE = 100 )
```

Рассмотрим значения, используемые для классов ресурсов в качестве рекомендуемых для request_min_resource_grant_percent.  В приведенной ниже таблице содержатся сведения о выделении ресурсов для 2-го поколения.

|Класс ресурсов|Процент ресурсов|
|---|---|
|Smallrc|3 %|
|Mediumrc|10 %|
|Largerc|22 %|
|Xlargerc|70 %|
|||

*REQUEST_MAX_RESOURCE_GRANT_PERCENT* = value</br>
Задает максимальный объем ресурсов, выделяемых для каждого запроса. *value* — это необязательный десятичный параметр со значением по умолчанию, равным значению request_min_resource_grant_percent. Значение *value* должно быть больше или равно значению request_min_resource_grant_percent. Если значение request_max_resource_grant_percent больше значения request_min_resource_grant_percent и доступны системные ресурсы, для запроса выделяются дополнительные ресурсы.

*IMPORTANCE* = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH }</br>
Указывает важность запроса по умолчанию в группе рабочей нагрузки. Важность представлена одним из следующих значений, причем значением по умолчанию является NORMAL.

- LOW
- BELOW_NORMAL
- NORMAL (по умолчанию)
- ABOVE_NORMAL
- HIGH.

Важность, заданная в группе рабочей нагрузки, является важностью по умолчанию для всех запросов в группе рабочей нагрузки. Пользователь также может задать важность на уровне классификатора, который может переопределить параметр важности группы рабочей нагрузки. Это позволяет различать уровень важности запросов в группе рабочей нагрузки для быстрого получения доступа к незарезервированным ресурсам. Если сумма min_percentage_resource в группах рабочей нагрузки меньше 100, значит имеются незарезервированные ресурсы, назначаемые на основе уровня важности.

*QUERY_EXECUTION_TIMEOUT_SEC* = value</br>
Указывает максимальное время в секундах, в течение которого может выполняться запрос до его отмены. *value* должно быть 0 или положительным целым числом. Значение value по умолчанию равно 0, что означает неограниченное время запроса. QUERY_EXECUTION_TIMEOUT_SEC начинает отсчет, когда запрос переходит в состояние выполнения, а не ставится в очередь.

## <a name="remarks"></a>Remarks

Группы рабочей нагрузки, соответствующие классам ресурсов, создаются автоматически для обеспечения обратной совместимости. Эти группы рабочей нагрузки, определенные системой, нельзя удалить. Можно создать восемь дополнительных групп рабочей нагрузки, определяемых пользователем.

Если группа рабочей нагрузки создается со значением min_percentage_resource больше нуля, инструкция `CREATE WORKLOAD GROUP` будет находиться в очереди до тех пор, пока не появится достаточно ресурсов для создания группы рабочей нагрузки.

## <a name="effective-values"></a>Действующие значения

Параметры min_percentage_resource, cap_percentage_resource, request_min_resource_grant_percent и request_max_resource_grant_percent имеют действующие значения, которые корректируются в контексте текущего уровня обслуживания и конфигурации других групп рабочей нагрузки.

Поддерживаемый уровень параллелизма для каждого уровня обслуживания остается таким же, что и при использовании классов ресурсов для определения выделений ресурсов для каждого запроса, поэтому поддерживаемые значения для request_min_resource_grant_percent зависят от уровня обслуживания, заданного для экземпляра. На самом низком уровне обслуживания DW100c требуется минимум 25 % ресурсов на запрос. На уровне DW100c действительное значение request_min_resource_grant_percent для настроенной группы рабочей нагрузки может составлять 25 % или выше. Дополнительные сведения о том, как извлекаются действующие значения, см. в таблице ниже.

|Уровень обслуживания|Наименьшее действительное значение для REQUEST_MIN_RESOURCE_GRANT_PERCENT|Максимальное число одновременных запросов|
|---|---|---|
|DW100c|25 %|4|
|DW200c|12,5 %|8|
|DW300c|8 %|12|
|DW400c|6,25 %|16|
|DW500c|5 %|20|
|DW1000c|3 %|32|
|DW1500c|3 %|32|
|DW2000c|2 %|48|
|DW2500c|2 %|48|
|DW3000c|1,5 %|64|
|DW5000c|1,5 %|64|
|DW6000c|0,75 %|128|
|DW7500c|0,75 %|128|
|DW10000c|0,75 %|128|
|DW15000c|0,75 %|128|
|DW30000c|0,75 %|128|
||||

Аналогичным образом, значение request_min_resource_grant_percent min_percentage_resource должно быть больше или равно действующему значению request_min_resource_grant_percent. Группа рабочей нагрузки с настроенным значением min_percentage_resource, которое меньше действующего значения min_percentage_resource, имеет значение, измененное во время выполнения до нуля. В этом случае ресурсы, настроенные для min_percentage_resource, будут общими для всех групп рабочей нагрузки. Например, группа рабочей нагрузки wgAdHoc со значением min_percentage_resource, равным 10 %, выполняющаяся на уровне обслуживания DW1000c, будет иметь действующее значение min_percentage_resource, равное 10 % (3,25 % — это минимальное поддерживаемое значение на уровне DW1000c). wgAdhoc на уровне обслуживания DW100c получит действующее значение min_percentage_resource, равное 0 %. Значение 10 %, настроенное для wgAdhoc, будет общим для всех групп рабочей нагрузки.

Cap_percentage_resource также имеет действующее значение. Если группа рабочей нагрузки wgAdhoc настроена со значением cap_percentage_resource, равным 100 %, а другая группа рабочей нагрузки wgDashboards создается со значением min_percentage_resource, равным 25 %, а действующим значением cap_percentage_resource для wgAdhoc становится 75 %.

Самый простой способ понять значения времени выполнения для групп рабочей нагрузки — выполнить запрос к системному представлению [sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md).

## <a name="permissions"></a>Разрешения

Требуется разрешение CONTROL DATABASE

## <a name="see-also"></a>См. также раздел

- [DROP WORKLOAD GROUP (Transact-SQL)](drop-workload-group-transact-sql.md)
- [sys.workload_management_workload_groups](../../relational-databases/system-catalog-views/sys-workload-management-workload-groups-transact-sql.md)
- [sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md)
- Краткое руководство по созданию и использованию [группы рабочей нагрузки](https://docs.microsoft.com/azure/sql-data-warehouse/quickstart-configure-workload-isolation-tsql)

::: moniker-end
