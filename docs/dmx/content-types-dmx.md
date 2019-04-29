---
title: Типы (данных DMX) содержимого | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 002dfef00f428f7fe87f3de06eb174e0566282c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853497"
---
# <a name="content-types-dmx"></a>Типы содержимого (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Для правильного функционирования алгоритмы интеллектуального анализа данных требуют дополнительных сведений помимо типа данных, например сведения о типе содержимого. Тип содержимого помогает алгоритму определить, как работать с данными в столбце.  
  
 Каждый алгоритм поддерживает определенные типы содержимого. Например, в упрощенном алгоритме Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]) не используются непрерывные столбцы. Чтобы использовать непрерывный столбец в модели упрощенного алгоритма Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]), необходимо дискретизировать данные в столбце. Некоторые алгоритмы для правильного функционирования требуют определенных типов содержимого. Например, для работы алгоритма [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series необходим ключевой столбец времени для определения времени, в течение которого собирались данные.  
  
 Полное описание содержимого типы, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает, см. в разделе [типы содержимого &#40;интеллектуального анализа данных&#41;](../analysis-services/data-mining/content-types-data-mining.md).  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; справочнике по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и методы использования прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
