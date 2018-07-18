---
title: Номер функция (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
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
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 65faec31c6e89421ce05bab28dae97e18195bdde
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38031522"
---
# <a name="functions-on-nodes---number"></a>Функции с узлами — number
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает числовое значение узла, который обозначается *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Узел, значение которого будет возвращено в виде числа.  
  
## <a name="remarks"></a>Примечания  
 Если *$arg* является не указан, возвращается числовое значение контекстного узла, преобразуемого к типу double. В SQL Server **fn:number()** без аргумента может быть использована только в контексте контекстно зависимого предиката. Точнее, она может использоваться только внутри квадратных скобок ([ ]). Например, следующее выражение возвращает элемент <`ROOT`>.  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 Если значение узла не лексические допустимым представлением простого числового типа, как определено в **XML Schema Part 2: типы данных, рекомендация консорциума W3C**, функция возвращает пустую последовательность. Синтаксис NaN не поддерживается.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных **xml** -столбец базы данных AdventureWorks.  
  
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
  
-   **Number()** функция принимает только узлы. Она не принимает атомарных значений;  
  
-   Если значения не может быть возвращен в виде числа, **number()** функция возвращает пустую последовательность вместо NaN.  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
