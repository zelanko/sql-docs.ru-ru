---
title: Generate (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c7a6008129d6b0a4c59412428c31f6e5de625f1f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68005905"
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
  
 *Разделитель*  
 Допустимый разделитель в виде строкового выражения.  
  
## <a name="remarks"></a>Remarks  
 Если указан второй набор, функция **Generate** возвращает набор, сформированный путем применения кортежей во втором наборе к каждому кортежу в первом наборе, и последующего объединения результирующих наборов по объединению. Если указан параметр **ALL** , функция оставляет дубликаты в результирующем наборе.  
  
 Если строковое выражение указано, функция **Generate** возвращает строку, созданную путем вычисления указанного строкового выражения для каждого кортежа в первом наборе, и последующего сцепления результатов. При необходимости строка может содержать разделители, отделяющие результаты в объединенной строке друг от друга.  
  
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
  
 Наиболее распространенным практическим использованием класса **Generate** является вычисление сложного набора, например TopCount, над набором элементов. Запрос в следующем примере показывает 10 лучших продуктов для каждого значения Calendar Year по строкам:  
  
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
  
 Обратите внимание, что для каждого года отображается другое 10 лучших, а для получения этого результата используется метод **Generate** . Простое перекрестное соединение таблицы Calendar Year и набора 10 лучших продуктов покажет 10 лучших продуктов за весь период времени с повтором для каждого года, как показано в следующем примере:  
  
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
  
### <a name="string"></a>Строка  
 В следующем примере показано использование **Generate** для возврата строки:  
  
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
>  Эта форма функции **Generate** может быть полезной при отладке вычислений, так как она позволяет возвращать строку, в которой отображаются имена всех элементов в наборе. Это может быть проще для чтения, чем в определенном МНОГОМЕРном представлении набора, возвращаемого функцией [SetToStr &#40;многомерных выражений&#41;](../mdx/settostr-mdx.md) .  
  
## <a name="see-also"></a>См. также:  
 [Справочник по функциям многомерных выражений (многомерные выражения)](../mdx/mdx-function-reference-mdx.md)  
  
  
