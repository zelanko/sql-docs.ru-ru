---
description: Ordinal (многомерные выражения)
title: Ordinal (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 74811da22f8c73536749acad41dfbe859b00eeea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471736"
---
# <a name="ordinal-mdx"></a>Ordinal (многомерные выражения)


  Возвращает начинающееся с нуля порядковое значение, связанное с уровнем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
## <a name="remarks"></a>Remarks  
 Функция **Ordinal** используется в сочетании с функциями **IIf** и **CurrentMember** для условного вывода различных значений на разных уровнях иерархии на основе порядкового номера каждой отдельной ячейки в результатах запроса. Например, можно использовать функцию **Ordinal** для выполнения вычислений на определенных уровнях и отобразить значение по умолчанию "н/д" на других уровнях.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается порядковый номер уровня Calendar Quarter в иерархии Calendar.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
