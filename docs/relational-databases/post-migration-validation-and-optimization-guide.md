---
title: "Руководство по оптимизации и проверке после миграции | Документация Microsoft"
ms.custom: 
ms.date: 5/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-migration validation and optimization
- guide, post-migration validation and optimization
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
caps.latest.revision: 
author: pelopes
ms.author: harinid
manager: 
ms.workload: Inactive
ms.openlocfilehash: 3264cab532c77a8e27daff0a3c5c1bd5ed801818
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="post-migration-validation-and-optimization-guide"></a>Руководство по оптимизации и проверке после миграции
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Проверка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] после миграции — очень важный шаг, позволяющий добиться точности и полноты данных, а также выявить проблемы с производительностью рабочей нагрузки.

# <a name="common-performance-scenarios"></a>Типовые сценарии производительности 
Ниже представлены некоторые типовые сценарии производительности, которые встречаются после миграции на платформу [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], а также способы устранения связанных с ними проблем. К ним относятся сценарии, связанные с миграцией с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (переход на более новые версии), а также с миграцией с внешней платформы (например, Oracle, DB2, MySQL и Sybase) на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

## <a name="CEUpgrade"></a> Замедление запросов из-за изменения в версии CE

**Область применения:** миграция с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

При миграции со старых версий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] или более новые версии и при обновлении [уровня совместимости базы данных](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) до новейшего существует риск замедления выполнения рабочей нагрузки.

Это объясняется тем, что, начиная с [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], все изменения в оптимизаторе запросов привязаны к последнему [уровню совместимости базы данных](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md), поэтому планы изменяются не в момент обновления, а когда пользователь изменяет параметр базы данных `COMPATIBILITY_LEVEL` на последнюю версию. В сочетании с хранилищем запросов эта возможность обеспечивает высокий уровень контроля над производительностью запросов в процессе обновления. 

Дополнительные сведения об изменениях оптимизатора запросов, появившихся в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], см. в документе [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](http://msdn.microsoft.com/library/dn673537.aspx) (Оптимизация планов запросов с помощью модуля оценки кратности SQL Server 2014).

### <a name="steps-to-resolve"></a>Действия по устранению

Измените [уровень совместимости базы данных](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) на исходную версию и следуйте рекомендуемому рабочему процессу обновления, показанному на следующем рисунке:

![query-store-usage-5](../relational-databases/performance/media/query-store-usage-5.png "query-store-usage-5")  

Дополнительные сведения по этой теме см. в разделе [Поддержание стабильной производительности во время обновления до более новой версии SQL Server](../relational-databases/performance/query-store-usage-scenarios.md#CEUpgrade).

## <a name="ParameterSniffing"></a> Чувствительность к пробному сохранению параметров

**Область применения:** внешняя платформа (например, Oracle, DB2, MySQL или Sybase) для миграции [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

> [!NOTE]
> Если при миграции с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] подобная проблема возникнет в источнике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], миграция на новую версию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] без изменений будет проходить без учета этого сценария. 

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] компилирует планы запросов для хранимых процедур, используя перехват входных параметров во время первой компиляции и создавая параметризованный план с возможностью повторного использования, оптимизированный для распространения этих параметров. Даже если хранимых процедур нет, большинство операторов, создающий простые планы, будет параметризовано. После первого кэширования плана любое выполнение сопоставляется с кэшированным ранее планом.
Проблемы могут возникнуть, если в первой компиляции не использовались наборы параметров, наиболее типичные для обычной рабочей нагрузки. С другими параметрами план выполнения будет неэффективным. Дополнительные сведения по этой теме см. в разделе [Сканирование параметров](../relational-databases/query-processing-architecture-guide.md#ParamSniffing).

### <a name="steps-to-resolve"></a>Действия по устранению

1.  Воспользуйтесь подсказкой `RECOMPILE`. Для каждого значения параметра план вычисляется заново.
2.  Перепишите хранимую процедуру, задействовав параметр `(OPTIMIZE FOR(<input parameter> = <value>))`. Определите, какое значение соответствует большей части рабочей нагрузки — это позволит создать и использовать единый план, который будет эффективным для параметризованного значения.
3.  Перепишите хранимую процедуру, добавив в нее локальную переменную. После этого оптимизатор будет использовать для оценки вектор плотностей, а значит план будет выполняться независимо от значения параметра.
4.  Перепишите хранимую процедуру, задействовав параметр `(OPTIMIZE FOR UNKNOWN)`. Результат будет точно таким же, как при использовании локальной переменной.
5.  Перепишите запрос, задействовав подсказку `DISABLE_PARAMETER_SNIFFING`. Результат будет таким же, как при использовании локальной переменной — в отсутствие `OPTION(RECOMPILE)`, `WITH RECOMPILE` или `OPTIMIZE FOR <value>` сканирование параметра будет полностью отключено.

> [!TIP] 
> Воспользуйтесь функцией анализа плана [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)], чтобы быстро определить наличие проблемы. Дополнительные сведения см. [здесь](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-query-performance-troubleshooting-made-easier/).

