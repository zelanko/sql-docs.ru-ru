---
title: Распределения столбцов (интеллектуальный анализ данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5db71b5a94285f8ae63afeb65bec3f9807f8da27
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66085707"
---
# <a name="column-distributions-data-mining"></a>Распределения столбцов (интеллектуальный анализ данных)
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]можно определить распределения столбцов в структуре интеллектуального анализа данных, чтобы влиять на то, как алгоритмы обрабатывают данные в этих столбцах при создании моделей интеллектуального анализа данных. В некоторых алгоритмах лучше задавать распределение для всех столбцов, содержащих непрерывные данные, до начала обработки модели в случае, если указанные столбцы содержат общие распределения значений. Если распределения не заданы, создаваемые модели интеллектуального анализа данных могут работать менее точно, чем модели с заданными распределениями, так как на вход алгоритмов будет подаваться меньшее количество данных для анализа.  
  
 Алгоритмы, доступные в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , поддерживают следующие типы распределения.  
  
 `Normal`  
 Значения для непрерывного столбца формируют гистограмму с нормальным распределением.  
  
 ![Гистограмма с нормальным распределением](../media/normal-distribution.gif "гистограмма с нормальным распределением")  
  
 `Log Normal`  
 Значения для непрерывного столбца формируют гистограмму, вытянутую в верхнем конце и скошенную в нижнем конце.  
  
 ![Гистограмма с логарифмически нормальным распределением](../media/log-normal-distribution.gif "гистограмма с логарифмически нормальным распределением")  
  
 `Uniform`  
 На основе значений столбца непрерывных данных может быть сформирована плоская кривая, на которой все значения являются равновероятными.  
  
 ![Гистограмма с равномерным распределением](../media/uniform-distribution.gif "гистограмма с равномерным распределением")  
  
 Дополнительные сведения об алгоритмах в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>См. также  
 [Типы содержимого (интеллектуальный анализ данных)](content-types-data-mining.md)   
 [Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](mining-structures-analysis-services-data-mining.md)   
 [Методы дискретизации (интеллектуальный анализ данных)](discretization-methods-data-mining.md)   
 [Распределения (расширения интеллектуального анализа данных)](/sql/dmx/distributions-dmx)   
 [Столбцы структуры интеллектуального анализа данных](mining-structure-columns.md)  
  
  
