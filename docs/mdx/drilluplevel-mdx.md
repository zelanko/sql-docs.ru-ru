---
title: DrillupLevel (многомерные Выражения) | Документы Microsoft
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
- DRILLUPLEVEL
dev_langs:
- kbMDX
helpviewer_keywords:
- DrillupLevel function
ms.assetid: 63431f79-f3a1-40c4-bf57-2b6bd8991cc3
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ec561536a098e927731a3359edae3f2e35f3d481
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Детализирует обобщением элементы набора, находящиеся ниже указанного уровня.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Remarks  
 **DrillupLevel** функция возвращает набор элементов, иерархически организованных на основе элементов, включенные в указанный набор. Порядок элементов в указанном наборе сохраняется.  
  
 Если выражение уровня указано, **DrillupLevel** функция формирует набор путем получения только элементы, расположенные выше указанного уровня. Если выражение уровня указано, но набор не содержит элементов на данном уровне, возвращается указанный набор.  
  
 Если выражение уровня не задано, функция извлекает элементы, расположенные на один уровень выше самого нижнего уровня первого измерения, на которое ссылается указанный набор.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается набор элементов первого набора, которые расположены выше уровня Subcategory.  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
