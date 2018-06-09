---
title: '&gt;= (Больше или равно) (расширения интеллектуального анализа данных) | Документы Microsoft'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bea462fcd0a2bd2258ae62be988eda2dff442a1
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841407"
---
# <a name="gt-greater-than-or-equal-to-dmx"></a>&gt;= (Больше или равно) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет операцию сравнения с целью определения, является ли одно выражение больше второго выражения расширений интеллектуального анализа данных или равным ему.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DMX_Expression >= DMX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *DMX_Expression*  
 Допустимое выражение расширений интеллектуального анализа данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение равно TRUE в случае, если оба аргумента не равны NULL, и значение первого аргумента больше значения второго аргумента или равно ему. Логическое значение равно FALSE, если оба аргумента не равны NULL, и первый аргумент имеет значение меньшее, чем второй. Логическое значение равно NULL, если один или оба аргумента имеют значение NULL.  
  
## <a name="see-also"></a>См. также  
 [Операторы сравнения &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-comparison.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-dmx.md)  
  
  
