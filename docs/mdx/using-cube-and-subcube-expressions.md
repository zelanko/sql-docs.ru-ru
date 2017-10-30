---
title: "С помощью куба и вложенного куба выражений | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- subcubes [MDX]
- cubes [Analysis Services], MDX
- CURRENTCUBE keyword
- expressions [MDX], subcubes
- expressions [MDX], cubes
ms.assetid: 95ae034d-8f88-4820-91c6-205ec424e119
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 71ba6c7d7d5040481ea13d80a160fc19c0704c10
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="using-cube-and-subcube-expressions"></a>Выражения куба и вложенного куба
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выражения куба и вложенного куба используются в инструкциях многомерных выражений для определения данных, управления данными и извлечения данных из куба или вложенного куба.  
  
## <a name="cube-expressions"></a>Выражения куба  
 Выражение куба содержит идентификатор куба или ключевое слово CURRENTCUBE и поэтому может быть только простым выражением. Ключевое слово CURRENTCUBE позволяет ссылаться на контекст текущего куба, не указывая его идентификатор в явном виде.  
  
 Идентификатор куба представлен как *Cube_Name* в форме БЭКУСА нотации описаниях инструкций многомерных Выражений.  
  
 Выражения куба могут встречаться в нескольких местах. В инструкции SELECT многомерных выражений они указывают куб, из которого должны быть получены данные. В следующем примере запроса выражение [Adventure Works] ссылается на куб с этим именем:  
  
 `SELECT [Measures].[Internet Sales Amount] ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 В инструкции CREATE MEMBER выражение куба задает куб, в котором появится создаваемый вычисляемый элемент. В следующем примере инструкция создает вычисляемую меру в измерения мер куба Adventure Works:  
  
 `CREATE MEMBER [Adventure Works].[Measures].[Test] AS 1`  
  
 Если инструкция CREATE MEMBER используется в скрипте многомерных выражений, то имя куба может быть заменено ключевым словом CURRENTCUBE, так как куб, в котором будет создан вычисляемый элемент, должен совпадать с кубом, которому принадлежит скрипт многомерных выражений, как показано в следующем примере:  
  
 `CREATE MEMBER CURRENTCUBE.[Measures].[Test] AS 1;`  
  
 В результате становится проще копировать и вставлять определения вычисляемого элемента из одного куба в другой, так как имя куба не задано жестко.  
  
## <a name="subcube-expressions"></a>Выражения вложенного куба  
 Выражение вложенного куба может содержать идентификатор вложенного куба или инструкцию многомерных выражений, возвращающую вложенный куб. Если выражение вложенного куба содержит идентификатор вложенного куба, то это будет простое выражение. Если оно содержит инструкцию многомерных выражений, которая возвращает вложенный куб, то это сложная инструкция. Например, инструкция многомерных выражений SELECT возвращает вложенный куб и может использоваться там, где допустимы выражения вложенного куба, как показано в следующем примере:  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Date].[Calendar Year].MEMBERS ON ROWS`  
  
 `FROM`  
  
 `(SELECT [Measures].[Internet Sales Amount] ON COLUMNS,`  
  
 `[Date].[Calendar Year].&[2004] ON ROWS`  
  
 `FROM [Adventure Works])`  
  
 Такое использование инструкции SELECT в предложении FROM называется также подзапросом выборки.  
  
 Другой типичный скрипт, где встречаются выражения вложенного куба, — это назначения с указанием области в скрипте многомерных выражений. В следующем примере используется инструкция SCOPE, чтобы ограничить назначение вложенным кубом, состоящим из [Measures].[Internet Sales Amount]:  
  
 `SCOPE([Measures].[Internet Sales Amount]);`  
  
 `This=1;`  
  
 `END SCOPE;`  
  
 Идентификатор вложенного куба представлен как *Subcube_Name*. в описаниях инструкций многомерных выражений в форме Бэкуса-Наура.  
  
## <a name="see-also"></a>См. также:  
 [Базовый запрос многомерных Выражений &#40; Многомерные Выражения &#41;](../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)   
 [Построение вложенных кубов в многомерных Выражений &#40; Многомерные Выражения &#41;](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md)   
 [CREATE SUBCUBE, инструкция #40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-subcube.md)   
 [Выражения &#40; Многомерные Выражения &#41;](../mdx/expressions-mdx.md)   
 [Инструкция SCOPE &#40; Многомерные Выражения &#41;](../mdx/mdx-scripting-scope.md)  
  
  

