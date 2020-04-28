---
title: Функция number (XQuery) | Документация Майкрософт
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
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
author: rothja
ms.author: jroth
ms.openlocfilehash: 31a52f86692d5769fe22f4cf0b5a04ad324c3ac0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67930117"
---
# <a name="functions-on-nodes---number"></a>Функции с узлами — number
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает числовое значение узла, обозначенное *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Узел, значение которого будет возвращено в виде числа.  
  
## <a name="remarks"></a>Remarks  
 Если *$arg* не указан, возвращается числовое значение узла контекста, преобразованное в Double. В SQL Server **fn: Number ()** без аргумента может использоваться только в контексте контекстно-зависимого предиката. Точнее, она может использоваться только внутри квадратных скобок ([ ]). Например, следующее выражение возвращает элемент <`ROOT`>.  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 Если значение узла не является допустимым лексическим представлением числового простого типа, как определено в **схеме XML часть 2: типы данных, рекомендация W3C**, функция возвращает пустую последовательность. Синтаксис NaN не поддерживается.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-number-xquery-function-to-retrieve-the-numeric-value-of-an-attribute"></a>А) Использование функции number() языка XQuery для получения числового значения атрибута  
 В следующем запросе получается числовое значение атрибута, представляющего объем партии, производимого в первом цехе, участвующем в производственном процессе для модели продукта 7.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
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
  
-   Функция **Number ()** не является обязательной, как показано в запросе для атрибута **лотсизеа** . Это функция языка XPath 1.0, и она включена в основном по причинам обратной совместимости;  
  
-   В языке XQuery для **лотсизеб** указана числовая функция и является избыточным.  
  
-   Запрос для **больших объемов** иллюстрирует использование числового значения в арифметической операции.  
  
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
  
-   Функция **Number ()** принимает только узлы. Она не принимает атомарных значений;  
  
-   Если значения не могут быть возвращены в виде числа, функция **Number ()** возвращает пустую последовательность вместо NaN.  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
