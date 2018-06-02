---
title: QTD (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 218e90b5e43a1603978ba912fccb85ae16b34072
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580926"
---
# <a name="qtd-mdx"></a>Qtd (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает набор из одноуровневых элементов того же уровня, что и данный элемент, начиная с первого такого элемента и заканчивая данным элементом, в соответствии с ограничениями *квартал* уровня в измерении времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Если выражение элемента не указано, по умолчанию используется текущий элемент первой иерархии с уровнем типа *кварталы* в первом измерении типа *время* в группе мер.  
  
 **Qtd** функция — это функция ярлык для [PeriodsToDate &#40;многомерных Выражений&#41; ](../mdx/periodstodate-mdx.md) функция, выражение уровня аргумента задано значение *квартал*. Таким образом, выражение `Qtd(Member_Expression)` равнозначно выражению `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` член, суммарный за первые два месяца третьего квартала 2003 г, содержащихся в `Date` измерения, от **Adventure Works** куба.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        QTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
