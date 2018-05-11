---
title: Определение контекста куба в запросе (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae3ae19d0d009eb0ef4621baf6559921e92ccac5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
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
 [Основные принципы запросов многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
