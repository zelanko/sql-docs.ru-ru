---
title: ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/02/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- ALTER_DATABASE_SCOPED_CONFIGURATION
- ALTER_DATABASE_SCOPED_CONFIGURATION_TSQL
- DATABASE_SCOPED_CONFIGURATION_TSQL
- SCOPED_CONFIGURATION_TSQL
- SCOPED_TSQL
- ALTER_DATABASE_SCOPED_TSQL
- DATABASE_SCOPED_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CONFIGURATION statement
- configuration [SQL Server], ALTER DATABASE SCOPED CONFIGURATION statement
ms.assetid: 63373c2f-9a0b-431b-b9d2-6fa35641571a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 744895bc3e2a60d8eb3edad4554f08bc1aaf6a95
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52641505"
---
# <a name="alter-database-scoped-configuration-transact-sql"></a>ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Эта инструкция включает несколько параметров конфигурации базы данных на уровне **отдельной базы данных**. Эта инструкция доступна в [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Речь идет о следующих параметрах:

- очистить кэш процедур;
- задать для параметра MAXDOP произвольное значение (1, 2,...) для базы данных-источника в зависимости от того, что лучше всего подходит для конкретной базы данных, и указать другое значение (например, 0) для всех используемых баз данных-получателей (например, для запросов отчетов);
- настроить модель оценки кратности оптимизатора запросов независимо от уровня совместимости базы данных;
- включить или выключить перехват параметров на уровне базы данных;
- включить или выключить исправления оптимизации запросов на уровне базы данных.
- включить или выключить кэширование идентификации на уровне базы данных;
- включить или выключить заглушку компилированного плана для сохранения в кэше при первом компилировании пакета.
- включить или выключить сбор статистики выполнения для скомпилированных в собственном коде модулей T-SQL.
- Включение или отключение параметров подключения по умолчанию для инструкций DDL, поддерживающих синтаксис ONLINE=.
- Включение или отключение параметров возобновления по умолчанию для инструкций DDL, поддерживающих синтаксис RESUMABLE=.
- Включение или отключение функции автоматического удаления глобальных временных таблиц

![Значок ссылки](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Синтаксис

```
ALTER DATABASE SCOPED CONFIGURATION
{
     {  [ FOR SECONDARY] SET <set_options>}
}
| CLEAR PROCEDURE_CACHE
| SET < set_options >
[;]

< set_options > ::=
{
    MAXDOP = { <value> | PRIMARY}
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}
    | IDENTITY_CACHE = { ON | OFF }
    | OPTIMIZE_FOR_AD_HOC_WORKLOADS = { ON | OFF }
    | XTP_PROCEDURE_EXECUTION_STATISTICS = { ON | OFF }
    | XTP_QUERY_EXECUTION_STATISTICS = { ON | OFF }
    | ELEVATE_ONLINE = { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED }
    | ELEVATE_RESUMABLE = { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED }
    | GLOBAL_TEMPORARY_TABLE_AUTODROP = { ON | OFF }
}
```

## <a name="arguments"></a>Аргументы

FOR SECONDARY

Задает параметры для баз данных-получателей (все базы данных-получатели должны иметь одинаковые значения).

MAXDOP **=** {\<value> | PRIMARY } **\<value>**

Задает используемый по умолчанию параметр MAXDOP для использования в инструкциях. 0 — это значение по умолчанию, указывающее, что вместо этого будет использоваться конфигурация сервера. MAXDOP на уровне базы данных переопределяет (если имеет значение, отличное от 0) **максимальную степень параллелизма**, заданную на уровне сервера процедурой sp_configure. Указания запросов все равно могут переопределять MAXDROP с областью действия "база данных", чтобы настроить конкретные запросы, требующие другой параметр. Все эти параметры ограничены параметром MAXDOP, заданным для группы рабочей нагрузки.

Для ограничения количества процессоров в плане параллельного выполнения может быть использован параметр max degree of parallelism. SQL Server учитывает планы параллельного выполнения для запросов, операций DDL с индексами, параллельной вставки, изменения столбца в режиме "в сети", параллельного сбора статистики и заполнения статических курсоров и курсоров, управляемых набором ключей.

Сведения о настройке этого параметра на уровне экземпляра см. в разделе [Настройка параметра конфигурации сервера max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).

> [!TIP]
> Для выполнения этого на уровне запросов добавьте [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) **MAXDOP**.

PRIMARY

Может задаваться только для баз данных-получателей, пока база данных находится на сервере-источнике, и указывает, что будет использоваться конфигурация, настроенная для сервера-источника. Если конфигурация для сервера-источника изменится, значение в базах данных-получателях изменится соответственно, задавать значение базы данных-получателя явным образом не требуется. **PRIMARY** — это параметр по умолчанию для баз данных-получателей.

LEGACY_CARDINALITY_ESTIMATION **=** { ON | **OFF** | PRIMARY }

Позволяет указывать модель оценки кратности оптимизатора запросов в SQL Server 2012 и более ранних версиях независимо от уровня совместимости базы данных. Значение по умолчанию **OFF**, задающее модель оценки кратности оптимизатора запросов с учетом уровня совместимости баз данных. Присвоение параметру LEGACY_CARDINALITY_ESTIMATION значения **ON** эквивалентно включению [флага трассировки 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).

> [!TIP]
> Для выполнения этого на уровне запросов добавьте [указание запроса](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) **QUERYTRACEON**.
> Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1) для выполнения этой задачи на уровне запроса добавьте [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) **USE HINT**, вместо того чтобы использовать флаг трассировки.

