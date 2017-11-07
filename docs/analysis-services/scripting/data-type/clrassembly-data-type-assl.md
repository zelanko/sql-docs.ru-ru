---
title: "Тип данных ClrAssembly (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ClrAssembly Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ClrAssembly
helpviewer_keywords:
- ClrAssembly data type
ms.assetid: 3f5dc5a1-ebd6-41b8-ac04-91d4de137eb4
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f120b0476b1615db1be21387c641d370cf72f8fa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="clrassembly-data-type-assl"></a>Тип данных ClrAssembly (ASSL)
  Определяет производный тип данных, представляющий [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборку, связанную с [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) или [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемент  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ClrAssembly>  
      <!-- The following elements extend Assembly -->  
   <Files>...</Files>  
      <PermissionSet>...</PermissionSet>  
</ClrAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Сборки](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|Нет (абстрактный тип)|  
|Дочерние элементы|[Файлы](../../../analysis-services/scripting/collections/files-element-assl.md), [PermissionSet](../../../analysis-services/scripting/properties/permissionset-element-assl.md)|  
|Производные элементы|В разделе [сборки](../../../analysis-services/scripting/objects/assembly-element-assl.md) ([сборки](../../../analysis-services/scripting/collections/assemblies-element-assl.md) коллекцию [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) или [сервера](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 **ClrAssembly** элемент содержит файлы, необходимые для повторного создания [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборки, связанной с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или с конкретной базой данных экземпляра [!INCLUDE[ssAS](../../../includes/ssas-md.md)], а также разрешения, необходимые для выполнения этой сборки.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент файла &#40; ASSL &#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Тип данных ClrAssemblyFile &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Элемент данных &#40; ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Тип данных DataBlock &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Элемент Blocks &#40; ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Блокировать элемент &#40; ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Тип данных ComAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

