---
title: Порядковый номер (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 61c5c3c4bbb2f04f1ebb9743e18eb8088632eab0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581266"
---
# <a name="ordinal-mdx"></a>Ordinal (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает начинающееся с нуля порядковое значение, связанное с уровнем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Примечания  
 **Порядковый номер** функция часто используется в сочетании с **IIF** и **CurrentMember** функции по условию отображать различные значения на разных уровнях иерархии, на основании порядковый номер каждой из ячеек в результатах запроса. Например, можно использовать **порядковый номер** функции для вычисления на определенных уровнях и отображение значения по умолчанию «N/a» на других уровнях.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается порядковый номер уровня Calendar Quarter в иерархии Calendar.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
