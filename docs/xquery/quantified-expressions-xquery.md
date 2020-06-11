---
title: Количественные выражения (XQuery) | Документация Майкрософт
description: Узнайте, как использовать количественные выражения в XQuery для применения существующий или универсального квантификации к выражению в одной или нескольких последовательностях.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- universal quantifiers
- effective Boolean value [XQuery]
- quantified expressions [XQuery]
- XQuery, quantified expressions
- every expression [XQuery]
- existential quantifiers [XQuery]
- some expression [XQuery]
- EBV
- expressions [XQuery], quantifiers
ms.assetid: a3a75a6c-8f67-4923-8406-1ada546c817f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f7c79cd185b88b8681460d2811f0d0ac4c20557
ms.sourcegitcommit: 9921501952147b9ce3e85a1712495d5b3eb13e5b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84215243"
---
# <a name="quantified-expressions-xquery"></a>Выражения с квантором (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Кванторы существования и кванторы всеобщности указывают различную семантику для логических операторов, применяемых к двум последовательностям. Это показано ниже.  
  
 *Квантор существования*  
 Если имеются две последовательности и любой элемент первой последовательности имеет соответствующую пару во второй последовательности согласно используемому оператору сравнения, возвращаемым значением будет True.  
  
 *Квантор всеобщности*  
 Если имеются две последовательности и любой элемент первой последовательности имеет соответствующую пару во второй последовательности, возвращаемым значением будет True.  
  
 XQuery поддерживает выражения с квантором в следующем виде:  
  
```  
( some | every ) <variable> in <Expression> (,...) satisfies <Expression>  
```  
  
 Можно использовать эти выражения в запросе для явного применения квантификации существования или всеобщности к выражению в отношении одной или нескольких последовательностей. В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] выражение в предложении `satisfies` должно привести к одному из следующих результатов: узловая последовательность, пустая последовательность или логическое значение. Действительное логическое значение результата этого выражения будет использовано в квантификации. Существующий квантификации, который использует **некоторые** , возвратит значение true, если хотя бы одно из значений, связанных с квантификатором, имеет истинный результат в выражении удовлетворения. Универсальные квантификации, использующие **все** , должны иметь значение true для всех значений, привязанных к квантификатор.  
  
 Например, следующий запрос проверяет каждый \<Location> элемент, чтобы определить, имеет ли он атрибут LocationID.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        if (every $WC in //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID)  
        then  
             <Result>All work centers have workcenterLocation ID</Result>  
         else  
             <Result>Not all work centers have workcenterLocation ID</Result>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Так как LocationID является обязательным атрибутом \<Location> элемента, вы получаете ожидаемый результат:  
  
```  
<Result>All work centers have Location ID</Result>   
```  
  
 Вместо использования [метода query ()](../t-sql/xml/query-method-xml-data-type.md)можно использовать [метод value ()](../t-sql/xml/value-method-xml-data-type.md) , чтобы вернуть результат в реляционный мир, как показано в следующем запросе. Запрос возвращает True, если все местоположения рабочих центров имеют атрибуты LocationID. В противном случае функция возвращает False.  
  
```  
SELECT Instructions.value('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        every $WC in  //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID',   
  'nvarchar(10)') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 В нижеследующем запросе проверяется, является ли одно из изображений продукции маленьким. В каталоге продукции в XML-формате хранятся разные ракурсы для каждого изображения продукта различного размера. Возможна необходимость, чтобы каждый каталог продукции в XML-формате содержал как минимум одно изображение маленького размера. Чтобы выполнить эту задачу, используется следующий запрос:  
  
```  
SELECT ProductModelID, CatalogDescription.value('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     some $F in /PD:ProductDescription/PD:Picture  
        satisfies $F/PD:Size="small"', 'nvarchar(20)') as SmallPicturesStored  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Частичный результат:  
  
```  
ProductModelID SmallPicturesStored   
-------------- --------------------  
19             true        
```  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Утверждение типов не поддерживается как часть привязки переменной в выражениях с квантором.  
  
## <a name="see-also"></a>См. также:  
 [Выражения языка XQuery](../xquery/xquery-expressions.md)  
  
  
