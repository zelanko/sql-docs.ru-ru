---
title: Функция VarP (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc1e6276de9a03af9800b9e242d54130c4241732
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743755"
---
# <a name="varp-mdx"></a>VarP (многомерные выражения)


  Возвращает дисперсию генеральной совокупности для числового выражения, вычисляемого на наборе по формуле смещенной совокупности (делением *n*-1).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 **VarP** функция возвращает смещенную дисперсию указанного числового выражения, рассчитанного для указанного набора.  
  
 **VarP** функция использует смещенной совокупности формул при [Var](../mdx/var-mdx.md) функции используется формула несмещенной совокупности.  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
