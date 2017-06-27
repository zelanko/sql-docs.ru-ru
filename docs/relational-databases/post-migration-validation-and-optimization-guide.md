---
title: "После миграции проверки и руководство по оптимизации | Документы Microsoft"
ms.custom: 
ms.date: 5/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-migration validation and optimization
- guide, post-migration validation and optimization
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
caps.latest.revision: 3
author: pelopes
ms.author: harinid
manager: 
ms.translationtype: Human Translation
ms.sourcegitcommit: dcbeda6b8372b358b6497f78d6139cad91c8097c
ms.openlocfilehash: 30a271511fff2d9c3c9eab73a0d118bfb3f8130d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# <a name="post-migration-validation-and-optimization-guide"></a>После миграции проверки и руководство по оптимизации
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]После миграции шаг очень важна при согласовании любые данные точности и полноты, а также выявлять проблемы с производительностью с рабочей нагрузкой.

# <a name="common-performance-scenarios"></a>Распространенные сценарии производительности 
Ниже перечислены некоторые распространенные сценарии производительности обнаружил после перехода на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] платформы и способы их устранения. К ним относятся сценарии, связанные с миграцией с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (переход на более новые версии), а также с миграцией с внешней платформы (например, Oracle, DB2, MySQL и Sybase) на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

## <a name="CEUpgrade"></a> Замедление запросов из-за изменения в версии CE

**Область применения:** миграция с [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

При миграции со старых версий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] или более новые версии и при обновлении [уровня совместимости базы данных](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) до новейшего существует риск замедления выполнения рабочей нагрузки.

Это объясняется тем, что, начиная с [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], все изменения в оптимизаторе запросов привязаны к последнему [уровню совместимости базы данных](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md), поэтому планы изменяются не в момент обновления, а когда пользователь изменяет параметр базы данных `COMPATIBILITY_LEVEL` на последнюю версию. В сочетании с хранилищем запросов эта возможность обеспечивает высокий уровень контроля над производительностью запросов в процессе обновления. 

Дополнительные сведения об изменениях оптимизатора запросов, появившихся в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], см. в документе [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](http://msdn.microsoft.com/library/dn673537.aspx) (Оптимизация планов запросов с помощью модуля оценки кратности SQL Server 2014).

### <a name="steps-to-resolve"></a>Действия по устранению

Измените [уровень совместимости базы данных](../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) на исходную версию и следуйте рекомендуемому рабочему процессу обновления, показанному на следующем рисунке:

![query-store-usage-5](../relational-databases/performance/media/query-store-usage-5.png "query-store-usage-5")  

Дополнительные сведения по этой теме см. в разделе [Поддержание стабильной производительности во время обновления до более новой версии SQL Server](../relational-databases/performance/query-store-usage-scenarios.md#CEUpgrade).

## <a name="ParameterSniffing"></a>Чувствительность к пробное сохранение параметров

**Применяется к:** внешнего платформы (например, Oracle, DB2, MySQL и Sybase) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] миграции.

> [!NOTE]
> Для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] миграций и, если эта проблема существует в источнике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], миграция до новой версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] как-оно будет не удовлетворения потребностей этого сценария. 

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Компилирует планы запросов для хранимых процедур с помощью перехвата во время первой компиляции, создания параметризованных с возможностью повторного использования плана, оптимизированный для входных параметрах, входных данных распространения. Даже если не хранимых процедур, будут параметризованы большинство инструкций, Создание обычных планов. После кэширования плана сопоставляет ранее кэшированный план выполнения в будущем.
Потенциальные проблемы возникает, когда этой первой компиляции не воспользовались наиболее распространенные наборов параметров для обычных рабочей нагрузки. Для различных параметров тот же план выполнения станет неэффективным. Дополнительные сведения по этой теме см. в разделе [Сканирование параметров](../relational-databases/query-processing-architecture-guide.md#ParamSniffing).

### <a name="steps-to-resolve"></a>Действия по устранению

1.  Используйте `RECOMPILE` подсказку. План вычисляется каждый раз, чтобы адаптировать для каждого значения параметра.
2.  Перепишите хранимой процедуры для использования параметра `(OPTIMIZE FOR(<input parameter> = <value>))`. Определите, какое значение следует использовать, подходит для большинства соответствующей рабочей нагрузки, создание и обслуживание один план, который становится эффективным параметризованное значение.
3.  Перепишите хранимой процедуры, с помощью локальной переменной в процедуре. Теперь оптимизатор использует вектор плотностей для оценки, что приводит к тому же плану независимо от значения параметра.
4.  Перепишите хранимой процедуры для использования параметра `(OPTIMIZE FOR UNKNOWN)`. Результату, используя метод локальной переменной.
5.  Перепишите запрос, чтобы использовать подсказку `DISABLE_PARAMETER_SNIFFING`. Тот же эффект, как при использовании локальной переменной метода, полностью отключить пробное сохранение параметров, если не `OPTION(RECOMPILE)`, `WITH RECOMPILE` или `OPTIMIZE FOR <value>` используется.

> [!TIP] 
> Использование [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] функция анализа плана, чтобы быстро определить, если это важно. Дополнительные сведения недоступны [здесь](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-query-performance-troubleshooting-made-easier/).

## <a name="MissingIndexes"></a>Отсутствующие индексы

**Применяется к:** внешнего платформы (например, Oracle, DB2, MySQL и Sybase) и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] миграции.

