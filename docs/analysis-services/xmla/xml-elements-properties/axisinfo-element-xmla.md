---
title: Элемент AxisInfo (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 858cb8be01a16d9ccb7d6455043d370865f1c3e6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="axisinfo-element-xmla"></a>Элемент AxisInfo (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Представляет метаданные одной оси, содержащейся в родительском [AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AxesInfo>  
   ...  
   <AxisInfo name="string">  
      <HierarchyInfo>...</HierarchyInfo>  
   </AxisInfo>  
   ...  
</AxesInfo>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md)|  
|Дочерние элементы|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Description|  
|---------------|-----------------|  
|Название|Обязательный атрибут типа **String** . Имя оси.|  
  
## <a name="remarks"></a>Примечания  
 В **корневой** элемент, который использует **MDDataSet** объекта, **AxisInfo** элемент содержит коллекцию **HierarchyInfo** элементов, , в сочетании со значением **имя** атрибут представляет определение одной оси, возвращаемых в многомерном наборе данных.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
