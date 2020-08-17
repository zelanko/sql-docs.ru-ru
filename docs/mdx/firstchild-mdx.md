---
description: FirstChild (многомерные выражения)
title: FirstChild (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 60194581eb5bd2bb7f0a6252ca33062b60809706
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387490"
---
# <a name="firstchild-mdx"></a>FirstChild (многомерные выражения)


  Возвращает первого потомка заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.FirstChild   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="example"></a>Пример  
 Следующий запрос возвращает первое полугодие финансового 2003 года, которое является первым потомком финансового 2003 года в иерархии Fiscal.  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [LastChild &#40;&#41;многомерных выражений ](../mdx/lastchild-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
