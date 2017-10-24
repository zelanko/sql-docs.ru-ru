---
title: "Связи атрибутов | Документы Microsoft"
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
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f2fc6db2abf6c23ae4b265255b2cc9d191632e7f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="attribute-relationships"></a>Связи атрибутов
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], атрибуты измерения всегда связаны прямо или косвенно с ключевым атрибутом. Когда измерение определяется по схеме «звезда», где все атрибуты измерения наследуются из одной реляционной таблицы, то связи между ключевыми и не ключевыми атрибутами определяются автоматически. Когда измерение определяется по схеме «снежинка», где атрибуты измерения наследуются от разных реляционных таблиц, связи атрибутов автоматически определяются следующим образом:  
  
-   Между ключевым атрибутом и каждым не ключевым атрибутом, привязанным к столбцу главной таблицы измерения.  
  
-   Между ключевым атрибутом и атрибутами, привязанными к внешнему ключу вспомогательной таблицы, которая связывает таблицы базового измерения.  
  
-   Между атрибутом, привязанным к внешнему ключу вспомогательной таблицы, и каждым не ключевым атрибутом, привязанным к столбцам вспомогательной таблицы.  
  
 Однако по ряду причин может понадобиться изменить связи атрибутов, определенные по умолчанию, например чтобы определить естественную иерархию, пользовательский порядок сортировки или степень гранулярности измерения на основе неключевого атрибута. Дополнительные сведения см. в разделе [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md).  
  
> [!NOTE]  
>  Связи атрибутов называются в языке многомерных выражений свойствами элементов.  
  
## <a name="natural-hierarchy-relationships"></a>Связи естественной иерархии  
 Иерархия является естественной, когда каждый атрибут пользовательской иерархии имеет связь типа «один ко многим» с атрибутом, находящимся непосредственно под ним. Допустим, измерение Customer основано на реляционной исходной таблице, содержащей восемь столбцов:  
  
-   CustomerKey  
  
-   CustomerName  
  
-   Возраст  
  
-   Пол  
  
-   Email  
  
-   Город  
  
-   Страна  
  
-   Регион  
  
 Соответствующее измерение служб Analysis Services содержит семь атрибутов:  
  
-   Customer (основанное на CustomerKey и CustomerName)  
  
-   Age, Gender, Email, City, Region, Country  
  
 Представляющие естественные иерархии связи создают, связывая атрибуты текущего и нижестоящего уровня. В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] это свойство определяет естественную иерархию и возможное статистическое вычисление. В измерении Customer естественная иерархия применяется для атрибутов Country, Region, City и Customer. Естественная иерархия атрибутов `{Country, Region, City, Customer}` описывается добавлением следующих связей атрибутов:  
  
-   атрибут Country как связь атрибутов к атрибуту Region;  
  
-   атрибут Region как связь атрибутов к атрибуту City;  
  
-   атрибут City как связь атрибутов к атрибуту Customer.  
  
 Для перемещения по данным куба, можно также создать пользовательскую иерархию, не представленную естественной иерархией данных (называемый *нерегламентированные* или *reporting* иерархии). Например, пользовательская иерархия может быть создана на основе `{Age, Gender}`. Пользователи не смогут увидеть разницу в поведении, отличить эти иерархии, хотя естественная иерархия предоставляет преимущество благодаря скрытым от пользователя статистическим выражениям и структурам индексирования, которые отвечают за естественные связи в исходных данных.  
  
 **SourceAttribute** свойства уровня определяет, какой атрибут используется для описания уровня. **KeyColumns** атрибута определяет столбец в представлении источника данных, который является источником элементов. **NameColumn** атрибута можно указать на другой столбец имен для элементов.  
  
 Для определения уровня в пользовательской иерархии, с помощью [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], **конструктор измерений** можно выбрать атрибут измерения, столбец в таблице измерения или столбец из связанной таблицы, включенные в представление источника данных для куб. Дополнительные сведения о создании пользовательских иерархий см. в разделе [Create User-Defined иерархий](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md).  
  
 В службах Analysis Services о содержимом элементов измерения обычно делается предположение. Конечные элементы не имеют потомков и содержат данные, полученные непосредственно из основных источников данных. Неконечные элементы имеют потомков и содержат данные из статистических вычислений, рассчитанных по дочерним элементам. Значения на неконечных уровнях вычисляются на основе статистических вычислений над нижестоящими уровнями. Таким образом, когда **IsAggregatable** свойству **False** исходного атрибута для уровня, статистически вычисляемые атрибуты не должны быть добавлены вышестоящие уровни.  
  
## <a name="defining-an-attribute-relationship"></a>Определения связи атрибутов  
 При создании атрибута главное проверить, чтобы атрибут, на который ссылается связь, имел не более одного значения для каждого элемента атрибута, к которому он принадлежит. Например, если определить связь между атрибутами City и State, каждый город будет принадлежать одному штату.  
  
## <a name="attribute-relationship-queries"></a>Запросы связи атрибутов  
 Можно использовать запросы многомерных Выражений для извлечения данных из связи атрибутов в форме свойств элементов с **свойства** ключевое слово многомерных выражений **ВЫБЕРИТЕ** инструкции. Дополнительные сведения об использовании многомерных Выражений для получения свойств элементов см. в разделе [свойства элементов с помощью &#40; Многомерные Выражения &#41; ](../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [Пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Свойства пользовательской иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  

