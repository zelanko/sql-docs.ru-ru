---
title: Занятие 2. Создание сценария прогнозирования (учебник по интеллектуальному анализу данных — средний уровень) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ee814dc0891e70dfeccf2b96383d1d7b5c324aa8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62931527"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Занятие 2. Создание сценария прогнозирования (учебник по интеллектуальному анализу данных — средний уровень)
  Предположим, что вы аналитик по сбыту в компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], получили задание составить прогноз продаж продуктов на следующий год. В частности, вам было предложено сравнить прогнозы для различных регионов и линеек продуктов. Кроме того, ему требуется понять, зависят ли продажи различных продуктов от времени года.  
  
 Для поиска необходимых сведений в этом занятии будут использованы помесячные данные о продажах организации. Кроме того, будут сведены данные по продажам в трех регионах: Европа, Северная Америка и Тихоокеанский регион.  
  
 В результате выполнения задач этого занятия будут получены ответы на следующие ниже вопросы.  
  
-   Как меняется динамика продаж разных моделей велосипедов с течением времени?  
  
-   Существуют ли отличия между шаблонами продаж в трех регионах?  
  
-   Возможно ли спрогнозировать пиковые значения продаж?  
  
 Занятие может быть завершено в два этапа:  
  
-   Первая часть содержит базовые понятия создания и использования модели временных рядов.  
  
-   Вторая часть содержит пошаговые указания по созданию общей модели временных рядов на основе всех регионов. Эту общую модель можно использовать для *перекрестного прогнозирования*.  
  
 Для выполнения задач этого занятия, которые перечислены ниже, будет использоваться источник [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] данных, созданный на [занятии 1. Создание промежуточного решения интеллектуального анализа данных &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).  
  
> [!WARNING]  
>  Даты, используемые в образце базы данных [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] , изменены для этой версии. При использовании более ранней версии [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]можно построить модель, выполнив эти действия, но полученные результаты могут оказаться другими.  
  
 **Создание простой модели прогнозирования**  
  
-   [Руководство по добавлению представления источников данных для прогнозирования &#40;промежуточного интеллектуального анализа данных&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [Руководство по созданию структуры прогнозирования и модели &#40;промежуточного интеллектуального анализа данных&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Изменение структуры прогнозирования &#40;промежуточное руководство по интеллектуальному анализу данных&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [Настройка и обработка модели прогнозирования &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Изучите учебник по модели прогнозирования &#40;промежуточного интеллектуального анализа данных&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание прогнозов временных рядов &#40;учебнике по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 **Создание общей модели прогнозирования для перекрестного прогнозирования**  
  
-   [Учебник по расширенному анализу временных рядов &#40;промежуточного интеллектуального анализа данных&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [Прогнозирование временных рядов с помощью обновленного учебника по интеллектуальному анализу данных &#40;данных&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [Прогнозирование временных рядов с использованием замещения данных &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [Сравнение прогнозов для моделей прогнозирования &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Руководство по добавлению представления источников данных для прогнозирования &#40;промежуточного интеллектуального анализа данных&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [Основные сведения о требованиях к модели временных рядов &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Все занятия  
 [Занятие 1. Создание промежуточного решения интеллектуального анализа данных &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 Урок 2. Сценарий прогнозирования (учебник по интеллектуальному анализу данных — средний уровень)  
  
 [Урок 3. Построение сценария покупательского поведения (учебник по интеллектуальному анализу данных — средний уровень)](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Занятие 4. Создание сценария кластеризации последовательностей &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Занятие 5. Построение моделей нейронной сети и логистической регрессии (учебник по интеллектуальному анализу данных — средний уровень)](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Учебник по основам интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Учебник по интеллектуальному анализу данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Алгоритм временных рядов (Майкрософт)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
