---
title: Урок 2. Построение сценария прогнозирования (учебник по интеллектуальному анализу интеллектуальному анализу данных) | Документация Майкрософт
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931527"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Урок 2. Построение сценария прогнозирования (учебник по интеллектуальному анализу интеллектуальному анализу данных)
  Предположим, что вы аналитик по сбыту в компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], получили задание составить прогноз продаж продуктов на следующий год. В частности, вам было предложено сравнить прогнозы для различных регионов и линеек продуктов. Кроме того, ему требуется понять, зависят ли продажи различных продуктов от времени года.  
  
 Чтобы найти требуемые сведения, на этом занятии будут использованы Помесячные данные о продажах компании уровень за месяц, и также будут использованы Помесячные данные по продажам трех регионах: Европа, Северная Америка и Тихоокеанский регион.  
  
 В результате выполнения задач этого занятия будут получены ответы на следующие ниже вопросы.  
  
-   Как меняется динамика продаж разных моделей велосипедов с течением времени?  
  
-   Существуют ли отличия между шаблонами продаж в трех регионах?  
  
-   Возможно ли спрогнозировать пиковые значения продаж?  
  
 Занятие может быть завершено в два этапа:  
  
-   Первая часть содержит базовые понятия создания и использования модели временных рядов.  
  
-   Вторая часть содержит пошаговые указания по созданию общей модели временных рядов на основе всех регионов. Воспользуйтесь следующей общей модели для *перекрестного прогнозирования*.  
  
 Для выполнения задач этого занятия, перечисленных ниже, будет использоваться [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] источника данных, который был создан [занятии 1: Создание промежуточного решения интеллектуального анализа &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).  
  
> [!WARNING]  
>  Даты, используемые в образце базы данных [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] , изменены для этой версии. При использовании более ранней версии [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]можно построить модель, выполнив эти действия, но полученные результаты могут оказаться другими.  
  
 **Создание простой модели прогнозирования**  
  
-   [Добавление данных представление источника для прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [Создание структуры и модели прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Изменение структуры прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [Настройка и обработка модели прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Изучение модели прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание прогнозов временных рядов &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 **Создание общей модели прогнозирования для перекрестного прогнозирования**  
  
-   [Расширенные прогнозы временных рядов &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [Прогнозы временных рядов с использованием обновленных данных &#40;учебника интеллектуальному анализу данных&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [Прогнозы временных рядов с заменой данных &#40;учебника интеллектуальному анализу данных&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [Сравнение прогнозов моделей прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Добавление данных представление источника для прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [Основные сведения о требования к временным рядам модели &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Все занятия  
 [Занятие 1. Создание промежуточного решения интеллектуального анализа &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 Урок 2. Прогнозирование сценария (учебник для интеллектуального анализа данных по интеллектуальному анализу данных)  
  
 [Занятие 3. Построение сценария потребительской корзины &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Занятие 4. Построение сценария кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Занятие 5. Построение моделей логистической регрессии нейронной сети и &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Учебник по основам интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Средний уровень учебник по интеллектуальному анализу данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Алгоритм временных рядов (Майкрософт)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
