---
title: MemberToStr (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ac9998edcf11477a2a4aff1af951d2dc4a17cbbb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581576"
---
# <a name="membertostr-mdx"></a>MemberToStr (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает строку в формате многомерных выражений, соответствующую указанному элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MemberToStr(Member_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает строку, содержащую уникальное имя элемента. Обычно она используется для передачи уникального имени элемента внешней функции.  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает строку «[Geography].[Geography].[Country].&[United States]»:  
  
 `WITH MEMBER Measures.x AS MemberToStr`  
  
 `([Geography].[Geography].[Country].[United States])`  
  
 `SELECT Measures.x ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
