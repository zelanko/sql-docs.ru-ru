---
title: "Классифицированных столбцов (интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d114c3495c213e5493e3ccb87c1201d0517e4edf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="classified-columns-data-mining"></a>Классифицированные столбцы (интеллектуальный анализ данных)
  При определении классифицированного столбца создается связь между текущим столбцом и другим столбцом в структуре интеллектуального анализа данных. Данные в столбце структуры интеллектуального анализа, обозначенном как классифицированный столбец, содержат сведения о разбивке по категориям, описывающие значения в другом столбце структуры интеллектуального анализа данных.  
  
 Например, предположим, что есть два столбца с числовыми данными. Первый столбец, [Yearly Purchases], содержит все покупки каждого заказчика в течение определенного года, а второй столбец, [Standard Deviations], содержит стандартные отклонения для этих значений. В этом случае можно обозначить столбец [Yearly Purchases] в качестве классифицированного, чтобы модель позволяла использовать эту связь в анализе.  
  
> [!NOTE]  
>  Алгоритмы в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживают использование классифицированных столбцов. Эта функция предназначена для использования при создании пользовательских алгоритмов.  
  
## <a name="defining-a-classified-column"></a>Определение классифицированного столбца  
 Тип данных, используемый в классифицированном столбце, должен быть либо **Long** , либо **Double**.  
  
 В следующем списке описываются типы содержимого, поддерживаемые службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для классифицированных столбцов.  
  
 **PROBABILITY**  
 Значение в столбце является вероятностью связанного значения и представлено числом от 0 до 1.  
  
 **VARIANCE**  
 Значение в столбце является отклонением связанного значения.  
  
 **STDEV**  
 Значение в столбце является среднеквадратичным отклонением связанного значения.  
  
 **PROBABILITY_VARIANCE**  
 Значение в столбце является отклонением вероятности для связанного значения.  
  
 **PROBABILITY_STDEV**  
 Значение в столбце является среднеквадратичным отклонением вероятности для связанного значения.  
  
 **Псевдоним**  
 Значение в столбце является весом, коэффициентом репликации объекта, связанного значения.  
  
## <a name="see-also"></a>См. также  
 [Типы содержимого (интеллектуальный анализ данных)](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Типы данных (интеллектуальный анализ данных)](../../analysis-services/data-mining/data-types-data-mining.md)  
  
  

