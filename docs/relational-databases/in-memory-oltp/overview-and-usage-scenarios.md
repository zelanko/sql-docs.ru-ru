---
title: Общие сведения и сценарии использования | Документация Майкрософт
ms.custom: ''
ms.date: 04/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 62c964c5-eae4-4cf1-9024-d5a19adbd652
caps.latest.revision: 5
author: jodebrui
ms.author: jodebrui
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eea70d193fb5f75249c59d6e1af8d9db904a085f
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43097055"
---
# <a name="overview-and-usage-scenarios"></a>Общие сведения и сценарии использования
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Выполняющаяся в памяти OLTP — первоклассная технология, доступная в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и предназначенная для оптимизации производительности обработки транзакций, приема и загрузки данных, а также сценариев с временными данными. В этой статье содержатся общие сведения о выполняющейся в памяти OLTP и описываются сценарии использования этой технологии. Эти сведения помогут вам выяснить, подходит ли вашему приложению эта технология. В конце этой статьи приведен пример, демонстрирующий объекты выполняющейся в памяти OLTP, ссылка на демонстрацию производительности, а также ссылки на ресурсы, которые можно использовать в следующих шагах.

В этой статье описывается технология выполняющейся в памяти OLTP, используемая для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. В следующей записи блога подробно рассматриваются вопросы производительности и преимущества использования ресурсов в [!INCLUDE[ssSDS](../../includes/sssds-md.md)]: 
- [Выполняющаяся в памяти OLTP в базе данных Azure SQL](https://azure.microsoft.com/blog/in-memory-oltp-in-azure-sql-database/)

## <a name="in-memory-oltp-overview"></a>Общие сведения о выполняющейся в памяти OLTP

Выполняющаяся в памяти OLTP может существенно повысить производительность соответствующих рабочих нагрузок. Одному клиенту, bwin, удалось [повысить производительность до 1,2 млн запросов в секунду](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/), используя выполняющуюся в памяти OLTP в одной виртуальной машине с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Другой клиент, Quorum, удвоил рабочую нагрузку и [сократил использование ресурсов на 70 %](https://customers.microsoft.com/en-US/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database), применяя выполняющуюся в памяти OLTP в [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. В некоторых случаях производительность у клиентов повышалась в 30 раз, но каков будет ваш прирост, зависит от типа и величины рабочей нагрузки.

Что же влияет на прирост производительности? По сути, выполняющаяся в памяти OLTP позволяет повысить производительность обработки транзакций путем оптимизации доступа к данным и выполнения транзакций, а также за счет устранения конфликтов блокировок и кратковременных блокировок между параллельно выполняемыми транзакциями: производительность повышается не из-за того, что данные находятся в памяти, а из-за оптимизации этих данных. Алгоритмы хранения и обработки данных, а также доступа к ним были полностью изменены с учетом последних улучшений в вычислениях в памяти и вычислениях с высоким уровнем параллелизма.

Теперь при сбое данные не будут утеряны только из-за того, что они находятся в памяти. По умолчанию все транзакции являются полностью устойчивыми. Таким образом обеспечивается такой же уровень надежности, что и для любой таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В ходе фиксации транзакции все изменения записываются в журнал транзакций на диске. В случае сбоя в любое время после фиксации транзакции данные не будут утеряны при переходе базы данных в оперативный режим. Кроме того, выполняющаяся в памяти OLTP поддерживает все возможности обеспечения высокой доступности и аварийного восстановления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], такие как AlwaysOn, резервное копирование, восстановление и т. д.

Чтобы использовать выполняющуюся в памяти OLTP в базе данных, следует применить один или несколько из следующих типов объектов:

- *Таблицы, оптимизированные для памяти* , используются для хранения пользовательских данных. Объявить таблицу в качестве оптимизированной для памяти можно при ее создании.
- *Неустойчивые таблицы* используются для временных данных, для кэширования или промежуточных результирующих наборов (вместо традиционных временных таблиц). Неустойчивая таблица — это таблица, оптимизированная для памяти и объявленная с помощью DURABILITY=SCHEMA_ONLY. Это означает, что при изменениях в этих таблицах не выполняются операции ввода-вывода. Таким образом можно избежать использования ресурсов ввода-вывода журнала в случаях, когда устойчивость не важна.
- *Табличные типы, оптимизированные для памяти* , используются для возвращающих табличные значения параметров, а также для промежуточных результирующих наборов в хранимых процедурах. Их можно использовать вместо традиционных табличных типов. Табличные переменные и возвращающие табличные значения параметры, которые объявляются с помощью табличных типов, оптимизированных для памяти, получают преимущества неустойчивых таблиц, оптимизированных для памяти: эффективный доступ к данным и отсутствие операций ввода-вывода.
- *Скомпилированные в собственном коде модули T-SQL* позволяют еще больше сократить продолжительность выполнения отдельной транзакции за счет сокращения циклов ЦП, необходимых для обработки операций. Объявить модуль Transact-SQL в качестве скомпилированного в собственном коде можно при его создании. Сейчас скомпилированными в машинном коде могут быть следующие модули T-SQL: хранимые процедуры, триггеры и скалярные определяемые пользователем функции.

Выполняющаяся в памяти OLTP встроена в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Так как эти объекты похожи на свои традиционные аналоги, чтобы повысить производительность, зачастую достаточно лишь немного изменить базу данных и приложение. Кроме того, в одной базе данных можно разместить как оптимизированные для памяти, так и традиционные дисковые таблицы, а также выполнять запросы и к тем, и к другим. Скрипт Transact-SQL, демонстрирующий пример каждого из этих типов объектов, представлен в конце этой статьи.

## <a name="usage-scenarios-for-in-memory-oltp"></a>Сценарии использования выполняющейся в памяти OLTP

Выполняющаяся в памяти OLTP — это не волшебное средство для повышения производительности. Она подходит не для всех рабочих нагрузок. Например, таблицы, оптимизированные для памяти, не снижают загрузку ЦП, если в большинстве запросов выполняется агрегирование в широких диапазонах данных. В этом сценарии могут помочь индексы columnstore.

Ниже приведен список сценариев и шаблонов приложений, в которых клиенты успешно использовали выполняющуюся в памяти OLTP.

### <a name="high-throughput-and-low-latency-transaction-processing"></a>Обработка транзакций с высокой пропускной способностью и низкой задержкой

Именно для этого сценария мы создали выполняющуюся в памяти OLTP: поддержка больших объемов транзакций и обеспечение постоянно низкой задержки для отдельных транзакций.

Общие сценарии рабочей нагрузки включают торговлю финансовыми инструментами, ставки на спортивные мероприятия, мобильные игры и доставку рекламных сообщений. Еще один распространенный шаблон — "каталог", который часто считывается и (или) обновляется. В качестве примера можно привести большие файлы, распределенные по узлам в кластере. Вы помещаете в каталог расположение каждого сегмента каждого файла в таблице, оптимизированной для памяти.

#### <a name="implementation-considerations"></a>Рекомендации по реализации

Используйте таблицы, оптимизированные для памяти, для основных таблиц транзакций, т. е. для таблиц с транзакциями, которые оказывают самое большое влияние на производительность. Используйте скомпилированные в собственном коде хранимые процедуры для оптимизации выполнения логики, связанной с бизнес-транзакциями. Чем больше логики можно отправить в хранимые процедуры в базе данных, тем больше преимуществ вы получите от выполняющейся в памяти OLTP.

Чтобы приступить к работе в имеющемся приложении, сделайте следующее:
1. Используйте [отчет анализа производительности транзакций](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) , чтобы выявить объекты, которые требуется перенести. 
2. Используйте помощников по [оптимизации памяти](memory-optimization-advisor.md) и [компиляции в собственном коде](native-compilation-advisor.md) для миграции.

#### <a name="customer-case-studies"></a>Клиентские сценарии

- Компания CMC Markets использует выполняющуюся в памяти OLTP в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], чтобы обеспечить постоянно низкую задержку: [Because a second is too long to wait, this financial services firm is updating its trading software now](https://customers.microsoft.com/en-us/story/because-a-second-is-too-long-to-wait-this-financial-services-firm-is-updating-its-trading-software) (Секунда — это слишком долго. Финансовая организация обновила программное обеспечение для торговли).
- Компания Derivco использует выполняющуюся в памяти OLTP в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] для поддержки возросшего показателя пропускной способности и обработки пиков рабочей нагрузки: [When an online gaming company doesn’t want to risk its future, it bets on [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]](https://customers.microsoft.com/en-us/story/when-an-online-gaming-company-doesnt-want-to-risk-its-future-it-bets-on-sql-server-2016) (Компания по разработке сетевых игр сделала ставку на SQL Server 2016, чтобы не рисковать собственным будущим).


### <a name="data-ingestion-including-iot-internet-of-things"></a>Прием данных из разных источников, включая Интернет вещей

Выполняющаяся в памяти OLTP удобна, если необходимо принимать большие объемы данных одновременно из разных источников. Зачастую лучше всего принимать данные в базу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в отличие от других мест назначения, ускоряет выполнение запросов к данным и позволяет получить ценные сведения в режиме реального времени.

Распространенные шаблоны применения: 
-  прием показаний и событий датчиков для вывода уведомлений и исторического анализа; 
-  управление пакетными обновлениями из нескольких источников и максимальное уменьшение влияния на рабочую нагрузку параллельного чтения.

#### <a name="implementation-considerations"></a>Рекомендации по реализации

Используйте таблицу, оптимизированную для памяти, чтобы принимать данные. Если прием состоит в основном из вставок (а не обновлений), а объем данных, хранимых в выполняющейся в памяти OLTP, играет важную роль, примените одну из следующих рекомендаций:

- Используйте задание для регулярной разгрузки пакетов данных в дисковую таблицу с [кластеризованным индексом columnstore](../indexes/columnstore-indexes-overview.md)с помощью задания, выполняющего операции `INSERT INTO <disk-based table> SELECT FROM <memory-optimized table>`.
- Используйте [временную таблицу, оптимизированную для памяти](../tables/system-versioned-temporal-tables-with-memory-optimized-tables.md) , для управления статистическими данными. В этом режиме статистические данные находятся на диске, а перемещением данных управляет система.

Репозиторий примеров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит приложение интеллектуальной сетки, которое использует временную таблицу, оптимизированную для памяти, табличный тип, оптимизированный для памяти, и скомпилированную в машинный код хранимую процедуру для повышения скорости приема данных, а также управляет объемом хранилища выполняющейся в памяти OLTP для данных датчиков: 

 - [smart-grid-release](https://github.com/Microsoft/sql-server-samples/releases/tag/iot-smart-grid-v1.0) 
 - [smart-grid-source-code](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/iot-smart-grid)
 
#### <a name="customer-case-studies"></a>Клиентские сценарии

- [Quorum doubles key database’s workload while lowering utilization by 70% by leveraging In-Memory OLTP in Azure SQL Database](http://customers.microsoft.com/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database)
- Компания EdgeNet повысила производительность загрузки пакетных данных и избавилась от необходимости поддержки кэша среднего уровня благодаря использованию выполняющейся в памяти OLTP в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]: [Data Services Firm Gains Real-Time Access to Product Data with In-Memory Technology](https://customers.microsoft.com/en-us/story/data-services-firm-gains-real-time-access-to-product-d) (Компания по разработке служб данных получила доступ к данным о продуктах в реальном времени, используя технологию в памяти).
- Больнице Beth Israel Deaconess Medical Center удалось значительно повысить скорость приема данных из контроллеров домена и обрабатывать пики рабочей нагрузки, используя выполняющуюся в памяти OLTP в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]: [https://customers.microsoft.com/en-us/story/strengthening-data-security-and-creating-more-time-for]

### <a name="caching-and-session-state"></a>Кэширование и состояние сеанса

Благодаря технологии выполняющейся в памяти OLTP среда SQL весьма привлекательна для поддержки состояния сеанса (например, для приложения ASP.NET) и кэширования.

Один из эффективных сценариев — использование выполняющейся в памяти OLTP для поддержки состояния сеанса ASP.NET. Работая с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], одним клиентам почти удалось добиться выполнения 1,2 млн запросов в секунду. В то же время они начали использовать выполняющуюся в памяти OLTP для кэширования всех приложений среднего уровня на предприятии. Подробные сведения: [How bwin is using [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/) (Как компания bwin добилась небывалой производительности и масштаба, используя выполняющуюся в памяти OLTP в SQL Server 2016)

#### <a name="implementation-considerations"></a>Рекомендации по реализации

Неустойчивые таблицы, оптимизированные для памяти, можно использовать в качестве простого хранилища пар "ключ —значение", сохраняя большие двоичные объекты в столбцах varbinary(max). Кроме того, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] можно внедрить полуструктурированный кэш с [поддержкой JSON](https://azure.microsoft.com/blog/json-support-is-generally-available-in-azure-sql-database/). Наконец, можно создать полностью реляционный кэш в неустойчивых таблицах с полной реляционной схемой, включая различные типы и ограничения данных.

Приступите к работе с оптимизированным для памяти состоянием сеанса ASP.NET, используя скрипты, опубликованные в GitHub, чтобы заменить объекты, которые создал встроенный поставщик состояний сеансов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:

- [aspnet-session-state](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/aspnet-session-state)

#### <a name="customer-case-studies"></a>Клиентские сценарии

- Компании bwin удалось значительно увеличить пропускную способность и сократить площадь, занимаемую оборудованием, для состояния сеанса ASP.NET, используя выполняющуюся в памяти OLTP в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]: [Gaming Site Can Scale to 250 000 Requests Per Second and Improve Player Experience](https://customers.microsoft.com/en-us/story/gaming-site-can-scale-to-250000-requests-per-second-an) (Игорный сайт смог повысить масштаб до 250 000 запросов в секунду и улучшить условия игры для игроков).
- Благодаря состоянию сеанса ASP.NET компании bwin удалось еще больше повысить пропускную способность и внедрить корпоративную систему кэширования среднего уровня, используя выполняющуюся в памяти OLTP в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]: [How bwin is using [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/) (Как компания bwin добилась небывалой производительности и масштаба, используя выполняющуюся в памяти OLTP в SQL Server 2016).

### <a name="tempdb-object-replacement"></a>Замена объекта tempdb

Используйте неустойчивые таблицы и табличные типы, оптимизированные для памяти, чтобы заменить традиционные структуры на основе TempDB, табличные переменные и возвращающие табличные значения параметры.

Табличные переменные и неустойчивые таблицы, оптимизированные для памяти, обычно уменьшают нагрузку ЦП и полностью ликвидируют операции ввода-вывода журналов по сравнению с традиционными табличными переменными и таблицами #temp.

#### <a name="implementation-considerations"></a>Рекомендации по реализации

Чтобы начать работу, см. запись блога [Improving temp table and table variable performance using memory optimization](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)(Повышение производительности временной таблицы и табличной переменной с помощью оптимизации памяти).

#### <a name="customer-case-studies"></a>Клиентские сценарии

- Одним нашим клиентам удалось повысить производительность на 40 %, просто заменив традиционные возвращающие табличное значение параметры на возвращающие табличное значение параметры, оптимизированные для памяти: [High Speed IoT Data Ingestion Using In-Memory OLTP in Azure](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/04/07/a-technical-case-study-high-speed-iot-data-ingestion-using-in-memory-oltp-in-azure/)(Скоростной прием данных Интернета вещей с помощью выполняющейся в памяти OLTP в Azure).

### <a name="etl-extract-transform-load"></a>Извлечение, преобразование и загрузка

Рабочие процессы извлечения, преобразования и загрузки часто включают загрузку данных в промежуточную таблицу, преобразование данных и их загрузку в итоговые таблицы.

#### <a name="implementation-considerations"></a>Рекомендации по реализации

Используйте неустойчивые таблицы, оптимизированные для памяти, для промежуточного хранения данных. Они позволяют полностью ликвидировать операции ввода-вывода и обеспечить эффективность доступа.

Чтобы ускорить преобразования в промежуточной таблице, выполняющиеся в ходе рабочего процесса, используйте скомпилированные в собственном коде хранимые процедуры. Если эти преобразования можно выполнять в параллельном режиме, при оптимизации памяти вы получаете дополнительные преимущества масштабирования.

## <a name="sample-script"></a>Образец скрипта

Прежде чем начать использовать выполняющуюся в памяти OLTP, необходимо создать файловую группу MEMORY_OPTIMIZED_DATA. Кроме того, мы рекомендуем использовать уровень совместимости базы данных 130 (или более высокий) и задать для параметра базы данных MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT значение ON.

С помощью скрипта в следующем расположении можно создать файловую группу в папке данных по умолчанию, а также настроить рекомендуемые параметры:

- [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)

В следующем скрипте показаны объекты выполняющейся в памяти OLTP, которые можно создать в базе данных.

```sql
-- configure recommended DB option
ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
GO
-- memory-optimized table
CREATE TABLE dbo.table1
( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
  c2 NVARCHAR(MAX))
WITH (MEMORY_OPTIMIZED=ON)
GO
-- non-durable table
CREATE TABLE dbo.temp_table1
( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
  c2 NVARCHAR(MAX))
WITH (MEMORY_OPTIMIZED=ON,
      DURABILITY=SCHEMA_ONLY)
GO
-- memory-optimized table type
CREATE TYPE dbo.tt_table1 AS TABLE
( c1 INT IDENTITY,
  c2 NVARCHAR(MAX),
  is_transient BIT NOT NULL DEFAULT (0),
  INDEX ix_c1 HASH (c1) WITH (BUCKET_COUNT=1024))
WITH (MEMORY_OPTIMIZED=ON)
GO
-- natively compiled stored procedure
CREATE PROCEDURE dbo.usp_ingest_table1
  @table1 dbo.tt_table1 READONLY
WITH NATIVE_COMPILATION, SCHEMABINDING
AS
BEGIN ATOMIC
    WITH (TRANSACTION ISOLATION LEVEL=SNAPSHOT,
          LANGUAGE=N'us_english')

  DECLARE @i INT = 1

  WHILE @i > 0
  BEGIN
    INSERT dbo.table1
    SELECT c2
    FROM @table1
    WHERE c1 = @i AND is_transient=0

    IF @@ROWCOUNT > 0
      SET @i += 1
    ELSE
    BEGIN
      INSERT dbo.temp_table1
      SELECT c2
      FROM @table1
      WHERE c1 = @i AND is_transient=1

      IF @@ROWCOUNT > 0
        SET @i += 1
      ELSE
        SET @i = 0
    END
  END

END
GO
-- sample execution of the proc
DECLARE @table1 dbo.tt_table1
INSERT @table1 (c2, is_transient) VALUES (N'sample durable', 0)
INSERT @table1 (c2, is_transient) VALUES (N'sample non-durable', 1)
EXECUTE dbo.usp_ingest_table1 @table1=@table1
SELECT c1, c2 from dbo.table1
SELECT c1, c2 from dbo.temp_table1
GO
```   

## <a name="resources-to-learn-more"></a>Ресурсы с дополнительными сведениями:

[Технологии выполнения OLTP в памяти для повышения производительности службы Transact-SQL](http://msdn.microsoft.com/library/mt694156.aspx)   
Демонстрацию производительности с использованием выполняющейся в памяти OLTP см. по адресу [in-memory-oltp-perf-demo-v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)   
[17-минутный видеоролик, в котором объясняется, что такое выполняющаяся в памяти OLTP, а также показывается демонстрация](https://www.youtube.com/watch?v=l5l5eophmK4) (демонстрация начинается с 8:25)   
[Скрипт, позволяющий включить выполняющуюся в памяти OLTP и задать рекомендуемые параметры](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)   
[Основная документация по выполняющейся в памяти OLTP](in-memory-oltp-in-memory-optimization.md)   
[Повышение производительности и использования ресурсов благодаря выполняющейся в памяти OLTP в базе данных SQL Azure](https://azure.microsoft.com/blog/in-memory-oltp-in-azure-sql-database/)  
[Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)   
[Оптимизация производительности с помощью технологий обработки в оперативной памяти в базе данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory)  
[Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)  
[Выполняющаяся в памяти OLTP — рекомендации по общим шаблонам рабочих нагрузок и миграции](http://msdn.microsoft.com/library/dn673538.aspx) 
