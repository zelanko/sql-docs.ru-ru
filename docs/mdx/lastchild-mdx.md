---
title: LastChild (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LASTCHILD
dev_langs:
- kbMDX
helpviewer_keywords:
- LastChild function
ms.assetid: 70d09bd0-4330-4be8-8bb5-7a30f44fb4ae
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 05ab9f9cda9738208028eae08395cbd6fb8e5dd3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="lastchild-mdx"></a>LastChild (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает последний дочерний элемент указанного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Member_Expression.LastChild   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
### <a name="example"></a>Пример  
 В следующем примере возвращается значение элемента «September 2001», который является последним потомком первого финансового квартала 2002-го финансового года.  
  
```  
SELECT [Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002].LastChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [FirstChild &#40; Многомерные Выражения &#41;](../mdx/firstchild-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
