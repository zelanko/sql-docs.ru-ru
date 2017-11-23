---
title: "Выражения (MDX) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- identifiers [MDX]
- expressions [MDX]
- expressions [MDX], about expressions
- MDX [Analysis Services], expressions
- Multidimensional Expressions [Analysis Services], expressions
ms.assetid: e20c34bc-30fa-4ac5-b896-9d4c9925ef59
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 8474c90f0cfbcd8ae0aabce14623c427106298a5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="expressions-mdx"></a>Выражения (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выражение представляет собой сочетание идентификаторов, значений и операторов, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] можно вычислить для получения результата. Данные могут использоваться в разных местах для доступа и изменения данных. Например, выражение можно использовать как часть данных, извлекаемых в запросе, либо как условие поиска для отбора данных, отвечающих набору критериев.  
  
## <a name="simple-and-complex-expressions"></a>Простые и сложные выражения  
 Многомерные выражения могут быть простыми или сложными.  
  
 Простыми выражениями являются следующие выражения:  
  
 Константа  
 Константа в языке многомерных выражений — это символ, представляющий отдельное конкретное значение. Константами могут быть представлены строковые, числовые и календарные значения. В отличие от числовых констант, строковые и календарные константы заключаются в одиночные кавычки (').  
  
 Скалярные функции  
 Скалярная функция в языке многомерных выражений возвращает единственное значение в контексте вычислений. Это отличие важно для понимания того, как в языке многомерных выражений разрешаются скалярные функции, поскольку большинство выражений, инструкций и скриптов многомерных выражений вычисляется не по одному элементу данных, а итерационно по группе звеньев данных — ячеек или элементов. Однако при вычислении скалярной функции функция обычно анализирует одно звено данных.  
  
 Идентификаторы объектов  
 Язык многомерных выражений является объектно-ориентированным благодаря природе многомерных данных. Идентификаторы объектов в нем рассматриваются как простые выражения. Дополнительные сведения об идентификаторах см. в разделе [идентификаторы &#40; Многомерные Выражения &#41; ](../mdx/identifiers-mdx.md).  
  
 Сложные выражения строятся из сочетания данных конструкций, соединенных операторами.  
  
## <a name="expression-results"></a>Результаты выражения  
 Для простых выражений, состоящих из одной константы, переменной, скалярной функции или имени столбца, в качестве типа данных, параметров сортировки, числа разрядов, точности и значения выражения используются тип данных, параметры сортировки, число разрядов, точность и значение элемента, на который они ссылаются. Поскольку язык многомерных выражений непосредственно поддерживает только тип данных OLE VARIANT, при работе с простыми выражениями приведение типа данных не происходит.  
  
 Для сложных выражений приведение типа данных происходит при использовании двух и более простых выражений с различными типами данных.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В следующем запросе показаны примеры вычисляемых мер, определения которых являются простыми выражениями:  
  
 `WITH`  
  
 `MEMBER MEASURES.CONSTANTVALUE AS 1`  
  
 `MEMBER MEASURES.SCALARFUNCTION AS [Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.OBJECTIDENTIFIER AS [Measures].[Internet Sales Amount]`  
  
 `SELECT {MEASURES.CONSTANTVALUE,MEASURES.SCALARFUNCTION,MEASURES.OBJECTIDENTIFIER } ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Выражение может также быть вычислением, например `[Measures].[Discount Amount] * 1.5`. В следующем примере демонстрируется использование вычисления для определения элемента в инструкции многомерных выражений SELECT:  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Использование выражений куба и вложенного куба](../mdx/using-cube-and-subcube-expressions.md)|Выражения куба и вложенного куба.|  
|[Использование выражений измерений](../mdx/using-dimension-expressions.md)|Выражения измерений.|  
|[Использование выражений элементов](../mdx/using-member-expressions.md)|Выражения элементов.|  
|[Использование выражений кортежей](../mdx/using-tuple-expressions.md)|Выражения кортежей.|  
|[Использование выражений наборов](../mdx/using-set-expressions.md)|Выражения наборов.|  
|[Использование скалярных выражений](../mdx/using-scalar-expressions.md)|Скалярные выражения.|  
|[Работа с пустыми значениями](../mdx/working-with-empty-values.md)|Пустые значения и способы их обработки.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по языку многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-language-reference-mdx.md)   
 [Основные принципы запросов многомерных Выражений &#40; Службы Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
