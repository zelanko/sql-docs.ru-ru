---
title: NextMember (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4535b837d81db10f41f1445a7051678ce4fdd688
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742183"
---
# <a name="nextmember-mdx"></a>NextMember (многомерные выражения)


  Возвращает следующий элемент уровня, содержащего заданный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.NextMember   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 **NextMember** функция возвращает следующий элемент на том же уровне, который содержит указанный элемент.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается элемент для августа 2001 г. как следующий по отношению к элементу для июля 2001 г.  
  
```  
SELECT [Date].[Calendar].[Month].[July 2001].NextMember ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
