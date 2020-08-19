---
description: Var (многомерные выражения)
title: Var (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 46aad9a9b7c328d23680df3c74bcf09a465b868d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483717"
---
# <a name="var-mdx"></a>Var (многомерные выражения)


  Возвращает выборку дисперсии числового выражения, вычисленную на множестве с помощью формулы несмещенной совокупности (делением на *n*).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Функция **var** возвращает несмещенную дисперсию указанного числового выражения, вычисленную для указанного набора.  
  
 Функция **var** использует формулу несмещенной совокупности, а функция [VARP](../mdx/varp-mdx.md) использует формулу смещенной совокупности.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
