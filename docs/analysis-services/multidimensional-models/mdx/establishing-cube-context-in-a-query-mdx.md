---
title: "Определение контекста куба в запросе (многомерные Выражения) | Документы Microsoft"
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
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 570d327b099508fc98f0e247b919fb222db54509
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>Определение контекста куба в запросе (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Каждый запрос многомерных выражений выполняется в заданном контексте куба. Контекст определяет элементы, вычисляемые в выражениях запроса.  
  
 В инструкции SELECT контекст куба определяется с помощью предложения FROM. В качестве контекста может выступать весь куб или его вложенный куб. Указав контекст куба при помощи предложения FROM, можно расширять или ограничивать его при помощи дополнительных функций.  
  
> [!NOTE]  
>  Инструкции SCOPE и CALCULATE также позволяют управлять контекстом куба в скрипте многомерных выражений. Дополнительные сведения см. в статье [Основные принципы создания скриптов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md).  
  
## <a name="from-clause-syntax"></a>Синтаксис предложения FROM  
 Предложение FROM имеет следующий синтаксис.  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 Обратите внимание на то, что в этом синтаксисе куб или вложенный куб, над которым выполняется инструкция SELECT, описывается предложением `<SELECT subcube clause>` .  
  
 Простым примером использования предложения FROM является запрос, обрабатывающий весь образец куба Adventure Works. Предложение FROM будет иметь следующий вид:  
  
```  
FROM [Adventure Works]  
```  
  
 Дополнительные сведения о предложении FROM в инструкции SELECT многомерных выражений см. в разделе [Инструкция SELECT (многомерные выражения)](../../../mdx/mdx-data-manipulation-select.md).  
  
## <a name="refining-the-context"></a>Уточнение контекста  
 Хотя в предложении FROM контекст задается внутри одного куба, это не запрещает одновременно работать с данными из нескольких кубов.  
  
 Для получения данных из кубов, которые не входят в заданный контекст куба, применяется функция многомерных выражений [LookupCube](../../../mdx/lookupcube-mdx.md) . Кроме того, для временного сужения контекста при вычислении запроса можно использовать такие функции как [Filter](../../../mdx/filter-mdx.md) .  
  
## <a name="see-also"></a>См. также  
 [Основные принципы запросов многомерных Выражений &#40; Службы Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
