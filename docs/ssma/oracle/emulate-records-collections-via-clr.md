---
title: Эмуляция записей и коллекций с помощью определяемой пользователем среды CLR
description: Описывает, как Помощник по миграции SQL Server (SSMA) для Oracle использует SQL Server определяемые пользователем типы данных среды CLR для эмуляции записей и коллекций Oracle.
authors: nahk-ivanov
ms.service: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: 39a7e8d59425db7ce2d7e81083012321caac35ef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "76762818"
---
# <a name="emulating-records-and-collections-via-clr-udt"></a>Эмуляция записей и коллекций с помощью определяемой пользователем среды CLR

В этой статье описывается, как Помощник по миграции SQL Server (SSMA) для Oracle использует SQL Server определяемые пользователем типы данных среды CLR для эмуляции записей и коллекций Oracle.

## <a name="declaring-record-or-collection-types-and-variables"></a>Объявление типов записей или коллекций и переменных

SSMA создает три определяемых пользователем типов на основе среды CLR:

* `CollectionIndexInt`
* `CollectionIndexString`
* `Record`

`CollectionIndexInt` Тип предназначен для эмуляции коллекций, индексируемых по целому числу, таких `VARRAY`как s, вложенные таблицы и ассоциативные массивы на основе целочисленных ключей. `CollectionIndexString` Тип используется для ассоциативных массивов, индексируемых ключами символов. Функциональность записей Oracle эмулируется `Record` типом.

Все объявления типов записей или коллекций преобразуются в это объявление Transact-SQL:

```sql
declare @Collection$TYPE varchar(max) = '<type definition>'
```

Ниже `<type definition>` приведен описательный текст, однозначно определяющий исходный тип PL/SQL.

Рассмотрим следующий пример.

```sql
DECLARE
    TYPE Manager IS RECORD
    (
        mgrid integer,
        mgrname varchar2(40),
        hiredate date
    );

    TYPE Manager_table is TABLE OF Manager INDEX BY PLS_INTEGER;

    Mgr_rec Manager;
    Mgr_table_rec Manager_table;
BEGIN
    mgr_rec.mgrid := 1;
    mgr_rec.mgrname := 'Mike';
    mgr_rec.hiredate := sysdate;

    select
        empno,
        ename,
        hiredate
    BULK COLLECT INTO
        mgr_table_rec
    FROM
        emp;
END;
```

При преобразовании с помощью SSMA он станет следующим кодом Transact-SQL:

```sql
BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) =
            ' TABLE INDEX BY INT OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'

    DECLARE
        @Mgr_rec$mgrid int,
        @Mgr_rec$mgrname varchar(40),
        @Mgr_rec$hiredate datetime2(0),
        @Mgr_table_rec dbo.CollectionIndexInt =
            dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

    SET @mgr_rec$mgrid = 1
    SET @mgr_rec$mgrname = 'Mike'
    SET @mgr_rec$hiredate = sysdatetime()

    SET @mgr_table_rec = @mgr_table_rec.RemoveAll()
    SET @mgr_table_rec =
        @mgr_table_rec.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionComplex((
                SELECT
                    CAST(EMP.EMPNO AS int) AS mgrid,
                    EMP.ENAME AS mgrname,
                    EMP.HIREDATE AS hiredate
                FROM dbo.EMP
                FOR XML PATH
            ))
        )
END
```

Здесь, поскольку `Manager` таблица связана с числовым индексом (`INDEX BY PLS_INTEGER`), используемое СООТВЕТСТВУЮЩЕЕ объявление T-SQL имеет тип. `@CollectionIndexInt$TYPE` Если таблица была связана с индексом набора символов, например `VARCHAR2`, соответствующее объявление T-SQL будет иметь тип: `@CollectionIndexString$TYPE`

```sql
-- Oracle
TYPE Manager_table is TABLE OF Manager INDEX BY VARCHAR2(40);

-- SQL Server
@CollectionIndexString$TYPE varchar(max) =
    ' TABLE INDEX BY STRING OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'
```

Функции записи Oracle имитируются только по `Record` типу.

Каждый из типов,, `CollectionIndexInt`и `CollectionIndexString` `Record`имеет статическое свойство `[Null]` , возвращающее пустой экземпляр. `SetType` Метод вызывается для получения пустого объекта определенного типа (как показано в примере выше).

## <a name="constructor-call-conversions"></a>Преобразования вызовов конструктора

