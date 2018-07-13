---
title: Элемент ReadSourceData (ASSL) | Документация Майкрософт
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38e24d324a6f29b55cfb8bf0b55289e2139bfb85
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194194"
---
# <a name="readsourcedata-element-assl"></a>Элемент ReadSourceData (ASSL)
  Определяет, как уникальные имена создаются для иерархий, содержащихся в [CubePermission](../objects/cubepermission-element-assl.md).  
  
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
|*Разрешено*|На этапе вычисления 0 доступ к имеющимся данным открыт.|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `ReadSourceData` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент куба &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Элемент измерения &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
