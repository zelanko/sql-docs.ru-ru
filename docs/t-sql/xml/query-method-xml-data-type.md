---
title: Метод query() (тип данных xml) | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|xml
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: 82f56308ec18e2c3b8bde437e2d776f9daf05120
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33071711"
---
# <a name="query-method-xml-data-type"></a>query() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет запрос XQuery для экземпляра типа данных **xml**. Результат имеет тип данных **xml**. Метод возвращает экземпляр нетипизированного XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>Аргументы  
 XQuery  
 Это строка, выражение XQuery, выполняющее в экземпляре XML запросы к узлам — элементам и атрибутам.  
  
## <a name="examples"></a>Примеры  
 В этом подразделе приведены примеры использования метода query() типа данных **xml**.  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. Использование метода query() для переменной типа xml  
 В следующем примере объявляется переменная **@myDoc** типа данных **xml**, и этой переменной присваивается экземпляр XML. Далее методом **query()** для документа определяется запрос XQuery.  
  
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
 В следующем примере метод **query()** используется для задания запроса XQuery к столбцу **CatalogDescription** типа данных **xml** в базе данных **AdventureWorks**:  
  
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
  
-   Столбец CatalogDescription является типизированным столбцом **xml**. Это означает, что имеется связанная с ним коллекция схем. В [прологе XQuery](../../xquery/modules-and-prologs-xquery-prolog.md) ключевое слово **namespace** используется для определения префикса, который в дальнейшем используется в теле запроса.  
  
-   Метод **query()** строит XML, элемент <`Product`>, имеющий атрибут **ProductModelID**, и значение атрибута **ProductModelID** извлекается из базы данных. Дополнительные сведения о конструировании XML см. в разделе [XML-конструкция (XQuery)](../../xquery/xml-construction-xquery.md).  
  
-   Метод [exist() (тип данных XML)](../../t-sql/xml/exist-method-xml-data-type.md) в предложении WHERE используется для нахождения только тех строк, которые в XML содержат элемент <`Warranty`>. Ключевое слово **namespace**, опять же, используется для определения двух префиксов пространства имен.  
  
 Частичный результат:  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 Заметим, что оба метода — и query(), и exist() — объявляют префикс PD. В этих случаях для первоначального определения префиксов и использования их в запросе можно использовать WITH XMLNAMESPACES.  
  
```  
WITH XMLNAMESPACES 
(  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM
)  
SELECT CatalogDescription.query('<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />')
       AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/PD:ProductDescription/PD:Features/WM:Warranty ') = 1;

```  
  
## <a name="see-also"></a>См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
