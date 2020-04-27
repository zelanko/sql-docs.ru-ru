---
title: Обработка данных (многомерные выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 4865192e-f46b-4ce5-b51c-9e08dbad5b85
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 29e569ec781d0015017d3009746c3299f0865c80
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074358"
---
# <a name="manipulating-data-mdx"></a>Манипулирование данными (многомерные выражения)

С помощью многомерных выражений можно осуществлять самые различные операции с данными. В статье, приведенной в этой статье, рассматриваются некоторые более сложные концепции обработки данных в языке многомерных выражений.

## <a name="in-this-section"></a>в этом разделе

|Раздел|Описание|  
|-----------|-----------------|  
|[Извлечение данных из источника с помощью функции DRILLTHROUGH (многомерные выражения)](mdx-data-manipulation-retrieve-source-data-using-drillthrough.md)|Рассматриваются вопросы применения инструкции многомерных выражений [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) для извлечения наборов строк исходных данных, применимых к ячейке в источнике многомерных данных|  
|[Работа с функцией RollupChildren (многомерные выражения)](mdx-data-manipulation-rollupchildren-function.md)|Обсуждается влияние [RollupChildrenности](/sql/mdx/rollupchildren-mdx) многомерных выражений
|[Основные сведения о порядке этапов и порядке вычисления (многомерные выражения)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|Подробно рассматривается концепция порядка разрешения и вопросы его влияния на выражения, инструкции и скрипты многомерных выражений.|  

<!-- ??

|[Script for Search and Replace] function on the analysis of multidimensional data.|

GeneMi is removing this commented row because it is unclear what article its link meant to link to.
Also, I had to add its leading '|' character, for consistency to aid bulk automated updated to our markdown source code.

GeneMi , 2019/01/19
-->

## <a name="see-also"></a>См. также

[Основные принципы запросов многомерных выражений (службы Analysis Services)](mdx-query-fundamentals-analysis-services.md)
