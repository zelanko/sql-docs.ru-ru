---
title: "Элемент LName (XML для Аналитики) | Документы Microsoft"
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
apiname: LName Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#LName
- http://schemas.microsoft.com/analysisservices/2003/engine#LName
- microsoft.xml.analysis.lname
helpviewer_keywords: LName element
ms.assetid: 2c8c2fa9-cb2d-44ea-b253-5e6ff61f1b66
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ec00014beadd5acf2f67efc5ab7952c97f984ca1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="lname-element-xmla"></a>Элемент LName (XML для аналитики)
  Содержит сведения об уникальных именах уровней для родительского [HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md) или [член](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LName>...</LName>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md), [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Для **HierarchyInfo** элементов, этот элемент содержит имя свойства, которое предоставляет уникальные имена для уровней иерархии. Значение эквивалентно свойству LEVEL_UNIQUE_NAME, определенному для наборов строк оси в спецификации OLE DB для OLAP.  
  
 Для **член** элементов, этот элемент содержит уникальное имя уровня в иерархии, содержащей элемент, представленного родительским **член** элемента.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
