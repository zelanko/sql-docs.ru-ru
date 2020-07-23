---
title: Использование (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cdbefcfeb6d638998ec2e0a01b8da5ca40f2aeaf
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971582"
---
# <a name="usage-dmx"></a>Использование (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  При использовании расширений интеллектуального анализа данных (DMX) для определения новой модели интеллектуального анализа данных в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] необходимо указать, как алгоритм интеллектуального анализа данных, создающий модель, будет использовать каждый столбец. Для столбца можно указать один из следующих типов:  
  
-   **Key**  
  
-   **Ключевая последовательность**  
  
-   **Ключевой столбец времени**  
  
-   **Сформировать**  
  
-   **PredictOnly**  
  
 Столбцы, не указанные в расширениях интеллектуального анализа данных, считаются входными столбцами.  
  
 Для правильной обработки модели алгоритму должен быть известен ключевой столбец, уникальным образом идентифицирующий каждую строку; целевой столбец для создания прогнозов в случае формирования прогнозируемой модели, а также столбцы, которые следует использовать в качестве входных при создании связей для предсказания целевого столбца.  
  
 Столбцы, указанные в качестве типа **прогноза** , используются как входные, так и выходные столбцы. Столбцы, указанные как **PredictOnly** , используются только в качестве выходных столбцов. Столбцы типа Predict могут обрабатываться конкретными алгоритмами по-разному.  
  
 Дополнительные сведения о типах использования столбцов, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживаемых, см. в разделе [столбцы модели интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
## <a name="see-also"></a>См. также:  
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Расширения интеллектуального анализа данных &#40;Справочник по DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические&#41; DMX-элементы](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические обозначения&#41; DMX](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использование прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции расширения интеллектуального анализа данных SELECT](../dmx/understanding-the-dmx-select-statement.md)  
  
  
