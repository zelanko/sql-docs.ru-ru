---
title: "BottomPercent (многомерные Выражения) | Документы Microsoft"
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
- BOTTOMPERCENT
dev_langs:
- kbMDX
helpviewer_keywords:
- BottomPercent function
ms.assetid: c04866e6-e6dd-4ed1-ae79-c718c194930c
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 416c5c68b30b72352ffc95658d0f34cc77f8e9af
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="bottompercent-mdx"></a>BottomPercent (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сортирует набор по возрастанию и возвращает набор кортежей с наименьшими значениями, совокупное значение которых больше или равно заданному проценту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Процент*  
 Допустимое числовое выражение, указывающее процент возвращаемых кортежей.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Замечания  
 **BottomPercent** функция вычисляет сумму указанного числового выражения, вычисленное на указанного набора, отсортированного в возрастающем порядке. Затем функция возвращает элементы с наименьшими значениями, доля суммы которых в суммарном значении меньше или равна указанному проценту. Эта функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному проценту. Возвращенные элементы упорядочены по убыванию.  
  
> [!IMPORTANT]  
>  **BottomPercent** функция, как [TopPercent](../mdx/toppercent-mdx.md) , всегда нарушает иерархию. Дополнительные сведения см. в описании функции Order.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается наименьший набор элементов уровня City в иерархии Geography в измерении Geography за 2003 финансовый год для категории Bike (начиная с элементов данного набора с наименьшим количеством продаж), совокупный итог этих элементов на основе меры Reseller Sales Amount равен по меньшей мере 15 %.  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

