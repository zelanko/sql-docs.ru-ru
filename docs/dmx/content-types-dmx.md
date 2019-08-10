---
title: Типы содержимого (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: da8a5e5602b877c12284d8410f6b2a1c7da6bc58
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889146"
---
# <a name="content-types-dmx"></a>Типы содержимого (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Для правильного функционирования алгоритмы интеллектуального анализа данных требуют дополнительных сведений помимо типа данных, например сведения о типе содержимого. Тип содержимого помогает алгоритму определить, как работать с данными в столбце.  
  
 Каждый алгоритм поддерживает определенные типы содержимого. Например, в упрощенном алгоритме Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]) не используются непрерывные столбцы. Чтобы использовать непрерывный столбец в модели упрощенного алгоритма Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]), необходимо дискретизировать данные в столбце. Некоторые алгоритмы для правильного функционирования требуют определенных типов содержимого. Например, для работы алгоритма [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series необходим ключевой столбец времени для определения времени, в течение которого собирались данные.  
  
 Полное описание типов [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] содержимого, поддерживаемых, см. в разделе [типы &#40;содержимого интеллектуальный анализ&#41;данных](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining).  
  
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
  
  
