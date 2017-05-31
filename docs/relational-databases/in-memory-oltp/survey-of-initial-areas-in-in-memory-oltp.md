---
title: "Краткое руководство 1. Технологии выполнения OLTP в памяти для повышения производительности службы Transact-SQL | Документация Майкрософт"
ms.custom: 
ms.date: 12/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c25a164-547d-43c4-8484-6b5ee3cbaf3a
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82286b0d52ff37697ad9197b88c45935137a8dae
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="survey-of-initial-areas-in-in-memory-oltp"></a>Обзор начальных областей в выполняющейся в памяти OLTP
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
Эта статья предназначена для разработчиков, которым нужно быстро изучить основы повышения производительности In-Memory OLTP в базе данных Microsoft SQL Server и Azure SQL.  
  
В этой статье рассматриваются следующие аспекты In-Memory OLTP:  
  
- Краткое описание функций.  
- Примеры кода с использованием этих функций.  
  
  
SQL Server и база данных SQL незначительно отличаются друг от друга в плане поддержки технологий выполнения в памяти.  
  
  
Некоторые блогеры называют выполняющуюся в памяти OLTP *Hekaton*.  
  
  
<a name="benefits-of-in-memory-features-21a"></a>  
  
## <a name="benefits-of-in-memory-features"></a>Преимущества функций выполнения в памяти  
  
SQL Server позволяет использовать функции выполнения в памяти, позволяющие значительно повысить производительность систем многих приложений. В этом разделе приводятся основные рекомендации.  
  
  
### <a name="features-for-oltp-online-transactional-processing"></a>Функции OLTP (обработка транзакций в реальном времени).  
  
  
Максимальную пользу функции OLTP принесут системам, которым приходится обрабатывать большие объемы операций SQL INSERT.  
  
- Наши тесты показывают, что за счет применения функций выполнения в памяти скорость обработки можно увеличить в 5–20 раз.  
  
  
Превосходными кандидатами станут также системы, выполняющие большой объем вычислений в Transact-SQL.  
  
- Хранимая процедура, предназначенная для больших вычислений, может выполняться до 99 раз быстрее.  
  
  
Увеличение производительности в результате применения In-Memory OLTP демонстрируется в следующих статьях:  
  
- [Демонстрация. Улучшение производительности выполняемой в памяти OLTP](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md) . Маленькая демонстрация больших возможностей получения выигрыша в производительности.  
- [Пример базы данных для выполняемой в памяти OLTP](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md) . Демонстрация большего масштаба.  
  
  
  
### <a name="features-for-operational-analytics"></a>Функции оперативной аналитики  
  
Модуль аналитики в памяти ссылается на операции SQL SELECT, которые объединяют данные транзакций (обычно за счет добавления предложения GROUP BY). Тип индекса *columnstore* является основным для операционной аналитики.  
  
Вот два основных сценария:  
  
- В*пакетной операционной аналитике* используются процессы статистической обработки, которые выполняются либо по окончании рабочего дня, либо на дополнительном оборудовании, где имеются копии данных транзакций.  
  - К пакетной операционной аналитике относится также[хранилище данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-overview-what-is/) .  
- В*операционной аналитике в режиме реального времени* используются процессы статистической обработки, которые выполняются в рабочее время и на том оборудовании, где обрабатываются транзакции.  
  
  
В этой статье основное внимание уделяется OLTP, а не аналитике. Сведения о том, как индексы columnstore обеспечивают аналитику в SQL, см. в разделе:  
  
