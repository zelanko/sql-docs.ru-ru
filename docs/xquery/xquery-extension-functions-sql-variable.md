---
title: "SQL: variable() (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- sql:variable() function
- sql:variable function
ms.assetid: 6e2e5063-c1cf-4b5a-b642-234921e3f4f7
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ffacec1b08bd0fa4fed107a1149273034057e405
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="xquery-extension-functions---sqlvariable"></a>Функции расширения XQuery - функции SQL: variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Представляет переменную, которая содержит реляционное значение SQL внутри выражения XQuery.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>Замечания  
 Как описано в разделе [Привязка реляционных данных внутри XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), эту функцию можно использовать при использовании [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md) для предоставления к реляционному значению внутри XQuery.  
  
 Например [метода query()](../t-sql/xml/query-method-xml-data-type.md) используется для указания запроса к экземпляру XML, который хранится в **xml** переменной или столбце типа данных. Иногда, если нужно одновременно передавать реляционные и XML-данные, может также потребоваться использовать в запросе значения из переменных или параметров [!INCLUDE[tsql](../includes/tsql-md.md)]. Чтобы сделать это, используйте **SQL: variable** функции.  
  
 Значение SQL будет сопоставлено с соответствующим значением XQuery и типом будет присвоен базовый тип XQuery, эквивалентный соответствующему типу SQL.  
  
 Может ссылаться только на **xml** инструкция insert экземпляр в контексте исходного выражения XML DML; в противном случае нельзя ссылаться на значения, которые относятся к типу **xml** или общеязыковая среда выполнения (CLR) определяемый пользователем тип.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>A. Передача переменной Transact-SQL в XML с помощью функции sql:variable()  
 Следующий пример показывает создание экземпляра XML, в котором содержатся следующие данные:  
  
-   Значение (`ProductID`) из реляционного столбца. [Функции SQL: column()](../xquery/xquery-extension-functions-sql-column.md) используется для связывания этого значения в XML.  
  
-   Значение (`ListPrice`) из реляционного столбца другой таблицы. В этом случае функция `sql:column()` также используется для связывания этого значения с XML.  
  
-   Значение (`DiscountPrice`) из переменной [!INCLUDE[tsql](../includes/tsql-md.md)]. С помощью метода `sql:variable()` это значение связывается с XML.  
  
-   Значение (`ProductModelName`) из **xml** тип столбца, чтобы сделать запрос более интересным.  
  
 Запрос является таковым:  
  
```  
DECLARE @price money  
  
SET @price=2500.00  
SELECT ProductID, Production.ProductModel.ProductModelID,CatalogDescription.query('  
declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
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
  
```  
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции расширения запросов XQuery в SQL Server](http://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Сравнение типизированного и нетипизированного XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Создание экземпляров XML-данных](../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных &#40; Язык XML DML &#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
