---
description: StdevP (многомерные выражения)
title: StdevP (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7b634f6bf6edf71f235458beb35e118165d126e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386930"
---
# <a name="stdevp-mdx"></a>StdevP (многомерные выражения)


  Возвращает среднеквадратичное отклонение совокупности числового выражения, вычисленное на наборе с использованием формулы смещенной совокупности (делением на *n*).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Функция **StDevP** использует формулу смещенной совокупности, а функция [STDEV](../mdx/stdev-mdx.md) использует формулу несмещенной совокупности.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается среднеквадратичное отклонение количества сделанных через Интернет заказов, которое вычисляется за первые три месяца 2003 г., при этом используется формула смещенной совокупности.  
  
```  
WITH MEMBER Measures.x AS   
   StdevP   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
