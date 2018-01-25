---
title: "(тип данных xml) метод exist() | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- exist() method
- exist method
ms.assetid: a55b75e0-0a17-4787-a525-9b095410f7af
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 74fc65730d0c46858c282b9625c86d1ab651ec49
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="exist-method-xml-data-type"></a>Метод exist() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает **бит** , представляющий один из следующих условий:  
  
-   1, означающее True, если выражение на языке XQuery при запросе возвращает непустой результат, то есть возвращается как минимум один узел XML.  
  
-   0, означающее False при возвращении пустого результата.  
  
-   Значение NULL, если **xml** экземпляр типа данных, для которого была выполнена запрос содержит значение NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
exist (XQuery)   
```  
  
## <a name="arguments"></a>Аргументы  
 XQuery  
 Выражение на языке XQuery, строковый литерал.  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]  
>  **Exist()** метод возвращает 1 для выражения XQuery, которое возвращает непустой результат. При указании **true()** или **false()** внутри **exist()** метода **exist()** метод возвращает 1, так как функции **true()** и **false()** возвращают логические значения True и False, соответственно. То есть они возвращают не пустой результат. Таким образом **exist()** возвращает значение 1 (True), как показано в следующем примере:  
  
```  
declare @x xml;  
set @x='';  
select @x.exist('true()');   
```  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано указание **exist()** метод.  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-variable"></a>Пример: Указание метода exist() по отношению к переменной типа xml  
 В следующем примере @x — **xml** типа переменной (нетипизированный xml) и @f является переменной целочисленного типа, который хранит значение, возвращаемое **exist()** метод. **Exist()** метод возвращает значение True (1), если значение даты, хранимое в экземпляре XML является `2002-01-01`.  
  
```  
declare @x xml;  
declare @f bit;  
set @x = '<root Somedate = "2002-01-01Z"/>';  
set @f = @x.exist('/root[(@Somedate cast as xs:date?) eq xs:date("2002-01-01Z")]');  
select @f;  
```  
  
 В сравнении дат в **exist()** метод, обратите внимание на следующее:  
  
-   Код `cast as xs:date?` используется для приведения значения к **xs: Date** тип сравнения для целей.  
  
-   Значение  **@Somedate**  является нетипизированным. В сравнении это значение неявно приводится к типу справа от оператора сравнения, **xs: Date** типа.  
  
-   Вместо **приведения, как xs: Date()**, можно использовать **xs: Date()** функции конструктора. Дополнительные сведения см. в разделе [функции-конструкторы &#40; XQuery &#41; ](../../xquery/constructor-functions-xquery.md).  
  
 Следующий пример похож на предыдущий, отличаясь только наличием элемента <`Somedate`>.  
  
```  
DECLARE @x xml;  
DECLARE @f bit;  
SET @x = '<Somedate>2002-01-01Z</Somedate>';  
SET @f = @x.exist('/Somedate[(text()[1] cast as xs:date ?) = xs:date("2002-01-01Z") ]')  
SELECT @f;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **Text()** метод возвращает текстовый узел, содержащий нетипизированное значение `2002-01-01`. (Тип XQuery **xdt: untypedAtomic**.) Необходимо явно привести это типизированное значение с **x** для **xsd: Date**, поскольку неявное приведение не поддерживается в этом случае.  
  
### <a name="example-specifying-the-exist-method-against-a-typed-xml-variable"></a>Пример: Указание метода exist() по отношению к типизированной переменной xml  
 Следующий пример иллюстрирует использование **exist()** метода для **xml** переменной типа. Это типизированная переменная XML, поскольку она указывает имя схемы коллекции пространства имен, `ManuInstructionsSchemaCollection`.  
  
 В примере с инструкциями по производству документ сначала присваивается переменной и затем **exist()** метод используется для поиска, содержится ли в документе <`Location`> элемент которого **LocationID**  значение атрибута равно 50.  
  
 **Exist()** метод, заданный относительно @x переменной возвращает 1 (True), если документ содержит инструкции по изготовлению <`Location`> элемент, имеющий `LocationID=50`. В противном случае метод возвращает значение 0 (False).  
  
```  
DECLARE @x xml (Production.ManuInstructionsSchemaCollection);  
SELECT @x=Instructions  
FROM Production.ProductModel  
WHERE ProductModelID=67;  
--SELECT @x  
DECLARE @f int;  
SET @f = @x.exist(' declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /AWMI:root/AWMI:Location[@LocationID=50]  
');  
SELECT @f;  
```  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-column"></a>Пример: Указание метода exist() к столбцу типа xml  
 Следующий запрос получает модели продукции идентификаторы, описания которых в каталоге будут отсутствовать спецификации, <`Specifications`> элемент:  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Предложение WHERE выбирает только те строки из **ProductDescription** table, удовлетворяющего условию, указанному для **CatalogDescription xml** тип столбца.  
  
-   **Exist()** метод в предложении WHERE возвращает 1 (True), если XML не содержит <`Specifications`> элемент. Обратите внимание на использование [функции not() (XQuery)](../../xquery/functions-on-boolean-values-not-function.md).  
  
-   [Функции SQL: column() (XQuery)](../../xquery/xquery-extension-functions-sql-column.md) функция используется для импорта значения из-XML столбца.  
  
-   Этот запрос возвращает пустой набор строк.  
  
 Запрос указывает **query()** и **exist()** методы типа данных xml и оба эти метода объявляют одинаковые пространства имен в прологе запроса. В этом случае для объявления префикса и использования его в запросе можно использовать предложение WITH XMLNAMESPACES.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных &#40; Язык XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
