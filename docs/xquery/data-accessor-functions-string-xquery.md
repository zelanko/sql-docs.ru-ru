---
title: Функция String (XQuery) | Документация Майкрософт
description: Сведения о строке функции XQuery (), возвращающей значение аргумента, представленного в виде строки.
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
ms.openlocfilehash: d4c0dee40eb08aac425f93570c98fc88d32bcc60
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730969"
---
# <a name="data-accessor-functions---string-xquery"></a>Функции метода доступа к данным — string (XQuery)
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  Возвращает значение *$arg* , представленное в виде строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:string() as xs:string  
fn:string($arg as item()?) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Узел или атомарное значение.  
  
## <a name="remarks"></a>Примечания  
  
-   Если *$arg* является пустой последовательностью, возвращается строка нулевой длины.  
  
-   Если *$arg* является узлом, функция возвращает строковое значение узла, полученное с помощью метода доступа к строковому значению. Это определено в спецификации W3C XQuery 1.0 и XPath 2.0 Data Model.  
  
-   Если *$arg* является атомарным значением, функция возвращает ту же строку, которая возвращается выражением, приведенным в виде **xs: String**, *$arg*, за исключением случаев, когда указано иное.  
  
-   Если *$arg* имеет тип **xs: anyURI**, URI преобразуется в строку без экранирования специальных символов.  
  
-   Эта реализация, **fn: String ()** без аргумента может использоваться только в контексте контекстно-зависимого предиката. Точнее, она может использоваться только внутри квадратных скобок ([ ]).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-string-function"></a>A. Использование строковой функции  
 Следующий запрос получает `Features` узел <> дочернего элемента элемента <`ProductDescription`>.  
  
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
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