PRIMARY

Это значение допустимо только для баз данных-получателей, пока база данных находится на сервере-источнике; оно указывает, что в качестве настройки модели оценки кратности оптимизатора запросов для всех баз данных-получателей будет использоваться значение, заданное для сервера-источника. При изменении конфигурации модели оценки кратности оптимизатора запросов на сервере-источнике значение в базах данных-получателях изменится соответственно. **PRIMARY** — это параметр по умолчанию для баз данных-получателей.

PARAMETER_SNIFFING **=** { **ON** | OFF | PRIMARY}

Включает или отключает [сканирование параметров](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing). Значение по умолчанию — ON. Присвоение параметру PARAMETER_SNIFFING значения OFF эквивалентно включению [флага трассировки 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).

> [!TIP]
> Для выполнения этой задачи на уровне запроса добавьте **указание запроса** [OPTIMIZE FOR UNKNOWN](../../t-sql/queries/hints-transact-sql-query.md).
> Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1) для выполнения этой задачи на уровне запроса также доступно [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) **USE HINT**.

PRIMARY

Это значение допустимо только для баз данных-получателей, пока база данных находится на сервере-источнике; оно указывает, что значение этого параметра для всех баз данных-получателей будет равно значению, заданному для сервера-источника. Если конфигурация сервера-источника для [сканирования параметров](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing) изменится, значение в базах данных-получателях изменится соответственно, задавать значение базы данных-получателя явным образом не требуется. PRIMARY — это параметр по умолчанию для баз данных-получателей.

<a name="qo_hotfixes"></a> QUERY_OPTIMIZER_HOTFIXES **=** { ON | **OFF** | PRIMARY }

Включает или отключает исправления оптимизации запросов независимо от уровня совместимости базы данных. Значение по умолчанию — **OFF**, которое отключает исправления оптимизации запросов, выпущенные после появления наивысшего доступного уровня совместимости для определенной версии (после RTM). Присвоение этому параметру значения **ON** эквивалентно включению [флага трассировки 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).

> [!TIP]
> Для выполнения этого на уровне запросов добавьте [указание запроса](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) **QUERYTRACEON**.
> Начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] с пакетом обновления 1 (SP1) для выполнения этой задачи на уровне запроса добавьте [указание запроса](../../t-sql/queries/hints-transact-sql-query.md) USE HINT, вместо того чтобы использовать флаг трассировки.

PRIMARY

Это значение допустимо только для баз данных-получателей, пока база данных находится на сервере-источнике; оно указывает, что значение этого параметра для всех баз данных-получателей будет равно значению, заданному для сервера-источника. Если конфигурация для сервера-источника изменится, значение в базах данных-получателях изменится соответственно, задавать значение базы данных-получателя явным образом не требуется. PRIMARY — это параметр по умолчанию для баз данных-получателей.

CLEAR PROCEDURE_CACHE

Очистка кэша процедур (планов) для базы данных. Может выполняться для баз данных-источников и баз данных-получателей.

IDENTITY_CACHE **=** { **ON** | OFF }

**Применимо к**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

