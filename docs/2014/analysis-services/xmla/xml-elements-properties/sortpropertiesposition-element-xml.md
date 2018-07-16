---
title: Элемент SortPropertiesPosition (XML) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 68b040a7-ab16-46f5-8610-21db07df9181
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d74e5c7a0b276eb33ab5e721190b67c03bf65c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269480"
---
# <a name="sortpropertiesposition-element-xml"></a>Элемент SortPropertiesPosition (XML)
  Содержит сведения о позиции элемента в коллекции элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <SortPropertiesPosition>...</SortPropertiesPosition>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|-1|  
|Количество элементов|0—1: необязательный элемент, который появляется только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элементов `RelationshipEndVisualizationProperties` элемент `SortPropertiesPosition` содержит положение элемента свойств сортировки в коллекции сведений. Значение по умолчанию указывает, что свойства сортировки не должны использоваться.  
  
  
