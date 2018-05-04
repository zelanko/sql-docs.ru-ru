---
title: TopSum (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TOPSUM
dev_langs:
- kbMDX
helpviewer_keywords:
- TopSum function
ms.assetid: e32496fd-4897-43c9-a388-4028609f4ffb
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 75c30d2874cfdbb46823f095d14685866d3e6252
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="topsum-mdx"></a>TopSum (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Сортирует набор и возвращает самые верхние элементы, совокупное значение которых не меньше указанного значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Value*  
 Допустимое числовое выражение, указывающее величину, с которой сравнивается каждый кортеж.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение, которое обычно является многомерным выражением, возвращающим меру.  
  
## <a name="remarks"></a>Замечания  
 **TopSum** функция вычисляет сумму заданной меры, рассчитанной указанного набора, отсортированного в убывающем порядке. Функция возвращает элементы с самыми высокими значениями, чьи итоги на основе указанного числового выражения по меньшей мере равны заданному значению. Функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному значению. Возвращенные элементы упорядочены по убыванию.  
  
> [!IMPORTANT]  
>  Как [BottomSum](../mdx/bottomsum-mdx.md) функции **TopSum** функция всегда нарушает иерархию.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается наименьший набор элементов уровня City в иерархии Geography в измерении Geography для категории Bike (начиная с элементов данного набора с наибольшим количеством продаж), совокупный итог этих элементов на основе меры Reseller Sales Amount равен по меньшей мере 6 000 000.  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
