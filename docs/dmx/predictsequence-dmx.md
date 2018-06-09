---
title: PredictSequence (расширения интеллектуального анализа данных) | Документы Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 813641b7fa72405a0ba5a026e255f03feb94bd05
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841557"
---
# <a name="predictsequence-dmx"></a>PredictSequence (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Дает предварительную оценку будущих значений заданной последовательности данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Объект \<таблицы выражения >.  
  
## <a name="remarks"></a>Примечания  
 Если *n* параметр указан, он возвращает следующие значения:  
  
-   Если *n* больше нуля, наиболее вероятные значения в следующем *n* действия.  
  
-   Если оба *n-start* и *n-end* заданы, выдается последовательность значений элементов из *n-start* для *n-end*.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает последовательность из пяти продуктов, которые, вероятнее всего, приобретет клиент из базы данных [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], с учетом модели интеллектуального анализа данных «Кластеризация последовательностей».  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
