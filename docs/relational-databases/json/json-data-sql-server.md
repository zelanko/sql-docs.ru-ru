---
title: Работа с данными JSON в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 02/19/2018
ms.prod: sql
ms.reviewer: douglasl
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
helpviewer_keywords:
- JSON
- JSON, built-in support
ms.assetid: c9a4e145-33c3-42b2-a510-79813e67806a
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6df3b020e125a807d84297abad445f3a3f0dd807
ms.sourcegitcommit: 67d5f2a654b36da7fcc7c39d38b8bcf45791acc3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2018
ms.locfileid: "39038121"
---
# <a name="json-data-in-sql-server"></a>Данные JSON в SQL Server
[!INCLUDE[appliesto-ss2016-asdb-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

JSON — это популярный формат текстовых данных, который используется для обмена данными в современных веб- и мобильных приложениях. Кроме того, JSON используется для хранения неструктурированных данных в файлах журналов или базах данных NoSQL, таких как Microsoft Azure Cosmos DB. Многие веб-службы REST возвращают результаты в формате текста JSON или принимают данные в формате JSON. Например, большинство служб Azure, таких как поиск Azure, служба хранилища Azure и Azure Cosmos DB, имеют конечные точки REST, которые возвращают или принимают JSON. JSON — это также основной формат обмена данными между веб-страницами и веб-серверами с помощью вызовов AJAX. 

Функции JSON в SQL Server позволяют объединить принципы NoSQL и реляционных баз данных в одной базе данных. Теперь вы можете объединять в одной таблице классические реляционные столбцы со столбцами, которые содержат документы в формате текста JSON, анализировать и импортировать документы JSON в реляционные структуры или форматировать реляционные данные в текст JSON. Посмотрите видео, чтобы понять, как функции JSON объединяют реляционные принципы и NoSQL в SQL Server и базе данных SQL Azure:

*JSON as a bridge between NoSQL and relational worlds* (JSON как мост между NoSQL и реляционными решениями)
> [!VIDEO https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds/player]
 
Вот пример текста JSON: 
 
```json 
[{
    "name": "John",
    "skills": ["SQL", "C#", "Azure"]
}, {
    "name": "Jane",
    "surname": "Doe"
}]
``` 
 
С помощью встроенных функций и операторов SQL Server вы можете выполнять указанные ниже действия с текстом JSON. 
 
- Синтаксический анализ текста JSON, а также считывание и изменение значений.  
- Преобразования массивов объектов JSON в табличный формат.  
- Выполнение любого запроса Transact SQL к преобразованным объектам JSON.  
- Форматирование результатов запросов Transact-SQL в формате JSON.  
  
![Обзор встроенной поддержки JSON](../../relational-databases/json/media/jsonslides1overview.png "Обзор встроенной поддержки JSON")  
  
## <a name="key-json-capabilities-of-sql-server-and-sql-database"></a>Основные возможности JSON, предоставляемые SQL Server и базой данных SQL
В следующих разделах описываются основные возможности, предоставляемые SQL Server со встроенной поддержкой JSON. Посмотрите видео, чтобы понять, как использовать функции и операторы JSON:

*SQL Server 2016 and JSON Support* (SQL Server 2016 и поддержка JSON)
> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support/player]

### <a name="extract-values-from-json-text-and-use-them-in-queries"></a>Извлечение значений из текста JSON и их использование в запросах
Если у вас есть текст JSON, который хранится в таблицах базы данных, вы можете прочитать или изменить значения в тексте JSON с помощью следующих встроенных функций.  
    
-   [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md) проверяет наличие в строке допустимых данных JSON.
-   [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md) извлекает из строки JSON скалярное значение.
-   [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md) извлекает из строки JSON объект или массив.
-   [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md) изменяет значение в строке JSON.


**Пример**
  
В следующем примере представлен запрос, в котором используются реляционные данные и данные JSON (хранятся в столбце `jsonCol`) из таблицы:  
  
```sql  
SELECT Name,Surname,
 JSON_VALUE(jsonCol,'$.info.address.PostCode') AS PostCode,
 JSON_VALUE(jsonCol,'$.info.address."Address Line 1"')+' '
  +JSON_VALUE(jsonCol,'$.info.address."Address Line 2"') AS Address,
 JSON_QUERY(jsonCol,'$.info.skills') AS Skills
FROM People
WHERE ISJSON(jsonCol)>0
 AND JSON_VALUE(jsonCol,'$.info.address.Town')='Belgrade'
 AND Status='Active'
ORDER BY JSON_VALUE(jsonCol,'$.info.address.PostCode')
```  
  
Приложения и средства не видят разницы между значениями, взятыми из скалярных столбцов таблицы, и значениями, взятыми из столбца JSON. Значения из текста JSON можно использовать в любой части запроса Transact-SQL (включая предложения WHERE, ORDER BY или GROUP BY, агрегатные операции с окнами и т. д.). Для ссылок на значения в тексте JSON функции JSON используют синтаксис типа JavaScript.

Дополнительные сведения см. в статьях [Проверка, создание запросов и изменение данных JSON с помощью встроенных функций (SQL Server)](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md), [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)и [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md).  
  
### <a name="change-json-values"></a>Изменение значений JSON
Если вам нужно изменить части текста JSON, используйте функцию [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md), чтобы обновить значение свойства в строке JSON и получить обновленную строку JSON. В следующем примере показано, как изменить значение свойства в переменной, которая содержит данные в формате JSON.  
  
```sql  
DECLARE @json NVARCHAR(MAX);
SET @json = '{"info":{"address":[{"town":"Belgrade"},{"town":"Paris"},{"town":"Madrid"}]}}';
SET @json = JSON_MODIFY(@json,'$.info.address[1].town','London');
SELECT modifiedJson = @json;
```  
**Результаты**  

|modifiedJson|  
|--------|  
|{"info":{"address":[{"town":"Belgrade"},{"town":"London"},{"town":"Madrid"}]}|  
  
### <a name="convert-json-collections-to-a-rowset"></a>Преобразование коллекций JSON в набор строк
Для выполнения запросов JSON в SQL Server никакой особый язык запросов не требуется. Для запроса данных JSON можно использовать стандартные инструкции T-SQL. Если вам нужно создать запрос или отчет по данным JSON, вы можете легко преобразовать данные JSON в строки и столбцы, вызвав функцию набора строк **OPENJSON**. Дополнительные сведения см. в статье [Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server)](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md).  
  
В следующем примере вызывается функция **OPENJSON**, и массив объектов, хранящийся в переменной `@json`, преобразуется в набор строк, который можно запросить с помощью стандартной инструкции SQL **SELECT**:  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json =  
N'[  
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
 ]'  
   
