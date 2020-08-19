---
description: PredictSequence (расширения интеллектуального анализа данных)
title: PredictSequence (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 31f99205f3e23db23c5c2a38750f75212763e8de
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426106"
---
# <a name="predictsequence-dmx"></a>PredictSequence (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Дает предварительную оценку будущих значений заданной последовательности данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Объект \<table expression>.  
  
## <a name="remarks"></a>Remarks  
 Если указан параметр *n* , он возвращает следующие значения:  
  
-   Если *n* больше нуля, наиболее вероятные значения последовательностей приведены в следующих *n* шагах.  
  
-   Если указаны как *n-start* , так и *n-End* , то значения последовательности из *n-start* в *n-End*.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает последовательность из пяти продуктов, которые, вероятнее всего, приобретет клиент из базы данных [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], с учетом модели интеллектуального анализа данных «Кластеризация последовательностей».  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/functions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)  
  
  
