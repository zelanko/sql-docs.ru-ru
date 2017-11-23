---
title: "Элемент ServerProperty (ASSL) | Документы Microsoft"
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
apiname: ServerProperty Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SERVERPROPERTY
helpviewer_keywords: ServerProperty element
ms.assetid: f152a1b5-0972-40d8-907f-f131c2a108bb
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: edf7c78a2486d7e09dfb8eeb437b1215bff50bc1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="serverproperty-element-assl"></a>Элемент ServerProperty (ASSL)
  Определяет свойство сервера, связанное с [сервера](../../../analysis-services/scripting/objects/server-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ServerProperties>  
   <ServerProperty>  
      <Name>...</Name>  
      <Value>...</Value>  
            <RequiresRestart>...</RequiresRestart>  
            <PendingValue>...</PendingValue>  
      <DefaultValue>...</DefaultValue>  
      <DisplayFlag>...</DisplayFlag>  
   </ServerProperty>  
</ServerProperties>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[ServerProperties](../../../analysis-services/scripting/collections/serverproperties-element-assl.md)|  
|Дочерние элементы|[Значение по умолчанию](../../../analysis-services/scripting/properties/defaultvalue-element-assl.md), [DisplayFlag](../../../analysis-services/scripting/properties/displayflag-element-assl.md), [имя](../../../analysis-services/scripting/properties/name-element-assl.md), [PendingValue](../../../analysis-services/scripting/properties/pendingvalue-element-assl.md), [RequiresRestart](../../../analysis-services/scripting/properties/requiresrestart-element-assl.md), [значение](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 **ServerProperty** элемент описывает данные и метаданные для свойства сервера, связанный с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В отличие от элементов, содержащихся в языке сценариев служб Analysis Services (ASSL), элемент **ServerProperty** для описания свойств сервера использует пары «имя-значение», а не явно поименованные свойства. Пары «имя-значение» обеспечивают гибкость применения и расширяемость.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Server &#40; ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
