---
title: Определяемые пользователем свойства элементов (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ba34243609b796eef635fc3b55cd99ef4f225638
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097364"
---
# <a name="user-defined-member-properties-mdx"></a>Пользовательские свойства элементов (многомерные выражения)
  Определяемые пользователем свойства элементов можно добавить к конкретному именованному уровню измерения в виде связей атрибутов. Невозможно добавить определенных пользователем свойств элементов `(All)` уровня иерархии или в саму иерархию.  
  
## <a name="creating-user-defined-member-properties"></a>Создание определяемых пользователем  свойств элементов  
 Определяемые пользователем свойства элементов можно добавлять в серверные измерения или кубы при помощи пользовательского интерфейса или программно.  
  
-   Для добавления определяемых пользователем свойств элементов через пользовательский интерфейс служит конструктор измерений в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделе [Определение связей атрибутов](../attribute-relationships-define.md).  
  
-   Для программного создания определяемых пользователем свойств элементов приложение может использовать либо объекты AMO, либо комбинацию XML для аналитики и языка ASSL. Дополнительные сведения см. в разделе [Связи атрибутов](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Извлечение определяемых пользователем свойств элементов  
 Можно извлечь с помощью свойства определяемого пользователем элемента `PROPERTIES` ключевое слово или [свойства](/sql/mdx/properties-mdx) функции.  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Получение определяемых пользователем свойств элементов с помощью ключевого слова PROPERTIES  
 Для получения определяемых пользователем свойств элементов применяется практически такой же синтаксис, как и при обращении к внутренним свойствам элементов.  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 `PROPERTIES` Ключевое слово указывается после выражения набора в определении оси. Например, в следующем Многомерном запросе `PROPERTIES` ключевое слово `List Price` и `Dealer Price` определенных пользователем свойств элементов находится после выражения набора, определяющего продукты, проданные в январе:  
  
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
 В качестве альтернативы к пользовательским свойствам элементов можно обращаться при помощи функции `Properties`. Например, следующий запрос многомерных Выражений использует `WITH` ключевое слово, чтобы создать вычисляемый элемент, состоящий из `List Price` свойство элемента:  
  
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
 [Использование свойств элементов &#40;многомерных Выражений&#41;](mdx-member-properties.md)   
 [Свойства &#40;многомерных Выражений&#41;](/sql/mdx/properties-mdx)  
  
  
