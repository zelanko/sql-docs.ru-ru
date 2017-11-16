---
title: "Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
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
manager: craigg
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 6e4a7b49bb01bd4254fad855daedd3981b2fa6a8
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="convert-json-data-to-rows-and-columns-with-openjson-sql-server"></a>Преобразование данных JSON в строки и столбцы с помощью функции OPENJSON (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Функция набора строк **OPENJSON** позволяет преобразовать текст JSON в набор строк и столбцов. После того как коллекция данных JSON будет преобразована в набор строк с помощью **OPENJSON**, вы сможете выполнять любые SQL-запросы к полученным данным или вставлять эти данные в таблицу SQL Server. 
  
Функция **OPENJSON** принимает один объект JSON или коллекцию объектов JSON и преобразовывает их в одну или несколько строк. По умолчанию функция **OPENJSON** возвращает следующие данные:
-   Из объекта JSON функция возвращает все пары "ключ-значение", которые она находит на первом уровне.
-   Из массива JSON она возвращает все элементы массива вместе с их индексами.  

Вы можете добавить дополнительное предложение **WITH**, чтобы предоставить схему, которая в явном виде определяет структуру выходных данных.  
  
## <a name="option-1---openjson-with-the-default-output"></a>Вариант 1. OPENJSON с выходными данными по умолчанию
При использовании функции **OPENJSON** без предоставления явной схемы для результатов (то есть без предложения **WITH** после **OPENJSON**) функция возвращает таблицу со следующими тремя столбцами:
1.  **Имя** свойства в поступающем на вход объекте (или индекс элемента в поступающем на вход массиве).
2.  **Значение** свойства или элемент массива.
3.  **Тип** (например, строка, число, логическое значение, массив или объект).

**OPENJSON** возвращает каждое свойство объекта JSON или каждый элемент массива в виде отдельной строки.  

Ниже приведен краткий пример, в котором **OPENJSON** используется со схемой по умолчанию (т. е. без дополнительного предложения **WITH**) и возвращает одну строку для каждого свойства JSON-объекта.  
 
**Пример**
```sql  
DECLARE @json NVARCHAR(MAX)

SET @json='{"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}';

SELECT *
FROM OPENJSON(@json);
```  
  
**Результаты**  
  
|ключ|value|type|  
|---------|-----------|----------|  
|имя|Джон|1|  
|surname|Doe|1|  
|age|45|2|  
|навыки|["SQL","C#","MVC"]|4|

### <a name="more-info-about-openjson-with-the-default-schema"></a>Дополнительные сведения об OPENJSON со схемой по умолчанию

Дополнительные сведения и примеры см. в статье [Использование функции OPENJSON со схемой по умолчанию (SQL Server)](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md).

Сведения о синтаксисе и использовании см. в статье [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md). 

    
## <a name="option-2---openjson-output-with-an-explicit-structure"></a>Вариант 2. Выходные данные OPENJSON с явной структурой
Если указана схема результатов (с помощью предложения **WITH** функции **OPENJSON**), функция возвращает таблицу только со столбцами, заданными в предложении **WITH**. В дополнительном предложении **WITH** вы можете указать набор выходных столбцов, их типы и пути исходных свойств JSON для каждого выходного значения. **OPENJSON** перебирает массив объектов JSON, считывает значение по указанному пути для каждого столбца и конвертирует его в заданный тип.  

Ниже представлен краткий пример использования **OPENJSON** с явно заданной схемой выходных данных в предложении **WITH**.  
  
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
  
|Количество|Дата|Customer|количество|  
|------------|----------|--------------|--------------|  
|SO43659|2011-05-31T00:00:00|AW29825|1|  
|SO43661|2011-06-01T00:00:00|AW73565|3|  
  
Эта функция возвращает и форматирует элементы массива JSON.  
  
-   Для каждого элемента в массиве JSON функция **OPENJSON** создает новую строку в выходной таблице. Два элемента в массиве JSON конвертируются в две строки в таблице результатов.  
  
-   Для каждого столбца, указанного с помощью синтаксиса `colName type json_path`, **OPENJSON** преобразует значение, найденное в каждом элементе массива по указанному пути, в указанный тип. В этом примере значения для столбца `Date` берутся из каждого элемента в пути `$.Order.Date` и преобразуются в значения даты и времени.  
  
### <a name="more-info-about-openjson-with-an-explicit-schema"></a>Дополнительные сведения об OPENJSON с явной схемой
Дополнительные сведения и примеры см. в статье [Использование функции OPENJSON с явной схемой (SQL Server)](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md).

Сведения о синтаксисе и использовании см. в статье [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).

## <a name="openjson-requires-compatibility-level-130"></a>OPENJSON необходим уровень совместимости 130.
Функция **OPENJSON** доступна только при **уровне совместимости 130**. Если уровень совместимости вашей базы данных меньше 130, SQL Server не сможет найти и выполнить функцию **OPENJSON**. Другие встроенные функции JSON доступны на всех уровнях совместимости.

Проверить уровень совместимости можно в представлении `sys.databases` или в свойствах базы данных.

Изменить уровень совместимости базы данных можно с помощью следующей команды:   
`ALTER DATABASE <DatabaseName> SET COMPATIBILITY_LEVEL = 130`  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Много определенных решений, варианты использования и рекомендации см. в [записях блога о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) (категории SQL Server и Azure SQL Database (База данных SQL Azure), автор — руководитель программ корпорации Майкрософт Йован Попович (Jovan Popovic)).
  
## <a name="see-also"></a>См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
  
  

