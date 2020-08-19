---
description: Деление (многомерные выражения)
title: Деление (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0999df34ff817131e890afade89fc5daad85796b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484017"
---
# <a name="divide-mdx"></a>Деление (многомерные выражения)


  Выполняет деление и возвращает альтернативный результат или выражение BLANK() при делении на 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Числитель*  
 Делимое число.  
  
 *подробно*  
 Делитель.  
  
 *alternateresult*  
 (Необязательно) Значение, возвращаемое когда деление на ноль приводит к ошибке. Если не указано, значение по умолчанию является выражением BLANK().  
  
## <a name="remarks"></a>Remarks  
 Альтернативный результат при делении на 0 должен быть константой.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
