---
title: Деление (многомерные Выражения) | Документация Майкрософт
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471315"
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
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
