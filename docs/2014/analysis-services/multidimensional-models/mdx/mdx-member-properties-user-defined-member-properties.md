---
title: Определяемые пользователем свойства элементов (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ead5a45bf163ca4e7998c30ab5c83f94cca9075b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074262"
---
# <a name="user-defined-member-properties-mdx"></a>Пользовательские свойства элементов (многомерные выражения)
  Определяемые пользователем свойства элементов можно добавить к конкретному именованному уровню измерения в виде связей атрибутов. Определяемые пользователем свойства элементов нельзя добавлять к уровню иерархии `(All)` или в саму иерархию.  
  
## <a name="creating-user-defined-member-properties"></a>Создание определяемых пользователем  свойств элементов  
 Определяемые пользователем свойства элементов можно добавлять в серверные измерения или кубы при помощи пользовательского интерфейса или программно.  
  
-   Для добавления определяемых пользователем свойств элементов через пользовательский интерфейс служит конструктор измерений в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделе [Определение связей атрибутов](../attribute-relationships-define.md).  
  
-   Для программного создания определяемых пользователем свойств элементов приложение может использовать либо объекты AMO, либо комбинацию XML для аналитики и языка ASSL. Дополнительные сведения см. в разделе [Связи атрибутов](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Извлечение определяемых пользователем свойств элементов  
 Можно извлечь с помощью свойства определяемый пользователем элемент `PROPERTIES` ключевое слово или [свойства](/sql/mdx/properties-mdx) функции.  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Получение определяемых пользователем свойств элементов с помощью ключевого слова PROPERTIES  
 Для получения определяемых пользователем свойств элементов применяется практически такой же синтаксис, как и при обращении к внутренним свойствам элементов.  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 Ключевое слово `PROPERTIES` указывается после выражения набора в определении оси. Например, в следующем многомерном запросе, извлекающем определяемых пользователем свойства `List Price` и `Dealer Price`, ключевое слово `PROPERTIES` находится после выражения набора, определяющего продукты, проданные в январе.  
  
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
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>Получение определяемых пользователем свойств элементов с помощью функции Properties  
 В качестве альтернативы к пользовательским свойствам элементов можно обращаться при помощи функции `Properties`. Например, в следующем многомерном запросе ключевое слово `WITH` применяется для создания вычисляемого элемента, состоящего из свойства элемента `List Price`.  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 Дополнительные сведения о создании вычисляемых элементов см. в разделе [Создание вычисляемых элементов в многомерных выражениях (многомерные выражения)](mdx-calculated-members-building-calculated-members.md).  
  
## <a name="see-also"></a>См. также  
 [Использование свойств элементов (многомерные выражения)](mdx-member-properties.md)   
 [Properties (многомерные выражения)](/sql/mdx/properties-mdx)  
  
  
