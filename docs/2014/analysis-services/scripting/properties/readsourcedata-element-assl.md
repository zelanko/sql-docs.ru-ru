---
title: Элемент ReadSourceData (ASSL) | Документы Microsoft
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
- ReadSourceData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ReadSourceData element
ms.assetid: 7da4665a-fba3-4aae-8dee-678dc14d3b05
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dcbb6ce5b9cda3b17b69558cd60f6030f9e097b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188331"
---
# <a name="readsourcedata-element-assl"></a>Элемент ReadSourceData (ASSL)
  Определяет, каким образом уникальные имена формируются для иерархий, содержащихся в [CubePermission](../objects/cubepermission-element-assl.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubePermission>  
   ...  
   <ReadSourceData>...</ReadSourceData>  
   ...  
</CubePermission>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*None*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*None*|На этапе вычисления 0 не разрешается никакого доступа к имеющимся данным.|  
|*Допускается*|На этапе вычисления 0 доступ к имеющимся данным открыт.|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `ReadSourceData` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>См. также  
 [Куб элемент &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Элемент измерения &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  