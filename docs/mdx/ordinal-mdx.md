---
title: Порядковый номер (многомерные Выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b22cc6d5a609f8e1f585ccc1229e0e1cd67e1796
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055638"
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
  
## <a name="remarks"></a>Примечания  
 **Порядковый номер** функция часто используется в сочетании с **IIF** и **CurrentMember** функции для отображения разных значений в другой уровни иерархии, в зависимости от порядкового номера каждой из ячеек в результатах запроса. Например, можно использовать **порядковый номер** функция для вычисления на определенных уровнях и отображение значение по умолчанию «N/a» на других уровнях.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается порядковый номер уровня Calendar Quarter в иерархии Calendar.  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
