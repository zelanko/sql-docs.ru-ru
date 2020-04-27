---
title: Указание содержимого оси среза (многомерные выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- filtering data [MDX]
ms.assetid: c56b0a70-cdec-427f-990e-425290344e7d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 12e2d2f543694a1da418f5e8eb4b900eaa123d97
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074061"
---
# <a name="specifying-the-contents-of-a-slicer-axis-mdx"></a>Определение содержимого оси среза (многомерные выражения)
  Ось среза фильтрует данные, возвращаемые инструкцией многомерных выражений SELECT. При этом возвращаются только данные, пересекающиеся с заданными элементами. Может рассматриваться как дополнительная невидимая ось в запросе. Ось среза определяется в предложении WHERE инструкции многомерных выражений SELECT.  
  
## <a name="slicer-axis-syntax"></a>Синтаксис определения оси среза  
 Для явного определения оси среза используется следующий синтаксис в инструкции многомерных выражений `<SELECT slicer axis clause>` .  
  
```  
<SELECT slicer axis clause> ::=  WHERE Set_Expression  
```  
  
 В приведенном синтаксисе определения оси среза аргумент `Set_Expression` может принимать либо кортежное выражение, интерпретируемое как набор при вычислении предложения, либо выражение набора. Если задано выражение набора, язык многомерных выражений пытается вычислить набор с использованием статистического вычисления по результирующим ячейкам в каждом кортеже набора. Иными словами, используется функция [Aggregate](/sql/mdx/aggregate-mdx) для набора, при этом каждая мера статистически обрабатывается с помощью связанной статистической функции. Кроме того, если выражение набора нельзя выразить в виде перекрестного соединения элементов иерархии атрибутов, при вычислении в языке многомерных выражений ячейки, находящиеся за пределами выражения набора, с помощью которого определена ось среза, интерпретируются как имеющие значения NULL.  
  
> [!IMPORTANT]  
>  В отличие от предложения WHERE в SQL, в котором предложение WHERE инструкции MDX SELECT напрямую не выполняет фильтрацию результатов запросов по оси строк. Для фильтрации данных, отображаемых по оси строк или столбцов запроса, можно использовать различные функции MDX, например FILTER, NONEMPTY и TOPCOUNT.  
  
### <a name="implicit-slicer-axis"></a>Неявная ось среза  
 Если элемент иерархии в кубе не включен явно в ось запроса, элемент по умолчанию этой иерархии неявно включается в ось среза. Дополнительные сведения об элементах по умолчанию см. в разделе [Определение элемента по умолчанию](../attribute-properties-define-a-default-member.md).  
  
## <a name="examples"></a>Примеры  
 Следующий запрос не содержит предложения WHERE и возвращает значение меры Internet Sales Amount для всех календарных лет:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
 Добавление предложения WHERE, которое выполняется следующим образом:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States])  
  
```  
  
 не изменяет возвращаемые результаты запроса по оси строк или столбцов, а изменяет значения, возвращаемые для каждой ячейки. В этом примере запрос отсекается таким образом, чтобы результаты содержали значение меры Internet Sales Amount для всех календарных лет только для клиентов, проживающих в США. К предложению WHERE можно добавить различные элементы из разных иерархий. В следующем запросе отображается значение Internet Sales Amount для всех календарных лет для клиентов, проживающих в США, которые приобрели продукты категории Bikes:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States], [Product].[Category].&[1])  
```  
  
 При включении нескольких элементов из одной иерархии необходимо включить набор в предложение WHERE. Например, в следующем запросе отображается значение Internet Sales Amount для всех календарных лет для клиентов, которые приобрели продукты категории Bikes и проживают в США или Великобритании:  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE(  
{[Customer].[Customer Geography].[Country].&[United States]  
, [Customer].[Customer Geography].[Country].&[United Kingdom]}  
, [Product].[Category].&[1])  
  
```  
  
 Как упоминалось выше, при использовании набора в предложении WHERE значения для всех элементов набора будут агрегированы. В этом случае в каждой ячейке запроса будут показаны агрегированные значения для США и Великобритании.  
  
  
