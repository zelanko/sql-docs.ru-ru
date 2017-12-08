---
title: "Элемент ClassifiedColumns (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ClassifiedColumns Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ClassifiedColumns
helpviewer_keywords: ClassifiedColumns element
ms.assetid: f16b4f51-c38d-4601-98b8-1497dbf12d02
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6af1a4057b4d8a927d6518035be71e7c424da4e0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="classifiedcolumns-element-assl"></a>Элемент ClassifiedColumns (ASSL)
  Содержит коллекцию связанных столбцов, классифицированных объектом [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructureColumn xsi:type="ScalarMiningStructureColumn">  
   ...  
   <ClassifiedColumns>  
      <ClassifiedColumnID>...</ClassifiedColumnID>  
   </ClassifiedColumns>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) типа[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|[ClassifiedColumnID](../../../analysis-services/scripting/properties/classifiedcolumnid-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **ClassifiedColumns** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также:  
 [Тип данных MiningStructureColumn &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)   
 [Элемент MiningStructure &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
