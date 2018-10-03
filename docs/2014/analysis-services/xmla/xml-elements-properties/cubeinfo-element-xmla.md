---
title: Элемент CubeInfo (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CubeInfo
- microsoft.xml.analysis.cubeinfo
- urn:schemas-microsoft-com:xml-analysis#CubeInfo
helpviewer_keywords:
- CubeInfo element
ms.assetid: a504bac5-4bf2-4f78-a288-e74a34eaa97e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f58bcd7cbd15c767196e9efc2654e24aeacf94d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214644"
---
# <a name="cubeinfo-element-xmla"></a>Элемент CubeInfo (XML для аналитики)
  Содержит метаданные куба, содержащегося в родительском [OlapInfo](olapinfo-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<OlapInfo>  
   ...  
   <CubeInfo>  
      <Cube>...</Cube>  
   </CubeInfo>  
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
|Дочерние элементы|[Cube](cube-element-olapinfo-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `CubeInfo` содержит один элемент `Cube` для каждого куба, на который есть ссылка в многомерном наборе данных.  
  
> [!NOTE]  
>  Службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвращают только один элемент `Cube` в этой коллекции, поскольку в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживаются инструкции, ссылающиеся на несколько кубов в предложении FROM языка многомерных выражений.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
