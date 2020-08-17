---
description: Crossjoin (многомерные выражения)
title: Перекрестное соединение (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 759feb8b64a06e6238d338d4d619dd1433819dda
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387540"
---
# <a name="crossjoin-mdx"></a>Crossjoin (многомерные выражения)


  Возвращает перекрестное произведение двух или нескольких наборов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Standard syntax  
Crossjoin(Set_Expression1 ,Set_Expression2 [,...n] )  
  
Alternate syntax  
Set_Expression1 * Set_Expression2 [* ...n]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
## <a name="remarks"></a>Remarks  
 Функция с **перекрестным** соединением Возвращает перекрестное произведение двух или более заданных наборов. Порядок кортежей в результирующем наборе зависит от порядка соединяемых наборов и от порядка их элементов. Например, если первый набор состоит из {x1, x2,..., x*n*}, а второй набор состоит из {Y1, Y2,..., y*n*}, перекрестное произведение этих наборов будет следующим:  
  
 {(x1, y1), (x1, Y2),..., (x1, y*n*), (x2, y1), (x2, y2),...,  
  
 (x2, y*n*),..., (x*n*, y1), (x*n*, Y2),..., (xn, y*n*)}  
  
> [!IMPORTANT]  
>  Если наборы в перекрестном соединении состоят из кортежей из различных иерархий атрибутов одного измерения, функция вернет только те кортежи, которые действительно существуют. Дополнительные сведения см. в разделе Основные [понятия в многомерных выражениях &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services).  
  
## <a name="examples"></a>Примеры  
 В следующем запросе показаны простые примеры использования функции Crossjoin по осям Columns и Rows запроса:  
  
 `SELECT`  
  
 `[Customer].[Country].Members *`  
  
 `[Customer].[State-Province].Members`  
  
 `ON 0,`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].Members,`  
  
 `[Product].[Category].[Category].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE Measures.[Internet Sales Amount]`  
  
 В следующем примере показана автоматическая фильтрация, которая выполняется при перекрестном соединении различных иерархий из одного измерения:  
  
 `SELECT`  
  
 `Measures.[Internet Sales Amount]`  
  
 `ON 0,`  
  
 `//Only the dates in Calendar Years 2003 and 2004 will be returned here`  
  
 `Crossjoin(`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]},`  
  
 `[Date].[Date].[Date].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующих трех примерах возвращается одинаковый результат — значение меры Internet Sales Amount по штатам в США. В первых двух примерах используются два синтаксиса перекрестного соединения, а в третьем демонстрируется применение предложения WHERE для извлечения тех же сведений.  
  
### <a name="example-1"></a>Пример 1  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
       [Customer].[State-Province].Members  
   ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-2"></a>Пример 2  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-3"></a>Пример 3  
  
```  
SELECT   
   [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
