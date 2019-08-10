---
title: Использование (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b961282ba6bc25caa260a3e156f843a413a5ef1a
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893114"
---
# <a name="usage-dmx"></a>Использование (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  При использовании расширений интеллектуального анализа данных (DMX) для определения новой модели интеллектуального анализа [!INCLUDE[msCoName](../includes/msconame-md.md)] данных в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]необходимо указать, как алгоритм интеллектуального анализа данных, создающий модель, будет использовать каждый столбец. Для столбца можно указать один из следующих типов:  
  
-   **Key**  
  
-   **Последовательность ключей**  
  
-   **Ключевое время**  
  
-   **Predict**  
  
-   **PredictOnly**  
  
 Столбцы, не указанные в расширениях интеллектуального анализа данных, считаются входными столбцами.  
  
 Для правильной обработки модели алгоритму должен быть известен ключевой столбец, уникальным образом идентифицирующий каждую строку; целевой столбец для создания прогнозов в случае формирования прогнозируемой модели, а также столбцы, которые следует использовать в качестве входных при создании связей для предсказания целевого столбца.  
  
 Столбцы, указанные в качестве типа **прогноза** , используются как входные, так и выходные столбцы. Столбцы, указанные как **PredictOnly** , используются только в качестве выходных столбцов. Столбцы типа Predict могут обрабатываться конкретными алгоритмами по-разному.  
  
 Дополнительные сведения о типах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] использования столбцов, поддерживаемых, см. в разделе [столбцы модели интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-reference.md)   
 [Элементы&#41; синтаксиса &#40;расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Справочник по &#40;функциям&#41; DMX расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Справочник по &#40;операторам&#41; DMX расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Справочник по DMX &#40;&#41; -инструкциям расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-statements.md)   
 [&#41; Синтаксические обозначения расширений &#40;расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [DMX-функции &#40;общих прогнозирующих функций&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и методы использования прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
