---
title: "Куб элемент (OlapInfo) (XMLA) | Документы Microsoft"
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
apiname: Cube Element (OlapInfo)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cube
- urn:schemas-microsoft-com:xml-analysis#Cube
- http://schemas.microsoft.com/analysisservices/2003/engine#Cube
helpviewer_keywords: Cube element
ms.assetid: c2b6fe41-6ad4-4181-98a9-3a2517f0b7cc
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7be9f0e7dbcdddc853debf2536d97ac9de0c25ce
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="cube-element-olapinfo-xmla"></a>Элемент Cube (OlapInfo) (XMLA)
  Содержит сведения о кубе для родительского [CubeInfo](../../../analysis-services/xmla/xml-elements-properties/cubeinfo-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeInfo>  
   <Cube>  
      <CubeName>...</CubeName>  
      <LastDataUpdate>...</LastDataUpdate>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
   </Cube>  
   ...  
</CubeInfo>  
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
|Родительские элементы|[CubeInfo](../../../analysis-services/xmla/xml-elements-properties/cubeinfo-element-xmla.md)|  
|Дочерние элементы|[Имя куба](../../../analysis-services/xmla/xml-elements-properties/cubename-element-xmla.md), [LastDataUpdate](../../../analysis-services/xmla/xml-elements-properties/lastdataupdate-element-xmla.md), [LastSchemaUpdate](../../../analysis-services/xmla/xml-elements-properties/lastschemaupdate-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