Неправильные или отсутствующие индексы в результате лишние ввода-вывода, которая приводит к дополнительной памяти и ЦП потрачены впустую. Это может быть так, как был изменен профиль рабочей нагрузки, например, с помощью различных предикаты, что делает недействительными существующие индекса конструктора. Следующие свидетельство неудачные индексы или изменения в профиле рабочей нагрузки.
-   Ищите повторяющиеся, избыточной, редко используемые и полностью неиспользуемых индексов.
-   Особое с неиспользуемых индексов с обновлениями.

### <a name="steps-to-resolve"></a>Действия по устранению

1.  Используйте графический план выполнения для ссылок на любые отсутствует индекс.
2.  Индексирование предложения, созданные [помощник по настройке ядра СУБД](../tools/dta/tutorial-database-engine-tuning-advisor.md).
3.  Использование [отсутствующих индексов динамического административного Представления](../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) или через [панель мониторинга производительности SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=29063).
4.  Используйте существующие сценарии, которые можно использовать существующие динамические административные представления для дают представление о отсутствует, повторяющиеся, избыточной, редко используемые и полностью неиспользуемые индексы, но также в том случае, если любая ссылка на индекс, есть и в коде существующих процедур и функций в базе данных. 

> [!TIP] 
> Примеры таких существующие сценарии [создания индекса](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Creation) и [сведения об индексе](https://github.com/Microsoft/tigertoolbox/tree/master/Index-Information). 

## <a name="InabilityPredicates"></a>Невозможно использовать полнотекстовые предикаты для фильтрации данных

**Применяется к:** внешнего платформы (например, Oracle, DB2, MySQL и Sybase) и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] миграции.

> [!NOTE]
> Для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] миграций и, если эта проблема существует в источнике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], миграция до новой версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] как-оно будет не удовлетворения потребностей этого сценария.

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Оптимизатор запросов может только учетной записи сведения, известным во время компиляции. Если рабочая нагрузка использует предикатов, которое может быть известен только во время выполнения, увеличивает вероятность выбора низкой плана. План более высокого качества, предикаты должны иметь **SARGable**, или **S**поиск **Arg**документами**может**.

