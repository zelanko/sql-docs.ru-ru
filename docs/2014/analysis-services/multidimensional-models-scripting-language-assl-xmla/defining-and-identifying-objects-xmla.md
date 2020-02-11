---
title: Определение и идентификация объектов (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: ad6c8de47577eccd7797517c8080957d7afe1abd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727561"
---
# <a name="defining-and-identifying-objects-xmla"></a>Определение и идентификация объектов (XMLA)
  В командах XML для аналитики (XMLA) объекты указываются при помощи идентификаторов и ссылок на объекты, а определяются при помощи элементов языка ASSL команд XMLA.  
  
## <a name="object-identifiers"></a>Идентификаторы объектов  
 Объект определяется с помощью уникального идентификатора объекта, определенного в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Идентификаторы объектов могут быть либо указаны явным образом, либо определены экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при создании этого объекта службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Метод [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) можно использовать для получения идентификаторов объектов для последующего `Discover` или [выполнения](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) вызовов метода.  
  
## <a name="object-references"></a>Ссылки на объекты  
 Некоторые команды XMLA, такие как [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) или [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), используют ссылку на объект для ссылки на объект в однозначном виде. Ссылка содержит идентификатор объекта, для которого выполняется команда, а также идентификаторы объектов-предков этого объекта. Например, для секции ссылка на объект содержит идентификатор объекта секции, а также идентификаторы объектов родительских группы мер, куба и базы данных этой секции.  
  
## <a name="object-definitions"></a>Определения объектов  
 Команды [CREATE](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) и [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) в XMLA CREATE или ALTER, соответственно, объекты в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] экземпляре. Определения этих объектов представлены элементом [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) , содержащим элементы из ASSL. Идентификаторы объектов можно явно указать для всех основных и многих вспомогательных объектов с помощью элемента [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) . Если элемент `ID` не используется, то уникальный идентификатор предоставляется экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. При этом используется соглашение об именах, которое зависит от объекта, которому назначается идентификатор. Дополнительные сведения об использовании команд `Create` и `Alter` для определения объектов см. в разделе [Создание и изменение объектов &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
## <a name="see-also"></a>См. также:  
 [Объектный элемент &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Элемент ParentObject &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)   
 [Исходный элемент &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)   
 [Элемент Target &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
