---
title: '&gt; (Больше) (DMX) | Документы Microsoft'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 17c48c5321a0eef25a7fdf3ad0fba5aa643398d4
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842867"
---
# <a name="gt-greater-than-dmx"></a>&gt; (Больше) (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="see-also"></a>См. также  
 [Операторы сравнения &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-comparison.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-dmx.md)  
  
  
