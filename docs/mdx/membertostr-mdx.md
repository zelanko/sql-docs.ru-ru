---
title: MemberToStr (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a33aede54557491dea50a557ed581929c5383e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68001464"
---
# <a name="membertostr-mdx"></a>MemberToStr (многомерные выражения)


  Возвращает строку в формате МНОГОМЕРных выражений, соответствующую указанному элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MemberToStr(Member_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Эта функция возвращает строку, содержащую уникальное имя элемента. Обычно он используется для передачи UniqueName элемента в внешнюю функцию.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается строка [Geography]. [Geography]. [Country]. & [США]:  
  
 `WITH MEMBER Measures.x AS MemberToStr`  
  
 `([Geography].[Geography].[Country].[United States])`  
  
 `SELECT Measures.x ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
