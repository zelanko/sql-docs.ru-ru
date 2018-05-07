---
title: Cousin (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COUSIN
dev_langs:
- kbMDX
helpviewer_keywords:
- Cousin function
ms.assetid: 9a416685-d35d-4d9c-a9f6-4574cbe59aea
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 30bfe88ded0c5723a673b4a99d89451339aadbd2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cousin-mdx"></a>Cousin (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает дочерний элемент, позиция которого относительно родительского элемента совпадает с позицией заданного дочернего элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Cousin( Member_Expression , Ancestor_Member_Expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Ancestor_Member_Expression*  
 Допустимое многомерное выражение элемента, возвращающее элемент-предок.  
  
## <a name="remarks"></a>Замечания  
 Функция обрабатывает порядок и положение элементов на уровнях. Если существуют две иерархии, первая из которых имеет четыре уровня, а вторая — пять, «кузен» третьего уровня первой иерархии находится на третьем уровне второй иерархии.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается родственный объект четвертого квартала 2002 финансового года, основанный на его предке на уровне года в 2003 финансовом году. Полученный родственный объект является четвертым кварталом 2003 финансового года.  
  
```  
SELECT Cousin   
   ( [Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002],  
     [Date].[Fiscal].[FY 2003]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
 В следующем примере возвращается родственный объект июля 2002 финансового года, основанный на его предке на уровне квартала в 2004 финансовом году (второй квартал). Полученный родственный объект является октябрем 2003 года.  
  
```  
SELECT Cousin   
   ([Date].[Fiscal].[Month].[July 2002] ,  
    [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2004]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
