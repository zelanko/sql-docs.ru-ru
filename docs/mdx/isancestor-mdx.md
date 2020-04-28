---
title: Ancestor (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5cc8352b0d087b54a623cce892a05dfed29258b5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105264"
---
# <a name="isancestor-mdx"></a>IsAncestor (многомерные выражения)


  Возвращает значение, сообщающее, является ли заданный элемент предком другого заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression1*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Member_Expression2*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Функция **an** возвращает **значение true** , если первый заданный элемент является предком указанного второго элемента. В противном случае функция возвращает **значение false**.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается **значение true** , если [DATE]. [Финансовый]. CurrentMember является предком 2003 января.  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [&#40;&#41;многомерных выражений предков](../mdx/ancestor-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
