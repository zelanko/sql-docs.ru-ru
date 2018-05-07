---
title: Порядковый номер (многомерные Выражения) | Документы Microsoft
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
- Ordinal
dev_langs:
- kbMDX
helpviewer_keywords:
- Ordinal function
ms.assetid: 9d416c39-da4a-4f0d-8d85-a76af5df0a87
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 3e1a3e550dd694972ce137d44f620bf87b1169de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ordinal-mdx"></a>Ordinal (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает начинающееся с нуля порядковое значение, связанное с уровнем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Замечания  
 **Порядковый номер** функция часто используется в сочетании с **IIF** и **CurrentMember** функции по условию отображать различные значения на разных уровнях иерархии, на основании порядковый номер каждой из ячеек в результатах запроса. Например, можно использовать **порядковый номер** функции для вычисления на определенных уровнях и отображение значения по умолчанию «N/a» на других уровнях.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается порядковый номер уровня Calendar Quarter в иерархии Calendar.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;Многомерные Выражения&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