## <a name="MissingIndexes"></a> Отсутствие индексов

**Область применения:** внешняя платформа (например, Oracle, DB2, MySQL или Sybase) для миграции с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

Неправильные индексы или их отсутствие создают дополнительную нагрузку по вводу-выводу, а значит и лишний расход ресурсов памяти и процессора. Это может быть связано с изменением профиля рабочей нагрузки, например применением других предикатов, нарушающим существующую структуру индекса. Как понять, что стратегия индексации или изменения в профиле рабочей нагрузки неадекватны:
-   обращайте внимание на повторяющиеся, избыточные, редко применяемые и абсолютно неиспользуемые индексы;
-   проявляйте особое внимание к неиспользуемым индексам с обновлениями.

### <a name="steps-to-resolve"></a>Действия по устранению

1.  Использование графического плана выполнения для отсутствующих ссылок на индексы.
2.  Индексирование предложений, созданных [помощником по настройке ядра СУБД](../tools/dta/tutorial-database-engine-tuning-advisor.md).
3.  Использование [динамического административного представления отсутствующих индексов ](../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) или [панели мониторинга производительности SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=29063).
4.  Использование существующих сценариев, которые могут обращаться к существующим динамическим административным представлениям для получения представления об отсутствующих, повторяющихся, избыточных, редко применяемых и абсолютно неиспользуемых индексах, а также в случае, если какая-либо ссылка на индекс указана в подсказке или прописана в коде процедур или функций, существующих в вашей базе данных. 

> [!TIP] 
> В качестве примеров таких существующих скриптов можно привести [создание индекса](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Creation) и [сведения об индексе](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Information). 

## <a name="InabilityPredicates"> </a>Невозможность использовать предикаты для фильтрации данных

**Область применения:** внешняя платформа (например, Oracle, DB2, MySQL или Sybase) для миграции с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

> [!NOTE]
> Если при миграции с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] подобная проблема возникнет в источнике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], миграция на новую версию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] без изменений будет проходить без учета этого сценария.

Оптимизатор запросов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] работает только с теми данными, которые известны на момент компиляции. Если рабочая нагрузка выполняется с предикатами, которые могут быть известны только во время выполнения, вероятность неадекватного выбора плана возрастает. Для получения плана оптимального качества требуются предикаты **SARGable** или **S**earch **Arg**ument**able**.

Приведем несколько примеров предикатов, отличных от SARGable:
-   Неявные преобразования данных, например VARCHAR в NVARCHAR или INT в VARCHAR. Ищите предупреждения CONVERT_IMPLICIT в фактических планах выполнения в среде выполнения. Преобразование одного типа в другой также может приводить к потере точности.
-   Сложные неопределенные выражения, такие как `WHERE UnitPrice + 1 < 3.975`, но не `WHERE UnitPrice < 320 * 200 * 32`.
-   Выражения с функциями, такие как `WHERE ABS(ProductID) = 771` или `WHERE UPPER(LastName) = 'Smith'`.
-   Строки, которые начинаются с подстановочных знаков, такие как `WHERE LastName LIKE '%Smith'`, но не `WHERE LastName LIKE 'Smith%'`.

