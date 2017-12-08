---
title: "Создание вычисляемых элементов в многомерных Выражениях (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 03ee94149faf02f0ef99bdde82f4f5847842fd57
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-calculated-members---building-calculated-members"></a>Многомерные Выражения вычисляемых элементов — Создание вычисляемых элементов
  В многомерных выражениях вычисляемым называется элемент, разрешаемый путем вычисления многомерного выражения, возвращающего значение. В этом определении кроется огромный потенциал. Возможность создания и использования вычисляемых элементов в многомерных запросах дает широкие возможности для манипулирования данными.  
  
 Вычисляемый элемент можно создать в любом месте иерархии. Кроме того, вычисляемые элементы могут зависеть не только от существующих элементов куба, но и от других вычисляемых элементов, определенных в том же многомерном выражении.  
  
 При определении вычисляемого элемента для него можно задать один из следующих контекстов.  
  
-   **Область запроса.** Для создания вычисляемого элемента, определяемого как часть многомерного запроса, область которого, следовательно, ограничена этим запросом, применяется ключевое слово WITH. После создания вычисляемый элемент можно использовать в инструкции многомерных выражений SELECT. Этот подход позволяет изменять вычисляемый элемент, созданный при помощи ключевого слова WITH, не изменяя инструкцию SELECT.  
  
     Дополнительные сведения о создании вычисляемых элементов с помощью ключевого слова WITH см. в разделе [Создание вычисляемых элементов с областью действия запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Область сеанса.** Для создания вычисляемого элемента, область которого шире контекста запроса и распространяется на весь сеанс многомерных выражений, применяется инструкция CREATE MEMBER. Вычисляемый элемент, определенный при помощи инструкции CREATE MEMBER, доступен для всех многомерных запросов текущего сеанса. Например, инструкцию CREATE MEMBER имеет смысл использовать в клиентском приложении, которое постоянно использует один и тот же набор в различных запросах.  
  
     Дополнительные сведения о создании вычисляемых элементов в сеансе с помощью инструкции CREATE MEMBER см. в разделе [Создание вычисляемых элементов с областью действия сеанса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>См. также:  
 [Инструкция CREATE MEMBER (многомерные выражения)](../../../mdx/mdx-data-definition-create-member.md)   
 [Справочник по функциям многомерных выражений (многомерные выражения)](../../../mdx/mdx-function-reference-mdx.md)   
 [Инструкция SELECT &#40; Многомерные Выражения &#41;](../../../mdx/mdx-data-manipulation-select.md)  
  
  
