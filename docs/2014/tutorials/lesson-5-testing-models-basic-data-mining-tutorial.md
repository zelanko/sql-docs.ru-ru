---
title: 'Занятие 5: Проверка моделей (учебник по интеллектуальному анализу данных) | Документы Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 280bca507905312aad5a17e307c8debf0537a185
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311842"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a>Занятие 5: Проверка моделей (учебник по интеллектуальному анализу данных)
  После того как модель была обработана с использованием проверочного набора сценария прямой почтовой рассылки, модели необходимо проверить по проверочному набору. Проверка — это важный шаг в процессе интеллектуального анализа данных. Очень важно выяснить, насколько хорошо модели интеллектуального анализа данных прямой почтовой рассылки работают с реальными данными, прежде чем выполнять их развертывание в рабочей среде.  
  
 Поскольку данные в проверочном наборе уже содержат известные значения для покупок велосипедов, очень просто определить, правильны ли полученные моделью прогнозы. Модель, которая дает наилучшие результаты будут использоваться [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] отдела маркетинга для идентификации заказчиков для их прямой почтовой рассылки.  
  
 На этом занятии вы проверите моделей с использованием различных методов:  
  
1.  Вы сделаете прогнозов по проверочному набору, чтобы видеть, насколько точна модель известных результатов. Вы воспользуетесь *диаграмма точности прогнозов* для измерения его эффективность.  
  
     [Проверка точности при помощи диаграммы точности прогнозов &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  Выполняется проверка моделей на отфильтрованном подмножестве данных. Можно сравнить несколько моделей в одной диаграмме точности прогнозов.  
  
     [Проверка модели с фильтром &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 Дополнительные сведения о том, как проверка модели в целом см. в разделе [основные понятия интеллектуального анализа данных](../../2014/analysis-services/data-mining/data-mining-concepts.md).  
  
## <a name="first-task-in-lesson"></a>Первая задача занятия  
 [Проверка точности при помощи диаграммы точности прогнозов &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>Предыдущее занятие  
 [Урок 4: Изучение моделей целевой рассылки &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 6: Создание прогнозов и работа с &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Вкладка Диаграмма точности прогнозов &#40;представление диаграммы точности интеллектуального анализа данных&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)   
 [Диаграмма точности прогнозов &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Тестирование и проверка &#40;интеллектуального анализа данных&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [Вкладка «матрица классификации» &#40;представление диаграммы точности интеллектуального анализа данных&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md)   
 [Матрица классификации &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  