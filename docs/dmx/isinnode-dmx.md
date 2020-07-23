---
title: IsInNode (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 063c436f2e0d76ca891f332f25be385c2f16fdfa
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969677"
---
# <a name="isinnode-dmx"></a>IsInNode (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Указывает, содержит ли заданный узел текущий вариант.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsInNode(<NodeID>)  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Тип Boolean.  
  
## <a name="remarks"></a>Примечания  
 **IsInNode** используется только в [&#62; модели SELECT &#60;. СЛУЧАИ &#40;&#41;расширений интеллектуального анализа данных](../dmx/select-from-model-cases-dmx.md) и [выбора &#60;&#62; модели. SAMPLE_CASES &#40;запросы DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md) .  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все варианты, использованные при создании модели и связанные с узлом, заданным функцией IsInNode.  
  
```  
Select * from [TM Decision Tree].Cases  
WHERE IsInNode('0')  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
