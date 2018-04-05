---
title: Элемент AttributeName (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AttributeName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AttributeName
- http://schemas.microsoft.com/analysisservices/2003/engine#AttributeName
- microsoft.xml.analysis.attributename
helpviewer_keywords:
- AttributeName element
ms.assetid: 4dc8260b-522e-46d9-9bd8-22a5a0068982
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5eae4d3973b0729e1794c8f968762fa62392ae43
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="attributename-element-xmla"></a>Элемент AttributeName (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Содержит имя атрибута, представленного родительским [атрибут](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute>  
   ...  
   <AttributeName>...</AttributeName>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Удалить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Вставить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Обновить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Где элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
