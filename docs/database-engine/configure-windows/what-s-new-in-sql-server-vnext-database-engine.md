---
title: "Новые возможности в SQL Server&#160;vNext (ядро СУБД) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42f45b23-6509-45e8-8ee7-76a78f99a920
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Новые возможности в SQL Server&#160;vNext (ядро СУБД)
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

**Примечание**. В SQL Server vNext также входят функции, добавленные в пакеты обновления для SQL Server 2016. Описание этих элементов см. в статье [Новые возможности в SQL Server 2016 (ядро СУБД)](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md).

## <a name="sql-server-database-engine-ctp-13"></a>Ядро СУБД SQL Server (CTP 1.3)
- Повышена производительность косвенных контрольных точек.
- Добавлена поддержка групп доступности без кластеризации.
- Добавлен параметр групп доступности для фиксации минимальных реплик.
- Теперь группы доступности могут работать как в Windows, так и в Linux, что обеспечивает возможность кроссплатформенной миграции и тестирования.
- Добавлена поддержка политики хранения темпоральных таблиц.
- Реализовано новое динамическое административное представление SYS.DM_DB_STATS_HISTOGRAM.
- Добавлена поддержка сборки и перестройки некластеризованного индекса columnstore в Интернете.
- Реализованы пять новых динамических административных представлений для возврата данных о процессе Linux. Дополнительные сведения см. в статье [Динамические административные представления процессов Linux (Transact-SQL)](../../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- Добавлено представление [sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) для проверки статистики.

## <a name="sql-server-database-engine-ctp-12"></a>Ядро СУБД SQL Server (CTP 1.2)

- В помощнике по настройке ядра СУБД (DTA) выпущенном в составе SQL Server Management Studio версии 16.4, реализованы дополнительные возможности для анализа SQL Server 2016 и более поздних версий.    
   - Повышенная производительность. Дополнительные сведения см. в статье [Performance Improvements using Database Engine Tuning Advisor (DTA) recommendations](../../relational-databases/performance/performance-improvements-using-dta-recommendations.md) (Повышение производительности с помощью рекомендаций помощника по настройке ядра СУБД (DTA)).
   - Параметр `-fc`, с помощью которого можно разрешить рекомендации индексов columnstore. Дополнительные сведения см. в статьях [dta, программа](../../tools/dta/dta-utility.md) и [Columnstore index recommendations in Database Engine Tuning Advisor (DTA)](../../relational-databases/performance/columnstore-index-recommendations-in-database-engine-tuning-advisor-dta.md) (Рекомендации по индексам сolumnstore в помощнике по настройке ядра СУБД (DTA)).  
   - Параметр `-iq`, с помощью которого можно разрешить DTA просматривать рабочую нагрузку хранилища запросов. Дополнительные сведения см. в статье [Tuning Database Using Workload from Query Store](../../relational-databases/performance/tuning-database-using-workload-from-query-store.md) (Настройка базы данных с помощью рабочей нагрузки из хранилища запросов).
   

## <a name="sql-server-database-engine-ctp-11"></a>Ядро СУБД SQL Server (CTP 1.1)

<a name="InMemoryBulletsCtp11"/>
- Далее перечислены дополнительные улучшения оптимизированных для памяти таблиц и функций, скомпилированных в машинном коде, которые необходимы для работы в памяти. Примеры кода приведены в [этом тексте](#InMemory_CodeSamples).
    - Добавлена поддержка вычисляемых столбцов в таблицы, оптимизированные для работы памяти, включая индексы в вычисляемых столбцах.
    - Добавлена полная поддержка JSON-функций в модули, скомпилированные в машинном коде, и проверочные ограничения.
    - В модули, скомпилированные в машинном коде, добавлен оператор `CROSS APPLY`.   
- Добавлены новые строковые функции [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md), [TRANSLATE](../../t-sql/functions/translate-transact-sql.md) и [TRIM](../../t-sql/functions/trim-transact-sql.md).   
- Предложение `WITHIN GROUP` теперь поддерживается для функции [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md).
- Добавлены два новых семейства параметров сортировки для японского языка (Japanese_Bushu_Kakusu_140 и Japanese_XJIS_140). Для использования в японских параметрах сортировки добавлен параметр Variation-selector-sensitive (_VSS). Подробные сведения см. в разделе [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md).   
- Новые параметры группового доступа ([BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) и [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md)) обеспечивают доступ к данным непосредственно из CSV-файлов и из файлов в хранилище BLOB-объектов Azure посредством нового параметра `BLOB_STORAGE`, [EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).


## <a name="sql-server-database-engine-ctp-10"></a>Ядро СУБД SQL Server (CTP 1.0)

- Добавлен уровень совместимости базы данных **COMPATIBILITY_LEVEL** 140.   Клиенты, использующие его, получат доступ к самым новым возможностям языков и режимам оптимизатора запросов. Сюда входят изменения, вносимые корпорацией Майкрософт в каждую предварительную версию.
- Улучшен способ вычисления пороговых значений для обновления добавочной статистики (требуется режим совместимости&140;).
- Добавлен [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md).
- Мы добавили множество улучшений производительности и языков для таблиц в памяти:
    - `sp_spaceused` теперь поддерживается для таблиц в памяти.
    - `sp_rename` теперь поддерживается для собственных модулей.
    - Инструкции `CASE` теперь поддерживаются для собственных модулей.
    - Удалено ограничение в 8 индексов для таблиц в памяти.
    - `TOP (N) WITH TIES` теперь поддерживается в собственных модулях.
    - Значительно повышена скорость `ALTER TABLE` для таблиц в памяти в некоторых случаях.
    - Повтор транзакций для таблиц в памяти теперь выполняется параллельно. Это значительно сокращает время отработки отказа, а в некоторых случаях — и перезапусков.
    - Файлы контрольных точек в памяти теперь можно сохранить в службе хранилища Azure. Это предоставляет для MDF-файлов такие возможности, которые уже имеются для LDF-файлов.
- Кластеризованные индексы Columnstore теперь поддерживают столбцы типа LOB (nvarchar(max), varchar(max), varbinary(max)).
- Добавлена агрегатная функция [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md).  
- Новые разрешения: `DATABASE SCOPED CREDENTIAL` теперь является классом защищаемого объекта, поддерживающим разрешения `CONTROL`, `ALTER`, `REFERENCES`, `TAKE OWNERSHIP` и `VIEW DEFINITION`. `ADMINISTER DATABASE BULK OPERATIONS`, которой ограничен базой данных SQL, теперь отображается в `sys.fn_builtin_permissions`.   
- Добавлено динамическое административное представление [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md), предоставляющее сведения об операционной системе как для Windows, так и для Linux.   
- Роли базы данных создаются с помощью служб R Services для управления разрешениями, связанными с пакетами. Дополнительные сведения см. в разделе [Управление пакетами R для SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).
 
<a name="InMemory_CodeSamples"/> 
## <a name="code-samples-for-new-in-memory-enhancements"></a>Примеры кода для новых улучшений в памяти

В следующих подразделах приводятся примеры кода Transact-SQL, иллюстрирующие новые функции в памяти, перечисленные выше в этой статье.

Маркированный список функций в памяти для CTP 1.1 см. [здесь](#InMemoryBulletsCtp11).

#### <a name="computed-column-in-a-memory-optimized-table"></a>Вычисляемый столбец в таблице, оптимизированной для памяти

В этой инструкции CREATE TABLE отображены функции, речь о которых шла выше в части о CTP 1.1:

- проверочное ограничение JSON в столбце;
- новые вычисляемые столбцы;
- индекс в вычисляемом столбце.

```tsql
CREATE TABLE Product(
    ProductID  int            PRIMARY KEY NONCLUSTERED,
    Name       nvarchar(400)  NOT NULL,
    Price      float,

    Data      nvarchar(4000)  CONSTRAINT [Data contains JSON]  CHECK (ISJSON(Data)=1),

    MadeIn  AS CAST(JSON_VALUE(Data, '$.MadeIn')            as NVARCHAR(50)) PERSISTED,
    Cost    AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float       ),

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)
)
        WITH (MEMORY_OPTIMIZED=ON);
```

#### <a name="cross-apply-and-json-functions"></a>Оператор CROSS APPLY и функции JSON

Эта инструкция CREATE PROCEDURE для скомпилированной в собственном коде хранимой процедуры иллюстрирует следующие компоненты, которые упоминались ранее в части о CTP 1.1:

- оператор CROSS APPLY;
- функции JSON.

```tsql
CREATE OR ALTER PROCEDURE ProductList()
    WITH SCHEMABINDING, NATIVE_COMPILATION
as begin
    atomic with (transaction isolation level = snapshot,  language = N'English')

    SELECT
            ProductID, Name, Price, Tags,
            Data,
            JSON_VALUE(Data,'$.MadeIn') AS MadeIn,
            value
        FROM Product
        CROSS APPLY OPENJSON(Data, '$.SalesReasons')
        FOR JSON PATH
end;
```
