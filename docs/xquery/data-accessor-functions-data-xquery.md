---
title: Функция Data (XQuery) | Документы Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:data function
- data function [XQuery]
ms.assetid: 511b5d7d-c679-4cb2-a3dd-170cc126f49d
caps.latest.revision: 31
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 126fb280c3fec43ee1cf882834460bfc3be62d6d
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="data-accessor-functions---data-xquery"></a>Функции доступа к данным - данных (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает типизированное значение для каждого элемента, указанного *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:data ($arg as item()*) as xdt:untypedAtomic*  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность элементов, типизированные значения которых будут возвращены.  
  
## <a name="remarks"></a>Замечания  
 Следующее применимо к типизированным значениям:  
  
-   Типизированное значение атомного значения является атомным значением.  
  
-   Типизированное значение узла текста является строковым значением узла текста.  
  
-   Типизированное значение комментария является строковым значением комментария.  
  
-   Типизированное значение инструкции по обработке является содержимым инструкции обработки, без целевого имени инструкции обработки.  
  
-   Типизированное значение узла документов является его строковым значением.  
  
 Следующее применимо к узлам атрибутов и элементов:  
  
-   Если узел атрибута типизирован посредством XML-схемы, его типизированное значение соответственно является типизированным значением.  
  
-   Если узел атрибута не типизирован, его типизированное значение соответствует строковому значению, возвращаемому как экземпляр **xdt: untypedAtomic**.  
  
-   Если узел элемента не типизирован, его типизированное значение соответствует строковому значению, возвращаемому как экземпляр **xdt: untypedAtomic**.  
  
 Следующие характеристики относятся к типизированным узлам элемента:  
  
-   Если элемент имеет простой тип содержимого **data()** возвращает типизированное значение элемента.  
  
-   Если узел относится к сложному типу, включая xs: anyType, **data()** возвращает статическую ошибку.  
  
 Хотя использование **data()** зачастую не является обязательным, как показано в следующих примерах, определение **data()** явно повышает удобочитаемость запроса. Дополнительные сведения см. в разделе [основы языка XQuery](../xquery/xquery-basics.md).  
  
 Нельзя указать **data()** для конструируемого XML, как показано ниже:  
  
```  
declare @x xml  
set @x = ''  
select @x.query('data(<SomeNode>value</SomeNode>)')  
```  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-data-xquery-function-to-extract-typed-value-of-a-node"></a>A. Использование функции data() XQuery для извлечения типизированного значения узла  
 Следующий запрос иллюстрирует использование **data()** функция используется для получения значения атрибута, элемента и текстовый узел:  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
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
  
 Как уже упоминалось, **data()** при создании атрибутов функция необязателен. Если вы не укажете **data()** функция, она неявно подразумевается. Этот запрос формирует те же результаты, что и предыдущий запрос:  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
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
  
 Следующие примеры иллюстрируют экземпляры, в которых **data()** функции не требуется.  
  
 В следующем запросе **$pd / P1: Specifications / Material** возвращает <`Material`> элемент. Кроме того **данных ($pd/P1: Specifications/Material)** Возвращает символьные данные, типизированные как xdt: untypedAtomic, так как <`Material`> является нетипизированным. Если входные данные не типизированы, результат **data()** типизируется как **xdt: untypedAtomic**.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
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
  
 В следующем запросе **data($pd/p1:Features/wm:Warranty)** возвращает статическую ошибку, так как <`Warranty`> является элементом сложного типа.  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
 <Root>  
   {     /p1:ProductDescription/p1:Features/wm:Warranty }  
   { data(/p1:ProductDescription/p1:Features/wm:Warranty) }  
 </Root>  
 ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID = 23  
```  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
