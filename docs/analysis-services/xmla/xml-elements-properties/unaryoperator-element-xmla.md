---
title: Элемент UnaryOperator (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
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
- UnaryOperator Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#UnaryOperator
- urn:schemas-microsoft-com:xml-analysis#UnaryOperator
- microsoft.xml.analysis.unaryoperator
helpviewer_keywords:
- UnaryOperator element
ms.assetid: 4dc9cfbe-6f8b-42bc-8d3a-42f48ca5d299
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9b463e13434bff72ef9886decd7c5cc4501c3c5f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="unaryoperator-element-xmla"></a>Элемент UnaryOperator (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит унарный оператор для элемента атрибута, представленного родительским элементом [Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute>  
   ...  
   <UnaryOperator>...</UnaryOperator>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Атрибут](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент **UnaryOperator** содержит многомерное выражение, определяющее унарный оператор для элемента атрибута, определенного родительским элементом **Attribute** .  
  
 Дополнительные сведения о Многомерных выражениях см. в разделе [выражения & #40; Многомерные Выражения & #41; ](../../../mdx/expressions-mdx.md).  
  
## <a name="see-also"></a>См. также:  
 [Вставить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Обновить элемент & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
