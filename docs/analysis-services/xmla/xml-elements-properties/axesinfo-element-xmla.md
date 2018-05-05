---
title: Элемент AxesInfo (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AxesInfo Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxesInfo
- microsoft.xml.analysis.axesinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxesInfo
helpviewer_keywords:
- AxesInfo element
ms.assetid: 15cfa67d-5acd-4737-8a81-2df34b334d3f
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0be066b5ba129e82998efc1b87a3a16191957f42
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="axesinfo-element-xmla"></a>Элемент AxesInfo (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию [AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md) элементов, представляющих метаданные оси, которые содержатся в родительском [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<OlapInfo>  
   ...  
   <AxesInfo>  
      <AxisInfo>...</AxisInfo>  
   </AxesInfo>  
   ...  
</OlapInfo>  
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
|Родительские элементы|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Дочерние элементы|[AxisInfo](../../../analysis-services/xmla/xml-elements-properties/axisinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 **AxesInfo** элемент содержит один **AxisInfo** элемент для каждой оси в многомерном наборе данных, возвращенных **корневой** элемента с помощью  **MDDataSet** тип данных.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
