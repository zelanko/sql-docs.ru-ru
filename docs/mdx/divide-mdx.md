---
title: Деление (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86b4d8c97996733396e3062e134b2e31d2819ec0
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739803"
---
# <a name="divide-mdx"></a>Деление (многомерные выражения)


  Выполняет деление и возвращает альтернативный результат или выражение BLANK() при делении на 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Аргументы  
 *числитель*  
 Делимое число.  
  
 *знаменатель*  
 Делитель.  
  
 *alternateresult*  
 (Необязательно) Значение, возвращаемое когда деление на ноль приводит к ошибке. Если не указано, значение по умолчанию является выражением BLANK().  
  
## <a name="remarks"></a>Примечания  
 Альтернативный результат при делении на 0 должен быть константой.  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
