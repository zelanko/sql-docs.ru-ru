---
title: StdevP (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14117ed4a3e3e7afc0152c5e659d1c7f040957e9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150139"
---
# <a name="stdevp-mdx"></a>StdevP (многомерные выражения)


  Возвращает среднеквадратичное отклонение совокупности для числового выражения, вычисляемого на наборе по формуле смещенной совокупности (делением *n*).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 **StdevP** функция использует смещенной совокупности формул при [Stdev](../mdx/stdev-mdx.md) функция использует формулу несмещенной совокупности.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
