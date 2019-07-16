---
title: DIMENSIONS (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 84d5ab0caa22c6f35f3e7b790dbfb3348df8ceb1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67999964"
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
 Если указан номер иерархии, **измерения** функция возвращает иерархию, отсчитываемый от нуля позиция в пределах куба которого является указанным номером иерархии.  
  
 Если имя иерархии указано, **измерения** функция возвращает указанную иерархию. Как правило, использовать это строковая версия **измерения** функции с помощью определяемых пользователем функций.  
  
> [!NOTE]  
>  **Меры** измерения всегда представляется `Dimensions(0)`.  
  
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