Нотация конструктора может использоваться только для вложенных таблиц `VARRAY`и s, поэтому все вызовы явных конструкторов преобразуются `CollectionIndexInt` с помощью типа. Пустые вызовы конструктора преобразуются `SetType` посредством вызова, вызванного на экземпляре со значением NULL `CollectionIndexInt`. `[Null]` Свойство возвращает экземпляр со значением NULL. Если конструктор содержит список элементов, то специальные вызовы метода применяются последовательно для добавления значения в коллекцию.

Пример:

```sql
-- Oracle

DECLARE
    TYPE nested_type IS TABLE OF VARCHAR2(20);
    TYPE varray_type IS VARRAY(5) OF INTEGER;

    v1 nested_type;
    v2 varray_type;
BEGIN
   v1 := nested_type('Arbitrary','number','of','strings');
   v2 := varray_type(10, 20, 40, 80, 160);
END;

-- SQL Server

BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) = ' VARRAY OF INT',
        @CollectionIndexInt$TYPE$2 varchar(max) = ' TABLE OF STRING',
        @v1 dbo.CollectionIndexInt,
        @v2 dbo.CollectionIndexInt

    SET @v1 =
        dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE$2)
            .AddString('Arbitrary')
            .AddString('number')
            .AddString('of')
            .AddString('strings')

   SET @v2 =
       dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE)
            .AddInt(10)
            .AddInt(20)
            .AddInt(40)
            .AddInt(80)
            .AddInt(160)
END
```

## <a name="referencing-and-assigning-record-and-collection-elements"></a>Создание ссылок и назначение элементов записи и коллекции

Каждый определяемый пользователем тип имеет набор методов, работающих с элементами различных типов данных. Например, `SetDouble` метод присваивает `float(53)` значение записи или коллекции и `GetDouble` может прочитать это значение. Ниже приведен полный список методов.

```sql
GetCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
SetCollectionIndexInt(@key <KeyType>, @value CollectionIndexInt) returns <UDT_type>;
GetCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
SetCollectionIndexString(@key <KeyType>, @value CollectionIndexString) returns <UDT_type>;
Record GetRecord(@key <KeyType>) returns Record;
SetRecord(@key <KeyType>, @value Record) returns <UDT_type>;
GetString(@key <KeyType>) returns nvarchar(max);
SetString(@key <KeyType>, @value nvarchar(max)) returns nvarchar(max);
GetDouble(@key <KeyType>) returns float(53);
SetDouble(@key <KeyType>, @value float(53)) returns <UDT_type>;
GetDatetime(@key <KeyType>) returns datetime;
SetDatetime(@key <KeyType>, @value datetime) returns <UDT_type>;
GetVarbinary(@key <KeyType>) returns varbinary(max);
SetVarbinary(@key <KeyType>, @value varbinary(max)) returns <UDT_type>;
SqlDecimal GetDecimal(@key <KeyType>);
SetDecimal(@key <KeyType>, @value numeric) returns <UDT_type>;
GetXml(@key <KeyType>) returns xml;
SetXml(@key <KeyType>, @value xml) returns <UDT_type>;
GetInt(@key <KeyType>) returns bigint;
SetInt(@key <KeyType>, @value bigint) returns <UDT_type>;
```

Эти методы используются при ссылке или присваивании значения элементу сбора или записи.

```sql
-- Oracle
a_collection(i) := 'VALUE';

-- SQL Server
SET @a_collection = @a_collection.SetString(@i, 'VALUE');
```

При преобразовании инструкций присваивания для многомерных коллекций или коллекций с элементами записи SSMA добавляет следующие методы для ссылки на родительский элемент в методе Set:

```sql
GetOrCreateCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
GetOrCreateCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
GetOrCreateRecord(@key <KeyType>) returns Record;
```

Например, коллекция элементов Record создается таким образом:

```sql
-- Oracle
DECLARE
    TYPE rec_details IS RECORD (id int, name varchar2(20));
    TYPE ntb1 IS TABLE of rec_details index BY binary_integer;
    c ntb1;
BEGIN
    c(1).id := 1;
END;

-- SQL Server
DECLARE
   @CollectionIndexInt$TYPE varchar(max) =
       ' TABLE INDEX BY INT OF ( RECORD ( ID INT , NAME STRING ) )',
   @c dbo.CollectionIndexInt =
       dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

SET @c = @c.SetRecord(1, @c.GetOrCreateRecord(1).SetInt(N'ID', 1))
```

