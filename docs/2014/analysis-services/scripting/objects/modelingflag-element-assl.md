---
title: Элемент ModelingFlag (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 611a93a27e5f668c9b367eb35d5df9eb454743b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275440"
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
  
  
