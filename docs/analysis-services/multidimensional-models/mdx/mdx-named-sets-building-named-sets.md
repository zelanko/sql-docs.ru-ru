---
title: "Построение именованных наборов в многомерных Выражениях (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
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
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: aff5c819f15c6c1117ded70fe34169811d4f3bd1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-named-sets---building-named-sets"></a>Многомерные Выражения именованных наборов - построение именованных наборов
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Выражение набора может быть длинной и сложной декларацией и трудно проследить и понять. Или выражение набора может использоваться настолько часто, что его повторное определение может стать утомительным. Чтобы облегчить работу с длинными, сложными или часто используемыми выражениями, в многомерных выражениях можно определить такое выражение, как *именованный набор*.  
  
 В сущности, именованный набор представляет собой выражение набора, которому назначен псевдоним. В именованный набор могут входить любые элементы или функции, которые могут обычно включаться в набор. Псевдоним набора рассматривается в многомерных выражениях как выражение набора, поэтому этот псевдоним может использоваться везде, где допустимы выражения набора.  
  
 Именованный набор можно определить в одном из следующих контекстов:  
  
-   **Контекст запроса.** Чтобы создать именованный набор, который определен как часть запроса многомерных выражений, с областью, ограниченной этим запросом, используется ключевое слово WITH. Затем именованный набор можно использовать внутри инструкции MDX SELECT. При таком подходе именованный набор, созданный с использованием ключевого слова WITH, может быть изменен без изменений в инструкции SELECT.  
  
     Дополнительные сведения об использовании ключевого слова WITH для создания именованных наборов см. в разделе [Создание именованных наборов с областью действия запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
-   **Контекст сеанса.** Чтобы создать именованный набор, область которого шире контекста запроса, то есть набор, действующий в течение сеанса многомерных выражений, следует использовать инструкцию CREATE SET. Именованный набор, определенный с использованием инструкции CREATE SET, доступен для всех запросов многомерных выражений в этом сеансе. Например, инструкция CREATE SET полезна в клиентском приложении, в котором набор многократно применяется в разнообразных запросах.  
  
     Дополнительные сведения об использовании инструкции CREATE SET для создания именованных наборов см. в разделе [Создание именованных наборов с областью действия сеанса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-session-scoped-named-sets.md).  
  
## <a name="see-also"></a>См. также:  
 [Инструкция SELECT (многомерные выражения)](../../../mdx/mdx-data-manipulation-select.md)   
 [СОЗДАТЬ инструкцию SET &#40; Многомерные Выражения &#41;](../../../mdx/mdx-data-definition-create-set.md)   
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
