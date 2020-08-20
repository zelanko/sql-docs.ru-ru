---
description: Инструкция CASE (многомерные выражения)
title: CASE, инструкция (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7a5907eb58fa102c46fa22af97116c4fad0f217a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466506"
---
# <a name="case-statement-mdx"></a>Инструкция CASE (многомерные выражения)


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
 Заданное скалярное значение, для которого вычисляется *input_expression* , при вычислении которого принимается значение true, возвращает скалярное значение *else_result_expression*.  
  
 *when_true_result_expression*  
 Скалярное значение, которое возвращается, если результатом предложения WHEN является TRUE.  
  
 *else_result_expression*  
 Скалярное значение, возвращаемое в том случае, если при вычислении ни одно из предложений WHEN не вернуло TRUE.  
  
 *Boolean_expression*  
 Многомерное выражение, результатом вычисления которого является скалярное значение.  
  
## <a name="remarks"></a>Комментарии  
 Если нет предложения ELSE, а все предложения WHEN дали значение false, тогда результатом будет пустая ячейка.  
  
## <a name="simple-case-expression"></a>Простое выражение CASE  
 MDX вычисляет простое выражение CASE, разрешающее *input_expression* скалярному значению. Это скалярное значение затем сравнивается с скалярным значением *when_expression*. Если два скалярных значения совпадают, оператор CASE возвращает значение *when_true_expression*. Если скалярные значения не совпадают, вычисляется следующее предложение WHEN. Если все предложения WHEN имеют значение false, то возвращается значение *else_result_expression* из предложения Else (при наличии).  
  
 В следующем примере значение меры Reseller Order Count сравнивается в нескольких предложениях WHEN и возвращается результат, зависящий от значения меры Reseller Order Count в каждом году. Для числа заказов торгового посредника, которые не соответствуют скалярному значению, указанному в *when_expression* в предложении WHEN, возвращается скалярное значение *else_result_expression* .  
  
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
  
 В следующем примере мера "число заказов торгового посредника" вычисляется на основе указанного *Boolean_expression* для каждого из нескольких предложений WHEN. Возвращается результат, зависящий от значения меры Reseller Order Count в каждом году. Поскольку предложения WHEN вычисляются в том порядке, в котором они перечислены, всем значениям больше 6 можно легко присвоить значение «VERY LARGE», не указывая все значения явно. Для числа заказов торгового посредника, которые не указаны в предложении WHEN, возвращается скалярное значение *else_result_expression* .  
  
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
 [Инструкции для создания скриптов многомерных выражений (многомерные выражения)](../mdx/mdx-scripting-statements-mdx.md)  
  
  
