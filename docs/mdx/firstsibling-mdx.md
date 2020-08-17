---
description: FirstSibling (многомерные выражения)
title: FirstSibling (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 265c3bce4ad873ec3c5d8ae0760455f87b1855f2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387480"
---
# <a name="firstsibling-mdx"></a>FirstSibling (многомерные выражения)


  Возвращает первого потомка предка заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.FirstSibling   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="example"></a>Пример  
 В следующем запросе возвращается первый элемент с таким же родителем, что и у 2003 финансового года, из иерархии «Fiscal»; это будет 2002 финансовый год.  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstSibling ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
