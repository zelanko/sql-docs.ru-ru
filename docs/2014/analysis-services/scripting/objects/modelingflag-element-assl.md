---
title: Элемент ModelingFlag (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ModelingFlag Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ModelingFlag
helpviewer_keywords:
- ModelingFlag element
ms.assetid: c9af1b9a-506f-4cc1-acd7-e57698cb672c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8137da94a03e560fbed2c263e8e0a10b187fa569
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118134"
---
# <a name="modelingflag-element-assl"></a>Элемент ModelingFlag (ASSL)
  Содержит флаг моделирования для столбца в структуре или модели интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ModelingFlags>  
   <ModelingFlag xsi:type="MiningModelingFlag">...</ModelingFlag>  
</ModelingFlags>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[MiningModelingFlag](../data-type/miningmodelingflag-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ModelingFlags](../collections/modelingflags-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Тесно связанный элемент в объектной модели AMO — это <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>См. также  
 [Элемент MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Элемент MiningStructure &#40;ASSL&#41;](miningstructure-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
