---
title: "Варианты использования XQuery Общие | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, general usage cases
ms.assetid: 5187c97b-6866-474d-8bdb-a082634039cc
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13b88814a7d0d9b0d0154b8e010b6aa76c85c6e6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="general-xquery-use-cases"></a>Общие способы применения запросов XQuery
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом подразделе приведены примеры использования запросов XQuery.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-query-catalog-descriptions-to-find-products-and-weights"></a>A. Запрос описаний каталога для поиска продукции и значений веса  
 Следующий запрос возвращает идентификаторы моделей продукции и их вес (если указан) из описания в каталоге продукции. Запрос формирует XML следующей структуры:  
  
```  
<Product ProductModelID="…">  
  <Weight>…</Weight>  
</Product>  
```  
  
 Запрос является таковым:  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  <Product  ProductModelID="{ (/p1:ProductDescription/@ProductModelID)[1] }">  
     {   
       /p1:ProductDescription/p1:Specifications/Weight   
     }   
  </Product>  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **Имен** ключевое слово в прологе XQuery определяет префикс пространства имен, который используется в теле запроса.  
  
-   Текст запроса формирует требуемый XML.  
  
-   В предложении WHERE **exist()** метод используется для нахождения только тех строк, которые содержат описания каталога продукции. То есть XML-данные, которые содержат элемент <`ProductDescription`>.  
  
 Результат:  
  
