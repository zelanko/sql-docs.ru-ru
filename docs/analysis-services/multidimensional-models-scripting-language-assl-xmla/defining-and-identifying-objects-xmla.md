---
title: "Определение и идентификация объектов (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d2d39b5057dd00d310c1d4f5581228ed6ae27ea0
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="defining-and-identifying-objects-xmla"></a>Определение и идентификация объектов (XMLA)
  В командах XML для аналитики (XMLA) объекты указываются при помощи идентификаторов и ссылок на объекты, а определяются при помощи элементов языка ASSL команд XMLA.  
  
## <a name="object-identifiers"></a>Идентификаторы объектов  
 Объект определяется с помощью уникальный идентификатор объекта, как определено в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Идентификаторы объектов могут быть либо указаны явным образом, либо определены экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при создании этого объекта службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Можно использовать [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) метод для получения идентификаторов объектов для последующих **Discover** или [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) вызовы методов.  
  
## <a name="object-references"></a>Ссылки на объекты  
 Несколько команд XML для Аналитики, таких как [удалить](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md) или [процесс](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), используйте ссылку на объект для ссылки на объект однозначным способом. Ссылка содержит идентификатор объекта, для которого выполняется команда, а также идентификаторы объектов-предков этого объекта. Например, для секции ссылка на объект содержит идентификатор объекта секции, а также идентификаторы объектов родительских группы мер, куба и базы данных этой секции.  
  
## <a name="object-definitions"></a>Определения объектов  
 [Создать](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) и [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) XML для Аналитики команды создания или изменения, соответственно, объектов на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра. Определения этих объектов представлены [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) элемент, который содержит элементы из языка ASSL. Идентификаторы объектов могут быть явно указано для всех основных и многих второстепенных объектов с помощью [идентификатор](../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md) элемента. Если **идентификатор** элемент не используется, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр предоставляет уникальный идентификатор, соглашение об именах, от которого зависит объект для идентификации. Дополнительные сведения об использовании **создать** и **Alter** команды для определения объектов, в разделе [&#40; Создание и изменение объектов XML для Аналитики &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Object &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Элемент ParentObject &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Исходный элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [Целевой элемент &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
