---
title: "Элемент MoveWithDescendants (XML для Аналитики) | Документы Microsoft"
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
apiname: MoveWithDescendants Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.movewithdescendants
- http://schemas.microsoft.com/analysisservices/2003/engine#MoveWithDescendants
- urn:schemas-microsoft-com:xml-analysis#MoveWithDescendants
helpviewer_keywords: MoveWithDescendants element
ms.assetid: d02285b6-1801-4da9-8e2b-9ab008e25558
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 61514f1cd5cb7371f92f5f763d3f1236fc955e0d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="movewithdescendants-element-xmla"></a>Элемент MoveWithDescendants (XML для аналитики)
  Указывает, является ли потомки элементов атрибутов обновляются в родительском [обновление](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Update>  
   ...  
   <MoveWithDescendants>...</MoveWithDescendants>  
   ...  
</Update>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Boolean|  
|Значение по умолчанию|False|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **MoveWithDescendants** определяет ли **обновление** команды должен обновлять не только элементы атрибутов, определенных в [атрибуты](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md) элемент, но Кроме того, должны также обновить потомки этих элементов атрибутов.  
  
> [!NOTE]  
>  Этот элемент применяется только к элементам атрибутов в иерархиях родителей-потомков.  
  
 Дополнительные сведения об обновлении элементов см. в разделе [Вставка, обновление и удаление элементов &#40; XML для Аналитики &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
