---
title: Используя измерения, иерархии и функции уровней | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8fa374ef93f56f8cddaed81bc9e3872d1eb206c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097180"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Функции измерений, иерархий и уровней


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
  
## <a name="see-also"></a>См. также  
 [Измерение &#40;многомерных Выражений&#41;](../mdx/dimension-mdx.md)   
 [Функции &#40;синтаксис многомерных Выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [Иерархия &#40;многомерных Выражений&#41;](../mdx/hierarchy-mdx.md)   
 [Уровень &#40;многомерных Выражений&#41;](../mdx/level-mdx.md)  
  
  