## <a name="collection-built-in-methods"></a>Встроенные методы коллекций

SSMA использует следующие методы определяемого пользователем типа для эмуляции встроенных методов в коллекциях PL/SQL.

Методы сбора Oracle | `CollectionIndexInt`и `CollectionIndexString` эквивалент
--- | ---
COUNT | `Count returns int`
DELETE | `RemoveAll() returns <UDT_type>`
УДАЛИТЬ (n) | `Remove(@index int) returns <UDT_type>`
УДАЛИТЬ (m, n) | `RemoveRange(@indexFrom int, @indexTo int) returns <UDT_type>`
EXISTS | `ContainsElement(@index int) returns bit`
РАСШИРЕНИЙ | `Extend() returns <UDT_type>`
РАСШИРЕНИЕ (n) | `Extend() returns <UDT_type>`
РАСШИРЕНИЕ (n, i) | `ExtendDefault(@count int, @def int) returns <UDT_type>`
FIRST | `First() returns int`
LAST | `Last() returns int`
LIMIT | Недоступно
PRIOR | `Prior(@current int) returns int`
NEXT | `Next(@current int) returns int`
TRIM | `Trim() returns <UDT_type>`
Обрезать (n) | `TrimN(@count int) returns <UDT_type>`

## <a name="bulk-collect-operation"></a>Операция с МАССОВЫм СБОРом

SSMA преобразует `BULK COLLECT INTO` операторы в оператор `SELECT ... FOR XML PATH` SQL Server, результат которого заключен в одну из следующих функций:

* `ssma_oracle.fn_bulk_collect2CollectionSimple`
* `ssma_oracle.fn_bulk_collect2CollectionComplex`

Выбор зависит от типа целевого объекта. Эти функции возвращают значения XML, которые могут быть `CollectionIndexInt`проанализированы `CollectionIndexString` типами `Record` и. Специальная `AssignData` функция присваивает определяемому пользователем типу коллекцию на основе XML.

SSMA распознает три типа `BULK COLLECT INTO` инструкций.

### <a name="the-collection-contains-elements-with-scalar-types-and-the-select-list-contains-one-column"></a>Коллекция содержит элементы с скалярными типами, а `SELECT` список содержит один столбец

```sql
-- Oracle
SELECT column_name_1
BULK COLLECT INTO <collection_name_1>
FROM <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionSimple(
            (SELECT column_name_1 FROM <data_source> FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-record-types-and-the-select-list-contains-one-column"></a>Коллекция содержит элементы с типами записей, а `SELECT` список содержит один столбец

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2...]
BULK COLLECT INTO
    <collection_name_1>
FROM
    <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionComplex(
            (SELECT
                column_name_1 as [collection_name_1_element_field_name_1],
                column_name_2 as [collection_name_1_element_field_name_2]
            FROM <data_source>
            FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-scalar-type-and-the-select-list-contains-multiple-columns"></a>Коллекция содержит элементы с скалярным типом, а `SELECT` список содержит несколько столбцов

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2 ...]
BULK COLLECT INTO
    <collection_name_1>[, <collection_name_2> ...]
FROM
    <data_source>

-- SQL Server
;WITH bulkC AS (
    SELECT
        column_name_1 [collection_name_1_element_field_name_1],
        column_name_2 [collection_name_1_element_field_name_2]
    FROM
        <data_source>
)
SELECT
    @<collection_name_1> =
        @<collection_name_1>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_1]
                FROM
                    bulkC
                FOR XML PATH))),
    @<collection_name_2> =
        @<collection_name_2>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_2]
                FROM bulkC
                FOR XML PATH)))
```

## <a name="select-into-record"></a>ВЫДЕЛИТЬ запись

Если результат запроса Oracle сохраняется в переменной записи PL/SQL, то у вас есть два варианта в зависимости от параметра SSMA для **преобразования записи в виде списка разделенных переменных** (доступно в меню **Сервис** > **Параметры проекта**, а затем — **Общее** -> **Преобразование**). Если этот параметр имеет значение **Да** (по умолчанию), то SSMA не создает экземпляр типа записи. Вместо этого он разделяет запись на поля образующей, создавая отдельную переменную Transact-SQL для каждого поля записи. Если значение параметра — **нет**, создается экземпляр записи и каждому полю присваивается значение с помощью `Set` методов.
