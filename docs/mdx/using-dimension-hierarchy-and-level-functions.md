---
title: Используя измерения, иерархии и функции уровней | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- dimensions [Analysis Services], functions
- level functions [MDX]
- hierarchy functions [MDX]
ms.assetid: e730f65a-1798-4094-9acf-2739e2505d52
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 95264cc1e894fdd2acd43b4f49807968ea9ce587
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Функции измерений, иерархий и уровней
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Функции измерений, иерархий и уровней применяются для обхода многомерных структур в службах Analysis Services. Обычно они используются совместно с другими функциями для получения сведений об элементах измерения, иерархии или уровня.  
  
 В следующем примере показано, как использовать **. Измерение**, **. Иерархия**, и **. Уровень** функции:  
  
 `WITH`  
  
 `MEMBER MEASURES.DIMENSIONNAME AS [Date].[Calendar].CURRENTMEMBER.DIMENSION.NAME`  
  
 `MEMBER MEASURES.HIERARCHYNAME AS [Date].[Calendar].CURRENTMEMBER.HIERARCHY.NAME`  
  
 `MEMBER MEASURES.LEVELNAME AS [Date].[Calendar].LEVEL.NAME`  
  
 `SELECT`  
  
 `{MEASURES.DIMENSIONNAME, MEASURES.HIERARCHYNAME, MEASURES.LEVELNAME}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Измерения &#40; Многомерные Выражения &#41;](../mdx/dimension-mdx.md)   
 [Функции &#40; Синтаксис многомерных Выражений &#41;](../mdx/functions-mdx-syntax.md)   
 [Иерархия &#40; Многомерные Выражения &#41;](../mdx/hierarchy-mdx.md)   
 [Уровень &#40; Многомерные Выражения &#41;](../mdx/level-mdx.md)  
  
  
