---
title: "Элемент Perspectives (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Perspectives Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Perspectives
helpviewer_keywords: Perspectives element
ms.assetid: d071acc3-469b-44f3-b724-423a48da2d41
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fd2b4fee77e2ada2dcda810a8055906ca2dc7bde
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="perspectives-element-assl"></a>Элемент Perspectives (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит коллекцию элементов [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элементы, связанные с [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube>  
   ...  
   <Perspectives>  
      <Perspective>...</Pespective>  
   </Perspectives>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|  
|Дочерние элементы|[Перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.PerspectiveCollection>.  
  
## <a name="see-also"></a>См. также:  
 [Коллекции &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
