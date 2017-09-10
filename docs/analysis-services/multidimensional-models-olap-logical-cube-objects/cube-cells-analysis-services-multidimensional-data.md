---
title: "Куб ячейки (службы Analysis Services — многомерные данные) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7da5c513675b85a209e76da5787828eb31be24f8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="cube-cells-analysis-services---multidimensional-data"></a>Ячейки куба (службы Analysis Services — многомерные данные)
  Куб состоит из ячеек, организованных по группам мер и по измерениям. Ячейка представляет собой уникальное логическое пересечение элементов — по одному из каждого измерения в кубе. Например, куб, описываемый следующей диаграммой, содержит одну группу мер с двумя мерами, организованными вдоль трех измерений, названных «Источник», «Маршрут» и «Время».  
  
 ![Диаграмма куба, определяющая одну ячейку](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro5.gif "Диаграмма куба, определяющая одну ячейку")  
  
 Выделенная ячейка на этой диаграмме представляет собой пересечение следующих элементов:  
  
-   Элемента «воздух» измерения «Маршрут».  
  
-   Элемента «Африка» измерения «Источник».  
  
-   Элемента «4-й квартал» измерения «Время».  
  
-   Мера «Посылки».  
  
## <a name="leaf-and-nonleaf-cells"></a>Конечные и неконечные ячейки  
 Значение для ячейки в кубе можно получить одним из нескольких способов. В предыдущем примере значение в ячейке можно непосредственно получить из таблицы фактов куба, поскольку все элементы, используемые для идентификации ячейки *конечных элементов*. Конечный элемент не имеет дочерних элементов с точки зрения иерархии и обычно ссылается на одну запись в таблице измерения. Этот вид ячейки называется *конечная ячейка*.  
  
 Однако ячейку также можно идентифицировать с помощью *неконечные элементы*. Неконечный элемент представляет собой элемент, имеющий один или несколько дочерних элементов. В этом случае значение ячейки обычно получается из статистического вычисления дочерних элементов, связанных с неконечным элементом. Например, пересечение следующих элементов и измерений относится к ячейке, значение предоставляется статистическим вычислением:  
  
-   Элемента «воздух» измерения «Маршрут».  
  
-   Элемента «Африка» измерения «Источник».  
  
-   Элемента «2-е полугодие» измерения «Время».  
  
-   Элемента «Посылки».  
  
 Элемент «2-е полугодие» измерения «Время» является неконечным элементом. Следовательно, все связанные с ним значения должны быть статистическими, как показано в следующей диаграмме.  
  
 ![ячейки третьего и четвертого квартала элемента второго полугодия](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro6.gif "третьего и четвертого квартала ячеек элемента второго полугодия")  
  
 Исходя из того, что агрегаты для элементов «3-й квартал» и «4-й квартал» получены суммированием, значение заданной ячейки равно 400, то есть сумме всех конечных ячеек, выделенных на предыдущей диаграмме. Поскольку значение ячейки является производным из статистического вычисления других ячеек, заданная ячейка считается *неконечной ячейки*.  
  
 Значения ячеек, производные для элементов, использующих пользовательские свертки и группы элементов, а также пользовательские элементы, обрабатываются аналогичным образом. Однако значения ячеек, производные для вычисляемых элементов, полностью основаны на многомерных выражениях, используемых для определения вычисляемого элемента; в отдельных случаях реальные данные ячеек могут не использоваться. Дополнительные сведения см. в разделе [пользовательские операторы свертки в измерениях родители-потомки](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [Определение формулы пользовательских элементов](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md), и [вычисления](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md).  
  
## <a name="empty-cells"></a>Пустые ячейки  
 В кубе не каждая ячейка обязательно содержит значение: могут существовать пересечения, не имеющие данных. Такие пересечения, называемые пустыми ячейками, возникают в кубах достаточно часто, поскольку не каждое пересечение атрибута измерения, соотносимое с мерой в кубе, содержит соответствующую запись в таблице фактов. Отношение пустых ячеек в кубе к общему количеству ячеек в кубе часто называется *степень незаполненности* куба.  
  
 Например, структура куба, показанная на следующей диаграмме, аналогична другим примерам в этом разделе. Однако в этом примере отсутствовали воздушные поставки в Африку в третьем квартале или в Австралию в четвертом квартале. В таблице фактов отсутствуют данные, поддерживающие пересечения этих измерений и мер, поэтому ячейки в этих пересечениях являются пустыми.  
  
 ![Диаграмма куба, определяющая пустые ячейки](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-cubeintro7.gif "Диаграмма куба, определяющая пустые ячейки")  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], пустая ячейка представляет ячейку с особыми свойствами. Поскольку пустые ячейки могут искажать результаты перекрестных соединений, подсчетов и т. п., многие функции многомерных выражений обеспечивают возможность пропуска пустых ячеек для целей вычислений. Дополнительные сведения см. в разделе [многомерных выражений &#40; Многомерные Выражения &#41; Справочник по](../../mdx/multidimensional-expressions-mdx-reference.md), и [ключевые понятия многомерных Выражений &#40; Службы Analysis Services &#41; ](../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="security"></a>безопасность  
 Доступ к данным ячеек в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] осуществляется на уровне ролей и может точно управляться с помощью многомерных выражений. Дополнительные сведения см. в разделе [предоставление настраиваемого доступа к измерению данных &#40; Службы Analysis Services &#41; ](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md), и [предоставление настраиваемого доступа к ячейке данных &#40; Службы Analysis Services &#41; ](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Хранилище куба &#40; Analysis Services — многомерные данные &#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)   
 [Агрегаты и статистические схемы](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
