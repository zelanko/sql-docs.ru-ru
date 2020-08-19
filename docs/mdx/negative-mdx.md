---
description: '- Отрицатель МНОГОМЕРНЫХ выражений'
title: '- Отрицатель (МНОГОМЕРНЫЕ ВЫРАЖЕНИЯ) | Документация Майкрософт'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8550e75d4f0807263678fc7badec8c8a0be52cfd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483740"
---
# <a name="--negative-mdx"></a>- (отрицательное значение) (многомерные выражения)


  Выполняет унарную операцию, возвращающую отрицательное значение числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
- Numeric_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *Numeric_Expression*  
 Допустимое многомерное выражение, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Отрицательное значение с типом данных заданного параметра.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется использование этого оператора.  
  
```  
-- This member creates a negative version of the  
-- Reseller Freight Cost.  
WITH MEMBER   
   Measures.[Resell Cost as Negative]   
   AS -Measures.[Reseller Freight Cost]  
SELECT   
   [Date].[Calendar Month of Year].Children ON COLUMNS,  
   [Product].[Product Categories].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    {[Measures].[Resell Cost as Negative]}  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по операторам многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-operator-reference-mdx.md)  
  
  
