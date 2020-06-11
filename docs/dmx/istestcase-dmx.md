---
title: IsTestCase (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 33c84ada33abee06a78fe0a9f8cc3f37242458ac
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670231"
---
# <a name="istestcase-dmx"></a>IsTestCase (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает, используется ли вариант в качестве проверочного для конкретной модели или структуры интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>Тип результата  
 Возвращает **значение true** , если вариант является частью набора проверочных данных. в противном случае — **false**.  
  
## <a name="remarks"></a>Комментарии  
 Если создание структуры интеллектуального анализа данных и соответствующей модели интеллектуального анализа производится при помощи мастера интеллектуального анализа данных, то по умолчанию 30% вариантов резервируются для использования в качестве проверочного набора данных. Оставшиеся варианты используются для обучения модели интеллектуального анализа данных. Один и тот же проверочный набор данных можно использовать со всеми моделями, созданными на основе этой структуры. Однако если для создания модели интеллектуального анализа данных использовались расширения интеллектуального анализа данных, то по умолчанию все данные используются для обучения модели и проверочный набор не создается. Чтобы разрешить создание проверочного набора данных, нужно задать значение параметров предложения WITH HOLDOUT.  
  
 Узнать, создавался ли для конкретной структуры интеллектуального анализа данных проверочный набор, можно, посмотрев значение свойств <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> и <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  Детализация должна быть включена в модели, если вы хотите использовать функции IsTrainingCase или IsTestCase, чтобы получить сведения о вариантах в определенной модели. Дополнительные сведения см. в разделе [Включение детализации для модели интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/enable-drillthrough-for-a-mining-model).  
  
 Чтобы вернуть варианты, которые являются частью набора обучающих данных, используйте функцию [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `Targeted Mailing` Структура интеллектуального анализа данных, созданная в [учебнике по основам интеллектуального анализа](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Запрос возвращает все варианты структуры, используемые для проверки.  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 Дополнительные сведения о запросах вариантов, используемых в интеллектуальном анализе данных, см. в разделе [Выбор из &#60;модели&#62;. В случаях &#40;&#41;расширений интеллектуального анализа данных](../dmx/select-from-model-cases-dmx.md) и [выберите &#60;структура&#62;. ВАРИАНТОВ](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>См. также:  
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Запросы интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/data-mining-queries)   
 [Обучающие и проверочные наборы данных](https://docs.microsoft.com/analysis-services/data-mining/training-and-testing-data-sets)  
  
  