SELECT *  
FROM OPENJSON(@json)  
  WITH (id int 'strict $.id',  
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',  
        age int, dateOfBirth datetime2 '$.dob')  
```  
  
**Результаты**  
  
|идентификатор|firstName|lastName|age|dateOfBirth|  
|--------|---------------|--------------|---------|-----------------|  
|2|Джон|Смит|25||  
|5|Джейн|Смит||2005-11-04T12:00:00|  
  
**OPENJSON** преобразует массив объектов JSON в таблицу, где каждый объект представлен в отдельной строке, а пары "ключ —значение" возвращаются как ячейки. К выходным данным применяются следующие правила.
- **OPENJSON** преобразует значения JSON в типы, указанные в предложении **WITH**.
- **OPENJSON** может обрабатывать плоские пары ключ:значение, а также вложенные объекты с иерархической организацией.
- Все поля в тексте JSON возвращать необязательно.
- Если значений JSON нет, **OPENJSON** возвращает значения NULL.
- Путь, обозначенный после указания типа, можно использовать для ссылки на вложенное свойство или просто для ссылки на свойство с другим именем.
- Необязательный префикс **strict** в пути означает, что значения указанных свойств должны присутствовать в тексте JSON.

Дополнительные сведения см. в статьях [Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server)](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md) и [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  

Документы JSON могут содержать вложенные элементы и иерархические данные, которые невозможно напрямую сопоставить со стандартными реляционными столбцами. В этом случае можно выполнить сведение иерархии JSON посредством соединения родительской сущности с вложенными массивами.

В следующем примере второй объект в массиве содержит вложенный массив, представляющий навыки сотрудника. Каждый вложенный объект может быть проанализирован с помощью дополнительных вызовов функции `OPENJSON`: 

```sql  
DECLARE @json NVARCHAR(MAX)
SET @json =  
N'[  
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith", "skills": ["SQL", "C#", "Azure"] }, "dob": "2005-11-04T12:00:00" }  
 ]'  
   
