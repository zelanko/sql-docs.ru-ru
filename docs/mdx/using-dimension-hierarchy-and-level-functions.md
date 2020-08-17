---
description: Функции измерений, иерархий и уровней
title: Использование функций измерения, иерархии и уровня | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: afb7d324a2a4450a4df09ec3493954f0566a2cfc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341110"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Функции измерений, иерархий и уровней


  Функции измерений, иерархий и уровней применяются для обхода многомерных структур в службах Analysis Services. Обычно они используются совместно с другими функциями для получения сведений об элементах измерения, иерархии или уровня.  
  
 В следующем примере показано, как использовать **. Измерение**, **. Иерархия**и **. Функции уровня** :  
  
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
 [Многомерные выражения &#40;измерения&#41;](../mdx/dimension-mdx.md)   
 [Функции &#40;синтаксиса многомерных выражений&#41;](../mdx/functions-mdx-syntax.md)   
 [Иерархия &#40;&#41;многомерных выражений ](../mdx/hierarchy-mdx.md)   
 [&#41;&#40;уровня многомерных выражений ](../mdx/level-mdx.md)  
  
  
