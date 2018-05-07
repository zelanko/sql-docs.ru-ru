---
title: IsTrainingCase (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsTrainingCase
dev_langs:
- DMX
helpviewer_keywords:
- IsTrainingCase function
ms.assetid: 63eab315-e743-470d-9c4c-edfc3f4058a3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 37a61a78e2706d0125e341819b8e829bd9602564
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает, используется ли вариант в качестве обучающего для конкретной модели или структуры интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>Тип результата  
 Возвращает **true** Если регистр является частью набора данных для обучения; в противном случае **false**.  
  
## <a name="remarks"></a>Замечания  
 Если создание структуры интеллектуального анализа данных и соответствующей модели интеллектуального анализа производится при помощи мастера интеллектуального анализа данных, то по умолчанию 30% вариантов резервируются для использования в качестве проверочного набора данных. Оставшиеся варианты в выбранном источнике данных будут использоваться для обучения модели. Однако если для создания модели интеллектуального анализа данных использовались расширения интеллектуального анализа данных, то по умолчанию все данные используются для обучения модели и проверочный набор не создается. Чтобы разрешить создание проверочного набора данных, нужно задать значение параметров предложения WITH HOLDOUT.  
  
 Узнать, были ли данные конкретной структуры интеллектуального анализа данных разделены на обучающие и проверочные, можно, посмотрев значение свойств <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> и <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  Необходимо включить детализацию на модели, если вы хотите использовать функции IsTrainingCase или IsTestCase для получения сведений о вариантах в модели. Дополнительные сведения см. в разделе [Включение детализации для модели интеллектуального анализа данных](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Чтобы вернуть варианты, которые являются частью набора проверочных данных, используйте функцию [IsTestCase &#40;расширений интеллектуального анализа данных&#41;](../dmx/istestcase-dmx.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется кластеризованная модель интеллектуального анализа из сценария прямой почтовой рассылки в [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Этот запрос возвращает только варианты, которые использовались для обучения модели интеллектуального анализа данных. Помимо этого обучающие варианты будут ограничены условием, что покупатель моложе 40 лет.  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 Другие примеры запросов к вариантам, используемым для интеллектуального анализа данных см. в разделе [SELECT FROM &#60;модель&#62;. СЛУЧАИ &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-from-model-cases-dmx.md) и [SELECT FROM &#60;структуры&#62;. СЛУЧАИ](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>См. также  
 [Обучающие и проверочные наборы данных](../analysis-services/data-mining/training-and-testing-data-sets.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Запросы интеллектуального анализа данных](../analysis-services/data-mining/data-mining-queries.md)  
  
  
