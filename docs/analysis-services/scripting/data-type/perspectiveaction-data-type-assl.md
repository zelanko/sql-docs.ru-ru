---
title: "Тип данных PerspectiveAction (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
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
apiname: PerspectiveAction Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PerspectiveAction
helpviewer_keywords: PerspectiveAction data type
ms.assetid: a0e4a545-688c-4d4e-b05f-0008d3503349
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9a01dec71914a33419c68888f06ff363e2d99b96
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="perspectiveaction-data-type-assl"></a>Тип данных PerspectiveAction (ASSL)
  Определяет тип-примитив, представляющий сведения о действии в [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID>  
   <Annotations>...</Annotations>  
</PerspectiveAction>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[ActionID](../../../analysis-services/scripting/properties/actionid-element-assl.md), [заметок](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Производные элементы|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md) ([действия](../../../analysis-services/scripting/collections/actions-element-assl.md) коллекцию [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.PerspectiveAction>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
