---
title: SIBLINGS (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9f292a67116fad324a3a4b2706698febc7713f59
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582226"
---
# <a name="siblings-mdx"></a>Siblings (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает элементы, имеющие общего родителя с указанным элементом, включая сам элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="example"></a>Пример  
 В следующем примере возвращается мера по умолчанию для элементов с общим родителем «Март 2003» (такими элементами являются «Январь 2003», «Февраль 2003») и самого элемента «Март 2003».  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
