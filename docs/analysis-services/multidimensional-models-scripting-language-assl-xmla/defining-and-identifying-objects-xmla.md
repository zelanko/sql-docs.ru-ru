---
title: Определение и идентификация объектов (XMLA) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7b3db6fdcd8d9e6bd604d310f8d7858a4a91180e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="defining-and-identifying-objects-xmla"></a>Определение и идентификация объектов (XMLA)
  В командах XML для аналитики (XMLA) объекты указываются при помощи идентификаторов и ссылок на объекты, а определяются при помощи элементов языка ASSL команд XMLA.  
  
## <a name="object-identifiers"></a>Идентификаторы объектов  
 Объект определяется с помощью уникальный идентификатор объекта, как определено в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Идентификаторы объектов могут быть либо указаны явным образом, либо определены экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при создании этого объекта службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Можно использовать [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) метод для получения идентификаторов объектов для последующих **Discover** или [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) вызовы методов.  
  
## <a name="object-references"></a>Ссылки на объекты  
 Несколько команд XML для Аналитики, таких как [удалить](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md) или [процесс](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), используйте ссылку на объект для ссылки на объект однозначным способом. Ссылка содержит идентификатор объекта, для которого выполняется команда, а также идентификаторы объектов-предков этого объекта. Например, для секции ссылка на объект содержит идентификатор объекта секции, а также идентификаторы объектов родительских группы мер, куба и базы данных этой секции.  
  
## <a name="object-definitions"></a>Определения объектов  
 [Создать](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) и [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) XML для Аналитики команды создания или изменения, соответственно, объектов на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра. Определения этих объектов представлены [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) элемент, который содержит элементы из языка ASSL. Идентификаторы объектов могут быть явно указано для всех основных и многих второстепенных объектов с помощью [идентификатор](../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md) элемента. Если **идентификатор** элемент не используется, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляр предоставляет уникальный идентификатор, соглашение об именах, от которого зависит объект для идентификации. Дополнительные сведения об использовании **создать** и **Alter** команды для определения объектов, в разделе [Создание и изменение объектов &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/creating-and-altering-objects-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент Object & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Элемент ParentObject &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)   
 [Элемент Source &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [Целевой элемент & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
