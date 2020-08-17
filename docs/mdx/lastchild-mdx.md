---
description: LastChild (многомерные выражения)
title: LastChild (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e7250be85dd96c5ae7d0dbfaf9ad013dbc3cff6a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387340"
---
# <a name="lastchild-mdx"></a>LastChild (многомерные выражения)


  Возвращает последний дочерний элемент указанного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.LastChild   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="example"></a>Пример  
 В следующем примере возвращается значение элемента «September 2001», который является последним потомком первого финансового квартала 2002-го финансового года.  
  
```  
SELECT [Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002].LastChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [FirstChild &#40;&#41;многомерных выражений ](../mdx/firstchild-mdx.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
