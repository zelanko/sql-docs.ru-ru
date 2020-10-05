---
description: Типы содержимого (расширения интеллектуального анализа данных)
title: Типы содержимого (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b1a400e5247cc812cb72ba3422cb361888342155
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726335"
---
# <a name="content-types-dmx"></a>Типы содержимого (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Для правильного функционирования алгоритмы интеллектуального анализа данных требуют дополнительных сведений помимо типа данных, например сведения о типе содержимого. Тип содержимого помогает алгоритму определить, как работать с данными в столбце.  
  
 Каждый алгоритм поддерживает определенные типы содержимого. Например, в упрощенном алгоритме Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]) не используются непрерывные столбцы. Чтобы использовать непрерывный столбец в модели упрощенного алгоритма Байеса ([!INCLUDE[msCoName](../includes/msconame-md.md)]), необходимо дискретизировать данные в столбце. Некоторые алгоритмы для правильного функционирования требуют определенных типов содержимого. Например, для работы алгоритма [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series необходим ключевой столбец времени для определения времени, в течение которого собирались данные.  
  
 Полное описание типов содержимого, которые [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает, см. в разделе [типы содержимого &#40;&#41;интеллектуального анализа данных ](/analysis-services/data-mining/content-types-data-mining).  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Расширения интеллектуального анализа данных &#40;Справочник по DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические&#41; DMX-элементы](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические обозначения&#41; DMX](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использование прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции расширения интеллектуального анализа данных SELECT](../dmx/understanding-the-dmx-select-statement.md)  
  
