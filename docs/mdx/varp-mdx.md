---
title: VarP (многомерные Выражения) | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251487"
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
  
 **VarP** функция использует смещенной совокупности формул при [Var](../mdx/var-mdx.md) функция использует формулу несмещенной совокупности.  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
