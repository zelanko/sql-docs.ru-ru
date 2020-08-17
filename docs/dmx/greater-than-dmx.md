---
description: '&gt; (Больше) DMX'
title: '&gt; (Больше) (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6f9c1ff74627f4fac5d9fb158b387b29e2ca1915
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88352900"
---
# <a name="gt-greater-than-dmx"></a>&gt; (Больше) DMX
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Выполняет операцию сравнения, определяющую, является ли одно значение меньшим или равным другому значению расширений интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DMX_Expression > DMX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *DMX_Expression*  
 Допустимое выражение расширений интеллектуального анализа данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логические значение, равное TRUE в случае, если оба аргумента не равны NULL, и значение первого аргумента больше значения второго аргумента. Логическое значение равно FALSE в случае, если оба аргумента не равны NULL, и значение первого аргумента равняется или меньше значения второго аргумента. Логическое значение равно NULL, если один или оба аргумента имеют значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Операторы сравнения &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-comparison.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-dmx.md)  
  
  
