---
title: "Построение вычислений значений ячеек в Многомерном выражении | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8e2e963c47746a85e760b3b4464edd5cbe39f1fe
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="mdx-cell-calculations---build-cell-calculations"></a>Вычисления многомерных Выражений ячейки - построение вычислений значений ячеек
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Многомерные выражения предоставляют целый ряд инструментов для формирования вычисляемых значений, таких как вычисляемые элементы, пользовательские свертки и пользовательские элементы.  Однако по этой причине применить эти средства так, чтобы повлиять только на часть ячеек или на одну ячейку, будет трудно.  
  
 Чтобы формировать вычисляемые значения ячеек, надо воспользоваться имеющимися в многомерных выражениях возможностями вычисляемых ячеек. Вычисляемые ячейки позволяют выделить особый срез ячеек, который называется *вложенным кубом вычисления*, и применить формулу к каждой ячейке вложенного куба вычисления, удовлетворяющей дополнительному условию, применимому к любой ячейке.  
  
 Вычисляемые ячейки также предлагают сложные функциональные возможности, такие как формулы целенаправленного поиска, которые используются в ключевых показателях эффективности, а также формулы для анализа гипотез. Этот уровень функциональных возможностей основан на возможности задавать порядок проходов в службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , что позволяет выполнять рекурсивные проходы по вычисляемым ячейкам, причем формулы для вычисления применяются в конкретных проходах в заданном порядке прохождения. Дополнительные сведения о порядке прохода и порядке разрешения см. в разделе [Основные сведения о порядке этапов и порядке вычисления (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 При создании вычисляемые ячейки похожи как на именованные наборы, так и на вычисляемые элементы тем, что вычисляемые ячейки можно временно создать на время жизни одного сеанса или отдельного запроса; и они становятся глобально доступными как часть куба:  
  
-   **Область — запрос** . Для создания вычисляемой ячейки, которая определена как часть запроса многомерных выражений (поэтому ее область ограничена этим запросом), надо применить ключевое слово WITH. Затем можно использовать эту вычисляемую ячейку в операторе MDX SELECT. При таком подходе вычисляемую ячейку, которая создается с применением ключевого слова **WITH** , можно изменить, не нарушая инструкцию SELECT.  
  
     Дополнительные сведения о создании вычисляемых элементов с помощью ключевого слова WITH см. в разделе [Создание вычислений ячеек с областью действия запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md).  
  
-   **Область — сеанс** . Чтобы создать вычисляемую ячейку, область которой шире контекста запроса (то есть область которой составляет время жизни сеанса многомерных выражений), можно воспользоваться инструкцией CREATE CELL CALCULATION или ALTER CUBE.  
  
     Дополнительные сведения о применении инструкций CREATE CELL CALCULATION и ALTER CUBE для создания вычисляемых ячеек в сеансе см. в разделе [Создание вычисляемых ячеек с областью действия сеанса](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md).  
  
## <a name="see-also"></a>См. также  
 [Инструкция ALTER CUBE &#40; Многомерные Выражения &#41;](../../../mdx/mdx-data-definition-alter-cube.md)   
 [Создать инструкции ВЫЧИСЛЕНИЯ ЯЧЕЙКИ &#40; Многомерные Выражения &#41;](../../../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Создание вычислений ячеек с областью действия запроса &#40; Многомерные Выражения &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [Основные принципы запросов многомерных Выражений &#40; Службы Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
