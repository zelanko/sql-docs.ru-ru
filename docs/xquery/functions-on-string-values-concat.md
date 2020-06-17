---
title: Функция Concat (XQuery) | Документация Майкрософт
description: Сведения о функции XQuery Concat (), возвращающей строку, созданную путем сцепления нуля или более строк, указанных в качестве аргументов.
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:concat function
- concat function [XQuery]
ms.assetid: d50afd20-a297-445e-be9e-13b48017e7ca
author: rothja
ms.author: jroth
ms.openlocfilehash: 02d3762f419789732406564606ad7a3b990e30fd
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84881811"
---
# <a name="functions-on-string-values---concat"></a>Функции со строковыми значениями — concat
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Принимает от нуля и более строк и возвращает строку, содержащую результат сцепления переданных аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:concat ($string as xs:string?  
           ,$string as xs:string?  
           [, ...]) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$string*  
 Необязательная строка для сцепления.  
  
## <a name="remarks"></a>Комментарии  
 Функции требуется как минимум два аргумента. Если в качестве аргумента передана пустая последовательность, она трактуется как строка нулевой длины.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 Поведение суррогатных пар в функциях XQuery зависит от уровня совместимости базы данных и, в некоторых случаях, от URI-кода пространства имен по умолчанию для функций. Дополнительные сведения см. в разделе "функции XQuery, поддерживающие суррогаты" в разделе [критические изменения ядро СУБД функций в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). См. также раздел [уровень совместимости ALTER database &#40;&#41;Transact-SQL](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) и [Параметры сортировки и поддержка Юникода](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в образце базы данных AdventureWorks.  
  
### <a name="a-using-the-concat-xquery-function-to-concatenate-strings"></a>A. Применение функции concat() языка XQuery для объединения строк  
 Для указанного изделия запрос возвращает строку, полученную сцеплением гарантийного строка и гарантийных обязательств. В документе описания каталога элемент> <состоит `Warranty` из <`WarrantyPeriod`> и <> `Description` дочерних элементов.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"  
        ProductModelName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE  PD.ProductModelID=28  
  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   В предложении SELECT CatalogDescription является столбцом типа **XML** . Поэтому используется [метод query () (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md), инструкции. Query (). Инструкция XQuery задана как аргумент метода query.  
  
-   Запрос к документу выполняется при использовании пространства имен,  Поэтому ключевое слово **Namespace** используется для определения префикса пространства имен. Дополнительные сведения см. в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md).  
  
 Результат:  
  
```  
<Product ProductModelID="28" ProductModelName="Road-450">1 year-parts and labor</Product>  
```  
  
 Приведенный запрос получает сведения об указанном изделии. Следующий запрос получает те же сведения по всем изделиям, для которых имеются описания каталога XML. Метод **exist ()** типа данных **XML** в предложении WHERE возвращает значение true, если XML-документ в строках содержит `ProductDescription` элемент <>.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"   
        ProductName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE CatalogDescription.exist('//pd:ProductDescription ') = 1  
  
```  
  
 Обратите внимание, что логическое значение, возвращаемое методом **exist ()** типа **XML** , сравнивается с 1.  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Функция **concat ()** в SQL Server принимает только значения типа xs: String. Все остальные значения должны быть явно приведены в xs:string или xdt:untypedAtomic.  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
