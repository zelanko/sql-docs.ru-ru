---
title: Использование свойств элементов (многомерные Выражения) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7876031fddb74115fd1fe412f4c8a9d9aacdb054
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53216043"
---
# <a name="mdx-member-properties"></a>Свойства элементов многомерных выражений
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Свойства элементов включают основные сведения о каждом элементе каждого кортежа. К таким основным сведениям относятся имя элемента, родительский уровень, число потомков и т. д. Свойства элемента доступны всем элементам данного уровня. С точки зрения организации свойства элемента рассматриваются как организованные по измерениям данные, хранимые в одном измерении.  
  
> [!NOTE]
>  В [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]свойства элемента рассматриваются как связь атрибутов. Дополнительные сведения см. в разделе [Связи атрибутов](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Существуют *внутренние* и *пользовательские*свойства:  
  
 Внутренние свойства элементов  
 Все элементы поддерживают внутренние свойства элементов, такие как форматированное значение элемента, а измерения и уровни обеспечивают еще и дополнительные внутренние свойства измерения и уровня элементов, например идентификатор элемента.  
  
 Дополнительные сведения см. в разделе [Внутренние свойства элементов (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md).  
  
 Пользовательские свойства элементов  
 С элементами часто связаны дополнительные свойства. Например, каждому товару уровня «Продукты» могут быть присвоены свойства SKU, SRP, Weight и Volume. Эти свойства не являются элементами, они содержат дополнительные сведения об элементах на уровне «Продукты».  
  
 Дополнительные сведения см. в разделе [Пользовательские свойства элементов (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
 Как внутренние, так и пользовательские свойства элементов можно извлечь с использованием ключевого слова **PROPERTIES** или функции [Properties](../../../mdx/properties-mdx.md).  
  
## <a name="using-the-properties-keyword"></a>Использование ключевого слова PROPERTIES  
 Ключевое слово **PROPERTIES** указывает свойства элементов, которые будут использоваться для данной оси измерения. Ключевое слово **PROPERTIES** находится в предложении `<axis specification>` инструкции многомерных выражений [SELECT](../../../mdx/mdx-data-manipulation-select.md) :  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 Предложение `<axis_specification>` содержит необязательное предложение `<dim_props>` , как видно в следующем синтаксисе:  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  Дополнительные сведения о значениях `<set>` и `<axis_name>` см. в разделе [Определение содержимого оси запроса (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
 Ключевое слово `<dim_props>` позволяет обратиться с запросом к свойствам измерения, уровня и элементов, используя ключевое слово **PROPERTIES** . Следующий синтаксис показывает формат предложения `<dim_props>` :  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 Синтаксическая конструкция `<property>` изменяется в зависимости от свойства, к которому обращен запрос.  
  
-   Чувствительным к контексту внутренним свойствам элементов должно предшествовать имя измерения или уровня. Однако нечувствительные к контексту внутренние свойства элементов не могут быть определены именем измерения или уровня. Дополнительные сведения об использовании ключевого слова **PROPERTIES** с внутренними свойствами элементов см. в разделе [Внутренние свойства элементов (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md).  
  
-   Заданным пользователем внутренним свойствам элемента должно предшествовать имя уровня, на котором они располагаются. Дополнительные сведения об использовании ключевого слова **PROPERTIES** с пользовательскими свойствами элементов см. в разделе [Пользовательские свойства элементов (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Создание и использование значений свойств (многомерные выражения)](http://msdn.microsoft.com/library/0cafb269-03c8-4183-b6e9-220f071e4ef2)  
  
  
