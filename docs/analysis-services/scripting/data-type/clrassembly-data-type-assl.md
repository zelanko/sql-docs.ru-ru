---
title: Тип данных ClrAssembly (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
ms.openlocfilehash: d5529e5782ecfb50479437a1c5d405d7567501bc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="clrassembly-data-type-assl"></a>Тип данных ClrAssembly (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет производный тип данных, представляющий сборку [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] , связанную с элементом [Database](../../../analysis-services/scripting/objects/database-element-assl.md) или [Server](../../../analysis-services/scripting/objects/server-element-assl.md) .  
  
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
|Дочерние элементы|[Files](../../../analysis-services/scripting/collections/files-element-assl.md), [PermissionSet](../../../analysis-services/scripting/properties/permissionset-element-assl.md)|  
|Производные элементы|См. [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) (коллекция[Assemblies](../../../analysis-services/scripting/collections/assemblies-element-assl.md) элементов [Database](../../../analysis-services/scripting/objects/database-element-assl.md) или [Server](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 **ClrAssembly** элемент содержит файлы, необходимые для повторного создания [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] сборки, связанной с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] или с конкретной базой данных экземпляра [!INCLUDE[ssAS](../../../includes/ssas-md.md)], а также разрешения, необходимые для выполнения этой сборки.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ClrAssembly>.  
  
## <a name="see-also"></a>См. также  
 [Элемент файла & #40; ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [Тип данных ClrAssemblyFile & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [Элемент данных & #40; ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [Тип данных DataBlock & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Элемент Blocks & #40; ASSL & #41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Блокировать элемент & #40; ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [Тип данных ComAssembly & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
