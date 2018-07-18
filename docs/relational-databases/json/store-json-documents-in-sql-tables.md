---
title: Хранение документов JSON в SQL Server или базе данных SQL | Microsoft Docs
ms.description: This article describes why and how to store and index JSON documents in SQL Server or SQL Database, and how to optimize queries over the JSON documents.
ms.custom: ''
ms.date: 01/04/2018
ms.prod: sql
ms.reviewer: douglasl
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: 03ffe17d11f571f7f5a6b718d20396cbe8694f88
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421523"
---
# <a name="store-json-documents-in-sql-server-or-sql-database"></a>Хранение документов JSON в SQL Server или базе данных SQL
SQL Server и база данных SQL Azure имеют собственные функции JSON, позволяющие анализировать документы JSON с помощью стандартного языка SQL. Теперь вы можете хранить документы JSON в SQL Server или базе данных SQL и запрашивать данные JSON так же, как в базе данных NoSQL. Эта статья описывает возможности хранения документов JSON в SQL Server или базе данных SQL.

## <a name="classic-tables"></a>Классические таблицы

Для хранения документов JSON в SQL Server или базе данных SQL проще всего создать обычную таблицу с двумя столбцами, содержащую идентификатор и содержимое документа. Пример:

```sql
create table WebSite.Logs (
    _id bigint primary key identity,
    log nvarchar(max)
);
```

Эта структура эквивалентна коллекциям из классических баз данных документов. Первичный ключ `_id` — это значение с автоматическим приращением, представляющее собой уникальный идентификатор каждого документа для быстрого поиска. Такая структура хорошо подходит для классических сценариев NoSQL, когда получение или изменение хранимого документа осуществляются по идентификатору.

Тип данных nvarchar(max) позволяет хранить документы JSON размером до 2 ГБ. Если вы уверены, что размер документов JSON не превышает 8 КБ, рекомендуем вместо NVARCHAR(max) использовать NVARCHAR(4000) для большей производительности.

В образце таблицы, созданном в предыдущем примере, предполагается, что в столбце `log` хранятся допустимые документы JSON. Если вы хотите убедиться, что в столбце `log` хранятся допустимые документы JSON, добавьте для столбца ограничение CHECK. Пример:

```sql
ALTER TABLE WebSite.Logs
    ADD CONSTRAINT [Log record should be formatted as JSON]
                   CHECK (ISJSON(log)=1)
```

Каждый раз, когда кто-то вставляет или изменяет документ в таблице, это ограничение проверяет, что документ JSON имеет правильный формат. Без этого ограничения таблица будет оптимизирована для операций вставки, так как любой документ JSON добавляется в столбец напрямую, без обработки.

При хранении в таблице документов JSON вы можете выполнять запросы к документам с помощью стандартного языка Transact-SQL. Пример:

```sql
SELECT TOP 100 JSON_VALUE(log, ‘$.severity’), AVG( CAST( JSON_VALUE(log,’$.duration’) as float))
 FROM WebSite.Logs
 WHERE CAST( JSON_VALUE(log,’$.date’) as datetime) > @datetime
 GROUP BY JSON_VALUE(log, ‘$.severity’)
 HAVING AVG( CAST( JSON_VALUE(log,’$.duration’) as float) ) > 100
 ORDER BY AVG( CAST( JSON_VALUE(log,’$.duration’) as float) ) DESC
```

Возможность использования *любой* функции и предложения запроса T-SQL для запросов к документам JSON является существенным преимуществом. SQL Server и база данных SQL не вводят никаких ограничений к запросам, используемым для анализа документов JSON. Вы можете извлекать из документа JSON значения с помощью функции `JSON_VALUE` и использовать их в запросе, как любые другие значения.

Наличие полнофункционального синтаксиса запросов T-SQL является ключевым отличием SQL Server и базы данных SQL от классических баз данных NoSQL: в Transact-SQL вам скорее всего доступны все необходимые функции для обработки данных JSON.

## <a name="indexes"></a>Индексы

Если окажется, что ваши запросы часто выполняют в документах поиск по определенному свойству (например, по свойству `severity` в документе JSON), добавьте к свойству классический индекс NONCLUSTERED, чтобы ускорить обработку запросов.

Вы можете создать вычисляемый столбец, который предоставляет значения JSON из столбцов JSON по заданному пути (то есть, по пути `$.severity`), и создать стандартный индекс в этом столбце. Пример:

```sql
create table WebSite.Logs (
    _id bigint primary key identity,
    log nvarchar(max),

    severity AS JSON_VALUE(log, '$.severity'),
    index ix_severity (severity)
);
```

Используемый в этом примере вычисляемый столбец является несохраняемым или виртуальным столбцом, который не добавляет дополнительное место в таблицу. Индекс `ix_severity` использует его для повышения производительности запросов, как показано в следующем примере.

```sql
SELECT log
FROM Website.Logs
WHERE JSON_VALUE(log, '$.severity') = 'P4'
```

