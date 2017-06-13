---
title: "Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OPENJSON
- JSON, importing
- importing JSON
ms.assetid: 0c139901-01e2-49ef-9d62-57e08e32c68e
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: c153135f84f7cb9671840a55f29927fb06ea819e
ms.contentlocale: ru-ru
ms.lasthandoff: 06/09/2017

---
# <a name="convert-json-data-to-rows-and-columns-with-openjson-sql-server"></a>Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Функция набора строк **OPENJSON** позволяет преобразовать текст JSON в набор строк и столбцов. Используйте функцию **OPENJSON** для выполнения запросов SQL к коллекциям JSON или для импорта текста JSON в таблицы SQL Server.  
  
 Функция **OPENJSON** принимает один объект JSON или коллекцию объектов JSON и преобразовывает их в одну или несколько строк. По умолчанию **эта** функция возвращает следующие данные.
-   Из объекта JSON — все пары "ключ —значение", которые находятся на первом уровне.
-   Из массива JSON — все элементы массива вместе с индексами.  
  
При необходимости добавьте предложение **WITH** для указания схемы строк, которую возвращает функция **OPENJSON**. Эта явная схема определяет структуру выходных данных.  
  
## <a name="use-openjson-without-an-explicit-schema-for-the-output"></a>Использование функции OPENJSON без явной схемы вывода
Если функция **OPENJSON** используется без указания явной схемы результатов (т. е. без предложения **WITH** после OPENJSON), она возвращает таблицу со следующими тремя столбцами:
1.  Имя свойства входного объекта (или индекс элемента входного массива).
2.  Значение свойства или элемента массива.
3.  Тип (например, строка, число, логическое значение, массив или объект).

Каждое свойство объекта JSON или каждый элемент массива возвращается в виде отдельной строки.  

Ниже приведен краткий пример, который использует **OPENJSON** со схемой по умолчанию и возвращает одну строку для каждого свойства объекта JSON.  
 
**Пример**
```sql  
DECLARE @json NVARCHAR(MAX)

SET @json='{"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}';

SELECT *
FROM OPENJSON(@json);
```  
  
**Результаты**  
  
|Key|value|type|  
|---------|-----------|----------|  
|имя|Джон|1|  
|surname|Doe|1|  
|age|45|2|  
|навыки|["SQL","C#","MVC"]|4|

### <a name="more-info"></a>Дополнительные сведения

Дополнительные сведения и примеры см. в статье [Использование функции OPENJSON со схемой по умолчанию (SQL Server)](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md).

Сведения о синтаксисе и использовании см. в статье [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md). 

    
## <a name="use-openjson-with-an-explicit-schema-for-the-output"></a>Использование функции OPENJSON с явной схемой вывода
Если указана схема результатов (с помощью предложения **WITH** функции **OPENJSON**), функция возвращает таблицу только со столбцами, заданными в предложении **WITH**. В предложении **WITH** укажите набор выходных столбцов, их типы и пути исходных свойств JSON для каждого выходного значения. **OPENJSON** перебирает массив объектов JSON, считывает значение по указанному пути для каждого столбца и конвертирует его в заданный тип.  

Ниже представлен краткий пример использования функции **OPENJSON** с явно заданной схемой результатов.  
  
**Пример**
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json =   
  N'[  
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
   
SELECT * FROM  
 OPENJSON ( @json )  
WITH (   
              Number   varchar(200) '$.Order.Number' ,  
              Date     datetime     '$.Order.Date',  
              Customer varchar(200) '$.AccountNumber',  
              Quantity int          '$.Item.Quantity'  
 ) 
```  
  
**Результаты**  
  
|Количество|Дата|Customer|Количество|  
|------------|----------|--------------|--------------|  
|SO43659|2011-05-31T00:00:00|AW29825|1|  
|SO43661|2011-06-01T00:00:00|AW73565|3|  
  
 Эта функция возвращает и форматирует элементы массива JSON.  
  
-   Для каждого элемента в массиве JSON функция **OPENJSON** создает новую строку в выходной таблице. Два элемента в массиве JSON конвертируются в две строки в таблице результатов.  
  
-   Для каждого столбца, указанного с помощью синтаксиса `colName type json_path`, функция **OPENJSON** конвертирует значение, найденное в каждом элементе массива по указанному пути, в указанный тип и заполняет ячейки в таблице результатов. В этом примере значения для столбца `Date` взяты из каждого объекта в пути `$.Order.Date` и конвертированы в значения даты и времени.  
  
После того как коллекция данных JSON будет преобразована в набор строк с помощью **OPENJSON**, можно выполнить любой запрос SQL к полученным данным или вставить их в любую таблицу.  

### <a name="more-info"></a>Дополнительные сведения
Дополнительные сведения и примеры см. в статье [Использование функции OPENJSON с явной схемой (SQL Server)](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md).

Сведения о синтаксисе и использовании см. в статье [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).

## <a name="openjson-requires-compatibility-level-130"></a>OPENJSON необходим уровень совместимости 130
Функция **OPENJSON** доступна только при **уровне совместимости 130**. Если уровень совместимости базы данных меньше 130, SQL Server не сможет найти и выполнить функцию **OPENJSON** . Другие встроенные функции JSON доступны на всех уровнях совместимости. Проверить уровень совместимости можно в представлении sys.databases или в свойствах базы данных.

Изменить уровень совместимости базы данных можно с помощью следующей команды:   
`ALTER DATABASE <DatabaseName> SET COMPATIBILITY_LEVEL = 130`  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество определенных решений варианты использования и рекомендации, см. в разделе [записи в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базы данных SQL Azure с руководителем программ Microsoft (Jovan Popovic).
  
## <a name="see-also"></a>См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
  
  

