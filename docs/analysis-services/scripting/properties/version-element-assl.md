---
title: "Элемент Version (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: Version Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Version
helpviewer_keywords: Version element
ms.assetid: fb26fe5d-de40-443b-a8bc-031c950552e6
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f1c70a88b761d3ff7c1b09315785bc3b6f4c5dde
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="version-element-assl"></a>Элемент Version (ASSL)
  Содержит номер версии только для чтения экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] представленный [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Server>  
      ...  
      <Version>...</Version>  
   ...  
</Server>  
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
|Родительский элемент|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 **Версии** описывает, какая версия [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] установлен.  
  
 Элемент, соответствующий родителю параметра **версии** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Server>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Edition &#40; ASSL &#41;](../../../analysis-services/scripting/properties/edition-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
