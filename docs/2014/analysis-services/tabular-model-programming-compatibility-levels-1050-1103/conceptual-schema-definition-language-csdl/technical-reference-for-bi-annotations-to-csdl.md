---
title: Технический справочник по заметки бизнес-Аналитики для языка CSDL | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 63b3e069-6ba5-474e-b769-47b7cc87b7dd
caps.latest.revision: 15
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 27ed1339d64dd3c4035288a96b31ae163a304733
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097807"
---
# <a name="technical-reference-for-bi-annotations-to-csdl"></a>Технический справочник по аннотациям бизнес-аналитики для языка CSDL
  В этом разделе приведен список элементов, атрибутов и свойств, используемых в CSDL, которые представляют табличные модели [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Некоторые элементы новые; другие помечены или расширены для поддержки построения моделей бизнес-аналитики.  
  
 Обзор табличной модели и как сущности, связи и формулы представлены на языке CSDL см. в разделе [заметки языка CSDL для бизнес-аналитики &#40;CSDLBI&#41;](../csdl-annotations-for-business-intelligence-csdlbi.md).  
  
## <a name="extended-csdl-elements-complex-types"></a>Расширенные элементы языка CSDL: Сложные типы  
 Следующие элементы языка CSDL добавлены или расширены для поддержки моделей данных бизнес-аналитики, как табличных, так и многомерных.  
  
-   [Элемент AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)  
  
-   [Элемент BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [Элемент DefaultDetails &#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md)  
  
-   [Элемент DisplayKey &#40;CSDLBI&#41;](displaykey-element-csdlbi.md)  
  
-   [Элемент EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)  
  
-   [Элемент EntitySet &#40;CSDLBI&#41;](entityset-element-csdlbi.md)  
  
-   [Элемент EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)  
  
-   [Элемент Hierarchy &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)  
  
-   [Элемент KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
-   [Элемент KpiGoal &#40;CSDLBI&#41;](kpigoal-element-csdlbi.md)  
  
-   [Элемент KpiStatus &#40;CSDLBI&#41;](kpistatus-element-csdlbi.md)  
  
-   [Уровень элемента &#40;CSDLBI&#41;](level-element-csdlbi.md)  
  
-   [Элемент измерения &#40;CSDLBI&#41;](measure-element-csdlbi.md)  
  
-   [Элемент member &#40;CSDLBI&#41;](member-element-csdlbi.md)  
  
-   [Элемент MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md)  
  
-   [Элемент NavigationProperty &#40;CSDLBI&#41;](navigationproperty-element-csdlbi.md)  
  
-   [Элемент свойства &#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [Элемент PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)  
  
## <a name="simple-type-and-subtypes"></a>Простой тип и подтипы  
 В следующей таблице приведены некоторые простые типы и некоторые малые сложные типы, входящие в определения сложных типов, перечисленных выше. Документация для каждого простого типа или подтипа, названного в левом столбце, содержится в родительских элементах, названных в правом столбце.  
  
|Простой тип|Есть в разделе|  
|-----------------|--------------------|  
|Выравнивание|[Элемент BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|CompareOptions|[Элемент EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|Содержание|[Элемент EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)|  
|ContextualNameRule|[Элемент member &#40;CSDLBI&#41;](member-element-csdlbi.md)|  
|DefaultAggregationFunction|[Элемент свойства &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|DirectQueryMode|[Элемент EntityContainer &#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|GroupingBehavior|[Элемент свойства &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|MemberRefs|[Элемент MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md)|  
|PropertyRefs|[Элемент PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)|  
|SortDirection|[Элемент BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|Состояние|[Элемент AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)|  
|Стабильность|[Элемент свойства &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|SortDirection|[Элемент BaseProperty &#40;CSDLBI&#41;](property-element-csdlbi.md)|  
  
## <a name="see-also"></a>См. также  
 [Основные понятия CSDLBI](../csdlbi-concepts.md)  
  
  