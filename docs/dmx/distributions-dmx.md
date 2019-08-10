---
title: Распределения (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: fda2eb169985eb670614f611764fbf149c71a42d
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892791"
---
# <a name="distributions-dmx"></a>Распределения (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  В [!INCLUDE[msCoName](../includes/msconame-md.md)] службахможно[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]определить содержимое столбцов в структуре интеллектуального анализа данных, чтобы повлиять на то, как алгоритмы обрабатывают данные в этих столбцах при создании моделей интеллектуального анализа данных. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] В некоторых алгоритмах лучше задавать распределение для всех столбцов, содержащих непрерывные данные, до начала обработки модели в случае, если указанные столбцы содержат общие распределения значений. Если распределения не заданы, создаваемые модели интеллектуального анализа данных могут работать менее точно, чем модели с заданными распределениями, так как на вход алгоритмов будет подаваться меньшее количество данных для анализа.  
  
 Алгоритмы интеллектуального анализа данных [!INCLUDE[msCoName](../includes/msconame-md.md)] могут работать с данными следующих типов:  
  
 **ОБЫЧНО**  
 На основе значений столбца, содержащего непрерывные данные, может быть построена гистограмма с нормальным Гауссовским распределением.  
  
 **Логарифмическое нормальное**  
 На основе значений столбца, содержащего непрерывные данные, может быть построена гистограмма с нормально распределенной функцией логарифма значений.  
  
 **СЧЕТ**  
 На основе значений столбца непрерывных данных может быть сформирована плоская кривая, на которой все значения являются равновероятными.  
  
 Дополнительные сведения о [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритмах интеллектуального анализа данных см. в разделе Алгоритмы [ &#40;интеллектуального анализа данных Analysis Services — интеллектуальный&#41;анализ данных](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining). Алгоритмы интеллектуального анализа данных третьих поставщиков могут также иметь возможность работы с другими типами распределений. Чтобы определить, какие типы распределения поддерживаются алгоритмом, используйте набор строк схемы **SUPPORTED_DISTRIBUTION_FLAGS** .  
  
 Дополнительные сведения о типах распространения см. в разделе [распределение столбцов &#40;по интеллектуальному анализу&#41;данных](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining).  
  
## <a name="see-also"></a>См. также  
 [Типы содержимого (интеллектуальный анализ данных)](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-reference.md)   
 [Элементы&#41; синтаксиса &#40;расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Справочник по &#40;функциям&#41; DMX расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Справочник по &#40;операторам&#41; DMX расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Справочник по DMX &#40;&#41; -инструкциям расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-statements.md)   
 [&#41; Синтаксические обозначения расширений &#40;расширений интеллектуального анализа данных](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [DMX-функции &#40;общих прогнозирующих функций&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Структура и методы использования прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции SELECT в расширении интеллектуального анализа данных](../dmx/understanding-the-dmx-select-statement.md)  
  
  