Некоторые примеры не SARGable предикатов.
-   Неявное преобразование данных, например VARCHAR в NVARCHAR или INT в VARCHAR. Просмотрите предупреждения CONVERT_IMPLICIT среды выполнения в фактических планов выполнения. Преобразование из одного типа в другой может также привести к потере точности.
-   Сложные выражения не определено, такие как `WHERE UnitPrice + 1 < 3.975`, но не `WHERE UnitPrice < 320 * 200 * 32`.
-   Выражения с помощью функций, таких как `WHERE ABS(ProductID) = 771` или`WHERE UPPER(LastName) = 'Smith'`
-   Строки начальные подстановочные знаки, такие как `WHERE LastName LIKE '%Smith'`, но не `WHERE LastName LIKE 'Smith%'`.

### <a name="steps-to-resolve"></a>Действия по устранению

1. Всегда объявлять переменные или параметры как намеченной цели [тип данных](../t-sql/data-types/data-types-transact-sql.md). 
  -   Для этого может потребоваться сравнение любой конструкции пользовательский код, хранящийся в базе данных (например, хранимые процедуры, определяемые пользователем функции и представления) с системными таблицами, которые содержат сведения о типах данных, используемых в базовых таблицах (таких как [sys.columns](../relational-databases/system-catalog-views/sys-columns-transact-sql.md)).
2. Если не удается, для перехода к предыдущей точке весь код, для той же цели, измените тип данных в таблице для соответствия любое объявление переменной или параметра.
3. Причина ожидания полезность следующие конструкции:
  -   Функции, используемого в качестве предикатов;
  -   Поиск с подстановочными знаками;
  -   Сложные выражения, основанные на один столбец данных — оценить необходимость вместо создания материализованные вычисляемые столбцы, которые могут быть проиндексированы;

> [!NOTE] 
> Все это можно сделать программным способом.

## <a name="TableValuedFunctions"></a>Использование функции с табличными значениями (vs нескольких инструкций встроенных)

**Применяется к:** внешнего платформы (например, Oracle, DB2, MySQL и Sybase) и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] миграции.

> [!NOTE]
> Для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] миграций и, если эта проблема существует в источнике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], миграция до новой версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] как-оно будет не удовлетворения потребностей этого сценария.

Функции с табличными значениями возвращают тип данных таблицы, который может быть альтернативой представлениям. То время как представления ограничены одной `SELECT` оператор, определяемые пользователем функции может содержать дополнительные инструкции, обеспечивающие дополнительные логика, чем возможна в представлениях.

> [!IMPORTANT] 
> Поскольку таблице результатов MSTVF (несколькими инструкциями функция с табличным значением) не создается во время компиляции, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] оптимизатор запросов полагается на эвристических правил, а не фактические статистику, чтобы определить строки оценок. Даже если индексы будут добавлены к базовым таблицам, это не должно помочь. Для MSTVFs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует фиксированный оценки 1 для ожидалось число строк, возвращенных MSTVF (начиная с [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] , фиксированный оценки составляет 100 строк).

### <a name="steps-to-resolve"></a>Действия по устранению
1.  Если Многооператорную является только одной инструкции, преобразование встроенной возвращающей табличное значение функции.

    ```tsql
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

    ```tsql
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

2.  Если более сложные, рассмотрите возможность использования промежуточные результаты хранятся в таблицах, оптимизированных для памяти или временные таблицы.

##  <a name="Additional_Reading"></a> Дополнительные материалы  
 [Рекомендации по хранилищу запросов](../relational-databases/performance/best-practice-with-the-query-store.md)  
[Таблицы, оптимизированные для памяти](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
[Определяемые пользователем функции](../relational-databases/user-defined-functions/user-defined-functions.md)  
[Табличных переменных, а строку оценки — часть 1](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/11/30/table-variables-and-row-estimations-part-1/)  
[Табличных переменных, а строку оценки — часть 2](https://blogs.msdn.microsoft.com/blogdoezequiel/2012/12/09/table-variables-and-row-estimations-part-2/)  
[Кэширование плана выполнения и повторного использования](../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse)

