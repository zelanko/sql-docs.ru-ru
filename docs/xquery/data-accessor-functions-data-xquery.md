---
title: Функция data (XQuery) | Документация Майкрософт
description: Узнайте, как использовать данные функции XQuery (), чтобы вернуть типизированное значение для каждого элемента в указанной последовательности элементов.
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
- fn:data function
- data function [XQuery]
ms.assetid: 511b5d7d-c679-4cb2-a3dd-170cc126f49d
author: rothja
ms.author: jroth
ms.openlocfilehash: ac340466d1d816139249e4b007c7b2bc733dd390
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84881870"
---
# <a name="data-accessor-functions---data-xquery"></a>Функции метода доступа к данным — data (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает типизированное значение для каждого элемента, заданного *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:data ($arg as item()*) as xdt:untypedAtomic*  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность элементов, типизированные значения которых будут возвращены.  
  
## <a name="remarks"></a>Комментарии  
 Следующее применимо к типизированным значениям:  
  
-   Типизированное значение атомного значения является атомным значением.  
  
-   Типизированное значение узла текста является строковым значением узла текста.  
  
-   Типизированное значение комментария является строковым значением комментария.  
  
-   Типизированное значение инструкции по обработке является содержимым инструкции обработки, без целевого имени инструкции обработки.  
  
-   Типизированное значение узла документов является его строковым значением.  
  
 Следующее применимо к узлам атрибутов и элементов:  
  
-   Если узел атрибута типизирован посредством XML-схемы, его типизированное значение соответственно является типизированным значением.  
  
-   Если узел атрибута является нетипизированным, его типизированное значение равно строковому значению, возвращаемому в качестве экземпляра **xdt: untypedAtomic**.  
  
-   Если узел элемента не был типизирован, его типизированное значение равно строковому значению, возвращаемому в качестве экземпляра **xdt: untypedAtomic**.  
  
 Следующие характеристики относятся к типизированным узлам элемента:  
  
-   Если элемент имеет простой тип содержимого, **Data ()** возвращает типизированное значение элемента.  
  
-   Если узел имеет сложный тип, включая xs: anyType, **Data ()** возвращает статическую ошибку.  
  
 Хотя использование функции **Data ()** часто является необязательным, как показано в следующих примерах, указание функции **Data ()** явно повышает удобочитаемость запроса. Дополнительные сведения см. в статье [основы XQuery](../xquery/xquery-basics.md).  
  
 Нельзя указать **Data ()** в созданном XML, как показано ниже:  
  
```  
declare @x xml  
set @x = ''  
select @x.query('data(<SomeNode>value</SomeNode>)')  
```  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-data-xquery-function-to-extract-typed-value-of-a-node"></a>A. Использование функции data() XQuery для извлечения типизированного значения узла  
 Следующий запрос иллюстрирует использование функции **Data ()** для извлечения значений атрибута, элемента и текстового узла:  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query(N'  
 for $pd in //p1:ProductDescription  
 return   
    <Root   
      ProductID = "{ data( ($pd//@ProductModelID)[1] ) }"   
      Feature =   "{ data( ($pd/p1:Features/wm:Warranty/wm:Description)[1] ) }" >  
    </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Результат:  
  
```  
<Root ProductID="19" Feature="parts and labor"/>  
```  
  
 Как уже упоминалось, функция **Data ()** является необязательной при создании атрибутов. Если не указать функцию **Data ()** , она неявно принимается. Этот запрос формирует те же результаты, что и предыдущий запрос:  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
      for $pd in //p1:ProductDescription  
         return   
          <Root    
                ProductID = "{ ($pd/@ProductModelID)[1] }"    
                Feature =   "{ ($pd/p1:Features/wm:Warranty/wm:Description)[1] }" >  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 В следующих примерах показаны экземпляры, в которых требуется функция **Data ()** .  
  
 В следующем запросе **$PD/P1: спецификации/материалы** возвращает `Material` элемент <>. Кроме того, **данные ($PD/P1: спецификации/материалы)** возвращают символьные данные, типизированные как xdt: untypedAtomic, так как <`Material`> не типизирован. Если входные данные не типизированы, результат типа **данных ()** вводится как **xdt: untypedAtomic**.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $pd in //p1:ProductDescription  
         return   
          <Root>  
             { $pd/p1:Specifications/Material }  
             { data($pd/p1:Specifications/Material) }  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Результат:  
  
```  
<Root>  
  <Material>Almuminum Alloy</Material>Almuminum Alloy  
</Root>  
```  
  
 В следующем запросе **данные ($PD/P1: Features/WM: Warranty)** возвращают статическую ошибку, поскольку <`Warranty`> является элементом сложного типа.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
 <Root>  
   {     /p1:ProductDescription/p1:Features/wm:Warranty }  
   { data(/p1:ProductDescription/p1:Features/wm:Warranty) }  
 </Root>  
 ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID = 23  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
