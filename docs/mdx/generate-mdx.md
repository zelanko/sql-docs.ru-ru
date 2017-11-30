---
title: "Generate (многомерные Выражения) | Документы Microsoft"
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
f1_keywords: GENERATE
dev_langs: kbMDX
helpviewer_keywords: Generate function
ms.assetid: 696a229d-c2f1-47b7-9dca-7b0a6b547d9b
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4ef13a4355c73458023c7d11663587a771d71c23
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="generate-mdx"></a>Generate (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Применяет набор к каждому элементу другого набора и соединяет результирующие наборы. В качестве альтернативы эта функция также возвращает сцепленную строку, созданную путем вычисления строкового выражения по набору.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set expression syntax  
Generate( Set_Expression1 ,  Set_Expression2 [ , ALL ]  )  
  
String expression syntax  
Generate( Set_Expression1 ,  String_Expression [ ,Delimiter ]  )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *String_Expression*  
 Допустимое строковое выражение, обычно обозначающее имя текущего элемента (CurrentMember.Name) каждого кортежа в указанном наборе.  
  
 *Разделитель*  
 Допустимый разделитель в виде строкового выражения.  
  
## <a name="remarks"></a>Замечания  
 Если указан второй набор, **формирования** функция возвращает набор, сформированный путем применения кортежей второго набора к каждому кортежу первого набора*,* и последующего объединения результирующих наборов. Если **все** указано, функция сохраняет повторяющиеся значения в результирующем наборе.  
  
 Если строковое выражение указано, **формирования** функция возвращает строку, сформированную путем вычисления выражения указанную строку для каждого кортежа первого набора*,* и последующим объединением результатов. При необходимости строка может содержать разделители, отделяющие результаты в объединенной строке друг от друга.  
  
## <a name="examples"></a>Примеры  
  
### <a name="set"></a>Присвойте параметру  
 В следующем примере запрос возвращает набор, содержащий меру Measure Internet Sales четыре раза, так как набор [Date].[Calendar Year].[Calendar Year].MEMBERS состоит из четырех элементов:  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]}, ALL)  
ON 0  
FROM [Adventure Works]  
```  
  
 После удаления атрибута ALL из запроса мера Internet Sales Amount возвращается только один раз:  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]})  
ON 0  
FROM [Adventure Works]  
```  
  
 Наиболее распространенное Практическое применение из **формирования** вычисление сложных выражений набора, например TopCount, по набору элементов. Запрос в следующем примере показывает 10 лучших продуктов для каждого значения Calendar Year по строкам:  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS  
, TOPCOUNT(  
[Date].[Calendar Year].CURRENTMEMBER  
*  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount]))  
ON 1  
FROM [Adventure Works]  
```  
  
 Обратите внимание, что для каждого года и что отображается 10 разных лучших использование **формирования** это единственный способ получить этот результат. Простое перекрестное соединение таблицы Calendar Year и набора 10 лучших продуктов покажет 10 лучших продуктов за весь период времени с повтором для каждого года, как показано в следующем примере:  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS  
*   
TOPCOUNT(  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount])  
ON 1  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>Строковые значения  
 В следующем примере показано использование **формирования** для возврата строки:  
  
```  
WITH   
MEMBER MEASURES.GENERATESTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME)  
MEMBER MEASURES.GENERATEDELIMITEDSTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME, " AND ")  
SELECT   
{MEASURES.GENERATESTRINGDEMO, MEASURES.GENERATEDELIMITEDSTRINGDEMO}  
ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  В этой форме **формирования** функция может оказаться полезной при отладке вычислений, как она позволяет вернуть строку, отображаются имена всех элементов в наборе. Это может оказаться легче читать, чем строгое представление многомерного Выражения набора, [SetToStr &#40; Многомерные Выражения &#41; ](../mdx/settostr-mdx.md) возврата функцией.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
