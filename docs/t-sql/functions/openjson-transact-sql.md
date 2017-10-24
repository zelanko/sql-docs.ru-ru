---
title: "OPENJSON (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENJSON
- OPENJSON_TSQL
helpviewer_keywords:
- OPENJSON rowset function
- JSON, importing
- JSON, converting from
ms.assetid: 233d0877-046b-4dcc-b5da-adeb22f78531
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: 27eeb54d6493bb200e56caada1238d6fafb5b339
ms.contentlocale: ru-ru
ms.lasthandoff: 10/11/2017

---
# <a name="openjson-transact-sql"></a>OPENJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

**OPENJSON** является табличная функция, которая выполняет синтаксический анализ текста JSON и возвращает объекты и свойства из входных данных JSON в виде строк и столбцов. Другими словами **OPENJSON** предоставляет представления наборов строк документа JSON. Можно явно указать столбцы в наборе строк и пути к свойствам JSON, используемый для заполнения столбцов. Поскольку **OPENJSON** возвращает набор строк, можно использовать **OPENJSON** в `FROM` предложения [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции так же, как можно использовать таблицу, представление или табличную функцию.  
  
Используйте **OPENJSON** для импорта данных JSON в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или преобразовать данные JSON в реляционный формат для приложения или службы, не могут использовать JSON напрямую.  
  
> [!NOTE]  
>  **OPENJSON** функция доступна только при уровне совместимости 130 или более поздней версии. Если уровень совместимости вашей базы данных меньше 130, SQL Server не сможет найти и выполнить функцию **OPENJSON**. Другие функции JSON доступны на всех уровнях совместимости.
> 
> Проверить уровень совместимости можно в представлении `sys.databases` или в свойствах базы данных. Можно изменить уровень совместимости базы данных с помощью следующей команды:  
> 
> `ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130`
>   
> При уровне совместимости 120 могут использоваться по умолчанию даже в новую базу данных SQL Azure.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел")[синтаксические обозначения Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
OPENJSON( jsonExpression [ , path ] )  [ <with_clause> ]

<with_clause> ::= WITH ( { colName type [ column_path ] [ AS JSON ] } [ ,...n ] )
```  

**OPENJSON** табличная функция выполняет синтаксический анализ *jsonExpression* указанные в качестве первого аргумента и возвращает одну или несколько строк, содержащих данные из объектов JSON в выражении. *jsonExpression* может содержать вложенные подчиненных объектах. Если вы хотите проанализировать дочерний объект изнутри *jsonExpression*, можно указать **путь** параметр для подчиненного объекта JSON.

### <a name="openjson"></a>openjson

![Синтаксис для возвращающей табличное значение функции OPENJSON](../../relational-databases/json/media/openjson-syntax.png "синтаксисом OPENJSON")  

По умолчанию **OPENJSON** табличная функция возвращает три столбца, содержащих имя ключа, значение и тип каждой пары {ключ: значение} найден в *jsonExpression*. Кроме того, можно явно указать схему результирующего набора, **OPENJSON** возвращает, предоставляя *with_clause*.
  
### <a name="withclause"></a>with_clause
  
![Синтаксис с предложением в возвращающей табличное значение функции OPENJSON](../../relational-databases/json/media/openjson-shema-syntax.png "OPENJSON с помощью синтаксиса")

*with_clause* содержит список столбцов с их типами для **OPENJSON** для возврата. По умолчанию **OPENJSON** соответствует ключей в *jsonExpression* с именами столбцов в *with_clause* (в этом случае ключи совпадений подразумевает, что существует с учетом регистра). Если имя столбца не соответствует имени ключа, можно предоставить необязательный *column_path*, который является [выражения пути JSON](../../relational-databases/json/json-path-expressions-sql-server.md) , ссылается на ключ в *jsonExpression*. 

## <a name="arguments"></a>Аргументы  
### <a name="jsonexpression"></a>*jsonExpression*  
Символьное выражение Юникода, содержащий текст JSON.  
  
OPENJSON выполняет итерацию по элементам массива или свойства объекта в выражении JSON и возвращает одну строку для каждого элемента или свойства. В следующем примере возвращается каждого свойства объекта, как *jsonExpression*:  
  
```sql  
DECLARE @json NVARCHAR(4000) = N'{  
   "StringValue":"John",  
   "IntValue":45,  
   "TrueValue":true,  
   "FalseValue":false,  
   "NullValue":null,  
   "ArrayValue":["a","r","r","a","y"],  
   "ObjectValue":{"obj":"ect"}  
}'

