---
title: 'Занятие 4: Построение сценария (учебник по интеллектуальному анализу интеллектуальному анализу данных) кластеризации последовательностей | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5e276d4a2b44c8d0fdc6be6787f58e359e4c15d5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122574"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Занятие 4: Построение сценария (учебник по интеллектуальному анализу интеллектуальному анализу данных) кластеризации последовательностей
  Отделу маркетинга [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] необходимо знать, как перемещаются заказчики по [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] веб-сайта. Компания полагает, что есть какой-то определенный порядок, в котором они помещают продукты в корзину заказа. Отделу требуется проанализировать порядок последовательностей покупок, чтобы узнать, как заказчики добавляют в корзины связанные элементы. Эти сведения можно также использовать для оптимизации веб-сайта таким образом, чтобы заказчики покупали больше продуктов.  
  
 После выполнения задач этого занятия, вы будет создана модель интеллектуального анализа данных, которая использует [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм кластеризации последовательностей для прогнозирования следующего элемента, который будет помещен заказчиком в корзину заказов. Эксперименты проводятся с двумя версиями модели: с версией, в которой анализируется только порядок продуктов в корзине, и с версией, которая содержит некоторые дополнительные демографические данные о заказчике для кластеризации. Наконец, будут использоваться модели для создания прогнозов, на основе которых можно рекомендовать продукцию клиентам.  
  
 Для выполнения задач занятия будет использоваться структура интеллектуального анализа данных market basket, созданный в [занятия 3: построение сценария потребительской корзины &#40;учебнике по интеллектуальному данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md). Это занятие содержит следующие задачи.  
  
-   [Создание структуры модели интеллектуального анализа данных кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Обработка модели кластеризации последовательностей](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Изучение модели кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание связанной модели кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание прогнозов для модели кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание структуры модели интеллектуального анализа данных кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Все занятия  
 [Урок 1: Создание промежуточного решения интеллектуального анализа &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Занятие 2: Построение сценария прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Занятие 3: Построение сценария потребительской корзины &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Урок 4. Сценарий кластеризации последовательностей (учебник по интеллектуальному анализу данных — средний уровень)  
  
 [Занятие 5: Построение моделей логистической регрессии нейронной сети и &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Учебник интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Средний уровень учебник по интеллектуальному анализу данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
