---
title: "число, функция (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dc0ea3abeb06377819bfae2486b5ddd44734123b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-nodes---number"></a>Функции на узлах - номер
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает числовое значение узла, который обозначается *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Узел, значение которого будет возвращено в виде числа.  
  
## <a name="remarks"></a>Замечания  
 Если *$arg* — не указан, возвращается числовое значение контекстного узла, преобразуемого к типу double. В SQL Server **fn:number()** без аргумента может использоваться только в контексте контекстно зависимого предиката. Точнее, она может использоваться только внутри квадратных скобок ([ ]). Например, следующее выражение возвращает элемент <`ROOT`>.  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 Если значение узла не является допустимым лексическим представлением простого числового типа, как определено в **схема XML, часть 2: типы данных, рекомендация W3C**, функция возвращает пустую последовательность. Синтаксис NaN не поддерживается.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-number-xquery-function-to-retrieve-the-numeric-value-of-an-attribute"></a>A. Использование функции number() языка XQuery для получения числового значения атрибута  
 В следующем запросе получается числовое значение атрибута, представляющего объем партии, производимого в первом цехе, участвующем в производственном процессе для модели продукта 7.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in (//AWMI:root//AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"   
                   LotSizeA="{  $i/@LotSize }"  
                   LotSizeB="{  number($i/@LotSize) }"  
                   LotSizeC="{ number($i/@LotSize) + 1 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **Number()** функция не является обязательным, как показано в запросе для **LotSizeA** атрибута. Это функция языка XPath 1.0, и она включена в основном по причинам обратной совместимости;  
  
-   Язык XQuery для **LotSizeB** указывает числовую функцию и является избыточным.  
  
-   Запрос для **LotSizeD** иллюстрирует использование числового значения в арифметической операции.  
  
 Результат:  
  
```  
ProductModelID   Result  
----------------------------------------------  
7              <Location LocationID="10"   
                         LotSizeA="100"   
                         LotSizeB="100"   
                         LotSizeC="101" />  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Number()** принимает только узлы. Она не принимает атомарных значений;  
  
-   Если значения не возвращены в виде числа, **number()** функция возвращает пустую последовательность вместо NaN.  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  

