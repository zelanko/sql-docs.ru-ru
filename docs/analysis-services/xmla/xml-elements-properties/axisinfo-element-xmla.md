---
title: "Элемент AxisInfo (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AxisInfo Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxisInfo
- microsoft.xml.analysis.axisinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxisInfo
helpviewer_keywords:
- AxisInfo element
ms.assetid: 060741db-b2ec-4174-9277-58d996440a88
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa8b5554573ebb3f34212fd7ba48b6583fb926af
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="axisinfo-element-xmla"></a>Элемент AxisInfo (XML для аналитики)
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
  
## <a name="remarks"></a>Замечания  
 В **корневой** элемент, который использует **MDDataSet** объекта, **AxisInfo** элемент содержит коллекцию **HierarchyInfo** элементов, , в сочетании со значением **имя** атрибут представляет определение одной оси, возвращаемых в многомерном наборе данных.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
