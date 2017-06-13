---
title: "Использование OPENJSON со схемой по умолчанию (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 2aa30c8c5e0257a819d58688c90b24782d3fd153
ms.contentlocale: ru-ru
ms.lasthandoff: 06/09/2017

---
# <a name="use-openjson-with-the-default-schema-sql-server"></a>Использование OPENJSON со схемой по умолчанию (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Использование **OPENJSON** со схемой по умолчанию возвращает таблицу, содержащую одну строку для каждого свойства объекта или для каждого элемента в массиве.  
  
 Ниже приведены несколько примеров использования **OPENJSON** со схемой по умолчанию. Дополнительные сведения и другие примеры см. в разделе [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="example---return-each-property-of-an-object"></a>Пример. Возвращение каждого свойства объекта  
 **Запрос**  
  
```sql  
SELECT *
FROM OPENJSON('{"name":"John","surname":"Doe","age":45}') 
```  
  
 **Результаты**  
  
|Key|Значение|  
|---------|-----------|  
|имя|Джон|  
|surname|Doe|  
|age|45|  
  
## <a name="example---return-each-element-of-an-array"></a>Пример. Возвращение каждого элемента массива  
 **Запрос**  
  
```sql  
SELECT [key],value
FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]') 
```  
  
 **Результаты**  
  
|Key|Значение|  
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
  
|Key|Значение|Тип|  
|---------|-----------|----------|  
|Тип|1|0|  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество определенных решений варианты использования и рекомендации, см. в разделе [записи в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базы данных SQL Azure с руководителем программ Microsoft (Jovan Popovic).
  
## <a name="see-also"></a>См. также:  
 [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
  
  

