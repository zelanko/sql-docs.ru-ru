---
title: Элемент AttributeAllMemberName (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeAllMemberName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeAllMemberName
helpviewer_keywords:
- AttributeAllMemberName element
ms.assetid: 5ede46a7-d8b0-40be-98d7-b01047b27d2e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c5d601864d3ceef1af243f819de8d7ef8466e91
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218774"
---
# <a name="attributeallmembername-element-assl"></a>Элемент AttributeAllMemberName (ASSL)
  Содержит заголовок на языке по умолчанию для элемента «Все» измерения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Dimension>  
      ...  
   <AttributeAllMemberName>...</AttributeAllMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Dimension](../objects/dimension-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент, соответствующий родителю параметра `AttributeAllMemberName` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>См. также  
 [Настройка &#40;все&#41; уровне для иерархий атрибутов](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  
