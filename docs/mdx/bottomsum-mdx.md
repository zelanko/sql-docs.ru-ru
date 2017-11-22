---
title: "BottomSum (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: BOTTOMSUM
dev_langs: kbMDX
helpviewer_keywords: BottomSum function
ms.assetid: b3b10e68-2a36-4c38-85f4-3bb7917d5ae8
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e7175a655406dd27f11c2594ad53dfc233a6c1a9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="bottomsum-mdx"></a>BottomSum (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сортирует заданный набор по возрастанию и возвращает набор кортежей с наименьшими значениями, совокупное значение которых меньше или равно заданному значению.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BottomSum(Set_Expression, Value, Numeric_Expression)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Значение*  
 Допустимое числовое выражение, указывающее величину, с которой сравнивается каждый кортеж.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Замечания  
 **BottomSum** функция вычисляет сумму заданной меры, рассчитанной указанного набора, отсортированного в возрастающем порядке. Функция возвращает элементы с самыми низкими значениями, чьи итоги на основе указанного числового выражения по меньшей мере равны заданному значению. Функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному значению. Возвращенные элементы упорядочены по возрастанию.  
  
> [!IMPORTANT]  
>  **BottomSum** функция, как [TopSum](../mdx/topsum-mdx.md) , всегда нарушает иерархию.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается наименьший набор элементов уровня City в иерархии Geography в измерении Geography за 2003 финансовый год для категории Bike, чей совокупный итог по мере Reseller Sales Amount составляет не менее 50 000.  
  
 `SELECT`  
  
 `[Product].[Product Categories].Bikes ON 0,`  
  
 `BottomSum`  
  
 `({[Geography].[Geography].[City].Members}`  
  
 `, 50000`  
  
 `, ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)`  
  
 `) ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