SELECT *
FROM OPENJSON(@json)
```  
  
**Результаты**  
  
|ключ|value|Тип|  
|---------|-----------|----------|  
|StringValue|Джон|1|  
|IntValue|45|2|  
|trueValue|true|3|  
|falseValue|false|3|  
|nullValue|NULL|0|  
|ArrayValue|[«», «r», «r», «y «,»»]|4|  
|ObjectValue|{«obj»: «и»}|5|  

### <a name="path"></a>*путь*  
Необязательное выражение пути JSON, ссылается на объект или массив в *jsonExpression*. **OPENJSON** операций поиска в текст JSON в указанной позиции и анализирует только фрагмент, на которую указывает ссылка. Дополнительные сведения см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).

В [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], можно ввести в качестве значения переменной *путь*.
  
Следующий пример возвращает вложенный объект, указывая *путь*:  

```sql  
DECLARE @json NVARCHAR(4000) = N'{  
      "path": {  
            "to":{  
                 "sub-object":["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]  
                 }  
              }  
 }';

SELECT [key], value
FROM OPENJSON(@json,'$.path.to."sub-object"')
```  
  
 **Результаты**  
  
|Key|Значение|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
 
Когда **OPENJSON** анализирует массив JSON, функция возвращает индексы элементов в тексте JSON как ключи.

Сравнение, используемое для сопоставления действия пути с помощью свойств JSON выражение с учетом регистра и не зависимых от параметров сортировки (то есть BIN2 сравнение). 

### <a name="withclause"></a>*with_clause*
Явным образом определяет выходные данные схемы для **OPENJSON** функции для возврата. Необязательный *with_clause* может содержать следующие элементы:

*colName* имя выходного столбца.  
  
По умолчанию **OPENJSON** использует имя столбца для сопоставления свойства в тексте JSON. Например, если указать столбец *имя* в схеме, пытается заполнение этого столбца со свойством «name» в тексте JSON OPENJSON. Это сопоставление по умолчанию можно переопределить с помощью *column_path* аргумент.  
  
*type*  
— Тип данных для выходного столбца.  

> [!NOTE]
> При использовании **AS JSON** параметр столбца *тип* должен быть `NVARCHAR(MAX)`.
  
*column_path*  
Это путь JSON, который определяет свойство для возврата в указанном столбце. Дополнительные сведения см. в описании *путь* параметр ранее в этом разделе.  
  
Используйте *column_path* для переопределения правила сопоставления по умолчанию, когда имя выходного столбца не соответствует имени свойства.  
  
Сравнение, используемое для сопоставления действия пути с помощью свойств JSON выражение с учетом регистра и не зависимых от параметров сортировки (то есть BIN2 сравнение).  
  
Дополнительные сведения о путях см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
*КАК JSON*  
Используйте **AS JSON** параметр в определении столбца, чтобы указать, что для указанного свойства содержит внутренний объект JSON или массива. При указании **AS JSON** , тип столбца должна быть NVARCHAR(MAX).

-   Если не указать **AS JSON** для столбца, функция возвращает скалярное значение (например, int, string, значение true, false) из заданного свойства JSON в заданном пути. Если путь представляет объект или массив, а не найти свойство по указанному пути, функция возвращает значение null, в режиме lax или возвращает сообщение об ошибке в строгом режиме. Это поведение аналогично поведению элемента **JSON_VALUE** функции.  
  
-   При указании **AS JSON** для столбца, функция возвращает фрагмент JSON из заданного свойства JSON в заданном пути. Если путь представляет скалярное значение, а не найти свойство по указанному пути, функция возвращает значение null, в режиме lax или возвращает сообщение об ошибке в строгом режиме. Это поведение аналогично поведению элемента **JSON_QUERY** функции.  
  
> [!NOTE]  
> Если вы хотите вернуть фрагмент JSON вложенных из свойства JSON, вы должны предоставить **AS JSON** флаг. Без этого параметра если не удается найти свойство, OPENJSON возвращает значение NULL вместо упоминаемого объекта JSON или массива, или он возвращает ошибку времени выполнения в строгом режиме.  
  
Например следующий запрос возвращает и форматирует элементы массива:  
  
```sql  
DECLARE @json NVARCHAR(MAX) = N'[  
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
   
