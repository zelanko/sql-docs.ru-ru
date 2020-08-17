---
description: '&lt; (Меньше) МНОГОМЕРНЫХ выражений'
title: '&lt; (Меньше) (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 935b75d17db379d761641d994a06373c8503fffc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387300"
---
# <a name="lt-less-than-mdx"></a>&lt; (Меньше) МНОГОМЕРНЫХ выражений


  Выполняет операцию сравнения, определяющую, является ли значение одного многомерного выражения меньшим, чем значение другого многомерного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MDX_Expression < MDX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение, определяемое исходя из следующих условий.  
  
-   **значение true** , если оба параметра не равны NULL, а первый параметр имеет значение ниже значения второго параметра.  
  
-   **значение false** , если оба параметра имеют значения, отличные от NULL, и первый параметр имеет значение, которое либо равно, либо больше значения второго параметра.  
  
-   Равно NULL, если любой из параметров или оба параметра возвращают значение NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for clothing sales where the GPM is less than 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] < .3,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT NON EMPTY  
    [Sales Territory].[Sales Territory Country].Members ON 0,  
    [Product].[Category].[Clothing] ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-operator-reference-mdx.md)  
  
  
