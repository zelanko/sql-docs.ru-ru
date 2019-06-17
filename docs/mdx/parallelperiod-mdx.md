---
title: ParallelPeriod (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c1f495ce1fad9a318ea5e6c1f3fadd88f8313cd6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63473076"
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
  
## <a name="remarks"></a>Примечания  
 Несмотря на то что аналогичную [Cousin](../mdx/cousin-mdx.md) функции **ParallelPeriod** функции более тесно связана с временных рядов. **ParallelPeriod** функция берет предок заданного элемента на заданном уровне, находит родственный элемент предка указан и наконец возвращает параллельный период среди указанного элемента потомки того же уровня.  
  
 **ParallelPeriod** функция имеет следующие значения по умолчанию:  
  
-   Если ни выражение уровня, ни выражение элемента указано, значение элемента по умолчанию используется текущий элемент первой иерархии первого измерения типа *время* в группе мер.  
  
-   Если выражение уровня определено, но выражение элемента не указано, значение элемента по умолчанию — *Level_Expression*. **Hierarchy.CurrentMember**.  
  
-   Значение Index по умолчанию равно 1.  
  
-   Уровень по умолчанию соответствует уровню родительского элемента для указанного элемента.  
  
 **ParallelPeriod** функция эквивалентна следующей инструкции многомерных Выражений:  
  
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
  
  
