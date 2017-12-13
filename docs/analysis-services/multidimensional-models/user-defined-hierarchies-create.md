---
title: "Создание определяемых пользователем иерархий | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a188eb62eb80e23ef5f20bc054653891958377f6
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="user-defined-hierarchies---create"></a>Создание определяемых пользователем иерархий-
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] позволяет создавать пользовательские иерархии. Иерархия — это набор уровней на основе атрибутов. Например, иерархия, связанная со временем, может содержать такие уровни, как «Год», «Месяц» и «День». В некоторых иерархиях каждый атрибут однозначно задает атрибут родительского элемента. Такую иерархию иногда называют естественной. Конечные пользователи могут использовать иерархии для просмотра данных в кубе. Иерархии задаются с помощью панели «Иерархии» конструктора измерений в среде разработки [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Вновь созданная пользовательская иерархия может оказаться *неровной*. Неровная иерархия — это иерархия, в которой по крайней мере у одного элемента логический родительский элемент не находится ровно на один уровень выше самого элемента. Существуют настройки, управляющие видимостью недостающих элементов в неровных иерархиях и способом их отображения. Дополнительные сведения об иерархиях см. в разделе [Неоднородные иерархии](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Дополнительные сведения о проблемах производительности, связанных с конструированием и настройкой пользовательских иерархий, см. в [руководстве по производительности служб SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="see-also"></a>См. также  
 [Свойства пользовательской иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Свойства уровня - пользовательских иерархий](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Родитель потомок измерения](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  