Включает и выключает кэширование идентификации на уровне базы данных. Значение по умолчанию — **ON**. Кэширование идентификаторов используется для повышения производительности инструкции INSERT в таблицах со столбцами идентификаторов. Во избежание пропусков значений столбца идентификаторов в случаях, когда сервер неожиданно перезапускается или выполняет обработку отказа на сервер-получатель, отключите параметр IDENTITY_CACHE. Этот параметр похож на существующий [флаг трассировки 272](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) с той разницей, что его можно задать на уровне базы данных, а не только на уровне сервера.

> [!NOTE]
> Этот параметр можно задать только для сервера-источника. Дополнительные сведения см. в статье [Столбцы идентификаторов](create-table-transact-sql-identity-property.md).

OPTIMIZE_FOR_AD_HOC_WORKLOADS **=** { ON | **OFF** }

**Область применения**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)]

Включает или отключает заглушку скомпилированного плана для сохранения в кэше при первой компиляции пакета. Значение по умолчанию — OFF. После включения конфигурации уровня базы данных OPTIMIZE_FOR_AD_HOC_WORKLOADS для базы данных заглушка скомпилированного плана будет сохранена в кэше при первой компиляции пакета. Заглушки плана расходуют меньше памяти по сравнению с полным скомпилированным планом. Если пакет компилируется или выполняется повторно, заглушка скомпилированного плана будет удалена и заменена полным скомпилированным планом.

XTP_PROCEDURE_EXECUTION_STATISTICS **=** { ON | **OFF** }

**Область применения**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]

Включает или отключает сбор статистики выполнения на уровне модуля для скомпилированных в собственном коде модулей T-SQL в текущей базе данных. Значение по умолчанию — OFF. Статистика выполнения отражается в [sys.dm_exec_procedure_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md).

Статистика выполнения на уровне модуля для скомпилированных в собственном коде модулей T-SQL собирается либо при значении ON этого параметра, либо если сбор статистики включен с помощью [sp_xtp_control_proc_exec_stats](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).

XTP_QUERY_EXECUTION_STATISTICS **=** { ON | **OFF** }

**Область применения**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]

Включает или отключает сбор статистики выполнения на уровне инструкций для скомпилированных в собственном коде модулей T-SQL в текущей базе данных. Значение по умолчанию — OFF. Статистика выполнения отражается в [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) и в [хранилище запросов](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).

Статистика выполнения на уровне инструкций для скомпилированных в собственном коде модулей T-SQL собирается либо при значении ON этого параметра, либо если сбор статистики включен с помощью [sp_xtp_control_query_exec_stats](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).

Дополнительные сведения о мониторинге производительности скомпилированных в собственном коде модулей T-SQL см. в статье [Отслеживание производительности скомпилированных в собственном коде хранимых процедур](../../relational-databases/in-memory-oltp/monitoring-performance-of-natively-compiled-stored-procedures.md).

ELEVATE_ONLINE = { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED }

**Применимо к**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] (компонент в общедоступной предварительной версии)

Позволяет выбирать параметры, предписывающие ядру автоматически переводить поддерживаемые операции в режим "в сети". Значение по умолчанию — OFF. Оно означает, что операции не будут переводиться в режим "в сети", если это явно не указано в инструкции. В представлении [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) указывается текущее значение ELEVATE_ONLINE. Эти параметры применяются только к операциям, которые поддерживают режим "в сети".

FAIL_UNSUPPORTED

Это значение переводит все поддерживаемые операции DDL в режим "в сети". Операции, не поддерживающие выполнение в режиме "в сети", завершатся сбоем и выдадут предупреждение.

WHEN_SUPPORTED

Это значение изменяет режим выполнения операций, поддерживающих режим "в сети". Операции, не поддерживающие режим "в сети", будут выполняться в режиме "вне сети".

> [!NOTE]
> Переопределить значение по умолчанию можно, отправив инструкцию с параметром ONLINE.

ELEVATE_RESUMABLE= { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED }

***Область применения**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssNoVersion](../../includes/sssqlv15-md.md)] в общедоступной предварительной версии.

Позволяет выбирать параметры, предписывающие ядру автоматически переводить поддерживаемые операции в возобновляемый режим. Значение по умолчанию — OFF. Оно означает, что операции не будут переводиться в возобновляемый режим, если это явно не указано в инструкции. В представлении [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) указывается текущее значение ELEVATE_RESUMABLE. Эти параметры применяются только к операциям, которые поддерживают возобновление.

