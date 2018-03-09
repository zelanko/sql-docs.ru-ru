---
title: "Создание вычисляемых элементов в многомерных Выражениях (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: cbfe97ab13483ccaf31134bfa45ab5b583f797d7
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="mdx-calculated-members---building-calculated-members"></a>Многомерные Выражения вычисляемых элементов — Создание вычисляемых элементов
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
В многомерных выражениях вычисляемым называется элемент, разрешаемый путем вычисления многомерного выражения, возвращающего значение. В этом определении кроется огромный потенциал. Возможность создания и использования вычисляемых элементов в многомерных запросах дает широкие возможности для манипулирования данными.  
  
 Вычисляемый элемент можно создать в любом месте иерархии. Кроме того, вычисляемые элементы могут зависеть не только от существующих элементов куба, но и от других вычисляемых элементов, определенных в том же многомерном выражении.  
  
 При определении вычисляемого элемента для него можно задать один из следующих контекстов.  
  
-   **Область запроса.** Для создания вычисляемого элемента, определяемого как часть многомерного запроса, область которого, следовательно, ограничена этим запросом, применяется ключевое слово WITH. После создания вычисляемый элемент можно использовать в инструкции многомерных выражений SELECT. Этот подход позволяет изменять вычисляемый элемент, созданный при помощи ключевого слова WITH, не изменяя инструкцию SELECT.  
  
     Дополнительные сведения о создании вычисляемых элементов с помощью ключевого слова WITH см. в разделе [Создание вычисляемых элементов с областью действия запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Область сеанса.** Для создания вычисляемого элемента, область которого шире контекста запроса и распространяется на весь сеанс многомерных выражений, применяется инструкция CREATE MEMBER. Вычисляемый элемент, определенный при помощи инструкции CREATE MEMBER, доступен для всех многомерных запросов текущего сеанса. Например, инструкцию CREATE MEMBER имеет смысл использовать в клиентском приложении, которое постоянно использует один и тот же набор в различных запросах.  
  
     Дополнительные сведения о создании вычисляемых элементов в сеансе с помощью инструкции CREATE MEMBER см. в разделе [Создание вычисляемых элементов с областью действия сеанса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>См. также:  
 [CREATE MEMBER, инструкция #40; Многомерные Выражения &#41;](../../../mdx/mdx-data-definition-create-member.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [Инструкция SELECT &#40; Многомерные Выражения &#41;](../../../mdx/mdx-data-manipulation-select.md)  
  
  
