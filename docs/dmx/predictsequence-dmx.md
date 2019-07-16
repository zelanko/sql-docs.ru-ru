---
title: PredictSequence (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c6828b77af36b5dbbc50fbca0210961a7f2ed20c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041922"
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
  
-   Если *n* не равно нулю, скорее всего, значений последовательности, в течение *n* действия.  
  
-   Если оба *n-start* и *n-end* указаны, выдается последовательность значений элементов из *n-start* для *n-end*.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает последовательность из пяти продуктов, которые, вероятнее всего, приобретет клиент из базы данных [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], с учетом модели интеллектуального анализа данных «Кластеризация последовательностей».  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
