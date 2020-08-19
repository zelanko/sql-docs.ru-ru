---
description: VarP (многомерные выражения)
title: VarP (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c850ba60ac9900228c6adaa03aa97b46b1abddf1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429726"
---
# <a name="varp-mdx"></a>VarP (многомерные выражения)


  Возвращает дисперсию совокупности числового выражения, вычисленную на множестве с помощью формулы смещенной совокупности (делением на *n*– 1).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Функция **VARP** возвращает смещенную дисперсию указанного числового выражения, вычисленную для указанного набора.  
  
 Функция **VARP** использует формулу смещенной совокупности, а функция [var](../mdx/var-mdx.md) использует формулу несмещенной совокупности.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
