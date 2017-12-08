---
title: "Элемент LastDataUpdate (XML для Аналитики) | Документы Microsoft"
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
apiname: LastDataUpdate Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.lastdataupdate
- http://schemas.microsoft.com/analysisservices/2003/engine#LastDataUpdate
- urn:schemas-microsoft-com:xml-analysis#LastDataUpdate
helpviewer_keywords: LastDataUpdate element
ms.assetid: 66e43b17-844f-4ec2-bd1d-35608e7b6524
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3eae9bd312c427f0d7f66498681c6ad94d2e1fed
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="lastdataupdate-element-xmla"></a>Элемент LastDataUpdate (XML для аналитики)
  Содержит дату и время последнего обновления данных в кубе, представленном родительским элементом [Cube](../../../analysis-services/xmla/xml-elements-properties/cube-element-olapinfo-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube>  
   ...  
   <LastDataUpdate>...</LastDataUpdate>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|dateTime|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Cube](../../../analysis-services/xmla/xml-elements-properties/cube-element-olapinfo-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
