---
title: Var (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5a9f9461f531f3a37feac40ac1f4af03f620bd3f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581696"
---
# <a name="var-mdx"></a>Var (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает выборочную дисперсию числового выражения, вычисляемого на наборе по формуле несмещенной совокупности (делением *n*).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 **Var** функция возвращает несмещенную дисперсию указанного числового выражения, вычисленную на множестве.  
  
 **Var** функция использует формулу несмещенной совокупности и [VarP](../mdx/varp-mdx.md) функции используется формула смещенной совокупности.  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
