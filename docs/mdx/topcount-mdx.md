---
title: TopCount (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fa8edcf8af510a41affdcbcc9924edf69cf4c220
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63228047"
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
  
## <a name="remarks"></a>Примечания  
 Если числовое выражение указано, **TopCount** функция сортирует в порядке убывания кортежи в наборе заданного набора по значениям числового выражения, вычисленного над указанным набор. После сортировки набора **TopCount** функция затем возвращает заданное число кортежей с наибольшим значением.  
  
> [!IMPORTANT]  
>  Как и [BottomCount](../mdx/bottomcount-mdx.md) функции **TopCount** всегда ломает иерархию.  
  
 Если числовое выражение не указано, функция возвращает набор элементов в естественном порядке без какой-либо сортировки, ведет себя подобно [Head (MDX)](../mdx/head-mdx.md) функции.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
