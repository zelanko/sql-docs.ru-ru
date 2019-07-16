---
title: Parent (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9449c81e9f8e8de0c21d96062337e91b2f56398d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037193"
---
# <a name="parent-mdx"></a>Parent (многомерные выражения)


  Возвращает родительский элемент заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 **Родительского** функция возвращает родительский элемент указанного элемента.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается родитель элемента «July 1, 2001». В первом примере вычисления осуществляются в контексте иерархии атрибута Date и возвращается элемент «All Periods».  
  
```  
SELECT [Date].[Date].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере элемент «July 1, 2001» указан в контексте иерархии Calendar.  
  
```  
SELECT [Date].[Calendar].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
