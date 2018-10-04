---
title: Атрибут элемента (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Attribute Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Attribute
- microsoft.xml.analysis.attribute
- urn:schemas-microsoft-com:xml-analysis#Attribute
helpviewer_keywords:
- Attribute element
ms.assetid: 0df9cf44-dc5f-4234-8a5a-daac8aabc0d6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7baad7e154cda5ce52e67f08af46e7344f6af1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128214"
---
# <a name="attribute-element-xmla"></a>Элемент Attribute (XML для аналитики)
  Определяет или фильтрует элемент атрибута, на котором родительского [вставить](../xml-elements-commands/insert-element-xmla.md), [обновление](../xml-elements-commands/update-element-xmla.md), или [Drop](../xml-elements-commands/drop-element-xmla.md) выполняет команду.  
  
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
|Родительские элементы|[Атрибуты](attributes-element-xmla.md)|  
  
 **Дочерние элементы**  
  
|||  
|-|-|  
|**Предок или родитель**|**Дочерний элемент**|  
|[DROP](../xml-elements-commands/drop-element-xmla.md), [где](name-element-xmla.md), [ключи](keys-element-xmla.md)|  
|[Вставить](../xml-elements-commands/insert-element-xmla.md), [обновления](../xml-elements-commands/update-element-xmla.md)|[AttributeName](name-element-xmla.md), [CustomRollup](customrollup-element-xmla.md), [CustomRollupProperties](properties-element-xmla.md), [ключи](keys-element-xmla.md), [имя](name-element-xmla.md), [ SkippedLevels](skippedlevels-element-xmla.md), [переводы](translations-element-xmla.md), [UnaryOperator](unaryoperator-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 `Attribute` Элемент определяет элемент атрибута, который вставлен, обновлен или удален, соответственно, `Insert`, `Update`, или `Drop` команды. Так как эти команды могут работать только с одним элемент атрибута одновременно, [атрибуты](attributes-element-xmla.md) коллекцию `Insert`, `Update`, и `Drop` команды может содержать только один `Attribute` элемент. Однако коллекция `Attributes` элемента `Where` для команд `Drop` и `Update` может содержать более одного элемента `Attribute`, таким образом возможна фильтрация атрибутов для удаления или обновления в доступном для записи измерении.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)   
 [Измерения, доступные для записи](../../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
