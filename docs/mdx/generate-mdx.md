---
title: Generate (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 222479dd03263f61a603e30202f2abf54307b0bc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740893"
---
# <a name="generate-mdx"></a>Generate (многомерные выражения)


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
  
 *разделитель*  
 Допустимый разделитель в виде строкового выражения.  
  
## <a name="remarks"></a>Примечания  
 Если указан второй набор, **формирования** функция возвращает набор, сформированный путем применения кортежей второго набора к каждому кортежу первого набора *,* и последующего объединения результирующих наборов. Если **все** указано, функция сохраняет повторяющиеся значения в результирующем наборе.  
  
 Если строковое выражение указано, **формирования** функция возвращает строку, сформированную путем вычисления выражения указанную строку для каждого кортежа первого набора *,* и последующим объединением результатов. При необходимости строка может содержать разделители, отделяющие результаты в объединенной строке друг от друга.  
  
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
  
### <a name="string"></a>String  
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
>  В этой форме **формирования** функция может оказаться полезной при отладке вычислений, как она позволяет вернуть строку, отображаются имена всех элементов в наборе. Это может оказаться легче читать, чем строгое представление многомерного Выражения набора, [SetToStr &#40;многомерных Выражений&#41; ](../mdx/settostr-mdx.md) возврата функцией.  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
