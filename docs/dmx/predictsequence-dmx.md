---
title: PredictSequence (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PredictSequence
dev_langs:
- DMX
helpviewer_keywords:
- PredictSequence function
ms.assetid: c2992dfc-b99d-4430-8dcd-21ad3ffd4590
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: aaeb95f70c9afc6872bd56df494a8eba88f98f91
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
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
  
## <a name="remarks"></a>Remarks  
 Если  *n*  параметр указан, он возвращает следующие значения:  
  
-   Если  *n*  больше нуля, наиболее вероятные значения в следующем  *n*  действия.  
  
-   Если оба *n-start* и *n-end* заданы, выдается последовательность значений элементов из *n-start* для *n-end*.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает последовательность из пяти продуктов, которые, вероятнее всего, приобретет клиент из базы данных [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], с учетом модели интеллектуального анализа данных «Кластеризация последовательностей».  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
