---
title: Измерения (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2703122b67debf0749abcd2ea01114fb6ecaa06
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740193"
---
# <a name="dimensions-mdx"></a>Dimensions (многомерные выражения)


  Возвращает иерархию, указанную числовым или строковым выражением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>Аргументы  
 *Hierarchy_Number*  
 Допустимое числовое выражение, указывающее номер иерархии.  
  
 *Hierarchy_Name*  
 Допустимое строковое выражение, указывающее имя иерархии.  
  
## <a name="remarks"></a>Примечания  
 Если указан номер иерархии, **измерения** функция возвращает иерархии, отсчитываемый от нуля позиция в пределах куба которого является указанным номером иерархии.  
  
 Если имя иерархии указано, **измерения** функция возвращает указанную иерархию. Как правило, используется это строковая версия **измерения** функцию с определяемой пользователем функции.  
  
> [!NOTE]  
>  **Меры** измерения всегда имеет `Dimensions(0)`.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах используется **измерения** функция возвращает имя, количество уровней и количество элементов указанной иерархии, с помощью числового выражения и строкового выражения.  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
