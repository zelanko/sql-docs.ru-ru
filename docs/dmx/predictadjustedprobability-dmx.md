---
title: "PredictAdjustedProbability (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PredictAdjustedProbability
dev_langs: DMX
helpviewer_keywords: PredictAdjustedProbability function
ms.assetid: 9a1e2ec5-5a37-4df6-a78e-26a495cc9301
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5ce9eb11c74da251c7d123c83e93d459c2718fed
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="predictadjustedprobability-dmx"></a>PredictAdjustedProbability (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает настроенную вероятность указанного состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictAdjustedProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Объект применения  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Remarks  
 Если прогнозируемое состояние не указано, используется состояние с наибольшей прогнозируемой вероятностью, за исключением сегмента отсутствующих состояний. Для включения сегмента отсутствующих состояний, установите \<прогнозируемое состояние > для **INCLUDE_NULL**.  
  
 Чтобы вернуть настроенную вероятность для пропущенных состояний, установите \<прогнозируемое состояние > в NULL.  
  
 **PredictAdjustedProbability** функция [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] расширение [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB для интеллектуального анализа данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется естественное прогнозируемое соединение для определения, станет ли человек покупать велосипед, основываясь на модели интеллектуального анализа данных TM-дерева принятия решений, а также определяется настроенная вероятность для прогноза.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictAdjustedProbability([Bike Buyer]) AS [Adjusted Probability]  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
