---
title: IsTestCase (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b7e80f8a9dfb82f13350b94b310690a081fae1de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62503726"
---
# <a name="istestcase-dmx"></a>IsTestCase (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает, используется ли вариант в качестве проверочного для конкретной модели или структуры интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>Тип результата  
 Возвращает **true** Если вариантом является частью проверочного набора данных; в противном случае **false**.  
  
## <a name="remarks"></a>Примечания  
 Если создание структуры интеллектуального анализа данных и соответствующей модели интеллектуального анализа производится при помощи мастера интеллектуального анализа данных, то по умолчанию 30% вариантов резервируются для использования в качестве проверочного набора данных. Оставшиеся варианты используются для обучения модели интеллектуального анализа данных. Один и тот же проверочный набор данных можно использовать со всеми моделями, созданными на основе этой структуры. Однако если для создания модели интеллектуального анализа данных использовались расширения интеллектуального анализа данных, то по умолчанию все данные используются для обучения модели и проверочный набор не создается. Чтобы разрешить создание проверочного набора данных, нужно задать значение параметров предложения WITH HOLDOUT.  
  
 Узнать, создавался ли для конкретной структуры интеллектуального анализа данных проверочный набор, можно, посмотрев значение свойств <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> и <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  Должна быть включена детализация на модели, если вы хотите использовать функции IsTrainingCase или IsTestCase для получения подробной информации о вариантах в конкретной модели. Дополнительные сведения см. в разделе [Включение детализации для модели интеллектуального анализа данных](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Для получения вариантов, которые являются частью набора данных для обучения, используйте функцию [IsTrainingCase &#40;расширений интеллектуального анализа данных&#41;](../dmx/istrainingcase-dmx.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `Targeted Mailing` структуры интеллектуального анализа данных, которая создается в [Basic Data Mining Tutorial](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Запрос возвращает все варианты структуры, используемые для проверки.  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 Дополнительные сведения о запросах к вариантам, используемым для интеллектуального анализа данных см. в разделе [SELECT FROM &#60;модели&#62;. СЛУЧАЯХ &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-from-model-cases-dmx.md) и [SELECT FROM &#60;структуры&#62;. СЛУЧАИ](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Запросы интеллектуального анализа данных](../analysis-services/data-mining/data-mining-queries.md)   
 [Обучающие и проверочные наборы данных](../analysis-services/data-mining/training-and-testing-data-sets.md)  
  
  
