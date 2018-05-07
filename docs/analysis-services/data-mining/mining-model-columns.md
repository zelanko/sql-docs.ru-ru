---
title: Столбцы модели интеллектуального анализа данных | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6d5e0b3f1952dcad9e77c240a65a56de38354209
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mining-model-columns"></a>Столбцы модели интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Модель интеллектуального анализа данных применяет алгоритм интеллектуального анализа к данным, представленным структурой интеллектуального анализа данных. Модель интеллектуального анализа данных, как и структура интеллектуального анализа, содержит столбцы. Модель интеллектуального анализа содержится в структуре интеллектуального анализа и наследует все значения свойств, определенных этой структурой. Модель может использовать все столбцы, содержащиеся в структуре интеллектуального анализа данных, или подмножества этих столбцов.  
  
 В столбце модели интеллектуального анализа данных можно определить два дополнительных элемента данных: использование и флаги моделирования.  
  
-   **Использование** — это свойство, определяющее, как модель использует столбец. Столбцы могут использоваться как входные, ключевые или прогнозируемые.  
  
-   **Флаги моделирования** обеспечивают алгоритм дополнительными сведениями о данных, определяемых в таблице вариантов, что помогает алгоритму создавать более точную модель. Флаги моделирования можно определять программным способом с помощью языка расширений интеллектуального анализа данных или в **конструкторе интеллектуального анализа данных** среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 В следующем списке описываются флаги моделирования, которые можно определить в столбце модели интеллектуального анализа данных.  
  
 **MODEL_EXISTENCE_ONLY**  
 Указывает на то, что наличие атрибута важнее значений столбца атрибутов. Например, рассмотрим таблицу вариантов, в которой содержится список элементов заказа, связанных с определенным заказчиком. В данные таблицы включается тип изделия, идентификатор и стоимость каждого элемента. Для целей моделирования факт приобретения заказчиком определенного элемента заказа может оказаться важнее стоимости самого элемента заказа. В таком случае столбец стоимости должен быть отмечен как **MODEL_EXISTENCE_ONLY**.  
  
 **REGRESSOR**  
 Указывает, что алгоритм может использовать заданный столбец в формуле регрессии алгоритмов регрессии. Этот флаг поддерживается алгоритмом дерева принятия решений [!INCLUDE[msCoName](../../includes/msconame-md.md)] и алгоритмом временных рядов [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 Дополнительные сведения об установке свойства использования и программном определении флагов моделирования с помощью расширений интеллектуального анализа данных см. в разделе [CREATE MINING MODEL (расширения интеллектуального анализа данных)](../../dmx/create-mining-model-dmx.md). Дополнительные сведения об установке свойства использования и определении флагов моделирования в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] см. в разделе [Перемещение объектов интеллектуального анализа данных](../../analysis-services/data-mining/moving-data-mining-objects.md).  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных & #40; Службы Analysis Services — Интеллектуальный анализ данных & #41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Структуры интеллектуального анализа данных и &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Изменение свойств модели интеллектуального анализа данных](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)   
 [Исключить столбец из модели интеллектуального анализа данных](../../analysis-services/data-mining/exclude-a-column-from-a-mining-model.md)   
 [Столбцы структуры интеллектуального анализа данных](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
