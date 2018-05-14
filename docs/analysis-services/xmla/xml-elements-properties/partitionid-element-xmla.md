---
title: Элемент PartitionID (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5b6d52e6347ee4f0a864d0ada84ae9971f1b54e3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="partitionid-element-xmla"></a>Элемент PartitionID (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Обозначает секцию в родительском элементе, которая содержит ссылку на объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <PartitionID>...</PartitionID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|См. таблицу ниже.|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md), [Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|Все остальные|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md), [Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md), [Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
