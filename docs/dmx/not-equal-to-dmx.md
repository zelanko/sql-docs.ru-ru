---
title: '&lt;&gt;(Не равно) (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1181e781da0e752cb68f0fbf1d8c84d257407a3e
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86968566"
---
# <a name="ltgt-not-equal-to-dmx"></a>&lt;&gt;(Не равно) DMX
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Выполняет операцию сравнения, определяющую, является ли значение одного выражения неравным значению другого выражения расширений интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DMX_Expression <> DMX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *DMX_Expression*  
 Допустимое выражение расширений интеллектуального анализа данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение равно TRUE, если оба аргумента не равны NULL, и значение первого аргумента не равно значению второго. Логическое значение равно FALSE, если оба аргумента не равны NULL и значение первого аргумента равно значению второго. Логическое значение равно NULL, если один или оба аргумента имеют значение NULL.  
  
## <a name="see-also"></a>См. также  
 [Операторы сравнения &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-comparison.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)  
  
  