- [Начало работы с columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
- [Руководство по индексам columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)  
  
  
> [!NOTE]
> Двухминутный видеоролик о функциях выполнения в памяти доступен на странице [Базы данных SQL Azure — технологии выполнения в памяти](http://channel9.msdn.com/Blogs/Windows-Azure/Azure-SQL-Database-In-Memory-Technologies). Видеоролик выпущен в декабре 2015 г.  


### <a name="columnstore"></a>columnstore

Серия отличных публикаций, доступно и изящно разъясняющих принципы работы с индексами columnstore с различных точек зрения. Большая часть этой серии более подробно описывает концепцию операционной аналитики в реальном времени, которая поддерживается индексами columnstore.  Автор этих записей, опубликованных в блоге в марте 2016 г., — Сунил Агарвал (Sunil Agarwal), руководитель программы в корпорации Майкрософт.

#### <a name="real-time-operational-analytics"></a>операционной аналитике в режиме реального времени

1. [Операционная аналитика в реальном времени на основе технологии в памяти](https://blogs.technet.microsoft.com/dataplatforminsider/2015/12/09/real-time-operational-analytics-using-in-memory-technology/)
2. [Операционная аналитика в реальном времени. Обзор некластеризованного индекса columnstore (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-using-nonclustered-columnstore-index/)
3. [Операционная аналитика в реальном времени. Простой пример использования некластеризованного индекса columnstore (NCCI) в SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-simple-example-using-nonclustered-clustered-columnstore-index-ncci/)
4. [Операционная аналитика в реальном времени. Операции DML и некластеризованный индекс columnstore (NCCI) в SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/04/real-time-operational-analytics-dml-operations-and-nonclustered-columnstore-index-ncci-in-sql-server-2016/)
5. [Операционная аналитика в реальном времени. Некластеризованный индекс columnstore (NCCI) с фильтрацией](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-filtered-nonclustered-columnstore-index-ncci/)
6. [Операционная аналитика в реальном времени. Параметр "Задержка сжатия" для некластеризованного индекса columnstore (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-for-nonclustered-columnstore-index-ncci/)
7. [Операционная аналитика в реальном времени. Параметр "Задержка сжатия" с индексом NCCI и производительность](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-with-ncci-and-the-performance/)
8. [Операционная аналитика в реальном времени. Таблицы, оптимизированные для памяти, и индекс columnstore](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/real-time-operational-analytics-memory-optimized-table-and-columnstore-index/)

#### <a name="defragment-a-columnstore-index"></a>Дефрагментация индекса columnstore

1. [Дефрагментация индекса columnstore с помощью команды REORGANIZE](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)
2. [Политика слияния индекса columnstore для команды REORGANIZE](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)

#### <a name="bulk-importation-of-data"></a>Массовый импорт данных

1. [Кластеризованный индекс columnstore. Массовая загрузка](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2014/07/27/clustered-column-store-index-bulk-loading-the-data/)
2. [Кластеризованный индекс columnstore. Оптимизация загрузки данных — минимальное ведение журналов](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/10/clustered-columnstore-index-data-load-optimizations-minimal-logging/)
3. [Кластеризованный индекс columnstore. Оптимизация загрузки данных — параллельный массовый импорт](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/28/clustered-columnstore-index-parallel-bulk-import/)





<a name="features-on-in-memory-oltp-13b"></a>  
  
## <a name="features-of-in-memory-oltp"></a>Функции выполняемой в памяти OLTP  
  
Рассмотрим основные функции выполняемой в памяти OLTP.  
  
  
#### <a name="memory-optimized-tables"></a>Таблицы, оптимизированные для памяти  
  
Для того чтобы таблица существовала в активной памяти, а не на диске, в инструкции CREATE TABLE указывается определенное ключевое слово T-SQL — MEMORY_OPTIMIZED.  
  
  
[Оптимизированная для памяти таблица](../../relational-databases/in-memory-oltp/memory-optimized-tables.md) имеет одно представление для активной памяти и дополнительную копию на диске.  
  
- Копия на диске предназначена только для восстановления после завершения работы и перезапуска сервера или базы данных. Такая двойственность памяти и диска скрыта от вас и вашего кода.  
  
  
#### <a name="natively-compiled-modules"></a>Модули, скомпилированные в собственном коде  
  
Для создания процедуры, компилируемой в собственном коде, в инструкцию CREATE PROCEDURE добавляется определенное ключевое слово T-SQL — NATIVE_COMPILATION. При первом использовании процедуры, компилируемой в собственном коде с запуском цикла базы данных в сети, инструкции T-SQL компилируются в машинном коде. Инструкции T-SQL больше не выдерживают медленную интерпретацию каждой инструкции.  
  
- Уже достигнут результат применения компиляции в собственном коде в 1/100 от длительности выполнения интерпретируемого кода.  
  
  
Модули, скомпилированные в собственном коде, могут обращаться только к таблицам, оптимизированным для памяти. К таблицам на диске они обращаться не могут.  
  
Модули, компилируемые в собственном коде, бывают трех типов:  
  
- [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
- Скомпилированные в собственном коде определяемые пользователем функции (UDF), которые являются скалярными.  
- Скомпилированные в собственном коде триггеры.  
  
  
#### <a name="availability-in-azure-sql-database"></a>Доступность базы данных Azure SQL  
  
Выполняющаяся в памяти OLTP и индекс columnstore доступны в Базе данных SQL Azure. Дополнительные сведения см. в статье [Приступая к работе с In-Memory (в режиме предварительной версии) в базе данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory).
  
  
<a name="ensure-compatibility-level-gteq-130-99c"></a>  
  
## <a name="1-ensure-compatibility-level--130"></a>1. Обеспечение уровня совместимости не менее 130  
  
  
Данный раздел начинается с ряда нумерованных разделов, которые демонстрируют синтаксис Transact-SQL, который можно использовать для реализации функций выполнения OLTP в памяти.  
  
  
Во-первых, очень важно, чтобы для базы данных был задан уровень совместимости не менее 130. Код T-SQL, с помощью которого можно узнать текущий уровень совместимости, заданный для текущей базы данных.  
  
  
  
  
  
    SELECT d.compatibility_level  
        FROM sys.databases as d  
        WHERE d.name = Db_Name();  
  
  
  
  
Код T-SQL, с помощью которого можно изменить уровень при необходимости.  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET COMPATIBILITY_LEVEL = 130;  
  
  
  
  
<a name="elevate-to-snapshot-26n"></a>  
  
## <a name="2-elevate-to-snapshot"></a>2. Повышение до моментального снимка  
  
  
Если в транзакции участвует как дисковая таблица, так и таблица, оптимизированная для памяти, это называется *межконтейнерная транзакция*. В такой транзакции очень важно обеспечить, чтобы оптимизированная для памяти часть транзакции выполнялась на уровне изоляции транзакции, который называется "моментальный снимок".  
  
Чтобы гарантированно обеспечить этот уровень для оптимизированных для памяти таблиц в межконтейнерной транзакции, [измените параметры базы данных](../../t-sql/statements/alter-database-transact-sql-set-options.md), выполнив следующий запрос T-SQL.  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
  
  
  
  
<a name="create-an-optimized-filegroup-24r"></a>  
  
## <a name="3-create-an-optimized-filegroup"></a>3. Создание оптимизированной файловой группы  
  
  
В Microsoft SQL Server прежде чем создать таблицу, оптимизированную для памяти, необходимо сначала создать файловую группу, для которой сделано объявление CONTAINS MEMORY_OPTIMIZED_DATA. Файловая группа назначается вашей базе данных. Дополнительные сведения см. в разделе:  
  
- [Оптимизированная для памяти файловая группа](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)  
  
  
В базе данных SQL Azure не требуется и нет возможности создавать такую файловую группу.  

Следующий пример скрипта T-SQL включает базу данных для выполняющейся в памяти OLTP и настраивает все рекомендуемые параметры. Он подходит и для SQL Server, и для Базы данных SQL Azure: [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql).
  
  
<a name="create-a-memory-optimized-table-26y"></a>  
  
## <a name="4-create-a-memory-optimized-table"></a>4. Создание таблицы с оптимизацией для памяти  
  
  
  
  
Главным ключевым словом в Transact-SQL является ключевое слово MEMORY_OPTIMIZED.  
  
  
  
  
    CREATE TABLE dbo.SalesOrder  
    (  
        SalesOrderId   integer        not null  IDENTITY  
            PRIMARY KEY NONCLUSTERED,  
        CustomerId     integer        not null,  
        OrderDate      datetime       not null  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_AND_DATA);  
  
  
  
  
Инструкции Transact-SQL INSERT и SELECT для таблицы, оптимизированной для памяти, такие же, как для обычной таблицы.  
  
#### <a name="alter-table-for-memory-optimized-tables"></a>Инструкция ALTER TABLE для таблиц, оптимизированных для памяти  
  
С помощью инструкций ALTER TABLE...ADD/DROP можно добавлять и удалять столбцы из оптимизированной для памяти таблицы или индекса.  
  
- Инструкции DROP INDEX и CREATE INDEX не могут выполняться для таблиц, оптимизированных для памяти. Вместо них можно использовать ALTER TABLE... и ADD/DROP INDEX.  
- Дополнительные сведения см. в разделе [Изменение таблиц с оптимизацией для памяти](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md).  
  
  
#### <a name="plan-your-memory-optimized-tables-and-indexes"></a>Планирование оптимизированных для памяти таблиц и индексов  
  
  
- [Индексы для оптимизированных для памяти таблиц](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)  
- [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
  
<a name="create-a-natively-compiled-stored-procedure-native-proc-29u"></a>  
  
## <a name="5-create-a-natively-compiled-stored-procedure-native-proc"></a>5. Создание скомпилированной в собственном коде хранимой процедуры  
  
  
Главное ключевое слово NATIVE_COMPILATION.  
  
  
  
  
    CREATE PROCEDURE ncspRetrieveLatestSalesOrderIdForCustomerId  
        @_CustomerId   INT  
        WITH  
            NATIVE_COMPILATION,  
            SCHEMABINDING  
    AS  
    BEGIN ATOMIC  
        WITH  
            (TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
            LANGUAGE = N'us_english')  
      
        DECLARE @SalesOrderId int, @OrderDate datetime;  
      
        SELECT TOP 1  
                @SalesOrderId = s.SalesOrderId,  
                @OrderDate    = s.OrderDate  
            FROM dbo.SalesOrder AS s  
            WHERE s.CustomerId = @_CustomerId  
            ORDER BY s.OrderDate DESC;  
      
        RETURN @SalesOrderId;  
    END;  
  
  
  
  
Ключевое слово SCHEMABINDING означает, что таблицы, на которые есть ссылки в скомпилированной в собственном коде хранимой процедуре, нельзя удалить без удаления самой процедуры. Дополнительные сведения см. в разделе [Создание хранимых процедур, скомпилированных в собственном коде](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md).  
  
  
<a name="execute-the-native-proc-31e"></a>  
  
## <a name="6-execute-the-native-proc"></a>6. Выполнение скомпилированной в собственном коде хранимой процедуры  
  
  
Заполните таблицу из двух строк данных.  
  
  
  
  
    INSERT into dbo.SalesOrder  
            ( CustomerId, OrderDate )  
        VALUES  
            ( 42, '2013-01-13 03:35:59' ),  
            ( 42, '2015-01-15 15:35:59' );  
  
  
  
  
Затем выполните инструкцию EXECUTE для скомпилированной в собственном коде хранимой процедуры.  
  
  
  
  
    DECLARE @LatestSalesOrderId int, @mesg nvarchar(128);  
      
    EXECUTE @LatestSalesOrderId =  
        ncspRetrieveLatestSalesOrderIdForCustomerId 42;  
      
    SET @mesg = CONCAT(@LatestSalesOrderId,  
        ' = Latest SalesOrderId, for CustomerId = ', 42);  
    PRINT @mesg;  
      
    -- Here is the actual PRINT output:  
    -- 2 = Latest SalesOrderId, for CustomerId = 42  
  
  
  
  
<a name="guide-to-the-documentation-and-next-steps-32w"></a>  
  
### <a name="guide-to-the-documentation-and-next-steps"></a>Руководство по документации и дальнейшие действия  
  
  
Описанные выше простые примеры создают основу для изучения более сложных функций выполнения OLTP в памяти. В следующих разделах описаны особенности, которые следует знать, и дополнительные сведения, касающиеся каждой из них.  
  
  
  
<a name="how-do-in-memory-oltp-features-work-so-much-faster-33v"></a>  
  
## <a name="how-in-memory-oltp-features-work-so-much-faster"></a>Почему функции выполнения OLTP в памяти работают намного быстрее?  
  
  
В следующих подразделах кратко описано, как функции выполнения OLTP в памяти реализуют улучшение производительности.  
  
  
<a name="how-do-memory-optimized-tables-perform-faster-34q"></a>  
  
### <a name="how-memory-optimized-tables-perform-faster"></a>Почему оптимизированные для памяти таблицы работают быстрее?  
  
  
**Двойное представление.** Таблица, оптимизированная для памяти, имеет два представления: одно представление в активной памяти, а другое — на жестком диске. Все транзакции фиксируются в обоих представлениях таблицы. Транзакции работают с более быстрым представлением в активной памяти. Оптимизированные для памяти таблицы используют преимущество более высокой скорости работы активной памяти по сравнению с диском. Кроме того, более высокое быстродействие активной памяти позволяет реализовать более сложные структуры таблицы, оптимизированные по скорости. Эта структура не имеет разбиения на страницы, поэтому она позволяет избежать издержек и конфликтов из-за кратковременных блокировок и спин-блокировок.  
  
  
**Без блокировок.** Таблица, оптимизированная для памяти, базируется на *оптимистичном* подходе к решению конкурирующих задач сохранения целостности данных и обеспечения параллелизма и высокой пропускной способности. Во время транзакции таблица не устанавливает блокировок ни на какие версии измененных строк данных. Это может значительно снизить вероятность возникновения конфликтов в некоторых системах большого объема.  
  
  
**Версии строк.** Вместо установки блокировки оптимизированная для памяти таблица добавляет новую версию измененной строки в саму таблицу, а не в базу данных tempdb. Исходная строка сохраняется до фиксации транзакции. Во время транзакции другие процессы могут читать исходную версию строки.  
  
- При создании нескольких версий строки для таблицы на диске версии строк временно хранятся в базе данных tempdb.  
  
  
**Меньше затрат на ведения журнала.** Предыдущая и последующая версии измененных строк хранятся в таблице, оптимизированной для памяти. В этих двух строках содержится значительная часть информации, которая обычно записывается в файл журнала. Это позволяет системе записывать в журнал меньше информации и делать это реже. И тем не менее целостность транзакций гарантируется.  
  
  
<a name="how-do-native-procs-perform-faster-35x"></a>  
  
### <a name="how-native-procs-perform-faster"></a>Почему скомпилированные в собственном коде хранимые процедуры выполняются быстрее?  
  
Преобразование обычных интерпретируемых хранимых процедур в скомпилированные в собственном коде процедуры позволяет значительно уменьшить количество инструкций, выполняемых во время выполнения.  
  
  
<a name="trade-offs-of-in-memory-features-36j"></a>  
  
## <a name="trade-offs-of-in-memory-features"></a>Преимущества и недостатки функций выполнения в памяти  
  
  
Как это часто бывает в компьютерных технологиях, прирост производительности, получаемый за счет применения функции выполнения в памяти, является компромиссом. Новые функции дают преимущества, выигрыш от которых перевешивает издержки, связанные с реализацией этих функций. Подробные сведения о компромиссах вы найдете в следующих статьях:

- [Планирование освоения возможностей выполняющейся в памяти OLTP в SQL Server](../../relational-databases/in-memory-oltp/plan-your-adoption-of-in-memory-oltp-features-in-sql-server.md)

В остальной части этого раздела перечислены некоторые важные аспекты планирования и компромиссов.
  
<a name="trade-offs-of-memory-optimized-tables-37d"></a>  
  
### <a name="trade-offs-of-memory-optimized-tables"></a>Преимущества и недостатки таблиц с оптимизацией для памяти  
  
  
**Оценка памяти.** Необходимо оценить объем активной памяти, который оптимизированная для памяти таблица будет занимать. Ваш компьютер должен обладать памятью достаточной емкости для размещения таблицы, оптимизированной для памяти. Дополнительные сведения см. в разделе:  
  
- [Мониторинг и устранение неполадок с использованием памяти](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)  
- [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)  
- [Размер строк и таблицы для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
  
**Секционирование больших таблиц.** Одним из способов обеспечить потребность в большом объеме активной памяти является разбиение большой таблицы на части. Одна часть, которая в памяти, будет хранить *новые* строки данных, а другая часть, которая на диске, будет хранить *старые* строки (например, заказы на продажу, полностью отгруженные и завершенные). Разработка секционирования и его реализация выполняются вручную. См.  
  
- [Секционирование уровня приложения](../../relational-databases/in-memory-oltp/application-level-partitioning.md)  
- [Модель приложения для секционирования таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/application-pattern-for-partitioning-memory-optimized-tables.md)  
  
  
<a name="trade-offs-of-native-procs-38p"></a>  
  
### <a name="trade-offs-of-native-procs"></a>Преимущества и недостатки скомпилированных в собственном коде хранимых процедур  
  
  
- Скомпилированная в собственном коде хранимая процедура не может обращаться к дисковой таблице. Скомпилированная в собственном коде хранимая процедура может обращаться только к таблицам, оптимизированным для памяти.  
- Когда скомпилированная в собственном коде хранимая процедура запускается в первый раз после того, как сервер или база данных возвращается в оперативный режим, процедура должна быть перекомпилирована один раз. Это приводит к задержке перед началом выполнения процедуры.  
  
  
<a name="advanced-considerations-for-memory-optimized-tables-39n"></a>  
  
## <a name="advanced-considerations-for-memory-optimized-tables"></a>Дополнительные соображения по оптимизированным для памяти таблицам  
  
  
[Индексы для таблиц, оптимизированные для памяти](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md) отличаются от индексов в обычных таблицах на диске.  
  
- [Хэш-индексы](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) доступны только в таблицах, оптимизированных для памяти.  
  
  
Необходимо убедиться, что для планируемой оптимизированной для памяти таблицы и ее индексов будет достаточно места в активной памяти. См.  
  
- [Создание и управление хранилищем для оптимизированных для памяти объектов](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
Объявить таблицу, оптимизированную для памяти, позволяет параметр DURABILITY = SCHEMA_ONLY:  
  
- Эта инструкция указывает системе, что необходимо уничтожить все данные из таблицы, оптимизированной для памяти, при переводе базы данных в автономный режим. Сохраняется только определение таблицы.  
- Когда база данных переходит в оперативный режим, оптимизированная для памяти таблица загружается обратно в активную память (без данных).  
- Если речь идет о множестве тысяч строк, таблицы SCHEMA_ONLY могут служить [альтернативой таблицам #temporary](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md) в базе данных tempdb.  
  
  
Табличные переменные также можно объявлять как оптимизированные для памяти. См.  
  
- [Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)  
  
  
  
<a name="advanced-considerations-for-natively-compiled-modules-40k"></a>  
  
## <a name="advanced-considerations-for-natively-compiled-modules"></a>Дополнительные соображения по скомпилированным в собственном коде модулям  
  
  
Ниже приведены типы скомпилированных в собственном коде модулей, доступные через Transact-SQL.  
  
- Хранимые процедуры, скомпилированные в собственном коде.  
- Скомпилированные в собственном коде [скалярные определяемые пользователем функции](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
- Скомпилированные в собственном коде триггеры.  
  - В таблицах, оптимизированных для памяти, разрешаются только триггеры, скомпилированные в собственном коде.  
- Скомпилированные в собственном коде [функции с табличными значениями](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md).  
  - [Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)  
  
  
Скомпилированная определяемая пользователем функция выполняется быстрее, чем интерпретированная определяемая пользователем функция. При работе с определяемыми пользователем функциями необходимо учитывать следующее:  
  
- Если инструкция T-SQL SELECT использует определяемую пользователем функцию, эта функция всегда вызывается один раз для каждой возвращаемой строки.  
  - Определяемые пользователем функции никогда не запускаются как встроенные, они всегда вызываются.  
  - Разница между этими вариантами менее важна, чем издержки, связанные с повторяющимися вызовами, присущие всем пользовательским функциям.  
  - Затраты на вызовы определяемых пользователем функций часто допустимы на практике.  
  
Данные тестов и сведения о производительности определяемых пользователем функций в собственном коде см. в следующих статьях:  
  
  - [Смягчение последствий RBAR с использованием скомпилированных в собственном коде определяемых пользователем функций в SQL Server 2016](https://blogs.msdn.microsoft.com/sqlcat/2016/02/17/soften-the-rbar-impact-with-native-compiled-udfs-in-sql-server-2016/)  
  - [Прекрасная публикация в блоге, написанная Гейлом Шо (Gail Shaw)](http://sqlinthewild.co.za/index.php/2016/01/12/natively-compiled-user-defined-functions/), выпущенная в январе 2016 г.  
  
  
<a name="documentation-guide-for-memory-optimized-tables-41z"></a>  
  
## <a name="documentation-guide-for-memory-optimized-tables"></a>Руководство по документации по оптимизированным для памяти таблицам  
  
  
Ниже приведены ссылки на другие статьи, посвященные некоторым соображениям, касающимся оптимизированных для памяти таблиц.  
  
- [Миграция в выполняющуюся в памяти OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  - [Определение, должна ли таблица или хранимая процедура быть перенесена в выполняющуюся в памяти OLTP](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  - Отчет об анализе производительности транзакции в SQL Server Management Studio позволяет оценить, улучшится ли производительность приложения в базе данных с помощью выполняемой в памяти OLTP.  
  - Инструкции по перемещению таблицы из дисковой базы данных в выполняемую в памяти OLTP см. в [Помощнике по оптимизации памяти](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md) .   
- [Резервное копирование и восстановление оптимизированных для памяти таблиц](http://msdn.microsoft.com/library/3f083347-0fbb-4b19-a6fb-1818d545e281)  
  - Объем хранилища, используемый оптимизированными для памяти таблицами, может быть значительно больше, чем размер таблиц в памяти. Это оказывает влияние на размер резервной копии базы данных.  
- [Транзакции с таблицами, оптимизированными для памяти](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)  
  - Содержит сведения о логике повторных попыток в T-SQL для транзакций в таблицах, оптимизированных для памяти.  
- [Поддержка Transact-SQL для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  - Поддерживаемые и неподдерживаемые инструкции T-SQL и типы данных для оптимизированной для памяти таблицы и скомпилированных в собственном коде хранимых процедур.  
- [Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)(Обсуждаются дополнительные расширенные рассмотрения).  
  
  
  
<a name="documentation-guide-for-native-procs-42b"></a>  
  
## <a name="documentation-guide-for-native-procs"></a>Руководство по документации по скомпилированным в собственном коде хранимым процедурам  
  
  
  
<a name="related-links-43f"></a>  
  
## <a name="related-links"></a>Связанные ссылки  
  
- Первая статья: [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
Следующие статьи содержат примеры кода и демонстрируют повышение производительности за счет применения In-Memory OLTP:  
  
- [Демонстрация. Улучшение производительности выполняемой в памяти OLTP](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md) . Маленькая демонстрация больших возможностей получения выигрыша в производительности.  
- [Пример базы данных для выполняемой в памяти OLTP](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md) . Демонстрация большего масштаба.  
  
  
  
\<!--  
  
e1328615-6b59-4473-8a8d-4f360f73187d, dn817827.aspx, "Начало работы с Columnstore для получения операционной аналитики в реальном времени"  
  
f98af4a5-4523-43b1-be8d-1b03c3217839, gg492088.aspx, "Руководство по индексам columnstore"  
  
14dddf81-b502-49dc-a6b6-d18b1ae32d2b, dn133165.aspx, "Таблицы, оптимизированные для памяти"  
  
d5ed432c-10c5-4e4f-883c-ef4d1fa32366, dn133184.aspx, "Хранимая процедура, скомпилированная в собственном коде"  
  
14106cc9-816b-493a-bcb9-fe66a1cd4630, dn639109.aspx, "Оптимизированная для памяти файловая группа"  
  
f222b1d5-d2fa-4269-8294-4575a0e78636, dn465873.aspx, "Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов"  
  
86805eeb-6972-45d8-8369-16ededc535c7, dn511012.aspx, "Индексы для оптимизированных для памяти таблиц"  
  
16ef63a4-367a-46ac-917d-9eebc81ab29b, dn133166.aspx, "Рекомендации по использованию индексов в таблицах, оптимизированных для памяти"  
  
e3f8009c-319d-4d7b-8993-828e55ccde11, dn246937.aspx, "Конструкции языка Transact-SQL, неподдерживаемые в выполняющейся в памяти OLTP"  
  
2cd07d26-a1f1-4034-8d6f-f196eed1b763, dn133169.aspx, "Транзакции в таблицах, оптимизированных для памяти"  
Примечание. См. mt668425.aspx Behaviors and Guidelines for Transactions with Memory-Optimized Tables (Поведение и рекомендации по транзакциям в таблицах, оптимизированных для памяти), скоро статья будет заменена.  
f2a35c37-4449-49ee-8bba-928028f1de66, dn169141.aspx, "Рекомендации для логики повторного выполнения транзакций для таблиц, оптимизированных для памяти"  
  
7a458b9c-3423-4e24-823d-99573544c877, dn465869.aspx, "Мониторинг и устранение неполадок с использованием памяти"  
  
5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8, dn282389.aspx, "Оценка требований к объему памяти для таблиц, оптимизированных для памяти"  
  
b0a248a4-4488-4cc8-89fc-46906a8c24a1, dn205318.aspx, "Размер строк и таблицы для таблиц, оптимизированных для памяти"  
  
162d1392-39d2-4436-a4d9-ee5c47864c5a, dn296452.aspx, "Секционирование уровня приложения"  
  
3f867763-a8e6-413a-b015-20e9672cc4d1, dn133171.aspx, "Модель приложения для секционирования таблиц, оптимизированных для памяти"  
  
86805eeb-6972-45d8-8369-16ededc535c7, dn511012.aspx, "Индексы для оптимизированных для памяти таблиц"  
  
d82f21fa-6be1-4723-a72e-f2526fafd1b6, dn465872.aspx, Managing Memory for Memory-Optimized OLTP (Управление памятью для OLTP, оптимизированной для памяти)  
  
622aabe6-95c7-42cc-8768-ac2e679c5089, dn133174.aspx, "Создание и управление хранилищем для оптимизированных для памяти объектов"  
  
bd102e95-53e2-4da6-9b8b-0e4f02d286d3, dn535766.aspx, "Оптимизированные для памяти табличные переменные", "табличная переменная таблицы, оптимизированной для памяти"  
Устаревшее. Вместо этого см. 38512a22-7e63-436f-9c13-dde7cf5c2202, mt718711.aspx, "Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти"  
  
  
f0d5dd10-73fd-4E05-9177-07f56552bdf7, ms191320.aspx, "Создание определяемых пользователем функций (ядро СУБД)", "функции с табличным значением"  
  
d2546e40-fdfc-414b-8196-76ed1f124bf5, dn935012.aspx, "Скалярные определяемые пользователем функции для выполняющейся в памяти OLTP", "скалярные определяемые пользователем функции"  
  
405cdac5-a0d4-47a4-9180-82876b773b82, dn247639.aspx, "Миграция в выполняющуюся в памяти OLTP"  
  
3f083347-0fbb-4b19-a6fb-1818d545e281, dn624160.aspx, "Резервное копирование и восстановление оптимизированных для памяти таблиц"  
  
690b70b7-5be1-4014-af97-54e531997839 dn269114.aspx, "Изменение таблиц с оптимизацией для памяти"  
  
  
b1cc7c30-1747-4c21-88ac-e95a5e58baac, dn133080.aspx, "Новые и обновленные свойства, системные представления, хранимые процедуры, типы ожидания и динамические административные представления для выполняющейся в памяти OLTP"  
, и делает это по-другому. . . . , и делает это по-другому.  
См. также статью "Поддержка Transact-SQL для выполняющейся в памяти OLTP".  
  
  
c1ef96f1-290d-4952-8369-2f49f27afee2, dn205133.aspx, "Определение, должна ли таблица или хранимая процедура быть перенесена в выполняющуюся в памяти OLTP"  
  
181989c2-9636-415a-bd1d-d304fc920b8a, dn284308.aspx, "Помощник по оптимизации памяти"  
  
55548cb2-77a8-4953-8b5a-f2778a4f13cf, dn452282.aspx, "Отслеживание производительности скомпилированных в собственном коде хранимых процедур"  
  
d3898a47-2985-4a08-bc70-fd8331a01b7b, dn358355.aspx, "Помощник по собственной компиляции"  
  
f43faad4-2182-4b43-a76a-0e3b405816d1, dn296678.aspx, "Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде"  
  
e1d03d74-2572-4a55-afd6-7edf0bc28bdb, dn133186.aspx, "Выполняющаяся в памяти OLTP (оптимизация в памяти)"  
  
c6def45d-D2D4-4d24-8068-fab4cd94d8cc, dn530757.aspx, "Демонстрация. Улучшение производительности выполняющейся в памяти OLTP"  
  
405cdac5-a0d4-47a4-9180-82876b773b82, dn247639.aspx, "Миграция в выполняющуюся в памяти OLTP"  
  
f76fbd84-df59-4404-806b-8ecb4497c9cc, bb522682.aspx, "Параметры ALTER DATABASE SET (Transact-SQL)"  
  
e6b34010-cf62-4f65-bbdf-117f291cde7b, dn452286.aspx, "Создание хранимых процедур, скомпилированных в собственном коде"  
  
df347f9b-b950-4e3a-85f4-b9f21735eae3, mt465764.aspx, "Пример базы данных для выполняющейся в памяти OLTP"  
  
38512a22-7e63-436f-9c13-dde7cf5c2202, mt718711.aspx, "Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти"  
  
38512a22-7e63-436f-9c13-dde7cf5c2202, mt718711.aspx, "Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти"  
  
  
  
  
H1 # Краткое руководство 1. Технологии выполнения OLTP в памяти для повышения производительности рабочих нагрузок по транзакциям  
{1c25a164-547d-43c4-8484-6b5ee3cbaf3a} в верхнем регистре  
mt718711.aspx на сайте MSDN  
  
GeneMi, 07.05.2016, 00:07  
-->  
  
  
  


