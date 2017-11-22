---
title: "IsGeneration (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ISGENERATION
dev_langs: kbMDX
helpviewer_keywords: IsGeneration function
ms.assetid: fd11d2e0-d81d-45af-ac45-c98634d05550
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9d0b8adb889a555155d8030413b855c5663a776e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="isgeneration-mdx"></a>IsGeneration (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает значение, сообщающее, принадлежит ли заданный элемент указанному поколению.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsGeneration(Member_Expression, Generation_Number)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Generation_Number*  
 Допустимое числовое выражение, указывающее поколение, для которого заданный элемент будет вычисляться.  
  
## <a name="remarks"></a>Замечания  
 **IsGeneration** возврата функцией **true** если заданный элемент находится в указанном поколении. В противном случае функция возвращает **false**. Кроме того, если заданный элемент равен empty-член **IsGeneration** возврата функцией **false**.  
  
 При индексировании поколения конечные элементы имеют индекс поколения 0. Индекс поколения неконечных элементов определяется путем получения наибольшего индекса поколения из объединения всех потомков заданного элемента и прибавления 1 к этому значению. В зависимости от способа определения индекса поколения неконечных элементов конкретный неконечный элемент может принадлежать нескольким поколениям.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается значение TRUE, если элемент [Date].[Fiscal].CurrentMember принадлежит ко второму поколению:  
  
 `WITH MEMBER MEASURES.ISGENERATIONDEMO AS`  
  
 `IsGeneration([Date].[Fiscal].CURRENTMEMBER, 2)`  
  
 `SELECT {MEASURES.ISGENERATIONDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
