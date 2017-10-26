---
title: "Флаги (DMX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- REGRESSOR flag
- DMX [Analysis Services], modeling flags
- MODEL_EXISTENCE_ONLY flag
- modeling flags [DMX]
- Data Mining Extensions [Analysis Services], modeling flags
- flags [DMX]
- NOT NULL flag
ms.assetid: 498d25f7-9597-47ae-8717-61ddd1d2fd15
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ce032085f10db22608aee69b886724309e83506b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="modeling-flags-dmx"></a>Флаги моделирования (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Флаги моделирования можно использовать в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], чтобы включить в алгоритм интеллектуального анализа данных дополнительные сведения о данных, определенных в таблице вариантов. Алгоритм может использовать эти сведения для создания более точной модели интеллектуального анализа данных. Флаги моделирования можно задавать для столбцов структуры и модели интеллектуального анализа данных.  
  
 Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают следующие флаги моделирования:  
  
 **НЕ NULL**  
 Значения столбца атрибутов никогда не должны включать значение NULL. Если службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] найдут значение NULL в данном столбце атрибутов в процессе обучения модели, будет выдана ошибка. Данный флаг задается для столбца структуры интеллектуального анализа данных.  
  
 **REGRESSOR**  
 Указывает, что алгоритм может использовать заданный столбец в формуле регрессии алгоритмов регрессии. Этот флаг поддерживается алгоритмами линейной регрессии [!INCLUDE[msCoName](../includes/msconame-md.md)] и дерева принятия решений [!INCLUDE[msCoName](../includes/msconame-md.md)], и задается для столбца модели интеллектуального анализа данных.  
  
 **MODEL_EXISTENCE_ONLY**  
 Значения столбца атрибутов являются менее важными, чем присутствие атрибута. Данный флаг задается для столбца модели интеллектуального анализа данных.  
  
 Алгоритмы сторонних разработчиков могут поддерживать дополнительные флаги моделирования. Чтобы определить флаги моделирования алгоритма поддерживает, используйте **SUPPORTED_MODELING_FLAGS** набора строк схемы. Можно также создавать запросы к службам интеллектуального анализа данных на сервере для определения того, какие флаги моделирования поддерживаются для того или иного алгоритма. К примеру, следующий запрос возвращает флаги моделирования, поддерживаемые алгоритмом линейной регрессии (Майкрософт) на текущем сервере:  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 Ожидаемый результат:  
  
 NOT NULL,REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>Указание флагов моделирования в модели интеллектуального анализа данных  
 Примеры синтаксиса, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает для указания флага для столбца структуры интеллектуального анализа данных, см. [CREATE MINING STRUCTURE &#40; расширений интеллектуального анализа данных &#41;](../dmx/create-mining-structure-dmx.md).  
  
 Пример синтаксиса для указания флага моделирования для столбца модели интеллектуального анализа данных см. в разделе [ALTER MINING STRUCTURE &#40; расширений интеллектуального анализа данных &#41;](../dmx/alter-mining-structure-dmx.md).  
  
 Дополнительные сведения о работе со столбцами модели интеллектуального анализа данных см. в разделе [столбцы модели интеллектуального анализа данных](../analysis-services/data-mining/mining-model-columns.md).  
  
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
  
  

