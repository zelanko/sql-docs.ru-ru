---
title: "Элемент StorageLocation (ASSL) | Документы Microsoft"
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
apiname: StorageLocation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: StorageLocation
helpviewer_keywords: StorageLocation element
ms.assetid: ecf8852f-56a1-4fcf-b0d8-d7eebb75e4ed
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f29d736c11dd7297d024bc9e6f72c93a521e84ff
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="storagelocation-element-assl"></a>Элемент StorageLocation (ASSL)
  Содержит расположение места хранения в файловой системе для содержимого родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube><!-- or MeasureGroup, Partition -->  
      ...  
   <StorageLocation>...</StorageLocation>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|См. в следующей таблице.|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
|Предок или родитель|Значение по умолчанию|  
|------------------------|-------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|Нет|  
|[Группа мер](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|Значение элемента **StorageLocation** из родительского элемента **Cube** .|  
|[Секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|Значение элемента **StorageLocation** из родительского элемента **MeasureGroup** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../../../analysis-services/scripting/objects/cube-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [секции](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элементы, соответствующие родителям элемента **StorageLocation** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MeasureGroup>, и <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
