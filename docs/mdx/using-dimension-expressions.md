---
title: Использование выражений измерений | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e492498ee6e15866e7fe6fd96588480c914b0622
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597522"
---
# <a name="using-dimension-expressions"></a>Использование выражений измерений


  Как правило, выражения измерений и иерархий используются при передаче параметров в функции многомерных выражений для получения элементов, наборов или кортежей из иерархии.  
  
 Выражения измерений могут быть только простыми выражениями, так как являются идентификаторами объектов. См. в разделе [выражения &#40;многомерных Выражений&#41; ](../mdx/expressions-mdx.md) объяснение простых и сложных выражениях.  
  
## <a name="dimension-expressions"></a>Выражения измерений  
 Выражение измерения содержит идентификатор измерения или функцию измерения.  
  
 Выражения измерений редко используются самостоятельно. Обычно нужно задать иерархию в измерении. Единственное исключение — измерение Measures, в котором нет иерархий.  
  
 В следующем примере показан вычисляемый элемент, в котором выражение [Measures] используется с функциями .Members и Count(), чтобы получить количество элементов в измерении Measures:  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Идентификатор измерения представлен как *Dimension_Name* в форме Бэкуса-Наура, используемой для описания инструкций многомерных Выражений.  
  
## <a name="hierarchy-expressions"></a>Выражения иерархии  
 Аналогично выражение иерархии содержит идентификатор иерархии или функцию иерархии. В следующем примере показано использование выражения иерархии [Дата].[Календарь] с функциями .Levels и .Count, чтобы возвратить количество уровней в иерархии «Календарь» измерения «Дата»:  
  
 `WITH MEMBER [Measures].[CalendarLevelCount] AS`  
  
 `[Date].[Calendar].Levels.Count`  
  
 `SELECT [Measures].[CalendarLevelCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Чаще всего выражения иерархии используются вместе с функцией .Members, чтобы получить все элементы иерархии. В следующем примере возвращаются все элементы иерархии [Дата].[Календарь] по оси строк:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Идентификатор иерархии представлен как *Dimension_Name.Hierarchy_Name* в форме Бэкуса-Наура, используемой для описания инструкций многомерных Выражений.  
  
## <a name="see-also"></a>См. также  
 [Выражения &#40;многомерных Выражений&#41;](../mdx/expressions-mdx.md)  
  
  
