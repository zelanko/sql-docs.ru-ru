---
title: "Метод Query() (тип данных xml) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: db0f9b1ffc4c6ca13084942144e13d64765d7019
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="query-method-xml-data-type"></a>query() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет запрос XQuery для экземпляра **xml** тип данных. Результат имеет **xml** типа. Метод возвращает экземпляр нетипизированного XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>Аргументы  
 XQuery  
 Это строка, выражение XQuery, выполняющее в экземпляре XML запросы к узлам — элементам и атрибутам.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры использования метода query() **xml** тип данных.  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. Использование метода query() для переменной типа xml  
 В следующем примере объявляется переменная  **@myDoc**  из **xml** введите и присваивает ей экземпляр XML. **Query()** метод используется для задания запроса XQuery к документу.  
  
 Запрос извлекает дочерний элемент <`Features`> элемента <`ProductDescription`>:  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 Результат:  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>Б. Использование метода query() для столбца типа XML  
 В следующем примере **query()** метод используется для указания запроса XQuery к **CatalogDescription** столбец **xml** введите  **AdventureWorks** базы данных:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   К столбцу CatalogDescription является типизированным **xml** столбца. Это означает, что имеется связанная с ним коллекция схем. В [прологе XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), **имен** ключевое слово используется для определения префикса, который впоследствии используется в теле запроса.  
  
-   **Query()** строит XML, <`Product`> элемент, имеющий **ProductModelID** атрибута, в котором **ProductModelID** значение атрибута получить из базы данных. Дополнительные сведения о конструировании XML см. в разделе [конструкции XML &#40; XQuery &#41; ](../../xquery/xml-construction-xquery.md).  
  
-   [Метод exist() (тип данных XML)](../../t-sql/xml/exist-method-xml-data-type.md) в предложении WHERE используется для нахождения только тех строк, содержащих <`Warranty`> элемент в XML. Опять же **имен** ключевое слово используется для определения двух префиксов пространства имен.  
  
 Частичный результат:  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 Заметим, что оба метода — и query(), и exist() — объявляют префикс PD. В этих случаях для первоначального определения префиксов и использования их в запросе можно использовать WITH XMLNAMESPACES.  
  
```  
WITH XMLNAMESPACES (  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
## <a name="see-also"></a>См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных &#40; Язык XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

