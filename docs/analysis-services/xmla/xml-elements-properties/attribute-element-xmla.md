---
title: "Атрибут элемента (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Attribute Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Attribute
- microsoft.xml.analysis.attribute
- urn:schemas-microsoft-com:xml-analysis#Attribute
helpviewer_keywords: Attribute element
ms.assetid: 0df9cf44-dc5f-4234-8a5a-daac8aabc0d6
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1556d139665387068b10cd034b19c3246096100b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="attribute-element-xmla"></a>Элемент Attribute (XML для аналитики)
  Определяет или фильтрует элемент атрибута, на котором родительского [вставить](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [обновление](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), или [Drop](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) выполняет команду.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attributes>  
   ...  
   <Attribute>  
      <AttributeName>...</AttributeName>  
      <Keys>...</Keys>  
      <!-- The following elements are included only for attributes contained in the Attributes element of a parent Insert or Update command -->  
      <Name>...</Name>  
      <Translations>...</Translations>  
      <CustomRollup>...</CustomRollup>  
      <CustomRollupProperties>...</CustomRollupProperties>  
      <UnaryOperator>...</UnaryOperator>  
      <SkippedLevels>...</SkippedLevels>  
   </Attribute>  
   ...  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Атрибуты](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)|  
|Дочерние элементы|См. в следующей таблице.|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Удалить](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [где](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md), [ключей](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|[Вставить](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [обновления](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|[AttributeName](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md), [CustomRollup](../../../analysis-services/xmla/xml-elements-properties/customrollup-element-xmla.md), [CustomRollupProperties](../../../analysis-services/xmla/xml-elements-properties/customrollupproperties-element-xmla.md), [ключей](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md), [имя](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md), [ SkippedLevels](../../../analysis-services/xmla/xml-elements-properties/skippedlevels-element-xmla.md), [переводы](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md), [UnaryOperator](../../../analysis-services/xmla/xml-elements-properties/unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Элемент **Attribute** определяет элемент атрибута, который вставлен, обновлен или удален командой **Insert**, **Update**или **Drop** соответственно. Как эти команды могут работать только с одним элемент атрибута одновременно, [атрибуты](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md) коллекцию **вставить**, **обновление**, и **Drop**команды может содержать только один **атрибут** элемента. Однако коллекция **Attributes** элемента **Where** для команд **Drop** и **Update** может содержать более одного элемента **Attribute** , таким образом возможна фильтрация атрибутов для удаления или обновления в доступном для записи измерении.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)   
 [Измерения, доступные для записи](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
