---
title: "Пользовательские свойства элементов (многомерные выражения) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "нестандартные свойства элементов [многомерные выражения]"
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Пользовательские свойства элементов (многомерные выражения)
  Определяемые пользователем свойства элементов можно добавить к конкретному именованному уровню измерения в виде связей атрибутов. Определяемые пользователем свойства элементов нельзя добавлять к уровню иерархии **(All)** или в саму иерархию.  
  
## Создание определяемых пользователем  свойств элементов  
 Определяемые пользователем свойства элементов можно добавлять в серверные измерения или кубы при помощи пользовательского интерфейса или программно.  
  
-   Для добавления определяемых пользователем свойств элементов через пользовательский интерфейс служит конструктор измерений в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделе [Определение связей атрибутов](../../../analysis-services/multidimensional-models/define-attribute-relationships.md).  
  
-   Для программного создания определяемых пользователем свойств элементов приложение может использовать либо объекты AMO, либо комбинацию XML для аналитики и языка ASSL. Дополнительные сведения см. в разделе [Связи атрибутов](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## Извлечение определяемых пользователем свойств элементов  
 Для извлечения определяемых пользователем свойств элементов используется ключевое слово **PROPERTIES** или функция [Properties](../../../mdx/properties-mdx.md).  
  
### Получение определяемых пользователем свойств элементов с помощью ключевого слова PROPERTIES  
 Для получения определяемых пользователем свойств элементов применяется практически такой же синтаксис, как и при обращении к внутренним свойствам элементов.  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 Ключевое слово **PROPERTIES** указывается после выражения набора в определении оси. Например, в следующем многомерном запросе, извлекающем определяемые пользователем свойства `List Price` и `Dealer Price`, ключевое слово **PROPERTIES** находится после выражения набора, определяющего продукты, проданные в январе.  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### Получение определяемых пользователем свойств элементов с помощью функции Properties  
 В качестве альтернативы к пользовательским свойствам элементов можно обращаться при помощи функции **Properties** . Например, в следующем многомерном запросе ключевое слово **WITH** применяется для создания вычисляемого элемента, состоящего из свойства элемента `List Price`.  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 Дополнительные сведения о создании вычисляемых элементов см. в разделе [Создание вычисляемых элементов в многомерных выражениях (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/building-calculated-members-in-mdx-mdx.md).  
  
## См. также  
 [Использование свойств элементов (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/using-member-properties-mdx.md)   
 [Properties (многомерные выражения)](../../../mdx/properties-mdx.md)  
  
  