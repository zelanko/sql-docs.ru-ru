---
title: PredictAdjustedProbability (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c2ae90886d6469802543f62bf5636ccaafeb32fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008088"
---
# <a name="predictadjustedprobability-dmx"></a>PredictAdjustedProbability (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает настроенную вероятность указанного состояния.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictAdjustedProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Применяется к  
 Скалярный столбец.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Скалярное значение.  
  
## <a name="remarks"></a>Remarks  
 Если прогнозируемое состояние не указано, используется состояние с наибольшей прогнозируемой вероятностью, за исключением сегмента отсутствующих состояний. Чтобы включить контейнер отсутствующих состояний, задайте для \<прогнозируемого состояния> значение **INCLUDE_NULL**.  
  
 Чтобы получить скорректированную вероятность для отсутствующих состояний, задайте для \<прогнозируемого состояния> значение null.  
  
 Функция **PredictAdjustedProbability** является [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] расширением [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB для спецификации интеллектуального анализа данных.  
  
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
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)  
  
  
