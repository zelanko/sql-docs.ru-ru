---
title: "Элемент SourceColumnID (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: SourceColumnID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SourceColumnID
helpviewer_keywords: SourceColumnID element
ms.assetid: 715c0be7-aa07-4dff-a909-9738224941ec
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 37bc05f9fb5d44261f5d0eb51fba7581e2f2f979
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sourcecolumnid-element-assl"></a>Элемент SourceColumnID (ASSL)
  Содержит идентификатор (ID) исходного столбца структуры интеллектуального анализа данных в родительском элементе [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <SourceColumnID>...</SourceColumnID>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение **SourceColumnID** совпадает с идентификатором столбца структуры интеллектуального анализа данных в [столбцы](../../../analysis-services/scripting/collections/columns-element-assl.md) коллекции родительского объекта **MiningStructure**.  
  
 Элемент, соответствующий родителю параметра **SourceColumnID** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningModelColumn>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
