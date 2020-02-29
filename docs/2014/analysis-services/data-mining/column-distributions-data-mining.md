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
ms.openlocfilehash: 6c7eab32f251b9622c6ac77febf2c004806c024b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78174652"
---
# <a name="column-distributions-data-mining"></a>Распределения столбцов (интеллектуальный анализ данных)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] В [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]можно определить распределения столбцов в структуре интеллектуального анализа данных, чтобы повлиять на то, как алгоритмы обрабатывают данные в этих столбцах при создании моделей интеллектуального анализа данных. В некоторых алгоритмах лучше задавать распределение для всех столбцов, содержащих непрерывные данные, до начала обработки модели в случае, если указанные столбцы содержат общие распределения значений. Если распределения не заданы, создаваемые модели интеллектуального анализа данных могут работать менее точно, чем модели с заданными распределениями, так как на вход алгоритмов будет подаваться меньшее количество данных для анализа.

 Алгоритмы, доступные в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , поддерживают следующие типы распределения.

 `Normal`Значения непрерывного столбца формируют гистограмму с нормальным распределением.

 ![Гистограмма с нормальным распределением](../media/normal-distribution.gif "Гистограмма с нормальным распределением")

 `Log Normal`Значения для непрерывного столбца формируют гистограмму, где кривая вытянута в верхней части и наклонена в сторону нижней границы.

 ![Гистограмма с логарифмически нормальным распределением](../media/log-normal-distribution.gif "Гистограмма с логарифмически нормальным распределением")

 `Uniform`Значения непрерывного столбца образуют плоскую кривую, в которой все значения имеют одинаковую вероятность.

 ![Гистограмма с равномерным распределением](../media/uniform-distribution.gif "Гистограмма с равномерным распределением")

 Дополнительные сведения об алгоритмах в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] см. в разделе [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](data-mining-algorithms-analysis-services-data-mining.md).

## <a name="see-also"></a>См. также:
 [Типы содержимого &#40;интеллектуального анализа&#41;](content-types-data-mining.md) [структур интеллектуального анализа данных &#40;Analysis Services —](mining-structures-analysis-services-data-mining.md) [методы дискретизации](discretization-methods-data-mining.md)&#41;интеллектуального анализа данных &#40;[распределения&#41;DMX](/sql/dmx/distributions-dmx) &#40;[столбцы структуры интеллектуального](mining-structure-columns.md) анализа данных


