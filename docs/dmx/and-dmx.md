---
description: AND (расширения интеллектуального анализа данных)
title: И (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 17dabee823323c63a2d36a21cd79b81e9a323803
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431206"
---
# <a name="and-dmx"></a>AND (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Выполняет логическое умножение двух числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
 *Expression2*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение принимает значение TRUE, если оба аргумента имеют значение TRUE, в противном случае возвращает значение FALSE.  
  
## <a name="remarks"></a>Remarks  
 Оба аргумента приводятся к значениям логического типа (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое умножение. В приведенной ниже таблице показаны результаты, соответствующие различным сочетаниям значений аргументов:  
  
|Если Expression1 равно|Если Expression2 равно|Возвращается значение|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|FALSE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>См. также:  
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Логические операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-logical.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-dmx.md)  
  
  
