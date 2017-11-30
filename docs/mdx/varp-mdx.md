---
title: "Функция VarP (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VARP
dev_langs: kbMDX
helpviewer_keywords: VarP function [MDX]
ms.assetid: feca648d-bbc8-44c8-9a0e-38f66d914c72
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9f223184c122daeae9f9b1e09daa252bd46882c0
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="varp-mdx"></a>VarP (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает дисперсию генеральной совокупности для числового выражения, вычисляемого на наборе по формуле смещенной совокупности (делением  *n* -1).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Замечания  
 **VarP** функция возвращает смещенную дисперсию указанного числового выражения, рассчитанного для указанного набора.  
  
 **VarP** функция использует смещенной совокупности формул при [Var](../mdx/var-mdx.md) функции используется формула несмещенной совокупности.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
