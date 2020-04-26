---
title: Занятие 5. Тестирование моделей (учебник по интеллектуальному анализу данных — базовый) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 88a9d564b297d277d1566152cc11599bec912ddc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63185428"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a>Занятие 5. Тестирование моделей (учебник по интеллектуальному анализу данных — базовый)
  После того как модель была обработана с использованием проверочного набора сценария прямой почтовой рассылки, модели необходимо проверить по проверочному набору. Проверка — это важный шаг в процессе интеллектуального анализа данных. Очень важно выяснить, насколько хорошо модели интеллектуального анализа данных прямой почтовой рассылки работают с реальными данными, прежде чем выполнять их развертывание в рабочей среде.  
  
 Поскольку данные в проверочном наборе уже содержат известные значения для покупок велосипедов, очень просто определить, правильны ли полученные моделью прогнозы. Модель, которая работает наилучшим образом, будет использоваться в [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] отделе маркетинга, чтобы определять клиентов для их кампании по целевой рассылке.  
  
 На этом занятии вы проверите модели с помощью нескольких методов:  
  
1.  Вы сделаете прогнозы в проверочном наборе, чтобы увидеть, насколько точна модель на основе известных результатов. Для измерения эффективности работы используется *Диаграмма точности прогнозов* .  
  
     [Проверка точности с помощью диаграмм точности прогнозов (учебник интеллектуального анализа данных — начальный уровень)](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  Вы проверите модели на отфильтрованном подмножестве данных. Можно сравнить несколько моделей в одной и той же диаграмме точности прогнозов.  
  
     [Тестирование фильтрованной модели &#40;учебник по интеллектуальному анализу данных (Basic)&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 Дополнительные сведения о проверке модели в целом см. в разделе [Основные понятия интеллектуального анализа данных](../../2014/analysis-services/data-mining/data-mining-concepts.md).  
  
## <a name="first-task-in-lesson"></a>Первая задача занятия  
 [Проверка точности с помощью диаграмм точности прогнозов (учебник интеллектуального анализа данных — начальный уровень)](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>Предыдущее занятие  
 [Занятие 4. изучение моделей целевой рассылки &#40;учебник по основам интеллектуального анализа данных&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 6. Создание прогнозов и работа с ними (учебник по интеллектуальному анализу данных — начальный уровень)](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Вкладка диаграммы точности прогнозов &#40;представление диаграммы точности интеллектуального анализа данных&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)   
 [Диаграмма точности прогнозов &#40;Analysis Services&#41;интеллектуального анализа данных](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Тестирование и проверка &#40;&#41;интеллектуального анализа данных](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [Вкладка Матрица классификации &#40;представление диаграммы точности интеллектуального анализа данных&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md)   
 [Матрица классификации (службы Analysis Services — интеллектуальный анализ данных)](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