SELECT *  
FROM OPENJSON(@json)  
  WITH (id int 'strict $.id',  
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',  
        age int, dateOfBirth datetime2 '$.dob',
    skills nvarchar(max) '$.info.skills' as json) 
    outer apply openjson( skills ) 
                     with ( skill nvarchar(8) '$' )
```  
Массив **skills** возвращается в первой функции `OPENJSON` в качестве исходного фрагмента текста JSON и передается в другую функцию `OPENJSON` с использованием оператора `APPLY`. Вторая функция `OPENJSON` анализирует массив JSON и возвращает строковые значения в виде единого набора строк столбцов, который будет соединен с результатами первой функции `OPENJSON`. Результат этого запроса показан в следующей таблице:

**Результаты**  
  
|идентификатор|firstName|lastName|age|dateOfBirth|skill|  
|--------|---------------|--------------|---------|-----------------|----------|  
|2|Джон|Смит|25|||  
|5|Джейн|Смит||2005-11-04T12:00:00|SQL| 
|5|Джейн|Смит||2005-11-04T12:00:00|C#|
|5|Джейн|Смит||2005-11-04T12:00:00|Azure|

Функция `OUTER APPLY OPENJSON` соединит сущности первого уровня с вложенным массивом и вернет преобразованный в плоскую структуру набор результатов. Из-за выполнения операции JOIN вторая строка будет повторяться для каждого навыка.

### <a name="convert-sql-server-data-to-json-or-export-json"></a>Преобразование данных SQL Server в JSON или экспортирование JSON
Данные из SQL Server в формате JSON или результаты запросов SQL можно отформатировать как JSON, добавив предложение **FOR JSON** к инструкции **SELECT** . **FOR JSON** позволяет делегировать форматирование выходных данных JSON из клиентских приложений в SQL Server. Дополнительные сведения см. в разделе [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
В следующем примере используется режим PATH с предложением **FOR JSON**.  
  
```sql  
SELECT id, firstName AS "info.name", lastName AS "info.surname", age, dateOfBirth as dob  
FROM People  
FOR JSON PATH  
```  
  
Это **FOR JSON** отформатирует результаты SQL как текст JSON, который можно предоставить любому приложению, которое понимает JSON. Параметр PATH содержит псевдонимы, разделенные точками, в предложении SELECT для вложения объектов в результаты запросов.  
  
**Результаты**  
  
```json  
[{
    "id": 2,
    "info": {
        "name": "John",
        "surname": "Smith"
    },
    "age": 25
}, {
    "id": 5,
    "info": {
        "name": "Jane",
        "surname": "Smith"
    },
    "dob": "2005-11-04T12:00:00"
}] 
```  
  
Дополнительные сведения см. в разделах [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md) и [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="use-cases-for-json-data-in-sql-server"></a>Варианты использования данных JSON в SQL Server

Поддержка JSON в SQL Server и базе данных SQL Azure позволяет объединить принципы NoSQL и реляционных баз данных. Вы можете легко преобразовывать реляционные данные в частично структурированные и наоборот. Однако JSON не заменяет существующие реляционные модели. Ниже приведены некоторые конкретные варианты использования с преимуществами поддержки JSON в SQL Server и базе данных SQL. Дополнительные сведения см. в статье о [вариантах использования JSON в SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2018/01/31/json-in-sql-server-use-cases/).

### <a name="simplify-complex-data-models"></a>Упрощение сложных моделей данных

Рассмотрите возможность денормализации модели данных с полями JSON вместо нескольких дочерних таблиц. Дополнительные сведения см. в статье об [упрощении доступа к данным с помощью денормализованных моделей](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2018/01/24/simplify-data-access-using-de-normalized-models/).

### <a name="store-retail-and-e-commerce-data"></a>Хранение данных розничной торговли и электронной коммерции

Храните сведения о продуктах, используя в денормализованной модели множество атрибутов переменных для обеспечения гибкости. Дополнительные сведения см. в статьях о [проектировании каталогов продуктов в SQL Server с помощью JSON](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/12/21/designing-product-catalogs-in-sql-server-2016-using-json/) и [индексации данных JSON в каталогах продуктов](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/12/21/indexing-data-in-json-product-catalogs/).

### <a name="process-log-and-telemetry-data"></a>Обработка данных журнала и данных телеметрии

Загружайте, запрашивайте и анализируйте данные журнала, хранящиеся в виде JSON-файлов, используя все возможности языка Transact-SQL. Дополнительные сведения см. в разделе об *анализе данных журналов и данных телеметрии* в статье о [вариантах использования JSON в SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2018/01/31/json-in-sql-server-use-cases/).

### <a name="store-semi-structured-iot-data"></a>Сохранение частично структурированных данных Интернета вещей

Чтобы проанализировать данные Интернета вещей в режиме реального времени, загружайте входящие данные непосредственно в базу данных, а не размещайте их в месте хранения. Дополнительные сведения см. в статье о [работе с данными Интернета вещей Azure в базе данных SQL Azure](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2018/01/23/working-with-azure-iot-data-in-azure-sql-database/).

### <a name="simplify-rest-api-development"></a>Упрощение разработки REST API

Легко преобразовывайте реляционные данных из базы данных в формат JSON, используемый интерфейсами REST API, которые поддерживают ваш веб-сайт. Дополнительные сведения см. в статье об [упрощении разработки REST API для современных одностраничных приложений с помощью SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2018/01/29/simplify-rest-api-development-modern-single-page-apps-sql-server/).

## <a name="combine-relational-and-json-data"></a>Объединение реляционных данных и данных JSON
SQL Server предоставляет гибридную модель для хранения и обработки реляционных данных и данных JSON с использованием стандартного языка Transact-SQL. Вы можете формировать коллекции документов JSON в таблицах, устанавливать отношения между ними, комбинировать строго типизированные скалярные столбцы, которые хранятся в таблицах с гибкими парами "ключ —значение", хранящимися в столбцах JSON, и запрашивать скалярные значения и значения JSON в одной таблице или нескольких с использованием полного Transact-SQL.
 
Текст JSON обычно хранится в столбцах varchar или nvarchar и индексируется как обычный текст. Любая функция или компонент SQL Server, которые поддерживают текст, поддерживают и JSON, поэтому в обмене данных между JSON и другими компонентами SQL Server нет практически никаких ограничений. JSON можно хранить во временных таблицах или в таблицах в памяти, применять к тексту JSON предикаты безопасности на уровне строк и т. д.

Если у вас есть рабочие нагрузки, в которых присутствует только JSON, и вы хотите использовать для них язык запросов, специально предназначенный для обработки документов JSON, рассмотрите Microsoft Azure [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/).  
  
Рассмотрим несколько способов применения встроенной поддержки JSON в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="store-and-index-json-data-in-sql-server"></a>Хранение и индексирование данных JSON в SQL Server

JSON — это текстовый формат, следовательно, документы JSON могут храниться в столбцах `NVARCHAR` в Базе данных SQL. Тип `NVARCHAR` поддерживается во всех подсистемах SQL Server, благодаря чему вы можете помещать документы JSON в таблицы с индексами **CLUSTERED COLUMNSTORE**, **оптимизированные для операций в памяти** таблицы, а также во внешние файлы, которые могут считываться с помощью OPENROWSET или Polybase.

Дополнительные сведения о возможностях хранения, индексирования и оптимизации данных JSON в SQL Server, см. в следующих статьях.
-   [Хранение документов JSON в SQL Server или базе данных SQL](store-json-documents-in-sql-tables.md)
-   [Индексирование данных JSON](index-json-data.md)
-   [Оптимизация обработки JSON с помощью выполняющейся в памяти OLTP](optimize-json-processing-with-in-memory-oltp.md)

### <a name="load-json-files-into-sql-server"></a>Загрузка файлов JSON в SQL Server  

Сведения, которые хранятся в файлах, можно отформатировать как стандартный JSON или JSON с разбивкой на строки. SQL Server может импортировать содержимое файлов JSON, проанализировать его с помощью функций **OPENJSON** или **JSON_VALUE** и загрузить их в таблицы.  
  
-   Если документы JSON хранятся в локальных файлах, на общих сетевых дисках или в хранилище файлов Azure, доступном для SQL Server, данные JSON можно загрузить в SQL Server с помощью массового импорта. Дополнительные сведения об этом сценарии см. в статье [Импорт файлов JSON в SQL Server с помощью функции OPENROWSET (BULK)](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2015/10/07/importing-json-files-into-sql-server-using-openrowset-bulk.aspx).  
  
-   Если файлы JSON с разбивкой на строки хранятся в хранилище BLOB-объектов Azure или в файловой системе Hadoop, вы можете загрузить текст JSON с помощью Polybase, проанализировать его в коде Transact-SQL и загрузить в таблицы.  

### <a name="import-json-data-into-sql-server-tables"></a>Импорт данных JSON в таблицы SQL Server  
Если требуется загрузка данных JSON из внешней службы в SQL Server, можно импортировать данные в SQL Server с помощью **OPENJSON** вместо того, чтобы использовать синтаксический анализ данных на уровне приложения.  
  
```sql  
DECLARE @jsonVariable NVARCHAR(MAX)

