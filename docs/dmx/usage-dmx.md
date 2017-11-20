---
title: "Использование (данных DMX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- column usage [DMX]
- Data Mining Extensions [Analysis Services], column usage types
- DMX [Analysis Services], column usage types
ms.assetid: 6d7ae72a-f5b5-4744-a3a2-46ccd6432c1a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2acfde9b8d7c9d13fc626b006116e9b3760fd432
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="usage-dmx"></a>Использование (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  При использовании расширений интеллектуального анализа данных (DMX) для определения новой модели интеллектуального анализа данных в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], необходимо указать способ использования каждого столбца алгоритм интеллектуального анализа данных, применяемым для построения модели. Для столбца можно указать один из следующих типов:  
  
-   **Key**  
  
-   **Сочетание клавиш**  
  
-   **Ключевой столбец времени**  
  
-   **Прогноз**  
  
-   **PredictOnly**  
  
 Столбцы, не указанные в расширениях интеллектуального анализа данных, считаются входными столбцами.  
  
 Для правильной обработки модели алгоритму должен быть известен ключевой столбец, уникальным образом идентифицирующий каждую строку; целевой столбец для создания прогнозов в случае формирования прогнозируемой модели, а также столбцы, которые следует использовать в качестве входных при создании связей для предсказания целевого столбца.  
  
 Столбцы, которые задаются в виде **Predict** тип, используются в качестве входных и выходных столбцов. Столбцы, которые задаются в виде **PredictOnly** используются только в качестве выходных столбцов. Столбцы типа Predict могут обрабатываться конкретными алгоритмами по-разному.  
  
 Дополнительные сведения о столбце, типах использования [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает, см. [Mining Model Columns](../analysis-services/data-mining/mining-model-columns.md).  
  
## <a name="see-also"></a>См. также:  
 [Алгоритмы интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Основные сведения об инструкции расширений интеллектуального анализа данных Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  

