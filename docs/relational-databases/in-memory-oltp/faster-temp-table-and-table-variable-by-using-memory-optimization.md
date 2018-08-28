---
title: Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти | Документация Майкрософт
ms.custom: ''
ms.date: 06/01/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 38512a22-7e63-436f-9c13-dde7cf5c2202
caps.latest.revision: 20
author: Jodebrui
ms.author: jodebrui
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 55e6fc3814163aa622cc834809b7106326bc18db
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43069647"
---
# <a name="faster-temp-table-and-table-variable-by-using-memory-optimization"></a>Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  
Если вы используете временные таблицы, табличные переменные или возвращающие табличные значения параметры, рекомендуем преобразовать их в оптимизированные для памяти таблицы и табличные переменные с целью повышения производительности. Изменения, которые необходимо внести в код, обычно минимальны.  
  
В этой статье рассматриваются следующие вопросы:  
  
- сценарии, в которых выгоднее преобразование в хранящиеся в памяти объекты;  
- технические инструкции по реализации преобразования в хранящиеся в памяти объекты;  
- предварительные требования для преобразования в хранящиеся в памяти объекты;  
- образец кода, демонстрирующий преимущества оптимизации для памяти в плане производительности.
  
  
## <a name="a-basics-of-memory-optimized-table-variables"></a>A. Основные сведения о табличных переменных, оптимизированных для памяти  
  
Оптимизированная для памяти табличная переменная позволяет повысить эффективность благодаря использованию тех же алгоритмов и структур данных, которые применяются в оптимизированных для памяти таблицах. Эффективность максимальна в случае, если доступ к табличной переменной осуществляется из модуля, скомпилированного в собственном коде.  
  
  
Оптимизированная для памяти табличная переменная:  
  
