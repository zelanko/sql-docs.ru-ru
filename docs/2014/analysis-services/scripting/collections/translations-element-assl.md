---
title: Элемент Translations (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Translations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Translations
helpviewer_keywords:
- Translations element
ms.assetid: 7f6b8ff2-e834-44d3-a176-216203158a8d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7ea3c98e2263b78f947d75c5b225d2a3a63ef40
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061234"
---
# <a name="translations-element-assl"></a>Элемент Translations (ASSL)
  Содержит коллекцию элементов [перевода](../objects/translation-element-assl.md) элементы, связанные с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action><!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Translations>  
      <Translation>...</Translation>  
      <!-- or -->  
      <Translation xsi:type="AttributeTranslation">...</Translation><!-- parent: DimensionAttribute or ScalarMiningStructureColumn -->  
      <!-- or -->  
      <Translation xsi:type="RelationshipEndTranslation">...</Translation><!-- parent: RelationshipEnd -->  
   </Translations>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Действие](../objects/action-element-assl.md), [AttributeRelationship](../objects/attributerelationship-element-assl.md), [CalculationProperty](../objects/calculationproperty-element-assl.md), [куба](../objects/cube-element-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [ База данных](../objects/database-element-assl.md), [измерения](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [иерархии](../objects/hierarchy-element-assl.md), [ключевого показателя эффективности](../objects/kpi-element-assl.md), [ Уровень](../objects/level-element-assl.md), [мер](../objects/measure-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [Перспективы](../objects/perspective-element-assl.md), [RelationshipEnd](../data-type/relationshipend-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [TableMiningStructureColumn](../data-type/tableminingstructurecolumn-data-type-assl.md)|  
  
 **Дочерние элементы**  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) или [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|[Перевод](../objects/translation-element-assl.md) типа [AttributeTranslation](../data-type/translation-data-type-assl.md)|  
|[RelationshipEnd](../data-type/relationshipendtranslation-element-assl.md) типа [RelationshipEndTranslation](../data-type/relationshipendtranslation-element-assl.md)|  
|Все остальные|[Перевод](../objects/translation-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующие элементы в модели объектов AMO — это <xref:Microsoft.AnalysisServices.TranslationCollection> и <xref:Microsoft.AnalysisServices.AttributeTranslationCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
