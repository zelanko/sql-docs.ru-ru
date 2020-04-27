---
title: Использование OPENJSON со схемой по умолчанию
ms.date: 06/02/2016
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: genemi
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 633737d8dd302d6546662fb048c3f3e1ea50c19b
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087364"
---
# <a name="use-openjson-with-the-default-schema"></a>Использование OPENJSON со схемой по умолчанию 
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Использование **OPENJSON** со схемой по умолчанию возвращает таблицу, содержащую одну строку для каждого свойства объекта или для каждого элемента в массиве.  
  
 Ниже приведены несколько примеров использования **OPENJSON** со схемой по умолчанию. Дополнительные сведения и другие примеры см. в разделе [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="example---return-each-property-of-an-object"></a>Пример. Возвращение каждого свойства объекта  
 **Запрос**  
  
```sql  
SELECT *
FROM OPENJSON('{"name":"John","surname":"Doe","age":45}') 
```  
  
 **Результаты**  
  
|Клавиши|Значение|  
|---------|-----------|  
|name|Джон|  
|surname|Doe|  
|age|45|  
  
## <a name="example---return-each-element-of-an-array"></a>Пример. Возвращение каждого элемента массива  
 **Запрос**  
  
```sql  
SELECT [key],value
FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]') 
```  
  
 **Результаты**  
  
|Клавиши|Значение|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
  
## <a name="example---convert-json-to-a-temporary-table"></a>Пример. Преобразование JSON во временную таблицу  
 Следующий запрос возвращает все свойства объекта **info** .  
  
```sql  
DECLARE @json NVARCHAR(MAX)

SET @json=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }'

SELECT *
FROM OPENJSON(@json,N'lax $.info')
```  
  
 **Результаты**  
  
|Клавиши|Значение|Тип|  
|---------|-----------|----------|  
|type|1|0|  
|address|{ "town":"Bristol", "county":"Avon", "country":"England" }|5|  
|tags|[ "Sport", "Water polo" ]|4|  
  
## <a name="example---combine-relational-data-and-json-data"></a>Пример. Объединение реляционных данных и данных JSON  
 В следующем примере таблица SalesOrderHeader имеет текстовый столбец SalesReason, содержащий массив SalesOrderReasons в формате JSON. Объекты SalesOrderReasons содержат такие свойства, как "Manufacturer" и "Quality". Пример создает отчет, который соединяет каждую строку заказа на продажу со связанными причинами покупки, развернув массив JSON причин покупки, как если бы причины хранились в отдельной дочерней таблице.  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
 В этом примере OPENJSON возвращает таблицу причин покупки, в которой причины отображаются как столбец значений. Оператор CROSS APPLY соединяет каждую строку заказа на продажу со строками, возвращенными функцией с табличным значением OPENJSON.  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
  
## <a name="see-also"></a>См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
