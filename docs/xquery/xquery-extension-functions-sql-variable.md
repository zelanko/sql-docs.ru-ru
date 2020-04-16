---
title: sql:переменная() Функция (X-Образ) Документы Майкрософт
description: Узнайте, как использовать функцию расширения X'ery sql:variable() для разоблачения переменной, содержащей реляционное значение S'L внутри выражения X'ery.
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
ms.openlocfilehash: 8241e15643eb4aa25912451ddfed94699954797f
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388603"
---
# <a name="xquery-extension-functions---sqlvariable"></a>Функции расширения XQuery — sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Представляет переменную, которая содержит реляционное значение SQL внутри выражения XQuery.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>Remarks  
 Как описано в теме [Связывание реляционных данных внутри XML,](../t-sql/xml/binding-relational-data-inside-xml-data.md)вы можете использовать эту функцию, когда вы используете [методы типа данных XML,](../t-sql/xml/xml-data-type-methods.md) чтобы разоблачить реляционную ценность внутри X'ери.  
  
 Например, [метод запроса ()](../t-sql/xml/query-method-xml-data-type.md) используется для указания запроса в отношении экземпляра XML, который хранится в переменной типа данных **xml** или столбце. Иногда, если нужно одновременно передавать реляционные и XML-данные, может также потребоваться использовать в запросе значения из переменных или параметров [!INCLUDE[tsql](../includes/tsql-md.md)]. Для этого используется функция **sql:variable.**  
  
 Значение S'L будет отображено к соответствующему значению X',',ry, а его тип будет базовым типом X''s, который эквивалентен соответствующему типу S'L.  
  
 Вы можете ссылаться только на экземпляр **xml** в контексте исходного выражения оператора вставки XML-DML; в противном случае вы не можете ссылаться на значения, которые имеют тип **xml** или общий язык времени выполнения (CLR) пользовательский тип.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>A. Передача переменной Transact-SQL в XML с помощью функции sql:variable()  
 Следующий пример показывает создание экземпляра XML, в котором содержатся следующие данные:  
  
-   Значение (`ProductID`) из реляционного столбца. [Функция sql:column()](../xquery/xquery-extension-functions-sql-column.md) используется для связывания этого значения в XML.  
  
-   Значение (`ListPrice`) из реляционного столбца другой таблицы. В этом случае функция `sql:column()` также используется для связывания этого значения с XML.  
  
-   Значение (`DiscountPrice`) из переменной [!INCLUDE[tsql](../includes/tsql-md.md)]. С помощью метода `sql:variable()` это значение связывается с XML.  
  
-   Значение (`ProductModelName`) из столбца типа **xml,** чтобы сделать запрос более интересным.  
  
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
  
-   Ключевое `namespace` слово используется для определения приставки пространства имен в [X''s Prolog](../xquery/modules-and-prologs-xquery-prolog.md). Это возможно потому, что значение атрибута `ProductModelName` получается из столбца типа `CatalogDescription xml`, с которым связана схема.  
  
 Результат:  
  
```xml
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции расширения сервера X-Образ](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Сравните Типированный XML с untyped XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML данные &#40;&#41;сервера S'L](../relational-databases/xml/xml-data-sql-server.md)   
 [Создание экземпляров данных XML](../relational-databases/xml/create-instances-of-xml-data.md)   
 [методы типа данных xml](../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
