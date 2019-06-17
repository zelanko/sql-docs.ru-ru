---
title: 'Занятие 4: Построение сценария (учебник по интеллектуальному анализу интеллектуальному анализу данных) кластеризации последовательностей | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d34125b7b750daa1da25c9e8788172b5d9ca2c35
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62710606"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Занятие 4: Построение сценария (учебник по интеллектуальному анализу интеллектуальному анализу данных) кластеризации последовательностей
  Отделу маркетинга компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] необходимо знать, как перемещаются заказчики по веб-сайту компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] . Компания полагает, что есть какой-то определенный порядок, в котором они помещают продукты в корзину заказа. Отделу требуется проанализировать порядок последовательностей покупок, чтобы узнать, как заказчики добавляют в корзины связанные элементы. Эти сведения можно также использовать для оптимизации веб-сайта таким образом, чтобы заказчики покупали больше продуктов.  
  
 После выполнения задач этого занятия будет создана модель интеллектуального анализа данных, использующая алгоритм кластеризации последовательностей ( [!INCLUDE[msCoName](../includes/msconame-md.md)] ), который позволит прогнозировать, какой элемент будет помещен заказчиком в корзину заказов следующим. Эксперименты проводятся с двумя версиями модели: с версией, в которой анализируется только порядок продуктов в корзине, и с версией, которая содержит некоторые дополнительные демографические данные о заказчике для кластеризации. Наконец, будут использоваться модели для создания прогнозов, на основе которых можно рекомендовать продукцию клиентам.  
  
 Для выполнения задач занятия будет использоваться структура интеллектуального анализа данных market basket, созданный в [занятия 3: Построение сценария потребительской корзины &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md). Это занятие содержит следующие задачи.  
  
-   [Создание структуры модели интеллектуального анализа данных кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Обработка модели кластеризации последовательностей](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Изучение модели кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание связанной модели кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание прогнозов для модели кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание структуры модели интеллектуального анализа данных кластеризации последовательностей &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Все занятия  
 [Занятие 1. Создание промежуточного решения интеллектуального анализа &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Занятие 2. Построение сценария прогнозирования &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Занятие 3. Построение сценария потребительской корзины &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Занятие 4: Сценарий кластеризации (учебник по интеллектуальному анализу интеллектуальному анализу данных) последовательностей  
  
 [Занятие 5. Построение моделей логистической регрессии нейронной сети и &#40;средний уровень учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Учебник по основам интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Средний уровень учебник по интеллектуальному анализу данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