FAIL_UNSUPPORTED

Это значение переводит все поддерживаемые операции DDL в возобновляемый режим. Операции, не поддерживающие возобновляемое выполнение, завершатся сбоем и выдадут предупреждение.

WHEN_SUPPORTED

Это значение изменяет режим выполнения операций, поддерживающих возобновляемое выполнение. Операции, не поддерживающие возобновляемый режим, будут выполняться в невозобновляемом режиме.

> [!NOTE]
> Переопределить значение по умолчанию можно, отправив инструкцию с параметром RESUMABLE.

GLOBAL_TEMPORARY_TABLE_AUTODROP = { ON | OFF }

**Применимо к**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] (компонент в общедоступной предварительной версии)

Настройка функции автоматического удаления [глобальных временных таблиц](create-table-transact-sql.md). По умолчанию имеет значение ON, то есть глобальные временные таблицы автоматически удаляются, когда не используются ни одним сеансом. Если задано значение OFF, глобальные временные таблицы следует удалять явным образом с помощью инструкции DROP TABLE, или они будут автоматически удалены при перезапуске сервера.

- В логическом сервере Базы данных SQL Azure этот параметр можно задать для отдельных баз данных пользователей логического сервера.
- В SQL Server и Управляемом экземпляре Базы данных SQL Azure этот параметр задается в `TEMPDB` и не учитывается на уровне отдельных пользовательских баз.

DISABLE_INTERLEAVED_EXECUTION_TVF = { ON | OFF }

**Применимо к**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

Позволяет включить или отключить выполнение с чередованием для функций с табличным значением и множеством инструкций в области базы данных или инструкции, сохранив уровень совместимости базы данных 140 или выше. Выполнение с чередованием — одна из возможностей адаптивной обработки запросов в базах данных SQL. Дополнительные сведения: [Адаптивная обработка запросов](../../relational-databases/performance/adaptive-query-processing.md)

DISABLE_BATCH_MODE_ADAPTIVE_JOINS = { ON | OFF }

**Применимо к**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

Позволяет включить или отключить адаптивные соединения в области базы данных или инструкции, сохранив уровень совместимости базы данных 140 или выше. Адаптивные соединения — одна из возможностей [адаптивной обработки запросов](../../relational-databases/performance/adaptive-query-processing.md), представленная в SQL Server 2017.

ROW_MODE_MEMORY_GRANT_FEEDBACK = { ON | OFF}

**Область применения**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssNoVersion](../../includes/sssqlv15-md.md)] в общедоступной предварительной версии.

Позволяет включить или отключить обратную связь по временно предоставляемому буферу памяти в построчном режиме в области базы данных или инструкции, сохранив уровень совместимости базы данных 150 или выше. Обратная связь по временно предоставляемому буферу памяти в построчном режиме — одна из возможностей [адаптивной обработки запросов](../../relational-databases/performance/adaptive-query-processing.md), представленная в SQL Server 2019.

## <a name="Permissions"></a> Permissions

Требует в базе данных разрешения ALTER ANY DATABASE SCOPE CONFIGURATION. Это разрешение может быть предоставлено пользователем, имеющим разрешение CONTROL для базы данных.

## <a name="general-remarks"></a>Общие замечания

Можно настроить базы данных-получатели с отличающимися по уровню от сервера-источника параметрами конфигурации, все базы данных-получатели используют одну и ту же конфигурацию. Невозможно настроить разные параметры для разных баз данных-получателей.

При выполнении этой инструкции очищается кэш процедур в текущей базе данных; это означает, что нужно перекомпилировать все запросы.

Что касается трехчастных запросов имен, для запроса соблюдаются параметры текущего подключения базы данных. Это не относится к модулям SQL (процедуры, функции и триггеры), которые компилируются в контексте текущей базы данных и применяют параметры базы данных, в которой они находятся.

Событие ALTER_DATABASE_SCOPED_CONFIGURATION добавляется дочерним элементом в группу триггеров ALTER_DATABASE_EVENTS в качестве события DDL, с помощью которого можно инициировать триггер DDL.

Параметры конфигурации уровня базы данных будут перенесены вместе с базой данных, то есть при восстановлении или подключении любой базы данных сохранятся ее текущие параметры конфигурации.

## <a name="limitations-and-restrictions"></a>Ограничения

### <a name="maxdop"></a>MAXDOP

