---
description: '&lt;= (Меньше или равно) (расширения интеллектуального анализа данных)'
title: '&lt;= (Меньше или равно) (расширения интеллектуального анализа данных) | Документация Майкрософт'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 91b043711d9f81d54d98dc455c806eac60e9a33a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491492"
---
# <a name="lt-less-than-or-equal-to-dmx"></a>&lt;= (Меньше или равно) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Выполняет операцию сравнения, определяющую, является ли одно значение меньшим или равным другому значению расширений интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DMX_Expression <= DMX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *DMX_Expression*  
 Допустимое выражение расширений интеллектуального анализа данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение логического типа равное TRUE в случае, если оба аргумента не равны NULL и значение первого аргумента больше значения второго аргумента или равно ему. Имеет значение FALSE, если оба аргумента не равны NULL и первый аргумент имеет значение меньшее, чем второй. Логическое значение равно NULL, если один или оба аргумента имеют значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Операторы сравнения &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-comparison.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-dmx.md)  
  
  
