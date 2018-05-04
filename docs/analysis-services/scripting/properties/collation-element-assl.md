---
title: Элемент collation (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Collation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Collation
helpviewer_keywords:
- Collation element
ms.assetid: 9b6dbe19-543e-43e6-abe9-1e8b4dfaa275
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 83223ec3e2f024e9f9d8ab6b0debd3a401aa79b2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="collation-element-assl"></a>Элемент Collation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Задает параметры сортировки, применяемые в родительском элементе.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Database> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Collation>...</Collation>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../../../analysis-services/scripting/objects/cube-element-assl.md), [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md), [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md), [измерения](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Строка **Collation** состоит из идентификатора локали и флага сравнения, разделенных символом подчеркивания. Например, строка Latin1_General_CI_AS является допустимой.  
  
 Элементы, соответствующие родителям элемента **сортировки** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataItem>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MiningModel>и <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