SELECT *
FROM OPENJSON ( @json )  
WITH (   
              Number   varchar(200)   '$.Order.Number',  
              Date     datetime       '$.Order.Date',  
              Customer varchar(200)   '$.AccountNumber',  
              Quantity int            '$.Item.Quantity',  
              [Order]  nvarchar(MAX)  AS JSON  
 )
```  
  
**Результаты**  
  
|Количество|Дата|Customer|количество|Порядок|  
|------------|----------|--------------|--------------|-----------|  
|SO43659|2011-05-31T00:00:00|AW29825|1|{«Number»: «SO43659», «Date»: «2011-05-31T00:00:00»}|  
|SO43661|2011-06-01T00:00:00|AW73565|3|{«Number»: «SO43661», «Date»: «2011-06-01T00:00:00»}|  
  

## <a name="return-value"></a>Возвращаемое значение  
Столбцы, которые возвращает функция OPENJSON зависит от параметра WITH.  
  
1. При вызове OPENJSON со схемой по умолчанию — то есть при явной схемой не указан в предложении WITH - функция возвращает таблицу со следующими столбцами:  
    1.  **Ключ**. Значение nvarchar(4000), содержащее имя указанного свойства или индекс элемента в указанном массиве. Ключевой столбец имеет параметры сортировки BIN2.  
    2.  **Значение**. Значение типа nvarchar(max), содержащее значение свойства. Значение столбца наследует параметры сортировки из *jsonExpression*.
    3.  **Тип**. Целочисленное значение, содержащее тип значения. **Тип** столбца, возвращается только в том случае, когда использование OPENJSON со схемой по умолчанию. Столбец типа может иметь одно из следующих значений:  
  
        |Значение типа столбца|Тип данных JSON|  
        |------------------------------|--------------------|  
        |0|null|  
        |1|строка|  
        |2|int|  
        |3|значение true или false|  
        |4|массиве|  
        |5|объект|  
  
     Возвращаются только свойства первого уровня. Выполнение инструкции завершается неудачно, если текст JSON имеет неправильный формат.  

2. При вызове OPENJSON, укажите явной схемой в предложении WITH, функция возвращает таблицу со схемой, определенные в предложении WITH.  

## <a name="remarks"></a>Замечания  

*json_path* используется в качестве второго аргумента из **OPENJSON** или в *with_clause* можно начать с **нестрогой** или **strict** Ключевое слово.

-   В **нестрогой** режиме **OPENJSON** не вызывает ошибку, если не удается найти объект или значение по указанному пути. Если не удается найти путь, **OPENJSON** возвращает пустой результирующий набор или значение NULL.
-   В **strict**, режим **OPENJSON** возвращает ошибку, если путь не найден.

Некоторые примеры на этой странице явно указать режим path значениями lax или strict. Режим path является необязательным. Если режим path не указан явно, нестрогой режим используется по умолчанию. Дополнительные сведения о режиме path и выражениях пути см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).    

Имена столбцов в *with_clause* сопоставляются с ключами в тексте JSON. Если указать имя столбца `[Address.Country]`, он сопоставляется с ключом `Address.Country`. Если требуется сослаться на ключ вложенной таблицы `Country` внутри объекта `Address`, нужно указать путь `$.Address.Country` в пути к столбцу.

*json_path* может содержать ключи с буквенно-цифровые символы. Имя ключа в escape- *json_path* в двойные кавычки, если у вас есть специальные символы в ключах. Например `$."my key $1".regularKey."key with . dot"` соответствует значение 1 в следующий текст JSON:

```json
{
  "my key $1": {
    "regularKey":{
      "key with . dot": 1
    }
  }
}
```  

## <a name="examples"></a>Примеры  
  
### <a name="example-1---convert-a-json-array-to-a-temporary-table"></a>Пример 1 - преобразование массива JSON во временную таблицу  
Приведенный ниже список идентификаторов как массив JSON чисел. Запрос преобразует массив JSON в таблицу идентификаторов и фильтрует все продукты с указанными идентификаторами.  
  
```sql  
DECLARE @pSearchOptions NVARCHAR(4000) = N'[1,2,3,4]'

SELECT *
FROM products
INNER JOIN OPENJSON(@pSearchOptions) AS productTypes
 ON product.productTypeID = productTypes.value
