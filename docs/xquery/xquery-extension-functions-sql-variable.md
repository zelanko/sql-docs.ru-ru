---
title: 'Функция SQL: variable () (XQuery) | Документация Майкрософт'
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
ms.openlocfilehash: 56a8c53a22fefec7fbda4c2ac7476ae46d664199
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946005"
---
# <a name="xquery-extension-functions---sqlvariable"></a>Функции расширения XQuery — sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Представляет переменную, которая содержит реляционное значение SQL внутри выражения XQuery.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>Remarks  
 Как описано в разделе [Привязка реляционных данных в XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), эту функцию можно использовать при использовании [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md) для предоставления реляционного значения в XQuery.  
  
 Например, [метод query ()](../t-sql/xml/query-method-xml-data-type.md) используется для указания запроса к экземпляру XML, который хранится в переменной или столбце типа данных **XML** . Иногда, если нужно одновременно передавать реляционные и XML-данные, может также потребоваться использовать в запросе значения из переменных или параметров [!INCLUDE[tsql](../includes/tsql-md.md)]. Для этого используется функция **SQL: variable** .  
  
 Значение SQL будет сопоставлено с соответствующим значением XQuery, а его тип будет базовым типом XQuery, эквивалентным соответствующему типу SQL.  
  
 Ссылаться на экземпляр **XML** можно только в контексте исходного выражения инструкции INSERT XML-DML. в противном случае нельзя ссылаться на значения, имеющие тип **XML** или определяемый пользователем тип среды CLR.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>A. Передача переменной Transact-SQL в XML с помощью функции sql:variable()  
 Следующий пример показывает создание экземпляра XML, в котором содержатся следующие данные:  
  
-   Значение (`ProductID`) из реляционного столбца. [Функция SQL: column ()](../xquery/xquery-extension-functions-sql-column.md) используется для привязки этого значения в XML.  
  
-   Значение (`ListPrice`) из реляционного столбца другой таблицы. В этом случае функция `sql:column()` также используется для связывания этого значения с XML.  
  
-   Значение (`DiscountPrice`) из переменной [!INCLUDE[tsql](../includes/tsql-md.md)]. С помощью метода `sql:variable()` это значение связывается с XML.  
  
-   Значение (`ProductModelName`) из столбца типа **XML** , чтобы сделать запрос более интересным.  
  
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
  
## <a name="see-also"></a>См. также:  
 [SQL Server функции расширения XQuery](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Сравнение типизированного XML с нетипизированным XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [SQL Server &#40;XML-данных&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Создание экземпляров XML-данных](../relational-databases/xml/create-instances-of-xml-data.md)   
 [Методы типа данных XML](../t-sql/xml/xml-data-type-methods.md)   
 [Язык изменения XML-данных &#40;XML DML&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
