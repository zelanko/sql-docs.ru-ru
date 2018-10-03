---
title: Элемент DefaultDetailsPosition (XML) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 851ad331-aefd-4277-a5e5-e32a8f5c5e22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95e8f7cecdd76ceb934f2c1d9d9483d8146e8e0d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083414"
---
# <a name="defaultdetailsposition-element-xml"></a>Элемент DefaultDetailsPosition (XML)
  Содержит сведения о позиции элемента в коллекции элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <DefaultDetailsPosition>...</DefaultDetailsPosition>  
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
 Для элементов `RelationshipEndVisualizationProperties` элемент `DefaultDetailsPosition` содержит положение элемента сведений по умолчанию в коллекции сведений. Значение по умолчанию, равное `false`, указывает, что свойства по умолчанию не используются.  
  
  