Детализированные параметры могут переопределять глобальные, а регулятор ресурсов может ограничивать все остальные параметры MAXDOP. Логика параметра MAXDOP выглядит следующим образом:

- Указание запроса переопределяет процедуру sp_configure и параметр уровня базы данных. Если для группы рабочей нагрузки задана группа ресурсов MAXDOP:

  - Если указание запроса имеет значение 0, оно переопределяется параметром регулятора ресурсов.

  - Если указание запроса имеет значение, отличное от 0, оно ограничивается параметром регулятора ресурсов.

- Параметр уровня БД (если он отличен от 0) переопределяет параметр процедуры sp_configure кроме случаев, когда имеется указание запроса и оно ограничено параметром регулятора ресурсов.

- Параметр процедуры sp_configure переопределяется параметром регулятора ресурсов.

### <a name="queryoptimizerhotfixes"></a>QUERY_OPTIMIZER_HOTFIXES

Указание QUERYTRACEON используется для включения оптимизатора устаревших запросов или исправлений оптимизатора запроса; между указанием запроса и параметром конфигурации уровня базы данных используется условие ИЛИ, что означает, что если хотя бы одна из этих сущностей включена, параметры будут применены.

### <a name="geodr"></a>GeoDR

Доступные для чтения базы данных-получатели (группы доступности AlwaysOn и геореплицируемые базы данных в службе "База данных SQL") используют значение базы данных-получателя, проверяя состояние базы данных. Несмотря на то что при отработке отказа не происходит компиляция и технически на новом сервере-источнике существуют запросы, использующие параметры базы данных-получателя, суть в том, что параметр между источником и получателем меняется только в том случае, если рабочая нагрузка различается. Следовательно, кэшированные запросы используют оптимальные параметры, а новые запросы выбирают подходящие для них новые параметры.

### <a name="dacfx"></a>DacFx

Так как ALTER DATABASE SCOPED CONFIGURATION — это новая функция в Базе данных SQL Azure и SQL Server, начиная с SQL Server 2016, которая влияет на схему базы данных, экспорты схемы (с данными или без них) невозможно импортировать в более старую версию SQL Server, например [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)]. Например, экспорт в [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3) или [BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4) из базы данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)] или [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], использовавшей эту новую функцию, невозможно будет импортировать на сервер нижнего уровня.

### <a name="elevateonline"></a>ELEVATE_ONLINE

Этот параметр применяется только к инструкциям DDL, поддерживающим синтаксис WITH(ONLINE=). Не затрагивает индексы XML.

### <a name="elevateresumable"></a>ELEVATE_RESUMABLE

Этот параметр применяется только к инструкциям DDL, поддерживающим синтаксис WITH(RESUMABLE= syntax). Не затрагивает индексы XML.

## <a name="metadata"></a>Метаданные

Системное представление [sys.database_scoped_configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) предоставляет информацию о конфигурациях ограниченной области применения в базах данных. Параметры конфигурации уровня БД отображаются только в sys.database_scoped_configurations, поскольку являются переопределениями параметров по умолчанию для всего сервера. В системном представлении [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) отображаются только параметры для всего сервера.

## <a name="examples"></a>Примеры

Эти примеры демонстрируют использование инструкции ALTER DATABASE SCOPED CONFIGURATION

### <a name="a-grant-permission"></a>A. Предоставление разрешений

В этом примере пользователю [Joe] предоставляется разрешение, необходимое для выполнения инструкции ALTER DATABASE SCOPED CONFIGURATION.

```sql
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;
```

### <a name="b-set-maxdop"></a>Б. Задание параметра MAXDOP

В этом примере задается MAXDOP = 1 для базы данных-источника и MAXDOP = 4 для базы данных-получателя в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;
```

В этом примере MAXDOP для базы данных-получателя задается равным этому параметру для базы данных-источника в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```

### <a name="c-set-legacycardinalityestimation"></a>В. Задание параметра LEGACY_CARDINALITY_ESTIMATION

В этом примере для параметра LEGACY_CARDINALITY_ESTIMATION задается значение ON для базы данных-получателя в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;
```

В этом примере параметр LEGACY_CARDINALITY_ESTIMATION для базы данных-получателя задается равным параметру для базы данных-источника в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;
```

### <a name="d-set-parametersniffing"></a>Г. Задание параметра PARAMETER_SNIFFING

