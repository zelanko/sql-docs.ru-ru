---
title: "ValidMeasure (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VALIDMEASURE
dev_langs: kbMDX
helpviewer_keywords: ValidMeasure function
ms.assetid: ecf20a86-c45e-4521-84ce-3a466e0c1136
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9309b0b62994e6d3199a7aa565d9edd2e88c5f73
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="validmeasure-mdx"></a>ValidMeasure (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает для указанного кортежа значение меры в кубе путем перемещения неприменимых измерений на уровень «Все» (или элемент по умолчанию, если статистическая обработка невозможна).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ValidMeasure(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
## <a name="remarks"></a>Замечания  
 **ValidMeasure** функция возвращает значение кортежа, пропуск атрибутов, не имеющие связей с группой мер, меры, значение которой возвращает кортеж. Атрибут может быть не связан с мерой по двум следующим причинам.  
  
-   Измерение атрибута не имеет связи с группой мер меры в кортеже.  
  
-   Измерение атрибута не имеет связи с группой мер данной меры, но атрибут гранулярности не является ключевым атрибутом и не имеет прямой связи с атрибутом в кортеже.  
  
 Поведение, заданное этой функцией серверные поведение по умолчанию и определяется **IgnoreUnrelatedDimensions** свойства объекта группы мер.  
  
 Для каждого атрибута в заданном кортеже с гранулярностью (то есть если элемент в кортеже не является элементом «Все») перемещение текущей координаты происходит следующим образом:  
  
-   атрибуты, связанные с заданным атрибутом элемента, переносятся на элемент, существующий с текущим элементом;  
  
-   атрибуты, связанные с заданным атрибутом элемента, переносятся на элемент уровня «Все» (или элемент по умолчанию, если статистическая обработка невозможна);  
  
-   несвязанные атрибуты на элемент уровня «Все» (на основе меры).  
  
## <a name="example"></a>Пример  
 Приведенный ниже запрос показывает пример использования функции ValidMeasure для переопределения поведения свойства IgnoreUnrelatedDimensions. В кубе Adventure Works группа мер Sales Targets имеет свойство IgnoreUnrelatedDimensions в значении False. Поскольку измерение Date соединяется с этой группой мер на гранулярности «Календарный квартал», это означает, что мера «Квота продаж» будет по умолчанию возвращать значение NULL для уровней ниже календарного квартала (хотя есть также вычисление в скрипте многомерных выражений, выделяющем значения вниз до уровня «Месяц»). Функцию ValidMeasure в вычисляемой мере можно использовать, чтобы мера «Квота продаж» вела себя, как если бы свойство IgnoreUnrelatedDimensions имело значение True и заставляло бы меру «Квота продаж» показывать значение текущего календарного квартала.  
  
```  
WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])  
SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,  
[Date].[Calendar].MEMBERS ON 1  
FROM [Adventure Works]  
```  
  
 Аналогичным образом группа мер «Sales Targets» вообще не имеет связей с измерением «Promotion», таким образом ниже уровня элемента «Все» любой иерархии в измерении «Promotion» группа мер будет возвращать значение NULL. Опять же это поведение можно изменить с помощью функции ValidMeasure:  
  
 `WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])`  
  
 `SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,`  
  
 `[Promotion].[Promotions].members ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
