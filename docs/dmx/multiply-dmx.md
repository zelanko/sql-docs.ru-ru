---
description: '* Перемножаемых DMX'
title: '* Перемножаемых (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3c7ef5a8893d29e2d20d31517c85abacfc4a3a9b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426286"
---
# <a name="-multiply-dmx"></a>* (Умножение) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Выполняет арифметическую операцию, которая умножает одно число на другое.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *Numeric_Expression*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение с типом данных параметра, имеющего более высокий приоритет.  
  
## <a name="remarks"></a>Remarks  
 Оба выражения должны иметь одинаковый тип данных, или одно из выражений должно допускать неявное преобразование к типу данных другого выражения. Если результатом вычисления одного выражения является значение NULL, то и оператор возвращает значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Арифметические операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-arithmetic.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-dmx.md)  
  
  