Важное свойство этого индекса — учет параметров сортировки. Если исходный столбец NVARCHAR имеет свойство COLLATION (например, для учета регистра или японского языка), индекс расставляется в соответствии с правилами языка или правилами учета регистра, связанными со столбцом NVARCHAR. Такой учет параметров сортировки может оказаться важным при разработке приложений для международного рынка, в которых нужно использовать особые языковые правила при обработке JSON-документов.

## <a name="large-tables--columnstore-format"></a>Большие таблицы и формат columnstore

Если в вашей коллекции планируется большое количество документов JSON, рекомендуем добавить в нее индекс CLUSTERED COLUMNSTORE, как показано в следующем примере.

```sql
create sequence WebSite.LogID as bigint;
go
create table WebSite.Logs (
    _id bigint default(next value for WebSite.LogID),
    log nvarchar(max),

    INDEX cci CLUSTERED COLUMNSTORE
);
```

Индекс CLUSTERED COLUMNSTORE обеспечивает высокую степень сжатия данных (максимум в 25 раз), которая позволит значительно снизить требования к дисковому пространству, сократить расходы на хранение и повысить производительность операций ввода-вывода рабочей нагрузки. Кроме того, индексы CLUSTERED COLUMNSTORE оптимизированы для сканирования таблиц и анализа документов JSON, поэтому они могут быть наилучшим выбором для аналитики журналов.

В примере выше для присвоения значений столбцу `_id` используется объект последовательности. И последовательности, и идентификаторы являются приемлемыми вариантами для этого столбца.

## <a name="frequently-changing-documents--memory-optimized-tables"></a>Часто изменяемые документы и таблицы, оптимизированные для памяти

Если в коллекциях ожидается множество операций изменения, вставки и удаления, вы можете хранить документы JSON в таблицах, оптимизированных для памяти. Оптимизированные для памяти коллекции JSON всегда хранят данные в памяти, что позволяет избежать нагрузки, связанной с операциями ввода-вывода в хранилище. Кроме того, эти коллекции абсолютно неблокируемые, то есть, действия с документами не препятствуют никаким другим операциям.

Единственное, что вам нужно сделать для преобразования классической коллекции в коллекцию, оптимизированную для памяти, — это указать параметр **with (memory_optimized=on)** после определения таблицы, как показано в следующем примере. После этого вы получите оптимизированную для памяти версию коллекции JSON.

```sql
create table WebSite.Logs (
  _id bigint identity primary key nonclustered,
  log nvarchar(4000)
) with (memory_optimized=on)
```

Таблица, оптимизированная для памяти, — лучший вариант для часто изменяемых документов. При их внедрении также учитывайте производительность. Если возможно, используйте в своих оптимизированных для памяти коллекциях NVARCHAR(4000) вместо NVARCHAR(max) для документов JSON, так как это может значительно увеличить производительность.

Как и с классическими таблицами, вы можете добавлять индексы в поля, предоставляемые в оптимизированных для памяти таблицах, с помощью вычисляемых столбцов. Пример:

```sql
create table WebSite.Logs (

  _id bigint identity primary key nonclustered,
  log nvarchar(4000),

  severity AS cast(JSON_VALUE(log, '$.severity') as tinyint) persisted,
  index ix_severity (severity)

) with (memory_optimized=on)
```

Чтобы обеспечить максимальную производительность, приведите значение JSON к наименьшему возможному типу, который можно использовать для хранения значения свойства. В примере выше используется **tinyint**.

Вы также можете поместить запросы SQL, которые изменяют документы JSON, в хранимые процедуры, чтобы воспользоваться преимуществами компиляции в машинный код. Пример:

```sql
CREATE PROCEDURE WebSite.UpdateData(@Id int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION

AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE WebSite.Logs
    SET log = JSON_MODIFY(log, @Property, @Value)
    WHERE _id = @Id;

END
```

Эта скомпилированная в машинный код процедура принимает запрос и создает .DLL-код, который выполняет запрос. Она является самым быстрым способом для создания запросов и изменения данных.

## <a name="conclusion"></a>Заключение

Собственные функции JSON в SQL Server и базе данных SQL позволяют работать с документами JSON так же, как в базах данных NoSQL. Каждая база данных (реляционная или NoSQL) обладает рядом преимуществ и недостатков в обработке данных JSON. Основное преимущество хранения документов JSON в SQL Server или базе данных SQL — это полная поддержка языка SQL. Вы можете использовать широкие возможности языка Transact-SQL для обработки данных и настройки множества параметров хранения (от индексов columnstore для высокой степени сжатия и быстрого анализа до оптимизированных для памяти таблиц, обеспечивающих обработку без блокирования). Кроме того, вам доступны обширные возможности обеспечения безопасности и оптимизации под различные рынки, которые можно легко переносить в сценарии NoSQL. Изложенные выше причины являются веским доводом в пользу хранения документов JSON в SQL Server или базе данных SQL.

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-blog-posts"></a>Публикации блога Майкрософт  
  
Конкретные решения, варианты использования и рекомендации см. в [записях блога](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) о встроенной поддержке JSON в SQL Server и базе данных SQL Azure.  

### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
