---
title: "ParallelPeriod (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARALLELPERIOD
dev_langs:
- kbMDX
helpviewer_keywords:
- ParallelPeriod function
ms.assetid: 9c87f5a6-5694-46f1-9890-bd9705190ea7
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 294bab2d1403b6f6195a0888c731c95cfd938df8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает элемент предыдущего периода, расположенный в той же относительной позиции, что и заданный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Индекс*  
 Допустимое числовое выражение, указывающее количество параллельных периодов для отставания.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 Несмотря на сходство с [Cousin](../mdx/cousin-mdx.md) функции **ParallelPeriod** функции более тесно связана с временным рядом. **ParallelPeriod** функция берет предок заданного элемента на заданном уровне, находит родственный элемент предка с указан и наконец возвращает параллельный период среди потомков того же уровня заданного элемента.  
  
 **ParallelPeriod** функция имеет следующие значения по умолчанию:  
  
-   Если ни выражение уровня, ни выражение элемента указано, значение элемента по умолчанию используется текущий элемент первой иерархии первого измерения с типом *время* в группе мер.  
  
-   Если выражение уровня указано, но выражение элемента не указано, значение элемента по умолчанию — *Level_Expression*. **Hierarchy.CurrentMember**.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

