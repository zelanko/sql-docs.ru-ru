---
description: Флаги моделирования (расширения интеллектуального анализа данных)
title: Флаги моделирования (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 52b28158c59e12886f8058883c65654b23ece9e0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466550"
---
# <a name="modeling-flags-dmx"></a>Флаги моделирования (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Флаги моделирования можно использовать в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], чтобы включить в алгоритм интеллектуального анализа данных дополнительные сведения о данных, определенных в таблице вариантов. Алгоритм может использовать эти сведения для создания более точной модели интеллектуального анализа данных. Флаги моделирования можно задавать для столбцов структуры и модели интеллектуального анализа данных.  
  
 Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживают следующие флаги моделирования:  
  
 **НЕ NULL**  
 Значения столбца атрибутов никогда не должны включать значение NULL. Если службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] найдут значение NULL в данном столбце атрибутов в процессе обучения модели, будет выдана ошибка. Данный флаг задается для столбца структуры интеллектуального анализа данных.  
  
 **РЕГРЕССОР**  
 Указывает, что алгоритм может использовать заданный столбец в формуле регрессии алгоритмов регрессии. Этот флаг поддерживается алгоритмами линейной регрессии [!INCLUDE[msCoName](../includes/msconame-md.md)] и дерева принятия решений [!INCLUDE[msCoName](../includes/msconame-md.md)], и задается для столбца модели интеллектуального анализа данных.  
  
 **MODEL_EXISTENCE_ONLY**  
 Значения столбца атрибутов являются менее важными, чем присутствие атрибута. Данный флаг задается для столбца модели интеллектуального анализа данных.  
  
 Алгоритмы сторонних разработчиков могут поддерживать дополнительные флаги моделирования. Чтобы определить, какие флаги моделирования поддерживает алгоритм, используйте набор строк схемы **SUPPORTED_MODELING_FLAGS** . Можно также создавать запросы к службам интеллектуального анализа данных на сервере для определения того, какие флаги моделирования поддерживаются для того или иного алгоритма. К примеру, следующий запрос возвращает флаги моделирования, поддерживаемые алгоритмом линейной регрессии (Майкрософт) на текущем сервере:  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 Ожидаемый результат:  
  
 NOT NULL,REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>Указание флагов моделирования в модели интеллектуального анализа данных  
 Примеры синтаксиса, который [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает для указания флага в столбце структуры интеллектуального анализа данных, см. в разделе [Создание структуры интеллектуального анализа данных &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
 Пример синтаксиса для указания флга моделирования в столбце модели интеллектуального анализа данных см. в разделе [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
 Дополнительные сведения о работе с столбцами модели интеллектуального анализа данных см. в разделе [столбцы модели интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
## <a name="see-also"></a>См. также:  
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)   
 [Расширения интеллектуального анализа данных &#40;Справочник по DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические&#41; DMX-элементы](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические обозначения&#41; DMX](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных ](../dmx/general-prediction-functions-dmx.md)   
 [Структура и использование прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции расширения интеллектуального анализа данных SELECT](../dmx/understanding-the-dmx-select-statement.md)  
  
  
