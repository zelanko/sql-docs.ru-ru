---
title: Тип данных PerspectiveMeasureGroup (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
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
- PerspectiveMeasureGroup Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- PerspectiveMeasureGroup
helpviewer_keywords:
- PerspectiveMeasureGroup data type
ms.assetid: 5927120d-f30e-4f87-8523-6d17012817d7
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ad2ff813a39fca0f8c0db50710035c74d328835e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="perspectivemeasuregroup-data-type-assl"></a>Тип данных PerspectiveMeasureGroup (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет примитивный тип данных, представляющий сведения о группе мер в элементе [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<PerspectiveMeasureGroup>  
   <MeasureGroupID>...</MeasureGroupID>  
   <Measures>...</Measures>  
   <Annotations>...</Annotations>  
</PerspectiveMeasureGroup>  
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
|Дочерние элементы|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [MeasureGroupID](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md), [Measures](../../../analysis-services/scripting/collections/measures-element-assl.md)|  
|Производные элементы|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) (коллекция[MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md) элемента [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Замечания  
 Структура группы мер в перспективе совпадает со структурой группы мер в базовом кубе.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
