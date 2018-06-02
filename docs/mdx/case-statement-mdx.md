---
title: Инструкция CASE (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c57276a75e8dd25f13a51c7bd0ea6c75a119a861
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577256"
---
# <a name="case-statement-mdx"></a>Инструкция CASE (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Позволяет возвращать указанные значения из нескольких сравнений согласно условию. Существуют два типа инструкции CASE.  
  
-   Простая инструкция CASE, сравнивающая выражение с набором простых выражений и возвращающая определенные значения.  
  
-   Инструкция CASE для поиска, вычисляющая набор выражений логического типа и возвращающая определенные значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Simple Case Statement  
CASE [input_expression]  
WHEN when_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
  
Search Case Statement  
CASE   
WHEN Boolean_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
```  
  
## <a name="arguments"></a>Аргументы  
 *input_expression*  
 Многомерное выражение, результатом вычисления которого является скалярное значение.  
  
 *when_expression*  
 Скалярное значение, по которому *input_expression* вычисляется, если результатом true, возвращается скалярное значение *результирующее_выражение_для_противоположного_случая*.  
  
 *when_true_result_expression*  
 Скалярное значение, которое возвращается, если результатом предложения WHEN является TRUE.  
  
 *результирующее_выражение_для_противоположного_случая*  
 Скалярное значение, возвращаемое в том случае, если при вычислении ни одно из предложений WHEN не вернуло TRUE.  
  
 *Boolean_expression*  
 Многомерное выражение, результатом вычисления которого является скалярное значение.  
  
## <a name="remarks"></a>Примечания  
 Если нет предложения ELSE, а все предложения WHEN дали значение false, тогда результатом будет пустая ячейка.  
  
## <a name="simple-case-expression"></a>Простое выражение CASE  
 Многомерное Выражение вычисляет простое выражение case, разрешая *input_expression* которого является скалярное значение. Это значение затем сравнивается со скалярным значением *when_expression*. Если скалярные значения совпадают, инструкция CASE возвращает значение *when_true_expression*. Если скалярные значения не совпадают, вычисляется следующее предложение WHEN. Если все предложения WHEN возвращают false, значение *результирующее_выражение_для_противоположного_случая* из предложения ELSE, возвращается при их наличии.  
  
 В следующем примере значение меры Reseller Order Count сравнивается в нескольких предложениях WHEN и возвращается результат, зависящий от значения меры Reseller Order Count в каждом году. Для значений меры Reseller Order Count, которые не соответствуют скалярное значение, указанное в *when_expression* в предложении WHEN, скалярное значение *результирующее_выражение_для_противоположного_случая* возвращается.  
  
```  
WITH MEMBER [Measures].x AS   
CASE [Measures].[Reseller Order Count]  
   WHEN 0 THEN 'NONE'  
   WHEN 1 THEN 'SMALL'  
   WHEN 2 THEN 'SMALL'  
   WHEN 3 THEN 'MEDIUM'  
   WHEN 4 THEN 'MEDIUM'  
   WHEN 5 THEN 'LARGE'  
   WHEN 6 THEN 'LARGE'  
      ELSE 'VERY LARGE'  
END  
SELECT Calendar.[Calendar Year] on 0  
, NON EMPTY [Geography].[Postal Code].Members ON 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="searched-case-expression"></a>Выражение CASE для поиска  
 Для более сложных вычислений можно использовать выражение CASE для поиска. Оно позволяет узнать, принадлежит ли значение входного выражения диапазону значений. Многомерное выражение вычисляет предложения WHEN, чтобы они появились в инструкции CASE.  
  
 В следующем примере мера Reseller Order Count вычисляется по заданному *Boolean_expression* для каждого несколько предложений WHEN. Возвращается результат, зависящий от значения меры Reseller Order Count в каждом году. Поскольку предложения WHEN вычисляются в том порядке, в котором они перечислены, всем значениям больше 6 можно легко присвоить значение «VERY LARGE», не указывая все значения явно. Для значений меры Reseller Order Count, которые не указаны в предложении WHEN, скалярное значение *результирующее_выражение_для_противоположного_случая* возвращается.  
  
```  
WITH MEMBER [Measures].x AS   
CASE   
   WHEN [Measures].[Reseller Order Count] > 6 THEN 'VERY LARGE'  
   WHEN [Measures].[Reseller Order Count] > 4 THEN 'LARGE'  
   WHEN [Measures].[Reseller Order Count] > 2 THEN 'MEDIUM'  
   WHEN [Measures].[Reseller Order Count] > 0 THEN 'SMALL'  
   ELSE "NONE"  
END  
SELECT Calendar.[Calendar Year] on 0,  
NON EMPTY [Geography].[Postal Code].Members on 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="see-also"></a>См. также  
 [Инструкции сценариев многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
