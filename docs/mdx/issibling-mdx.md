---
title: Коуровневый (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 15c80cec67b0a40c8ac4c436a45a4551132858f1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105352"
---
# <a name="issibling-mdx"></a>IsSibling (многомерные выражения)


  Возвращает значение, сообщающее, имеет ли указанный элемент общего родителя с другим указанным элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsSibling(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression1*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Member_Expression2*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Функция **Коэлементного уровня** возвращает **значение true** , если первый указанный элемент является элементом того же уровня, что и второй заданный элемент. В противном случае функция возвращает **значение false**.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение TRUE, если текущий элемент иерархии Fiscal в измерении Date является одноуровневым элементом с July 2002:  
  
 `WITH MEMBER MEASURES.ISSIBLINGDEMO AS`  
  
 `IsSibling([Date].[Fiscal].CURRENTMEMBER, [Date].[Fiscal].[Month].&[2002]&[7])`  
  
 `SELECT {MEASURES.ISSIBLINGDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
