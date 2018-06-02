---
title: Parent (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 32922aebffd9704725e534742656b86348f5e1ee
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580646"
---
# <a name="parent-mdx"></a>Parent (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает родительский элемент заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
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
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