### <a name="steps-to-resolve"></a>Действия по устранению

1. Всегда объявляйте переменные или параметры как намеченный целевой [тип данных](../t-sql/data-types/data-types-transact-sql.md). 
  -   Для этого может потребоваться сравнение конструкции пользовательского кода, хранящийся в базе данных (например, хранимых процедур, определяемых пользователем функций или представлений), с системными таблицами, которые содержат сведения о типах данных, используемых в базовых таблицах (таких как [sys.columns](../relational-databases/system-catalog-views/sys-columns-transact-sql.md)).
2. Если перебрать весь код до указанной выше точки нельзя, то с той же целью можно изменить тип данных в таблице в соответствии с объявлением переменной или параметра.
3. Рассмотрите целесообразность применения следующих конструкций:
  -   функции, используемые в качестве предикатов;
  -   поиск с подстановочными знаками;
  -   сложные выражения на основе данных, расположенных в один столбец (подумайте, не стоит ли вместо них создать материализованные вычисляемые столбцы, которые можно проиндексировать).

> [!NOTE] 
> Все это можно сделать программным способом.

## <a name="TableValuedFunctions"></a> Применение функций, возвращающих табличные значения (многооператорные и встроенные функции)

**Область применения:** внешняя платформа (например, Oracle, DB2, MySQL или Sybase) для миграции с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

> [!NOTE]
> Если при миграции с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] подобная проблема возникнет в источнике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], миграция на новую версию [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] без изменений будет проходить без учета этого сценария.

Функции, возвращающие табличные значения, возвращают табличные данные, которые можно просматривать в различных представлениях. В то время как представления ограничены одной инструкцией `SELECT`, пользовательские функции могут содержать дополнительные инструкции, обеспечивающие более обширную логику, чем та, которая возможна в представлениях.

> [!IMPORTANT] 
> Поскольку во время компиляции таблица результатов многооператорных функций, возвращающих табличные значения, не создается, оптимизатор запросов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] при подсчете строк обращается к эвристическим правилам, а не к фактической статистике. Не помогает даже добавление индексов в базовую таблицу (или таблицы). Для многооператорных функций, возвращающих табличные значения, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует в качестве количества строк, которое должна возвращать такая функция, фиксированное значение 1 (начиная с [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], фиксированное значение составляет 100 строк).

### <a name="steps-to-resolve"></a>Действия по устранению
1.  Если многооператорной функцией, возвращающей табличное значение, является только одна инструкция, преобразуйте ее во встроенную функцию.

    ```sql
    CREATE FUNCTION dbo.tfnGetRecentAddress(@ID int)
    RETURNS @tblAddress TABLE
    ([Address] VARCHAR(60) NOT NULL)
    AS
    BEGIN
      INSERT INTO @tblAddress ([Address])
      SELECT TOP 1 [AddressLine1]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    RETURN
    END
    ```
    Чтобы 

    ```sql
    CREATE FUNCTION dbo.tfnGetRecentAddress_inline(@ID int)
    RETURNS TABLE
    AS
    RETURN (
      SELECT TOP 1 [AddressLine1] AS [Address]
      FROM [Person].[Address]
      WHERE  AddressID = @ID
      ORDER BY [ModifiedDate] DESC
    )
    ```

2.  Для более сложных вариантов можно использовать промежуточные результаты, которые хранятся в таблицах, оптимизированных для памяти, или во временных таблицах.

##  <a name="Additional_Reading"></a> Дополнительные материалы  
 [Рекомендации по хранилищу запросов](../relational-databases/performance/best-practice-with-the-query-store.md)  
[Таблицы, оптимизированные для памяти](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
[Определяемые пользователем функции](../relational-databases/user-defined-functions/user-defined-functions.md)  
[Табличные переменные и расчетное количество строк — часть 1](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/11/30/table-variables-and-row-estimations-part-1/)  
[Табличные переменные и расчетное количество строк — часть 2](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/12/09/table-variables-and-row-estimations-part-2/)  
[Кэширование и повторное использование плана выполнения](../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse)
