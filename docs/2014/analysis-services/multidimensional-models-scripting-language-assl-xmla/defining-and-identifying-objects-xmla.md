---
title: Определение и идентификация объектов (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 595a792e515e862297389faccc324fff8727b8da
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147989"
---
# <a name="defining-and-identifying-objects-xmla"></a>Определение и идентификация объектов (XMLA)
  В командах XML для аналитики (XMLA) объекты указываются при помощи идентификаторов и ссылок на объекты, а определяются при помощи элементов языка ASSL команд XMLA.  
  
## <a name="object-identifiers"></a>Идентификаторы объектов  
 Объект определяется с помощью уникальный идентификатор объекта, как определено в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Идентификаторы объектов могут быть либо указаны явным образом, либо определены экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при создании этого объекта службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Можно использовать [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) метод позволяет получать идентификаторы объектов для последующих `Discover` или [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) вызовы методов.  
  
## <a name="object-references"></a>Ссылки на объекты  
 Несколько команд XML для Аналитики, такие как [удалить](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) или [процесс](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), используйте ссылку на объект для ссылки на объект однозначным образом. Ссылка содержит идентификатор объекта, для которого выполняется команда, а также идентификаторы объектов-предков этого объекта. Например, для секции ссылка на объект содержит идентификатор объекта секции, а также идентификаторы объектов родительских группы мер, куба и базы данных этой секции.  
  
## <a name="object-definitions"></a>Определения объектов  
 [Создать](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) и [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) XML для Аналитики команды создания или изменения, соответственно, объектов на [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляра. Определения этих объектов представлены [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) элемент, содержащий элементы из языка ASSL. Идентификаторы объектов могут быть явно указано для всех основных и многих второстепенных объектов с помощью [идентификатор](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) элемент. Если элемент `ID` не используется, то уникальный идентификатор предоставляется экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. При этом используется соглашение об именах, которое зависит от объекта, которому назначается идентификатор. Дополнительные сведения об использовании `Create` и `Alter` команды для определения объектов, см. в разделе [Создание и изменение объектов &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
## <a name="see-also"></a>См. также  
 [Объект элемента &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Элемент ParentObject &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Элемент Source &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [Элемент target &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
