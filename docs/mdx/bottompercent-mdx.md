---
title: BottomPercent (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 26df73b692843cf11cc0fc0caa07ab84158ae47f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577276"
---
# <a name="bottompercent-mdx"></a>BottomPercent (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Сортирует набор по возрастанию и возвращает набор кортежей с наименьшими значениями, совокупное значение которых больше или равно заданному проценту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Процент*  
 Допустимое числовое выражение, указывающее процент возвращаемых кортежей.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 **BottomPercent** функция вычисляет сумму указанного числового выражения, вычисленное на указанного набора, отсортированного в возрастающем порядке. Затем функция возвращает элементы с наименьшими значениями, доля суммы которых в суммарном значении меньше или равна указанному проценту. Эта функция возвращает самый маленький поднабор набора, совокупное значение которого равно по меньшей мере заданному проценту. Возвращенные элементы упорядочены по убыванию.  
  
> [!IMPORTANT]  
>  **BottomPercent** функция, как [TopPercent](../mdx/toppercent-mdx.md) , всегда нарушает иерархию. Дополнительные сведения см. в описании функции Order.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается наименьший набор элементов уровня City в иерархии Geography в измерении Geography за 2003 финансовый год для категории Bike (начиная с элементов данного набора с наименьшим количеством продаж), совокупный итог этих элементов на основе меры Reseller Sales Amount равен по меньшей мере 15 %.  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
