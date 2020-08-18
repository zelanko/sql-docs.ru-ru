---
description: TopCount (многомерные выражения)
title: TopCount (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b7d917963d8500e06bf9d2adcd1057e72e50512a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412881"
---
# <a name="topcount-mdx"></a>TopCount (многомерные выражения)


  Сортирует набор по убыванию и возвращает заданное число элементов с самыми высокими значениями.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopCount(Set_Expression,Count [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Count*  
 Допустимое числовое выражение, указывающее количество возвращаемых кортежей.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Remarks  
 Если числовое выражение указано, функция **TopCount** сортирует кортежи в наборе, заданном в указанном наборе, в порядке убывания значений, заданных числовым выражением, в соответствии с вычислением для указанного набора. После сортировки набора функция **TopCount** возвращает указанное число кортежей с наибольшим значением.  
  
> [!IMPORTANT]  
>  Как и функция [BottomCount](../mdx/bottomcount-mdx.md) , функция **TopCount** всегда прерывает иерархию.  
  
 Если числовое выражение не указано, функция возвращает набор элементов в естественном порядке без какой-либо сортировки, как в функции [head (многомерные выражения)](../mdx/head-mdx.md) .  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается 10 дат с самыми высокими значениями по мере Internet Sales Amount:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `TOPCOUNT([Date].[Date].[Date].MEMBERS, 10, [Measures].[Internet Sales Amount])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 В следующем примере из категории Bike возвращаются первые пять элементов набора, содержащего все сочетания элементов с уровнем City в иерархии Geography в измерении Geography и все финансовые годы из иерархии Fiscal измерения Date, отсортированные по мере Reseller Sales Amount (начиная с элементов этого набора с наибольшим объемом продаж).  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopCount  
   ({[Geography].[Geography].[City].Members   
      *[Date].[Fiscal].[Fiscal Year].Members}  
   , 5  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
