---
title: Элемент AxesInfo (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AxesInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxesInfo
- microsoft.xml.analysis.axesinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxesInfo
helpviewer_keywords:
- AxesInfo element
ms.assetid: 15cfa67d-5acd-4737-8a81-2df34b334d3f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bde7feb88ad570665200c1c3357bbba4127a963
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178494"
---
# <a name="axesinfo-element-xmla"></a>Элемент AxesInfo (XML для аналитики)
  Содержит коллекцию [AxisInfo](axisinfo-element-xmla.md) элементов, представляющих метаданные оси, которые содержатся в родительском [OlapInfo](olapinfo-element-xmla.md) элемент.  
  
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
|Родительские элементы|[OlapInfo](olapinfo-element-xmla.md)|  
|Дочерние элементы|[AxisInfo](axisinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `AxesInfo` содержит по одному элементу `AxisInfo` для каждой оси в многомерном наборе данных, возвращаемом элементом `root` с использованием типа данных `MDDataSet`.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
