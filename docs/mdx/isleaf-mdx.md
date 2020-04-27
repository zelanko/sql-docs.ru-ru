---
title: Листьев (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 400c55cdfcea35ae60859fb66489384870172744
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905947"
---
# <a name="isleaf-mdx"></a>IsLeaf (многомерные выражения)


  Возвращает значение, сообщающее, является ли элемент конечным.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsLeaf(Member_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Функция **листьев** возвращает **значение true** , если указанный элемент является конечным элементом. В противном случае функция возвращает **значение false**.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение TRUE, если элемент [Date].[Fiscal].CurrentMember является конечным:  
  
 `WITH MEMBER MEASURES.ISLEAFDEMO AS`  
  
 `IsLeaf([Date].[Fiscal].CURRENTMEMBER)`  
  
 `SELECT {MEASURES.ISLEAFDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
