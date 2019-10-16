---
title: Метод exist() (тип данных xml) | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- exist() method
- exist method
ms.assetid: a55b75e0-0a17-4787-a525-9b095410f7af
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9621d6be1c309930f6104d2193d6127a3167cd7a
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278154"
---
# <a name="exist-method-xml-data-type"></a>Метод exist() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает значение типа **bit**, которое представляет одно из следующих состояний:  
  
-   1, означающее True, если выражение на языке XQuery при запросе возвращает непустой результат, то есть возвращается как минимум один узел XML.  
  
-   0, означающее False при возвращении пустого результата.  
  
-   Значение NULL, если экземпляр типа **xml**, к которому был выполнен запрос, содержит значение NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
exist (XQuery)   
```  
  
## <a name="arguments"></a>Аргументы  
 XQuery  
 Выражение на языке XQuery, строковый литерал.  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]  
>  Метод **exist()** возвращает 1 для выражения XQuery, которое возвращает непустой результат. Если указать функции **true()** или **false()** внутри метода **exist()** , то метод **exist()** возвратит 1, так как функции **true()** и **false()** возвращают логические значения True и False соответственно. То есть они возвращают не пустой результат. Поэтому функция **exist()** возвратит 1 (True), как показано в следующем примере:  
  
```  
declare @x xml;  
set @x='';  
select @x.exist('true()');   
```  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано использование метода **exist()** .  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-variable"></a>Пример Указание метода exist() по отношению к переменной типа xml  
 В следующем примере @x является переменной типа **xml** (нетипизированный xml), а @f является переменной целочисленного типа, которая хранит значение, возвращенное методом **exist()** . Метод **exist()** возвращает значение True (1), если значение даты, хранимое в экземпляре XML, равно `2002-01-01`.  
  
```  
declare @x xml;  
declare @f bit;  
set @x = '<root Somedate = "2002-01-01Z"/>';  
set @f = @x.exist('/root[(@Somedate cast as xs:date?) eq xs:date("2002-01-01Z")]');  
select @f;  
```  
  
 В сравнении дат в методе **exist()** обратите внимание на следующее:  
  
-   Код `cast as xs:date?` используется для приведения значения к типу **xs:date** с целью сравнения.  
  
-   Значение атрибута **\@Somedate** является нетипизированным. При сравнении это значение неявно приводится к типу правой части выражения сравнения, а именно — к типу **xs:date**.  
  
-   Вместо выражения **cast as xs:date()** можно использовать функцию-конструктор **xs:date()** . Дополнительные сведения см. в разделе [Функции конструктора (XQuery)](../../xquery/constructor-functions-xquery.md).  
  
 Следующий пример похож на предыдущий, отличаясь только наличием элемента <`Somedate`>.  
  
```  
DECLARE @x xml;  
DECLARE @f bit;  
SET @x = '<Somedate>2002-01-01Z</Somedate>';  
SET @f = @x.exist('/Somedate[(text()[1] cast as xs:date ?) = xs:date("2002-01-01Z") ]')  
SELECT @f;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Метод **text()** возвращает текстовый узел, содержащий нетипизированное значение `2002-01-01`. (XQuery имеет тип **xdt:untypedAtomic**.) Необходимо явно привести это типизированное значение из типа **x** к типу **xsd:date**, поскольку неявное приведение в данном случае не поддерживается.  
  
### <a name="example-specifying-the-exist-method-against-a-typed-xml-variable"></a>Пример Указание метода exist() по отношению к типизированной переменной xml  
 В следующем примере иллюстрируется применение метода **exist()** к переменной типа **xml**. Это типизированная переменная XML, поскольку она указывает имя схемы коллекции пространства имен, `ManuInstructionsSchemaCollection`.  
  
 В этом примере переменной сначала присваивается документ с инструкциями по производству, а затем с помощью метода **exist()** проверяется, содержит ли документ элемент <`Location`>, атрибут **LocationID** которого имеет значение 50.  
  
 Метод **exist()** , примененный к переменной @x, возвращает значение 1 (True), если документ с инструкциями по производству содержит элемент <`Location`> с атрибутом `LocationID=50`. В противном случае метод возвращает значение 0 (False).  
  
```  
DECLARE @x xml (Production.ManuInstructionsSchemaCollection);  
SELECT @x=Instructions  
FROM Production.ProductModel  
WHERE ProductModelID=67;  
--SELECT @x  
DECLARE @f int;  
SET @f = @x.exist(' declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /AWMI:root/AWMI:Location[@LocationID=50]  
');  
SELECT @f;  
```  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-column"></a>Пример Указание метода exist() по отношению к столбцу типа xml  
 В результате выполнения следующего запроса возвращаются идентификаторы моделей, описание каталогов для которых не включает спецификации, элемент <`Specifications`>:  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Предложение WHERE выбирает только те строки из таблицы **ProductDescription**, которые удовлетворяют условию, указанному для столбца типа xml **CatalogDescription**.  
  
-   Метод **exist()** в предложении WHERE возвращает 1 (True), если XML не содержит элемент <`Specifications`>. Обратите внимание на использование функции [not() (XQuery)](../../xquery/functions-on-boolean-values-not-function.md).  
  
-   Функция [sql:column() (XQuery)](../../xquery/xquery-extension-functions-sql-column.md) используется для импорта значения из столбца, тип которого отличается от XML.  
  
-   Этот запрос возвращает пустой набор строк.  
  
 В этом запросе указаны методы **query()** и **exist()** типа xml, и оба эти метода объявляют одинаковые пространства имен в прологе запроса. В этом случае для объявления префикса и использования его в запросе можно использовать предложение WITH XMLNAMESPACES.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
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
  
## <a name="see-also"></a>См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
