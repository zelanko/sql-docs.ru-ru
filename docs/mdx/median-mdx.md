---
title: "Median (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: MEDIAN
dev_langs: kbMDX
helpviewer_keywords: Median function
ms.assetid: 7a326a3f-0123-45c4-9b18-31f83b90d986
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3cfa0b03deae60d9354e2e7056e0725125355ff4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="median-mdx"></a>Median (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает медиант числового выражения, вычисляемого на наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Median(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, оно вычисляется для всех элементов набора и затем возвращается медиана вычислений. Если числовое выражение не указано, указанный набор вычисляется в текущем контексте элементов набора и возвращается медиана вычислений.  
  
 Медиана — это значение из середины набора упорядоченных чисел. (Не путайте медиана со средним значением, которое представляет собой сумму набора чисел, разделенную на их количество). Для определения медианы находится такое наименьшее значение, которое не превышает минимум половину всех значений набора. Если набор содержит нечетное количество чисел, медиана равняется одному значению. Если количество чисел четное, медиана равняется усредненному значению двух чисел посередине.  
  
> [!NOTE]  
>  Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] не обрабатывают неопределенные значения при вычислении значения медианы для набора упорядоченных чисел.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается медиана сумм от продаж за месяц для каждого квартала и страны в кубе Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Median   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
