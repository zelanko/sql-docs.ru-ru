---
title: Прочитать элемент (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Read Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Read element
ms.assetid: 2e2c1173-72ca-4e8a-a6cd-fd348ef96d78
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f950d35e74a64b75ec239c7d35ba31660ec8f08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157384"
---
# <a name="read-element-assl"></a>Элемент Read (ASSL)
  Определяет, можно ли читать данные или метаданные для заданного [CubeDimensionPermission](../data-type/permission-data-type-assl.md) или [разрешение](../data-type/permission-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
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
|Родительские элементы|[CubeDimensionPermission](../objects/cubepermission-element-assl.md), [разрешение](../data-type/permission-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*None*|Из родительского объекта запрещен доступ к данным и метаданным.|  
|*Разрешено*|Доступ для чтения разрешен к данным и метаданным из родительского объекта.|  
  
## <a name="remarks"></a>Примечания  
 Элементы, соответствующие родителям элемента `Read` в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.CubeDimensionPermission> и <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>См. также  
 [Элемент куба &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Элемент измерения &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Элемент CubePermission &#40;ASSL&#41;](../objects/cubepermission-element-assl.md)   
 [Тип данных Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
