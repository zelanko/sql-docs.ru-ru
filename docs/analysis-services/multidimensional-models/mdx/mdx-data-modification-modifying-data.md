---
title: "Изменение данных (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4c490f3998b148691f35328fe5543874be92f997
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-data-modification---modifying-data"></a>Изменение данных MDX - изменение данных
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Помимо использования многомерных выражений (MDX) для получения и обработки данных измерений и кубов, многомерных Выражений можно использовать для обновления или *обратной записи* данных измерений и кубов. Обновления могут быть как временными, например в случае гипотетического анализа «что, если...», так и постоянными, когда изменения должны происходить на основе анализа данных.  
  
 Данные могут обновляться на уровне измерения или куба.  
  
 **Обратная запись в измерение**  
 Для изменения данных измерения, доступного для записи, используется [Инструкция ALTER CUBE (многомерные выражения)](../../../mdx/mdx-data-definition-alter-cube.md) , а для отражения операций удаления, создания и обновления значений атрибутов используется [Инструкция REFRESH CUBE (многомерные выражения)](../../../mdx/mdx-data-definition-refresh-cube.md) . Кроме того, при помощи инструкции ALTER CUBE можно выполнять такие сложные операции, как удаление всего вложенного дерева в иерархии и продвижение потомков удаленного элемента.  
  
 **Обратная запись в куб**  
 Для обновления данных куба, доступного для записи, используется инструкция [UPDATE CUBE](../../../mdx/mdx-data-manipulation-update-cube.md) . Инструкция UPDATE CUBE позволяет записать конкретное значение в кортеж. [Инструкция REFRESH CUBE (многомерные выражения)](../../../mdx/mdx-data-definition-refresh-cube.md) используется для отражения обновленных данных в клиентском сеансе.  
  
 Дополнительные сведения см. в разделе [Обратная запись в куб (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