SET @jsonVariable = N'[  
        {  
          "Order": {  
            "Number":"SO43659",  
            "Date":"2011-05-31T00:00:00"  
          },  
          "AccountNumber":"AW29825",  
          "Item": {  
            "Price":2024.9940,  
            "Quantity":1  
          }  
        },  
        {  
          "Order": {  
            "Number":"SO43661",  
            "Date":"2011-06-01T00:00:00"  
          },  
          "AccountNumber":"AW73565",  
          "Item": {  
            "Price":2024.9940,  
            "Quantity":3  
          }  
       }  
  ]'
  
INSERT INTO SalesReport  
SELECT SalesOrderJsonData.*  
FROM OPENJSON (@jsonVariable, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData;  
```  
  
Вы можете предоставить содержимое переменной JSON из внешней службы REST, отправить его в виде параметра из платформы JavaScript на стороне клиента или загрузить из внешних файлов. Результаты можно легко вставить, обновить или объединить из текста JSON в таблицу SQL Server. Дополнительные сведения об этом сценарии см. в следующих записях блога.
-   [Импорт данных JSON в SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/09/22/openjson-the-easiest-way-to-import-json-text-into-table/)
-   [Вставка документов JSON в SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/03/upsert-json-documents-in-sql-server-2016)
-   [Загрузка данных GeoJSON в SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/)  

## <a name="analyze-json-data-with-sql-queries"></a>Анализ данных JSON с помощью запросов SQL  
Если вам нужно отфильтровать или вычислить данные JSON для целей отчетности, JSON можно преобразовать в реляционный формат с помощью **OPENJSON**. После подготовьте отчеты, используя стандартный [!INCLUDE[tsql](../../includes/tsql-md.md)] и встроенные функции.  
  
```sql  
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date  
FROM   SalesOrderRecord AS Tab  
          CROSS APPLY  
     OPENJSON (Tab.json, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData  
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'  
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified  
```  
  
В одном и том же запросе можно использовать стандартные столбцы таблицы и значения из текста JSON. Для повышения эффективности запроса можно добавить индексы в выражение `JSON_VALUE(Tab.json, '$.Status')`. Дополнительные сведения см. в разделе [Индексирование данных JSON](../../relational-databases/json/index-json-data.md).
 
## <a name="return-data-from-a-sql-server-table-formatted-as-json"></a>Возврат данных из таблицы SQL Server в формате JSON  
Если у вас есть веб-служба, которая получает данные с уровня базы данных и возвращает их в формате JSON, либо платформы или библиотеки JavaScript, которые принимают данные в формате JSON, вы можете отформатировать выходные данные JSON прямо в запросе SQL. Вместо написания кода или включения библиотеки для преобразования результатов табличных запросов и последующей сериализации объектов в формате JSON вы можете делегировать форматирование в SQL Server с помощью **FOR JSON**.  
  
Например, можно сформировать выходные данные JSON, совместимые со спецификацией OData. Веб-служба ожидает запрос и ответ в указанном ниже формате. 
  
-   Запрос: `/Northwind/Northwind.svc/Products(1)?$select=ProductID,ProductName`  
  
-   Ответ: `{"@odata.context":"http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity","ProductID":1,"ProductName":"Chai"}`  
  
URL-адрес OData представляет запрос столбцов ProductID и ProductName для продукта с `id` 1. **FOR JSON** можно использовать для форматирования выходных данных для SQL Server.  
  
```sql  
SELECT 'http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity'
 AS '@odata.context',   
 ProductID, Name as ProductName   
FROM Production.Product  
WHERE ProductID = 1  
FOR JSON AUTO  
```  
  
Выходные данные этого запроса — текст JSON, который полностью соответствует спецификации OData. Форматирование и экранирование выполняются SQL Server. SQL Server может также выдать результаты запроса в любом формате, таком как OData JSON или GeoJSON. Дополнительные сведения см. в разделе [Возврат пространственных данных в формате GeoJSON](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/returning-spatial-data-in-geojson-format-part-1).  
  
## <a name="test-drive-built-in-json-support-with-the-adventureworks-sample-database"></a>Проверка встроенной поддержки JSON с образцом базы данных AdventureWorks
Чтобы получить образец базы данных AdventureWorks, скачайте по меньшей мере файл базы данных и примеры сценариев в [Центре загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=49502). 
 
После восстановления образца базы данных в экземпляре SQL Server 2016 распакуйте файлы образца и откройте файл *JSON Sample Queries procedures views and indexes.sql* в папке JSON. Выполните сценарии в этом файле, чтобы переформатировать некоторые данные как данные JSON, протестируйте образцы запросов и отчеты по данным JSON, индексируйте данные JSON, а затем импортируйте и экспортируйте JSON.  
  
Вот, что делать с помощью скриптов, включенных в файл.  
  
* Выполнить денормализацию существующей схемы для создания столбцов данных JSON.
  
    * Сохраните данные из SalesReasons, SalesOrderDetails, SalesPerson, Customer и других таблиц, которые содержат сведения, относящиеся к заказам на продажу, в столбцы JSON таблицы SalesOrder_json.  
  
    * Сохраните данные из таблиц EmailAddresses/PersonPhone в таблицу Person_json как массивы объектов JSON.  
  
* Создайте процедуры и представления для запроса данных JSON.  
  
* Проиндексируйте данные JSON. Создайте индексы свойств JSON и полнотекстовые индексы.  
  
* Импортируйте и экспортируйте JSON. Создайте и выполните процедуры для экспорта содержимого таблиц Person и SalesOrder как результатов JSON, а затем импортируйте и обновите таблицы Person и SalesOrder, используя входные данные JSON.  
  
* Выполните примеры запросов. Выполните несколько запросов, вызывающих хранимые процедуры и представления, которые были созданы при выполнении шагов 2 и 4.  
  
* Очистите скрипты. Не выполняйте это действие, если хотите оставить хранимые процедуры и представления, которые были созданы при выполнении шагов 2 и 4.  
  
## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-blog-posts"></a>Публикации блога Майкрософт  
  
Конкретные решения, варианты использования и рекомендации см. в [записях блога](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) о встроенной поддержке JSON в SQL Server и базе данных SQL Azure.  

### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующем видео:

*Using JSON in SQL Server 2016 and Azure SQL Database* (Использование JSON в SQL Server 2016 и базе данных SQL Azure)
> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database/player]

*Создание REST API с SQL Server с помощью функций JSON*
> [!VIDEO https://www.youtube.com/embed/0m6GXF3-5WI]

### <a name="reference-articles"></a>Справочные статьи  
  
-   [Предложение FOR (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md) (FOR JSON)  
-   [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
-   [Функции JSON (Transact-SQL)](../../t-sql/functions/json-functions-transact-sql.md)  
    -   [ISJSON (Transact-SQL)](../../t-sql/functions/isjson-transact-sql.md)  
    -   [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)  
    -   [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)  
    -   [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md)  
