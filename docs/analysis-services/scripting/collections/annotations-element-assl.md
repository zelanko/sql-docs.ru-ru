---
title: "Элемент Annotations (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
apiname: Annotations Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Annotations
helpviewer_keywords: Annotations element
ms.assetid: b2236075-6a48-470d-8182-b0de112e258a
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 56d48f46676f262002ecba58345359a5edd5289f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="annotations-element-assl"></a>Элемент Annotations (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит коллекцию элементов [заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md) элементы, связанные с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Account>  
<!-- or another object in the Analysis Services Scripting Language -->  
   ...  
   <Annotations>  
      <Annotation>...</Annotation>  
   </Annotations>  
   ...  
</Account>  
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
|Родительские элементы|Большинство объектов языка сценариев служб Analysis Services|  
|Дочерние элементы|[Заметки](../../../analysis-services/scripting/objects/annotation-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.AnnotationCollection>.  
  
  