```  
<Product ProductModelID="19"/>  
<Product ProductModelID="23"/>   
<Product ProductModelID="25"/>   
<Product ProductModelID="28"><Weight>Varies with size.</Weight></Product>  
<Product ProductModelID="34"/>  
<Product ProductModelID="35"/>  
```  
  
 Следующий запрос получает те же сведения, но лишь для моделей продукции, описания которых в каталоге включают значение веса (элемент <`Weight`>) в спецификациях (элемент <`Specifications`>). В данном примере для объявления префикса pd и привязки пространства имен используется предложение WITH XMLNAMESPACES. Таким образом, Описание привязки отсутствует как в **query()** метод и в **exist()** метод.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT CatalogDescription.query('  
          <Product  ProductModelID="{ (/pd:ProductDescription/@ProductModelID)[1] }">  
                 {   
                      /pd:ProductDescription/pd:Specifications/Weight   
                 }   
          </Product>  
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription/pd:Specifications//Weight ') = 1  
```  
  
 В предыдущем запросе **exist()** метод **xml** типа данных в предложении WHERE проверяет, существует ли <`Weight`> элемента <`Specifications`> элемент.  
  
### <a name="b-find-product-model-ids-for-product-models-whose-catalog-descriptions-include-front-angle-and-small-size-pictures"></a>Б. Поиск идентификаторов моделей продукции, описания которых в каталоге имеют фронтальные и малоразмерные изображения.  
 Описание в каталоге продукции формата XML включает рисунки товаров — элемент <`Picture`>. Каждый рисунок обладает несколькими свойствами, среди которых угол рисунка (элемент <`Angle`>) и размер (элемент <`Size`>).  
  
 Для тех моделей продукции,описания которых в каталоге содержат фронтальные и малоразмерные изображения, запрос формирует XML со следующей структурой:  
  
```  
< Product ProductModelID="…">  
  <Picture>  
    <Angle>front</Angle>  
    <Size>small</Size>  
  </Picture>  
</Product>  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT CatalogDescription.query('  
   <pd:Product  ProductModelID="{ (/pd:ProductDescription/@ProductModelID)[1] }">  
      <Picture>  
         {  /pd:ProductDescription/pd:Picture/pd:Angle }   
         {  /pd:ProductDescription/pd:Picture/pd:Size }   
      </Picture>  
   </pd:Product>  
') as Result  
FROM  Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription/pd:Picture') = 1  
AND   CatalogDescription.value('(/pd:ProductDescription/pd:Picture/pd:Angle)[1]', 'varchar(20)')  = 'front'  
AND   CatalogDescription.value('(/pd:ProductDescription/pd:Picture/pd:Size)[1]', 'varchar(20)')  = 'small'  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   В предложении WHERE **exist()** метод используется для получения только тех строк, которые содержат описания каталога продукции с <`Picture`> элемент.  
  
-   В предложении WHERE используется **value()** дважды для сравнения значений <`Size`> и <`Angle`> элементов.  
  
 Частичный результат:  
  
```  
<p1:Product   
  xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
  ProductModelID="19">  
  <Picture>  
    <p1:Angle>front</p1:Angle>  
    <p1:Size>small</p1:Size>  
  </Picture>  
</p1:Product>  
...  
```  
  
### <a name="c-create-a-flat-list-of-the-product-model-name-and-feature-pairs-with-each-pair-enclosed-in-the-features-element"></a>В. Создание списка продукта пар имен и характеристик моделей, где каждая пара заключена в \<функции > элемент  
 В описании каталога моделей продукции XML содержит несколько характеристик продукта. Все эти характеристики включены в элемент <`Features`>. В запросе используется [построение XML (XQuery)](../xquery/xml-construction-xquery.md) для формирования требуемого XML. Выражение в фигурных скобках заменяется результатом.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  for $pd in /p1:ProductDescription,  
   $f in $pd/p1:Features/*  
  return  
   <Feature>  
     <ProductModelName> { data($pd/@ProductModelName) } </ProductModelName>  
     { $f }  
  </Feature>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   $pd/p1:Features/* возвращает только дочерние узлы элементов <`Features`>, а $pd/p1:Features/node() возвращает все узлы. В их число входят узлы элементов, текстовые узлы, инструкции по обработке, а также примечания.  
  
-   Два контейнера «цикл по элементам» формируют декартов продукт, из которого возвращаются имя продукта и отдельная характеристика.  
  
-   **ProductName** является атрибутом. Построение XML в этом запросе возвращает его как элемент.  
  
 Частичный результат:  
  
```  
<Feature>  
 <ProductModelName>Mountain 100</ProductModelName>  
 <ProductModelID>19</ProductModelID>  
 <p1:Warranty   
   xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
 </p1:Warranty>  
</Feature>  
<Feature>  
 <ProductModelName>Mountain 100</ProductModelName>  
 <ProductModelID>19</ProductModelID>  
 <p2:Maintenance xmlns:p2="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer   
           or any AdventureWorks retail store.</p2:Description>  
    </p2:Maintenance>  
</Feature>  
...  
...      
```  
  
### <a name="d-from-the-catalog-description-of-a-product-model-list-the-product-model-name-model-id-and-features-grouped-inside-a-product-element"></a>Г. В описании каталога моделей продукции, список продукта модели идентификатор, имя, модели и сгруппированных функции в \<продукта > элемент  
 С помощью сведений, хранящихся в описании каталога моделей продукции, следующий запрос возвращает имя модели продукции, идентификатор модели, а также функции группировки внутри \<продукта > элемент.  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
     declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>  
         <ProductModelName>   
           { data(/pd:ProductDescription/@ProductModelName) }   
         </ProductModelName>  
         <ProductModelID>   
           { data(/pd:ProductDescription/@ProductModelID) }   
         </ProductModelID>  
         { /pd:ProductDescription/pd:Features/* }  
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Частичный результат:  
  
```  
<Product>  
  <ProductModelName>Mountain 100</ProductModelName>  
  <ProductModelID>19</ProductModelID>  
  <p1:Warranty>... </p1:Warranty>  
  <p2:Maintenance>...  </p2:Maintenance>  
  <p3:wheel xmlns:p3="http://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p3:wheel>  
  <p4:saddle xmlns:p4="http://www.adventure-works.com/schemas/OtherFeatures">  
    <p5:i xmlns:p5="http://www.w3.org/1999/xhtml">Anatomic design</p5:i> and made from durable leather for a full-day of riding in comfort.</p4:saddle>  
  <p6:pedal xmlns:p6="http://www.adventure-works.com/schemas/OtherFeatures">  
    <p7:b xmlns:p7="http://www.w3.org/1999/xhtml">Top-of-the-line</p7:b> clipless pedals with adjustable tension.</p6:pedal>  
   ...  
```  
  
### <a name="e-retrieve-product-model-feature-descriptions"></a>Д. Получение описаний характеристик для модели продукции.  
 Следующий запрос создает XML, включающий <`Product`> элемент, имеющий **ProducModelID**, **ProductModelName** атрибуты и первые две характеристики продукта. Следует уточнить, что первые две характеристики продукта являются первыми двумя дочерними элементами элемента <`Features`>. При наличии большего числа характеристик данный запрос возвращает пустой элемент <`There-is-more/`>.  
  
```  
SELECT CatalogDescription.query('  
declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /pd:ProductDescription/@ProductModelID }  
          { /pd:ProductDescription/@ProductModelName }   
          {  
            for $f in /pd:ProductDescription/pd:Features/*[position()<=2]  
            return  
            $f   
          }  
          {  
            if (count(/pd:ProductDescription/pd:Features/*) > 2)  
            then <there-is-more/>  
            else ()  
          }   
     </Product>          
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not NULL  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Чтобы RETURN получает первые две характеристики продукта. **Position()** функция используется для определения положения элементов в последовательности.  
  
### <a name="f-find-element-names-from-the-product-catalog-description-that-end-with-ons"></a>Е. Поиск в описании каталога продукции имен элементов, которые заканчиваются на «ons».  
 Следующий запрос используется для поиска в описаниях каталога всех элементов в элементе <`ProductDescription`>, имена которых заканчиваются на «ons».  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
     declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $pd in /p1:ProductDescription/*[substring(local-name(.),string-length(local-name(.))-2,3)="ons"]  
      return   
          <Root>  
             { $pd }  
          </Root>  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not NULL  
```  
  
 Частичный результат:  
  
```  
ProductModelID   Result  
-----------------------------------------  
         19        <Root>         
                     <p1:Specifications xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">          
                          ...         
                     </p1:Specifications>         
                   </Root>          
```  
  
### <a name="g-find-summary-descriptions-that-contain-the-word-aerodynamic"></a>Ж. Поиск сводных описаний, содержащих слово «Aerodynamic».  
 Следующий запрос получает модели продукции, описания которых в каталоге содержат слово «Aerodynamic»:  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
          <Prod >  
             { /pd:ProductDescription/@ProductModelID }  
             { /pd:ProductDescription/pd:Summary }  
          </Prod>  
 ') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.value('  
     contains( string( (/pd:ProductDescription/pd:Summary)[1] ),"Aerodynamic")','bit') = 1  
```  
  
 Обратите внимание, что запрос SELECT определяет **query()** и **value()** методы **xml** тип данных. Поэтому вместо повторения декларации пространства имен дважды в двух разных прологах запроса, в запросе используется префикс pd, который определяется только один раз в предложении WITH XMLNAMESPACES.  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Предложение WHERE используется для получения лишь тех строк, которые содержат слово «Aerodynamic» в элементе <`Summary`> описания каталога.  
  
-   **Contains()** функция используется для проверки, если указан в тексте.  
  
-   **Value()** метод **xml** тип данных сравнивает значение, возвращаемое **contains()** значение 1.  
  
 Результат:  
  
```  
ProductModelID Result        
-------------- ------------------------------------------  
28     <Prod ProductModelID="28">  
        <pd:Summary xmlns:pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
       <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">  
         A TRUE multi-sport bike that offers streamlined riding and a  
         revolutionary design. Aerodynamic design lets you ride with the   
         pros, and the gearing will conquer hilly roads.</p1:p>  
       </pd:Summary>  
      </Prod>    
```  
  
### <a name="h-find-product-models-whose-catalog-descriptions-do-not-include-product-model-pictures"></a>З. Поиск моделей продукции, описания которых в каталоге не содержат изображений моделей продукции.  
 Следующий запрос получает значения ProductModelID моделей продукции, описания которых в каталоге не содержат элемента <`Picture`>.  
  
```  
SELECT  ProductModelID  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not NULL  
AND     CatalogDescription.exist('declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /p1:ProductDescription/p1:Picture  
') = 0  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Если **exist()** метод в предложении WHERE возвращает значение False (0), возвращается код модели продукта. В противном случае идентификатор не извлекается.  
  
-   В данном случае результирующий набор пуст, поскольку все описания продукции содержат элемент <`Picture`>.  
  
## <a name="see-also"></a>См. также  
 [Запросы XQuery, использующие иерархию](../xquery/xqueries-involving-hierarchy.md)   
 [Запросы XQuery, использующие упорядочивание](../xquery/xqueries-involving-order.md)   
 [Запросы XQuery, обрабатывающие реляционные данные](../xquery/xqueries-handling-relational-data.md)   
 [Поиск строки в XQuery](../xquery/string-search-in-xquery.md)   
 [Поддержка пространств имен в XQuery](../xquery/handling-namespaces-in-xquery.md)   
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)  
  
  
