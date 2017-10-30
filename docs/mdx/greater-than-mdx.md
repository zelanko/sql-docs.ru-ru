---
title: "&gt;(Больше) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '>'
dev_langs:
- kbMDX
helpviewer_keywords:
- greater than operator (>)
- '> (greater than operator)'
ms.assetid: 36ba6462-5517-43be-8e7d-a38b7343c5d3
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a80b1ad48b5e98f2c3489377b1d901a2b2500e20
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="gt-greater-than-mdx"></a>&gt;(Больше) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выполняет операцию сравнения, в которой определяется, превышает ли значение одного многомерного выражения значение другого многомерного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MDX_Expression > MDX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, определяемое исходя из следующих условий.  
  
-   **значение true,** Если оба аргумента не равны null и первый параметр имеет значение, которое больше значения второго параметра.  
  
-   **false** Если оба аргумента не равны null и первый параметр имеет значение, которое равно или меньше значения второго параметра.  
  
-   Равно NULL, если любой из параметров или оба параметра возвращают значение NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере запроса демонстрируется использование этого оператора:  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is more than 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] > .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[HighGPM])  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам Многомерных &#40; Многомерные Выражения &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  

