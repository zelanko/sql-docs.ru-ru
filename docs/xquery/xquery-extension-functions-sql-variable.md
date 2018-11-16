---
title: 'SQL: variable() (XQuery) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:variable() function
- sql:variable function
ms.assetid: 6e2e5063-c1cf-4b5a-b642-234921e3f4f7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fe1115c7e0cf0e4f78ff09acb405c64912af3471
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51658003"
---
# <a name="xquery-extension-functions---sqlvariable"></a>Функции расширения XQuery — sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Представляет переменную, которая содержит реляционное значение SQL внутри выражения XQuery.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>Примечания  
 Как описано в разделе [Привязка реляционных данных внутри XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), эту функцию можно использовать при использовании [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md) на доступ к реляционному значению внутри XQuery.  
  
 Например [метода query()](../t-sql/xml/query-method-xml-data-type.md) используется для указания запроса к экземпляру XML, который хранится в **xml** переменной или столбце типа данных. Иногда, если нужно одновременно передавать реляционные и XML-данные, может также потребоваться использовать в запросе значения из переменных или параметров [!INCLUDE[tsql](../includes/tsql-md.md)]. Чтобы сделать это, используйте **SQL: variable** функции.  
  
 Значение SQL будет сопоставлено с соответствующим значением XQuery, и его тип будет присвоен базовый тип XQuery, которое эквивалентно значению в соответствующий тип SQL.  
  
 Может ссылаться только на **xml** инструкция insert экземпляр в контексте исходного выражения XML DML; в противном случае нельзя ссылаться на значения, которые относятся к типу **xml** или среда CLR (CLR) определяемый пользователем тип.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>A. Передача переменной Transact-SQL в XML с помощью функции sql:variable()  
 Следующий пример показывает создание экземпляра XML, в котором содержатся следующие данные:  
  
-   Значение (`ProductID`) из реляционного столбца. [Функция SQL: column()](../xquery/xquery-extension-functions-sql-column.md) используется для привязки этого значения в XML.  
  
-   Значение (`ListPrice`) из реляционного столбца другой таблицы. В этом случае функция `sql:column()` также используется для связывания этого значения с XML.  
  
-   Значение (`DiscountPrice`) из переменной [!INCLUDE[tsql](../includes/tsql-md.md)]. С помощью метода `sql:variable()` это значение связывается с XML.  
  
-   Значение (`ProductModelName`) из **xml** тип столбца, чтобы сделать запрос более интересным.  
  
 Запрос является таковым:  
  
```sql
DECLARE @price money  
  
SET @price=2500.00  
SELECT ProductID, Production.ProductModel.ProductModelID,CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
       <Product   
           ProductID="{ sql:column("Production.Product.ProductID") }"  
           ProductModelID= "{ sql:column("Production.Product.ProductModelID") }"  
           ProductModelName="{/pd:ProductDescription[1]/@ProductModelName }"  
           ListPrice="{ sql:column("Production.Product.ListPrice") }"  
           DiscountPrice="{ sql:variable("@price") }"  
        />')   
FROM Production.Product   
JOIN Production.ProductModel  
ON Production.Product.ProductModelID = Production.ProductModel.ProductModelID  
WHERE ProductID=771  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   XQuery внутри метода `query()` формирует XML.  
  
-   `namespace` Ключевое слово используется для определения префикса пространства имен в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md). Это возможно потому, что значение атрибута `ProductModelName` получается из столбца типа `CatalogDescription xml`, с которым связана схема.  
  
 Результат:  
  
```xml
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>См. также  
 [Функции расширения XQuery для SQL Server](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Сравнение типизированного и нетипизированного XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Создание экземпляров XML-данных](../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
