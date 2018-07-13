---
title: 'Занятие 2: Построение сценария прогнозирования (учебник по интеллектуальному анализу интеллектуальному анализу данных) | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5db75cbdabd62b569c782bd48755ce817819a475
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155505"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Занятие 2: Построение сценария прогнозирования (учебник по интеллектуальному анализу интеллектуальному анализу данных)
  Предположим, что вы аналитик по сбыту в компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], получили задание составить прогноз продаж продуктов на следующий год. В частности, вам было предложено сравнить прогнозы для различных регионов и линеек продуктов. Кроме того, ему требуется понять, зависят ли продажи различных продуктов от времени года.  
  
 Для поиска необходимых сведений в этом занятии будут использованы помесячные данные о продажах организации. Кроме того, будут сведены данные по продажам в трех регионах: Европа, Северная Америка и Тихоокеанский регион.  
  
 В результате выполнения задач этого занятия будут получены ответы на следующие ниже вопросы.  
  
-   Как меняется динамика продаж разных моделей велосипедов с течением времени?  
  
-   Существуют ли отличия между шаблонами продаж в трех регионах?  
  
-   Возможно ли спрогнозировать пиковые значения продаж?  
  
 Занятие может быть завершено в два этапа:  
  
-   Первая часть содержит базовые понятия создания и использования модели временных рядов.  
  
-   Вторая часть содержит пошаговые указания по созданию общей модели временных рядов на основе всех регионов. Воспользуйтесь следующей общей модели для *перекрестного прогнозирования*.  
  
 Для выполнения задач этого занятия, перечисленных ниже, будет использоваться [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] источника данных, который был создан [занятии 1: Создание промежуточного решения интеллектуального анализа &#40;данных учебник по интеллектуальному анализу&#41; ](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).  
  
> [!WARNING]  
>  Даты в [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] образца базы данных были обновлены для этого выпуска. При использовании более ранней версии [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] можно построить модель, выполнив эти действия, но полученные результаты могут оказаться другими.  
  
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
 [Урок 1: Создание промежуточного решения интеллектуального анализа &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 Урок 2. Сценарий прогнозирования (учебник по интеллектуальному анализу данных — средний уровень)  
  
 [Занятие 3: Построение сценария потребительской корзины &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Занятие 4: Построение сценария кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Занятие 5: Построение моделей логистической регрессии нейронной сети и &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Учебник интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Средний уровень учебник по интеллектуальному анализу данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Алгоритм временных рядов (Майкрософт)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
