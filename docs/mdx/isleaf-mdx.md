---
description: IsLeaf (многомерные выражения)
title: Листьев (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b7dd1d76b417633ff50a77b3f2822e6f7cfd462
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471826"
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
