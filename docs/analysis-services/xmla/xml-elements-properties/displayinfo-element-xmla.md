---
title: "Элемент DisplayInfo (XML для Аналитики) | Документы Microsoft"
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
apiname: DisplayInfo Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.displayinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#DisplayInfo
- urn:schemas-microsoft-com:xml-analysis#DisplayInfo
helpviewer_keywords: DisplayInfo element
ms.assetid: 059ce038-38de-4c7d-a72f-4f919cfc7c4a
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9b9539d20fa1d6f6f27f5277d665717d826c15d6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="displayinfo-element-xmla"></a>Элемент DisplayInfo (XML для аналитики)
  Содержит сведения об отображении для родительского элемента [HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md) или [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <DisplayInfo>...</DisplayInfo>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|unsignedInt|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md), [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент **DisplayInfo** содержит различные сведения, которые помогают клиентскому приложению подготовить к просмотру родительский элемент **HierarchyInfo** или **Member** . Значение эквивалентно свойству DISPLAY_INFO, определенному для набора строк осей в OLE DB для спецификации OLAP.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
