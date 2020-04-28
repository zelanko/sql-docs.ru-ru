---
title: Descending (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7f6f3532165b8e958eb03cdf4954543159309a08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67937715"
---
# <a name="isdescendant-dmx"></a>IsDescendant (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает, является ли текущий узел потомком заданного узла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Тип Boolean.  
  
## <a name="remarks"></a>Remarks  
 **Descending** используется только в [&#62; модели SELECT &#60;. CONTENT &#40;&#41;расширений интеллектуального анализа данных](../dmx/select-from-model-content-dmx.md) и [выберите из &#60;&#62; модели. DIMENSION_CONTENT &#40;запросы DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md) .  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере выдаются все объекты, которые являются потомками узла, заданного в функции IsDescendant.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
