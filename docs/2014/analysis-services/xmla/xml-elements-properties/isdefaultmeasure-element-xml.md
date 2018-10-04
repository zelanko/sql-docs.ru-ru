---
title: Элемент IsDefaultMeasure (XML) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 523cf3d7-9df0-4f9d-8486-9109de8d3cca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 110acfb559b36e8bae77ca8860d59ca8963aaf87
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058924"
---
# <a name="isdefaultmeasure-element-xml"></a>Элемент IsDefaultMeasure (XML)
  Указывает, что для этой сущности можно получить меру по умолчанию, перейдя по этой связи к другой таблице и получив элемент с атрибутом DefaultMeasure.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|false|  
|Количество элементов|0—1: необязательный элемент, который появляется только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элементов `RelationshipEndVisualizationProperties` элемент `IsDefaultMeasure` указывает, что для данной сущности можно получить меру по умолчанию, перейдя к другой стороне этой связи. Значение по умолчанию, равное `false`, указывает, что мера по умолчанию отсутствует и не может быть получена.  
  
  
