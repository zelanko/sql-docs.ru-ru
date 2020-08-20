---
description: ParallelPeriod (многомерные выражения)
title: ParallelPeriod (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4c8a6c91bae50ca06be46926f34de172e424e613
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471726"
---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (многомерные выражения)


  Возвращает элемент предыдущего периода, расположенный в той же относительной позиции, что и заданный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Index*  
 Допустимое числовое выражение, указывающее количество параллельных периодов для отставания.  
  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Комментарии  
 Хотя функция **ParallelPeriod** похожа на функцию [родственника](../mdx/cousin-mdx.md) , она более тесно связана с временными рядами. Функция **ParallelPeriod** принимает предка указанного элемента на заданном уровне, находит родственный элемент предка с заданной задержкой и, наконец, возвращает параллельный период указанного элемента среди потомков одноуровневого элемента.  
  
 Функция **ParallelPeriod** имеет следующие значения по умолчанию:  
  
-   Если не указано ни выражение уровня, ни выражение элемента, значением элемента по умолчанию является текущий элемент первой иерархии в первом измерении с типом *времени* в группе мер.  
  
-   Если выражение уровня задано, но выражение элемента не указано, значение элемента по умолчанию — *Level_Expression*. **Hierarchy. CurrentMember**.  
  
-   Значение Index по умолчанию равно 1.  
  
-   Уровень по умолчанию соответствует уровню родительского элемента для указанного элемента.  
  
 Функция **ParallelPeriod** эквивалентна следующей инструкции многомерных выражений:  
  
 `Cousin(Member_Expression, Ancestor(Member_Expression, Level_Expression) .Lag(Numeric_Expression))`  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается параллельный период для октября 2003 г. с отставанием в три периода, основанный на квартальном уровне, будет возвращен январь 2003 г.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Quarter]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 В следующем примере возвращается параллельный период для октября 2003 г. с отставанием в три периода, основанный на полугодовом уровне, будет возвращен апрель 2002 г.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Semester]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
