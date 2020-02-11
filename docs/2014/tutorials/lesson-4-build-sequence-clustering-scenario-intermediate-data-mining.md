---
title: Занятие 4. Создание сценария кластеризации последовательностей (учебник по интеллектуальному анализу данных — средний уровень) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62710606"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Занятие 4. Создание сценария кластеризации последовательностей (учебник по интеллектуальному анализу данных — средний уровень)
  Отделу маркетинга компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] необходимо знать, как перемещаются заказчики по веб-сайту компании [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] . Компания полагает, что есть какой-то определенный порядок, в котором они помещают продукты в корзину заказа. Отделу требуется проанализировать порядок последовательностей покупок, чтобы узнать, как заказчики добавляют в корзины связанные элементы. Эти сведения можно также использовать для оптимизации веб-сайта таким образом, чтобы заказчики покупали больше продуктов.  
  
 После выполнения задач этого занятия будет создана модель интеллектуального анализа данных, использующая алгоритм кластеризации последовательностей ( [!INCLUDE[msCoName](../includes/msconame-md.md)] ), который позволит прогнозировать, какой элемент будет помещен заказчиком в корзину заказов следующим. Эксперименты проводятся с двумя версиями модели: с версией, в которой анализируется только порядок продуктов в корзине, и с версией, которая содержит некоторые дополнительные демографические данные о заказчике для кластеризации. Наконец, будут использоваться модели для создания прогнозов, на основе которых можно рекомендовать продукцию клиентам.  
  
 Для выполнения задач на этом занятии будет использоваться структура интеллектуального анализа данных "потребительская корзина", созданная на [занятии 3. Создание сценария потребительской корзины &#40;учебнике по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md). Это занятие содержит следующие задачи.  
  
-   [Создание структуры модели интеллектуального анализа кластеризации последовательностей &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Обработка модели кластеризации последовательностей](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Изучение модели кластеризации последовательностей &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание связанной модели кластеризации последовательностей &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Создание прогнозов на модели кластеризации последовательностей &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание структуры модели интеллектуального анализа кластеризации последовательностей &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Все занятия  
 [Занятие 1. Создание промежуточного решения интеллектуального анализа данных &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Занятие 2. Создание сценария прогнозирования &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Занятие 3. Создание сценария потребительской корзины &#40;учебнике по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Урок 4. Сценарий кластеризации последовательностей (учебник по интеллектуальному анализу данных — средний уровень)  
  
 [Занятие 5. Создание моделей нейронной сети и логистической регрессии &#40;учебнике по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также:  
 [Учебник по основам интеллектуального анализа данных](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Учебник по интеллектуальному анализу данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