- хранится только в памяти и не имеет компонента на диске;  
- не требует операций ввода-вывода;  
- не требуется использования базы данных tempdb и не создает соответствующих конфликтов;  
- может передаваться в хранимую процедуру как возвращающий табличное значение параметр;  
- должна иметь по крайней мере один индекс (некластеризованный или хэш-индекс):  
  - для хэш-индекса число контейнеров в идеале должно в 1–2 раза превышать предполагаемое число уникальных ключей индекса, но допускается и более значительное превышение (до 10 раз). Дополнительные сведения см. в разделе [Индексы для оптимизированных для памяти таблиц](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  

  
  
#### <a name="object-types"></a>Типы Object  
  
Выполняющаяся в памяти OLTP предоставляет следующие объекты, которые можно использовать для оптимизированных для памяти временных таблиц и табличных переменных:  
  
- Таблицы, оптимизированные для памяти  
  - Durability = SCHEMA_ONLY  
- Оптимизированные для памяти табличные переменные  
  - Должны объявляться в два этапа (а не как встроенные):  
    - `CREATE TYPE my_type AS TABLE ...;` , а затем  
    - `DECLARE @mytablevariable my_type;`.  
  
  
## <a name="b-scenario-replace-global-tempdb-x23x23table"></a>Б. Сценарий: замена глобальной таблицы tempdb &#x23;&#x23;table  
  
Замена глобальной временной таблицы на оптимизированную для памяти таблицы SCHEMA_ONLY достаточно проста. Наиболее существенное изменение состоит в том, что таблица создается во время развертывания, а не во время выполнения. Создание оптимизированных для памяти таблиц занимает больше времени, чем у традиционных, из-за оптимизации во время компиляции. Создание и удаление оптимизированных для памяти таблиц в составе рабочей нагрузки повлияло бы на ее производительность, а также на производительность повтора на серверах-получателях AlwaysOn и восстановления баз данных.

Предположим, что у вас есть приведенная ниже глобальная временная таблица.  
  
  
```sql
CREATE TABLE ##tempGlobalB  
    (  
        Column1   INT   NOT NULL ,  
        Column2   NVARCHAR(4000)  
    );  
```
  
  
  
Рассмотрите возможность замены глобальной временной таблицы на приведенную ниже таблицу, оптимизированную для памяти, с параметром DURABILITY = SCHEMA_ONLY.  
  
  
  
```sql
CREATE TABLE dbo.soGlobalB  
(  
    Column1   INT   NOT NULL   INDEX ix1 NONCLUSTERED,  
    Column2   NVARCHAR(4000)  
)  
    WITH  
        (MEMORY_OPTIMIZED = ON,  
        DURABILITY        = SCHEMA_ONLY);  
```  
  
  
  
#### <a name="b1-steps"></a>Б.1. Этапы  
  
Чтобы преобразовать глобальную временную таблицу в таблицу с параметром SCHEMA_ONLY, выполните указанные ниже действия.  
  
  
1. Однократно создайте таблицу **dbo.soGlobalB** так же, как любую традиционную таблицу на диске.  
2. В коде Transact-SQL удалите инструкцию для создания таблицы **&#x23;&#x23;tempGlobalB**.  Важно создавать оптимизированную для памяти таблицу во время развертывания, а не во время выполнения, чтобы избежать дополнительных временных затрат при компиляции, связанных с созданием таблицы.
3. В коде T-SQL замените все упоминания таблицы **&#x23;&#x23;tempGlobalB** на **dbo.soGlobalB**.  
  
  
## <a name="c-scenario-replace-session-tempdb-x23table"></a>В. Сценарий: замена таблицы сеансов tempdb &#x23;table  
  
Для подготовки к замене временной таблицы сеансов требуется больше кода T-SQL, чем в предыдущем сценарии с глобальной временной таблицей. К счастью, больший объем кода T-SQL не означает, что для преобразования потребуется больше усилий.  

Как и в случае с глобальной временной таблицей, самым значительным изменением является создание таблицы во время развертывания, а не выполнения, позволяющее избежать дополнительной нагрузки при компиляции.
  
Предположим, что у вас есть приведенная ниже временная таблица сеансов.  
  
  
  
```sql  
CREATE TABLE #tempSessionC  
(  
    Column1   INT   NOT NULL ,  
    Column2   NVARCHAR(4000)  
);  
```
  
  
  
Сначала создайте приведенную ниже функцию, возвращающую табличное значение, для фильтрации по **@@spid**. Эту функцию смогут использовать все таблицы SCHEMA_ONLY, преобразованные из временных таблиц сеансов.  
  
  
  
```sql  
CREATE FUNCTION dbo.fn_SpidFilter(@SpidFilter smallint)  
    RETURNS TABLE  
    WITH SCHEMABINDING , NATIVE_COMPILATION  
AS  
    RETURN  
        SELECT 1 AS fn_SpidFilter  
            WHERE @SpidFilter = @@spid;  
```
  
  
  
Затем создайте таблицу SCHEMA_ONLY, а также политику безопасности для нее.  
  
  
Обратите внимание на то, что каждая оптимизированная для памяти таблица должна содержать как минимум один индекс.  
  
- Для таблицы dbo.soSessionC, возможно, лучше подойдет хэш-индекс, если вычислить соответствующее значение BUCKET_COUNT. Но для простоты в этом примере мы используем некластеризованный индекс.  
  
  
  
```sql
CREATE TABLE dbo.soSessionC  
(  
    Column1     INT         NOT NULL,  
    Column2     NVARCHAR(4000)  NULL,  

    SpidFilter  SMALLINT    NOT NULL   DEFAULT (@@spid),  

    INDEX ix_SpidFiler NONCLUSTERED (SpidFilter),  
    --INDEX ix_SpidFilter HASH  
    --    (SpidFilter) WITH (BUCKET_COUNT = 64),  
        
    CONSTRAINT CHK_soSessionC_SpidFilter  
        CHECK ( SpidFilter = @@spid ),  
)  
    WITH  
        (MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_ONLY);  
go  
  
  
CREATE SECURITY POLICY dbo.soSessionC_SpidFilter_Policy  
    ADD FILTER PREDICATE dbo.fn_SpidFilter(SpidFilter)  
    ON dbo.soSessionC  
    WITH (STATE = ON);  
go  
```  
  
  
  
Наконец, в общем коде T-SQL сделайте следующее:  
  
1. Измените все ссылки на временную таблицу в инструкциях Transact-SQL, чтобы они указывали на новую таблицу, оптимизированную для работы в памяти.
    - _Старое имя:_ &#x23;tempSessionC  
    - _Новое имя:_ dbo.soSessionC  
2. Замените инструкции `CREATE TABLE #tempSessionC` в своем коде на `DELETE FROM dbo.soSessionC`, чтобы сеанс не обращался к содержимому таблицы, добавленному в предыдущем сеансе с тем же идентификатором session_id. Важно создавать оптимизированную для памяти таблицу во время развертывания, а не во время выполнения, чтобы избежать дополнительных временных затрат при компиляции, связанных с созданием таблицы.
3. Удалите из кода инструкции `DROP TABLE #tempSessionC`. Если есть опасения относительно размера используемой памяти, вы можете добавить инструкцию `DELETE FROM dbo.soSessionC`.
  
  
  
  
## <a name="d-scenario-table-variable-can-be-memoryoptimizedon"></a>Г. Сценарий: табличная переменная может иметь параметр MEMORY_OPTIMIZED=ON  
  
  
Традиционная табличная переменная представляет таблицу в базе данных tempdb. Чтобы значительно повысить производительность, можно оптимизировать табличную переменную для памяти.  
  
Ниже приведен код T-SQL для традиционной табличной переменной. Ее область действия завершается, когда заканчивается пакет или сеанс.  
  
  
  
```sql
DECLARE @tvTableD TABLE  
    ( Column1   INT   NOT NULL ,  
      Column2   CHAR(10) );  
```
  
  
  
#### <a name="d1-convert-inline-to-explicit"></a>Г.1. Преобразование встроенной переменной в явную  
  
Предыдущий синтаксис создает так называемую *встроенную*табличную переменную. Встроенный синтаксис не поддерживает оптимизацию для памяти. Поэтому давайте преобразуем встроенный синтаксис в явный для TYPE.  
  
*Область действия.* Определение TYPE, созданное первым пакетом, отделенным командой GO, сохраняется даже после завершения работы и перезапуска сервера. Но после первого разделителя GO объявленная таблица @tvTableC сохраняется только до тех пор, пока не будет достигнут следующий разделитель GO и пакет не завершится.  
  
  
  
```sql  
CREATE TYPE dbo.typeTableD  
    AS TABLE  
    (  
        Column1  INT   NOT NULL ,  
        Column2  CHAR(10)  
    );  
go  
        
SET NoCount ON;  
DECLARE @tvTableD dbo.typeTableD  
;  
INSERT INTO @tvTableD (Column1) values (1), (2)  
;  
SELECT * from @tvTableD;  
go  
```
  
  
  
#### <a name="d2-convert-explicit-on-disk-to-memory-optimized"></a>Г.2. Преобразование явной таблицы на диске в оптимизированную для памяти таблицу  
  
Оптимизированная для памяти табличная переменная не хранится в базе данных tempdb. Оптимизация для памяти приводит к повышению скорости работы до 10 раз и более.  
  
Преобразование таблиц в оптимизированные для памяти производится в один шаг. Оптимизируйте явное создание TYPE следующим образом. При этом добавляются:  
  
- Индекс. Еще раз напомним, что каждая оптимизированная для памяти таблица должна содержать как минимум один индекс.  
- MEMORY_OPTIMIZED = ON.  
  
  
  
```sql
CREATE TYPE dbo.typeTableD  
    AS TABLE  
    (  
        Column1  INT   NOT NULL   INDEX ix1,  
        Column2  CHAR(10)  
    )  
    WITH  
        (MEMORY_OPTIMIZED = ON);  
```  
  
  
  
Готово.  
  
  
## <a name="e-prerequisite-filegroup-for-sql-server"></a>Д. Файловая группа, необходимая для SQL Server  
  
Для использования оптимизированных для памяти функций в Microsoft SQL Server база данных должна иметь файловую группу, объявленную с параметром **MEMORY_OPTIMIZED_DATA**.  
  
- База данных SQL Azure не требует создания такой файловой группы.  
  
  
*Предварительное требование.* Приведенный ниже код Transact-SQL для файловой группы необходим для развернутых образцов кода T-SQL в дальнейших подразделах этого раздела.  
  
1. Необходимо использовать SSMS.exe или другое средство, позволяющее отправлять код T-SQL.  
2. Вставьте образец кода T-SQL для файловой группы в среду SSMS.  
3. Отредактируйте код T-SQL, изменив имена и пути к каталогам по своему желанию.  
  - Все каталоги в значении FILENAME уже должны существовать, за исключением последнего каталога, который не должен существовать.  
4. Выполните отредактированный код T-SQL.  
  - Запускать файловую группу T-SQL несколько раз не нужно, даже если вы повторно настраиваете и перезапускаете скрипт T-SQL для сравнения скорости в следующем подразделе.  
  
  
  
 
```sql
ALTER DATABASE InMemTest2  
    ADD FILEGROUP FgMemOptim3  
        CONTAINS MEMORY_OPTIMIZED_DATA;  
go  
ALTER DATABASE InMemTest2  
    ADD FILE  
    (  
        NAME = N'FileMemOptim3a',  
        FILENAME = N'C:\DATA\FileMemOptim3a'  
                    --  C:\DATA\    preexisted.  
    )  
    TO FILEGROUP FgMemOptim3;  
go  
```  


Следующий скрипт создает файловую группу и настраивает рекомендованные параметры базы данных: [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)
  
Дополнительные сведения о `ALTER DATABASE ... ADD` для FILE и FILEGROUP см. в следующих разделах:  
  
- [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
- [Оптимизированная для памяти файловая группа](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)    
  
  
## <a name="f-quick-test-to-prove-speed-improvement"></a>Е. Небольшой тест для проверки повышения быстродействия  
  
  
В этом разделе приводится код Transact-SQL, с помощью которого можно протестировать и оценить прирост скорости выполнения операций INSERT-DELETE при использовании табличной переменной, оптимизированной для памяти. Код состоит из двух половин, которые почти одинаковы за тем исключением, что в первой половине используется таблица оптимизированного для памяти типа.  
  
Сравнительный тест длится примерно 7 секунд. Запуск примера:  
  
1. *Предварительное требование.* Вы уже должны были выполнить код T-SQL для файловой группы из предыдущего подраздела.  
2. Выполните приведенный ниже скрипт T-SQL INSERT-DELETE.  
  - Обратите внимание на инструкцию GO 5001, которая повторно отправляет код T-SQL 5001 раз. Вы можете изменить это число и перезапустить тест.  
  
В базе данных SQL скрипт следует запускать из виртуальной машины, находящейся в вашем регионе.

  
```sql
PRINT ' ';  
PRINT '---- Next, memory-optimized, faster. ----';  

DROP TYPE IF EXISTS dbo.typeTableC_mem;  
go  
CREATE TYPE dbo.typeTableC_mem  -- !!  Memory-optimized.  
        AS TABLE  
        (  
            Column1  INT NOT NULL INDEX ix1,  
            Column2  CHAR(10)  
        )  
        WITH  
            (MEMORY_OPTIMIZED = ON);  
go  
DECLARE @dateString_Begin nvarchar(64) =  
    Convert(nvarchar(64), GetUtcDate(), 121);  
PRINT Concat(@dateString_Begin, '  = Begin time, _mem.');  
go  
SET NoCount ON;  
DECLARE @tvTableC dbo.typeTableC_mem;  -- !!  

INSERT INTO @tvTableC (Column1) values (1), (2);  
INSERT INTO @tvTableC (Column1) values (3), (4);  
DELETE @tvTableC;  

GO 5001  

DECLARE @dateString_End nvarchar(64) =  
    Convert(nvarchar(64), GetUtcDate(), 121);  
PRINT Concat(@dateString_End, '  = End time, _mem.');  
go  
DROP TYPE IF EXISTS dbo.typeTableC_mem;  
go  

---- End memory-optimized.  
-------------------------------------------------  
---- Start traditional on-disk.  

PRINT ' ';  
PRINT '---- Next, tempdb based, slower. ----';  

DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
go  
CREATE TYPE dbo.typeTableC_tempdb  -- !!  Traditional tempdb.  
    AS TABLE  
    (  
        Column1  INT NOT NULL ,  
        Column2  CHAR(10)  
    );  
go  
DECLARE @dateString_Begin nvarchar(64) =  
    Convert(nvarchar(64), GetUtcDate(), 121);  
PRINT Concat(@dateString_Begin, '  = Begin time, _tempdb.');  
go  
SET NoCount ON;  
DECLARE @tvTableC dbo.typeTableC_tempdb;  -- !!  

INSERT INTO @tvTableC (Column1) values (1), (2);  
INSERT INTO @tvTableC (Column1) values (3), (4);  
DELETE @tvTableC;  

GO 5001  

DECLARE @dateString_End nvarchar(64) =  
    Convert(nvarchar(64), GetUtcDate(), 121);  
PRINT Concat(@dateString_End, '  = End time, _tempdb.');  
go  
DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
go  
----  

PRINT '---- Tests done. ----';  

go  

/*** Actual output, SQL Server 2016:  

---- Next, memory-optimized, faster. ----  
2016-04-20 00:26:58.033  = Begin time, _mem.  
Beginning execution loop  
Batch execution completed 5001 times.  
2016-04-20 00:26:58.733  = End time, _mem.  

---- Next, tempdb based, slower. ----  
2016-04-20 00:26:58.750  = Begin time, _tempdb.  
Beginning execution loop  
Batch execution completed 5001 times.  
2016-04-20 00:27:05.440  = End time, _tempdb.  
---- Tests done. ----  
***/
```
  
  
  
## <a name="g-predict-active-memory-consumption"></a>Ж. Прогнозирование потребления активной памяти  
  
Чтобы узнать, как прогнозировать потребность оптимизированных для памяти таблиц в активной памяти, обратитесь к следующим ресурсам:  
  
- [Оценка требований к объему памяти для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)  
- [Размер строк и таблицы для таблиц, оптимизированных для памяти: пример вычисления](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
В случае с большими табличными переменными некластеризованные индексы потребляют больше памяти, чем в случае с *таблицами*, оптимизированными для памяти. Чем больше число строк и ключ индекса, тем сильнее эта разница.  
  
Если в каждой операции доступа к оптимизированной для памяти табличной переменной используется только одно точное значение ключа, хэш-индекс может быть предпочтительнее некластеризованного индекса. Однако, если вы не можете оценить подходящее значение BUCKET_COUNT, можно использовать и некластеризованный индекс.  
  
## <a name="h-see-also"></a>З. См. также раздел  
  
- [Таблицы, оптимизированные для памяти.](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)

- [Определение устойчивости для оптимизированных для памяти объектов.](../../relational-databases/in-memory-oltp/defining-durability-for-memory-optimized-objects.md)

- [Накопительное обновление, позволяющее исключить вероятность возникновения неправильных ошибок нехватки памяти, объявленное в блоге в сентябре 2017 г.](https://support.microsoft.com/help/4025208/fix-memory-leak-occurs-when-you-use-memory-optimized-tables-in-microso)
    - В статье [Версии сборки SQL Server 2016](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions) приводятся подробные сведения о выпусках, пакетах обновления и накопительных обновлениях.
    - Эти случайные неправильные ошибки не возникали в выпуске Enterprise для SQL Server.