```  
  
Этот запрос эквивалентен приведенному ниже. Тем не менее в приведенном ниже примере необходимо внедрить чисел в запрос вместо передачи их в качестве параметров.  
  
```sql  
SELECT *
FROM products
WHERE product.productTypeID IN (1,2,3,4)
```  
  
### <a name="example-2---merge-properties-from-two-json-objects"></a>Пример 2. свойства слияния из двух объектов JSON  
В следующем примере выбираются объединение всех свойств двух объектов JSON. Оба объекта имеют дубликат *имя* свойства. В примере используется значение ключа, чтобы исключить повторяющиеся строки из результатов.  
  
```sql  
DECLARE @json1 NVARCHAR(MAX),@json2 NVARCHAR(MAX)

SET @json1=N'{"name": "John", "surname":"Doe"}'

SET @json2=N'{"name": "John", "age":45}'

SELECT *
FROM OPENJSON(@json1)
UNION ALL
SELECT *
FROM OPENJSON(@json2)
WHERE [key] NOT IN (SELECT [key] FROM OPENJSON(@json1))
```  
  
### <a name="example-3---join-rows-with-json-data-stored-in-table-cells-using-cross-apply"></a>Пример 3 строки соединения с данными JSON, хранящихся в ячейках таблицы с помощью CROSS APPLY.  
В следующем примере `SalesOrderHeader` таблица имеет `SalesReason` текстовый столбец, содержащий массив `SalesOrderReasons` в формате JSON. `SalesOrderReasons` Объекты содержат такие свойства, как *качество* и *производителя*. В примере создается отчет, который соединяет каждую строку заказа на продажу на со связанными причинами покупки. Оператор OPENJSON расширяется массив JSON причин покупки, как если бы причины хранились в отдельной дочерней таблице. Затем оператор CROSS APPLY соединяет каждую строку заказа на продажу для строк, возвращаемых функцией табличным значением OPENJSON.  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
> [!TIP] 
> При необходимости разверните массивы JSON хранятся в отдельных полей и соединить их родительских строк, как правило, используется [!INCLUDE[tsql](../../includes/tsql-md.md)] оператора CROSS APPLY. Дополнительные сведения о CROSS APPLY см. в разделе [FROM &#40; Transact-SQL &#41; ](../../t-sql/queries/from-transact-sql.md).  
  
Тот же запрос можно переписать с методом `OPENJSON` с явно определенной схемой возвращаемых строк:  
  
```sql  
SELECT SalesOrderID, OrderDate, value AS Reason  
FROM Sales.SalesOrderHeader  
     CROSS APPLY OPENJSON (SalesReasons) WITH (value nvarchar(100) '$')
```  
  
В этом примере `$` путь ссылается на каждый элемент в массиве. Если необходимо явно привести возвращаемое значение, можно использовать этот тип запроса.  
  
### <a name="example-4---combine-relational-rows-and-json-elements-with-cross-apply"></a>Пример 4. Объединение реляционных строк и элементы JSON с CROSS APPLY  
Следующий запрос объединяет реляционные строк и элементы JSON в результаты, показанные в следующей таблице.  
  
```sql  
SELECT store.title, location.street, location.lat, location.long  
FROM store  
CROSS APPLY OPENJSON(store.jsonCol, 'lax $.location')   
     WITH (street varchar(500) ,  postcode  varchar(500) '$.postcode' ,  
     lon int '$.geo.longitude', lat int '$.geo.latitude')  
     AS location
```  
  
**Результаты**  
  
|title|Улица|Индекс|lon|LAT|  
|-----------|------------|--------------|---------|---------|  
|Всего Food рынки|Способ Redmond 17991|WA 98052|47.666124|-122.10155|  
|Sears|148th Ave NE|WA 98052|47.63024|-122.141246,17|  
  
### <a name="example-5---import-json-data-into-sql-server"></a>Пример 5 - Импорт данных JSON в SQL Server  
В следующем примере весь объект JSON загружается в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```sql  
DECLARE @json NVARCHAR(max)  = N'{  
  "id" : 2,  
  "firstName": "John",  
  "lastName": "Smith",  
  "isAlive": true,  
  "age": 25,  
  "dateOfBirth": "2015-03-25T12:00:00",  
  "spouse": null  
  }';  
   
  INSERT INTO Person  
  SELECT *   
  FROM OPENJSON(@json)  
  WITH (id int,  
        firstName nvarchar(50), lastName nvarchar(50),   
        isAlive bit, age int,  
        dateOfBirth datetime2, spouse nvarchar(50)
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения пути JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON &#40; SQL Server &#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)   
 [Использование OPENJSON со схемой по умолчанию &#40; SQL Server &#41;](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md)   
 [Использование функции OPENJSON с явной схемой &#40; SQL Server &#41;](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md)  
  
  

