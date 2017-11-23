---
title: "Файл элемента (ASSL) | Документы Microsoft"
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
apiname: File Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: File
helpviewer_keywords: File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a5d37a6ace9b56fe9bf5ae808c9a89bf49b6c568
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="file-element-assl"></a>Элемент File (ASSL)
  Определяет один из файлов, составляющих [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|Значение по умолчанию|None|  
|Количество элементов|1-N: обязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Файлы](../../../analysis-services/scripting/collections/files-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Элемент, соответствующий родителю параметра **файлы** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ClrAssemblyFile>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Server &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Элемент Database &#40; ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Элемент Assemblies &#40; ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Элемент Assembly &#40; ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [Тип данных ClrAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Элемент данных &#40; ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Тип данных DataBlock &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Элемент Blocks &#40; ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Блокировать элемент &#40; ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Тип данных ComAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
