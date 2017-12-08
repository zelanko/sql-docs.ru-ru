---
title: "Элемент CaptionColumn (ASSL) | Документы Microsoft"
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
apiname: CaptionColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: CaptionColumn
helpviewer_keywords: CaptionColumn element
ms.assetid: bdb1b9b8-b5d5-4d91-81c7-8de8635bbb83
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 10da909705f2348c401451375a8e889c5d26bebf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="captioncolumn-element-assl"></a>Элемент CaptionColumn (ASSL)
  Определяет столбец с заголовком атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<AttributeTranslation>  
   ...  
   <CaptionColumn xsi:type="DataItem">...</CaptionColumn>  
   ...  
</AttributeTranslation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о **DataItem** типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) и свойства **DataItem** введите см. в разделе [DataItem, тип данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Элемент, соответствующий родителю параметра **CaptionColumn** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AttributeTranslation>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
