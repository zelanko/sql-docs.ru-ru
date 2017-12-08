---
title: "Тип данных StandardAction (ASSL) | Документы Microsoft"
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
apiname: StandardAction Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: StandardAction
helpviewer_keywords: StandardAction data type
ms.assetid: 81b574d5-06c1-4587-8bd2-0e5c5e3b1d99
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 27f3ae41d9dd941e1fa372005ddbdcbc39534c24
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="standardaction-data-type-assl"></a>Тип данных StandardAction (ASSL)
  Определяет производный тип данных, представляющий любой [действия](../../../analysis-services/scripting/objects/action-element-assl.md) элементом, кроме [DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md) элемент или [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<StandardAction>  
   <!-- The following elements extend Action -->  
   <Expression>...</Expression>  
</StandardAction>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Действие](../../../analysis-services/scripting/data-type/action-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Выражение](../../../analysis-services/scripting/properties/expression-element-assl.md)|  
|Производные элементы|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md) ([действия](../../../analysis-services/scripting/collections/actions-element-assl.md) коллекцию [куба](../../../analysis-services/scripting/objects/cube-element-assl.md) или [перспективы](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>См. также:  
 [Службы Analysis Services сценариев типы данных XML в &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
