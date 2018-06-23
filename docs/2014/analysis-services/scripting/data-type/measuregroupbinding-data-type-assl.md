---
title: Тип данных MeasureGroupBinding (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MeasureGroupBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupBinding
helpviewer_keywords:
- MeasureGroupBinding data type
ms.assetid: 47e83eec-e0bc-4118-9a0f-5bfdd6218297
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 12c54f8a61d75afd7689f19b2936bb6aefa3b4c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194585"
---
# <a name="measuregroupbinding-data-type-assl"></a>Тип данных MeasureGroupBinding (ASSL)
  Определяет производный тип данных, представляющий привязку к [MeasureGroup](../objects/group-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroupBinding>  
   <!-- The following elements extend Binding -->  
   <DataSourceID>...</DataSourceID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <Persistence>...</Persistence>  
   <RefreshPolicy>...</RefreshPolicy>  
   <RefreshInterval>...</RefreshInterval>  
   <Filter>...</Filter>  
</MeasureGroupBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[CubeID](../properties/id-element-assl.md), [DataSourceID](../properties/datasourceid-element-assl.md), [фильтра](../properties/filter-element-binding-assl.md), [MeasureGroupID](../properties/measuregroupid-element-assl.md), [сохраняемости](../properties/persistence-element-assl.md), [RefreshInterval ](../properties/refreshinterval-element-assl.md), [RefreshPolicy](../properties/refreshpolicy-element-assl.md)|  
|Производные элементы|В разделе [привязки](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL), типа привязки и иерархию наследования `Binding` типов, в разделе [тип привязки данных &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Обзор привязок данных в ASSL см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.MeasureGroupBinding>.  
  
## <a name="see-also"></a>См. также  
 [Службы Analysis Services сценариев типы данных XML в &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  