В этом примере параметру PARAMETER_SNIFFING присваивается значение OFF для базы данных-источника в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;
```

В этом примере параметру PARAMETER_SNIFFING присваивается значение OFF для базы данных-источника в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;
```

В этом примере параметр PARAMETER_SNIFFING для базы данных-получателя задается равным параметру для базы данных-источника в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=PRIMARY ;
```

### <a name="e-set-queryoptimizerhotfixes"></a>Д. Задание параметра QUERY_OPTIMIZER_HOTFIXES

Задайте для параметра QUERY_OPTIMIZER_HOTFIXES значение ON для базы данных-источника в сценарии георепликации.

```sql
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;
```

### <a name="f-clear-procedure-cache"></a>Е. Очистка кэша процедур

В этом примере очищается кэш процедур (возможно только для базы данных-источника).

```sql
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;
```

### <a name="g-set-identitycache"></a>Ж. Задание параметра IDENTITY_CACHE

**Применимо к**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] (компонент в общедоступной предварительной версии)

В этом примере отключается кэш идентификаторов.

```sql
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ;
```

### <a name="h-set-optimizeforadhocworkloads"></a>З. Задание параметра OPTIMIZE_FOR_AD_HOC_WORKLOADS

**Область применения**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)]

В этом примере включается заглушка скомпилированного плана для сохранения в кэше при первой компиляции пакета.

```sql
ALTER DATABASE SCOPED CONFIGURATION SET OPTIMIZE_FOR_AD_HOC_WORKLOADS = ON;
```

### <a name="i-set-elevateonline"></a>И. Задание ELEVATE_ONLINE

**Область применения**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] и как общедоступная предварительная версия функции

В этом примере параметру ELEVATE_ONLINE присваивается значение FAIL_UNSUPPORTED.

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ELEVATE_ONLINE=FAIL_UNSUPPORTED ;
```

### <a name="j-set-elevateresumable"></a>К. Задание ELEVATE_RESUMABLE

**Область применения**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssNoVersion](../../includes/sssqlv15-md.md)] в общедоступной предварительной версии.

В этом примере параметру ELEVEATE_RESUMABLE присваивается значение WHEN_SUPPORTED.

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ELEVATE_RESUMABLE=WHEN_SUPPORTED ;
```

## <a name="additional-resources"></a>Дополнительные ресурсы

### <a name="maxdop-resources"></a>Ресурсы MAXDOP

- [Степень параллелизма](../../relational-databases/query-processing-architecture-guide.md#DOP)
- [Рекомендации и инструкции по использованию параметра конфигурации "max degree of parallelism" в SQL Server](https://support.microsoft.com/kb/2806535)

### <a name="legacycardinalityestimation-resources"></a>Ресурсы по параметру LEGACY_CARDINALITY_ESTIMATION

- [Оценка количества элементов (SQL Server)](../../relational-databases/performance/cardinality-estimation-sql-server.md)
- [Оптимизация планов запроса с помощью средства оценки кратности SQL Server 2014](https://msdn.microsoft.com/library/dn673537.aspx)

### <a name="parametersniffing-resources"></a>Ресурсы по параметру PARAMETER_SNIFFING

- [Сканирование параметров](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)
- ["Кажется, здесь есть параметр!"](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>Ресурсы по параметру QUERY_OPTIMIZER_HOTFIXES

- [Флаги трассировки](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
- [Модель обслуживания флага трассировки 4199 для исправления оптимизатора запросов SQL Server](https://support.microsoft.com/kb/974006)

### <a name="elevateonline-resources"></a>Ресурсы по ELEVATE_ONLINE

[Рекомендации по операциям с индексами в оперативном режиме](../../relational-databases/indexes/guidelines-for-online-index-operations.md)

### <a name="elevateresumable-resources"></a>Ресурсы по ELEVATE_RESUMABLE

[Рекомендации по операциям с индексами в оперативном режиме](../../relational-databases/indexes/guidelines-for-online-index-operations.md)

## <a name="more-information"></a>Дополнительные сведения

- [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)
- [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)
- [Представления каталога баз данных и файлов](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)
- [Параметры конфигурации сервера](../../database-engine/configure-windows/server-configuration-options-sql-server.md)
- [Об операциях с индексами в сети](../../relational-databases/indexes/how-online-index-operations-work.md)
- [Выполнение операции с индексами в сети](../../relational-databases/indexes/perform-index-operations-online.md)
- [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)
- [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)
