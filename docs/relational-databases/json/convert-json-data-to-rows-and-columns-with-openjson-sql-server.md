---
title: Анализ и преобразование данных JSON с помощью OPENJSON
ms.date: 07/18/2017
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OPENJSON
- JSON, importing
- importing JSON
ms.assetid: 0c139901-01e2-49ef-9d62-57e08e32c68e
author: jovanpop-msft
ms.author: jovanpop
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||= azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: feac4a3e00164837373f9b3024c322dbf7c49818
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095828"
---
# <a name="parse-and-transform-json-data-with-openjson-sql-server"></a>Анализ и преобразование данных JSON с помощью OPENJSON (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

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
|name|Джон|1|  
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

Функция **OPENJSON** доступна только при **уровне совместимости 130**. Если уровень совместимости вашей базы данных меньше 130, SQL Server не сможет найти и выполнить функцию **OPENJSON** . Другие встроенные функции JSON доступны на всех уровнях совместимости.

Проверить уровень совместимости можно в представлении `sys.databases` или в свойствах базы данных.

Изменить уровень совместимости базы данных можно с помощью следующей команды:   
`ALTER DATABASE <DatabaseName> SET COMPATIBILITY_LEVEL = 130`  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

- [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

- [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

- [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
  
## <a name="see-also"></a>См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
  