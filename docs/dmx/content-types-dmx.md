---
title: "Типы (данных DMX) содержимого | Документы Microsoft"
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
dev_langs: DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], content types
- content types [DMX]
- DMX [Analysis Services], content types
ms.assetid: ab9dd887-df8d-4878-96b0-635881892573
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 50abed6d5ef74a341bf7d49b47597ea82b77df94
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="content-types-dmx"></a>Типы содержимого (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Для правильного функционирования алгоритмы интеллектуального анализа данных требуют дополнительных сведений помимо типа данных, например сведения о типе содержимого. Тип содержимого помогает алгоритму определить, как работать с данными в столбце.  
  
 Каждый алгоритм поддерживает определенные типы содержимого. Например, в упрощенном алгоритме Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]) не используются непрерывные столбцы. Чтобы использовать непрерывный столбец в модели упрощенного алгоритма Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]), необходимо дискретизировать данные в столбце. Некоторые алгоритмы для правильного функционирования требуют определенных типов содержимого. Например, для работы алгоритма [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series необходим ключевой столбец времени для определения времени, в течение которого собирались данные.  
  
 Полное описание содержимого типы, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает, см. [типы содержимого &#40; интеллектуального анализа данных &#41;](../analysis-services/data-mining/content-types-data-mining.md).  
  
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
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
