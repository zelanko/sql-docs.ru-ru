---
title: Функция String (XQuery) | Документация Майкрософт
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
- string function
- fn:string function
ms.assetid: 7baa2959-9340-429b-ad53-3df03d8e13fc
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cb30d81102c17f2c3ce04b31ac7ff2b9689343e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038944"
---
# <a name="data-accessor-functions---string-xquery"></a>Функции метода доступа к данным — string (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение *$arg* , представленное в виде строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:string() as xs:string  
fn:string($arg as item()?) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Узел или атомарное значение.  
  
## <a name="remarks"></a>Remarks  
  
-   Если *$arg* является пустой последовательностью, возвращается строка нулевой длины.  
  
-   Если *$arg* является узлом, функция возвращает строковое значение узла, полученное с помощью метода доступа к строковому значению. Это определено в спецификации W3C XQuery 1.0 и XPath 2.0 Data Model.  
  
-   Если *$arg* является атомарным значением, функция возвращает ту же строку, которая возвращается выражением, приведенным в виде **xs: String**, *$arg*, за исключением случаев, когда указано иное.  
  
-   Если *$arg* имеет тип **xs: anyURI**, URI преобразуется в строку без экранирования специальных символов.  
  
-   Эта реализация, **fn: String ()** без аргумента может использоваться только в контексте контекстно-зависимого предиката. Точнее, она может использоваться только внутри квадратных скобок ([ ]).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-string-function"></a>A. Использование строковой функции  
 Следующий запрос получает узел <`Features`> дочернего элемента элемента <`ProductDescription`>.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 /PD:ProductDescription/PD:Features  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Частичный результат:  
  
```  
<PD:Features xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
   These are the product highlights.   
   <p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 years</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
   </p1:Warranty>  
       ...  
</PD:Features>  
```  
  
 Если указать функцию **String ()** , будет получено строковое значение указанного узла.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 string(/PD:ProductDescription[1]/PD:Features[1])  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Частичный результат.  
  
```  
These are the product highlights.   
3 yearsparts and labor...    
```  
  
### <a name="b-using-the-string-function-on-various-nodes"></a>Б. Использование строковой функции в различных узлах  
 В следующем примере экземпляр XML назначается переменной типа xml. Запросы указываются для иллюстрации результата применения **String ()** к различным узлам.  
  
```  
declare @x xml  
set @x = '<?xml version="1.0" encoding="UTF-8" ?>  
<!--  This is a comment -->  
<root>  
  <a>10</a>  
just text  
  <b attr="x">20</b>  
</root>  
'  
```  
  
 Следующий запрос получает строковое значение узла документов. Это значение формируется сцеплением строкового значения всех текстовых узлов, являющихся его потомками.  
  
```  
select @x.query('string(/)')  
```  
  
 Результат:  
  
```  
This is a comment 10  
just text  
 20  
```  
  
 Следующий запрос пытается получить строковое значение узла инструкции по обработке. Результатом будет пустая последовательность, так как он не содержит текстового узла.  
  
```  
select @x.query('string(/processing-instruction()[1])')  
```  
  
 Следующий запрос получает строковое значение узла комментариев и возвращается текстовый узел.  
  
```  
select @x.query('string(/comment()[1])')  
```  
  
 Результат:  
  
```  
This is a comment   
```  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
